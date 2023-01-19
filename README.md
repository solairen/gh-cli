### About:
* OS: Alpine Linux 3.17.1

This docker container contains:
* [GitHub CLI](https://cli.github.com/)

### Tag version
Check latest container tag [version](https://hub.docker.com/repository/docker/moleszek/ghcli/tags?page=1&ordering=last_updated) and change **<tag>** with proper tag version.

### How to build or download:
#### To build docker images from Dockerfile:
* docker build . -t {tagname}

#### Download from Docker repository:
* docker pull moleszek/ghcli:<tag>

### To run GHCLI Docker image directly:

Windows:

```PowerShell
docker run --rm -ti -e TOKEN=$env:GHTOKEN -v <pathToGitRepository>:/gh -v <pathToConfig>:/root/.config/gh/ -v <pathToSSH>:/root/.ssh/ moleszek/ghcli:<tag>
```

Linux:

```Bash
docker run --rm -ti -e TOKEN=$GHTOKEN -v <pathToGitRepository>:/gh -v <pathToConfig>:/root/.config/gh/ -v <pathToSSH>:/root/.ssh/ moleszek/ghcli:<tag>
```

#### Important
To run this docker image correctly those things should be made before run:
* TOKEN => GitHub token.
* pathToGitRepository => path to folder where .git is created.
* pathToConfig => path to folder where GitHub CLI config will be stored.
* pathToSSH => path to .ssh keys.


#### Additional info

Set alias to be able to use this docker image as `gh` for example:

* On windows open `$PROFILE`:

```PowerShell
function gh_cli {
    docker run --rm -ti -e TOKEN=$env:GHTOKEN -v <pathToGitRepository>:/gh -v <pathToConfig>:/root/.config/gh/ -v <pathToSSH>:/root/.ssh/ moleszek/ghcli:<tag>

Set-Alias -Name gh -Value gh_cli
}
```

Save and restart `$PROFILE`:

```PowerShell
. $PROFILE
```

* On linux open `~/.bashrc`:

```Bash
alias gh="docker run --rm -ti -e TOKEN=$GHTOKEN -v <pathToGitRepository>:/gh -v <pathToConfig>:/root/.config/gh/ -v <pathToSSH>:/root/.ssh/ moleszek/ghcli:<tag>"
```

Save and restart `.bashrc`:

```Bash
. ~/.bashrc
```
