# Server Configurations

A quick and easy media server configuration for storage and consumption. I haven't used any of this for quite a while so it may
not work anymore, but it should be simple enough to update. Enjoy!

## Installation

Theoretically, you can just clone this repo:

`git clone https://github.com/novafacing/server_config`

Change all of the things in all of the `docker-compose.yml` and `.service` files that
look like `%SOME_SPECIFIC_OR_SENSITIVE_CONFIG_VALUE%` to your own values. Copy the files
from `services` into `/etc/systemd/system/`. Then for each you can, for example:

`sudo systemctl enable --now gitea`

And it should start right up! See below for what to set each of the root paths to.

## Layout

All services run in containers, and the `docker-compose.yml` files for all of them
live in `containers_censored`. Many (all?) of the containers mount local directories.

Here is how I had mine set up:

* `%YOUR_TZ_HERE%`: look yours up. `America/Chicago` or something.
* `%YOUR_CONFIGS_ROOT%`: /home/novafacing/volumes/ (mounted on a 512GB flash drive in my root partition)
* `%YOUR_STORAGE_ROOT%`: /home/novafacing/data/ (mounted on a 24TB redundant hard drive array)
* `%YOUR_VPN_CONFIGS_ROOT%`: /home/novafacing/vpn/ (just contains the openvpn config for your chosen vpn)

The various passwords and such should be as secure as you're okay with
possibly typing into a recovery prompt.

## Frontend

Frontend/Consumption services:

* Plex, for video content.
* Filerun, for photos.
* Gitea, for code.
* The Lounge, for chat.
  
## Backend

Backend/Collection services:

* Pihole, for network management.
* Transmission+OpenVPN, for torrent management.
* Jackett, Radarr, Sonarr, Readarr for aggregation.
* Unifi, for controlling my pesky access point.