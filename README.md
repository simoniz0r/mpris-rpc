# mpris-rpc

A wrapper for [EasyRP](https://github.com/Pizzabelly/EasyRP) that tracks MPRIS playing status for Discord RPC.

# Usage

**Dependencies**: curl (used for downloading EasyRP on first run), playerctl, some player that supports MPRIS (mpv currently not supported as it didn't work in my tests).

Just run `mpris-rpc`, and it will automatically update your Discord RPC status when a new song starts playing, the player status changes, or if the player changes.  Run `mpris-rpc stop` to stop `mpris-rpc`.

On first run, `~/.local/share/mpris-rpc` will be created, and EasyRP will be downloaded to `~/.local/share/mpris-rpc`.  `mpris-rpc` runs in the background and gets the status of players that support MPRIS using `playerctl  metadata --ignore-player=mpv --format '{{playerName}}|{{lc(status)}}|{{artist}}|{{title}}|{{position}}|{{mpris:length}}`.  If the song name, player status, or player changes, `mpris-rpc` updates EasyRP's config file with the new information.
