# RCC-Scripts

RCC-Scripts is a collection of Apple scripts and bash scripts to control various programs (primarily Spotify) on a Mac.  They are designed to be modular and be called directly from Companion or streamdeck.

## Installation

Either clone the repo or download and extract the zip file.

```bash
git clone --depth=1 https://github.com/zmcandee/RCC-Scripts.git
```

## Usage

Copy `spotify-prepost` and edit it to call functions in the `spotify` directory.  

### Example
```bash
# Launch Spotify and hide the window
./spotify/launch

# Set the volume to 0 so we can fade in gracefully
./spotify/volume 0

# Shuffle and repeat to play a random song from playlist
./spotify/repeat
./spotify/shuffle

# Start playing, skip ahead 5 seconds, and fade the volume to 100 over 3 seconds
./spotify/play spotify:playlist:6hcFyKwUzRjVgy8YTua9M8
./spotify/skipToSec 5
./spotify/fadeUp
```

### Commands
**Note:** `<xxx>` is a required parameter but `[xxxx=yyy]` indicates an optional parameter (xxxx) with default value of yyy when not provided.

#### launch
Launches Spotify if not already open and immediately hides the window.
```bash
./spotify/launch
```
#### fadeUp/fadeDown/volume
Controls the spotify apps volume fader either fading gently or by immediately jumping to the given volume (0-100).
```bash
./spotify/volume [volume=100]
./spotify/fadeUp [seconds=3] [volume=100]
./spotify/fadeDown [seconds=3] [volume=0]
```
**Note:** Fades do not return until the fade is complete so excessively long fades may cause Companion to time out

#### play
Plays the provided track/album/artist/playlist URI in Spotify optionally allows passing a second URI to define the context (ie <track URI> in [playlist URI] context will play the track then queue songs from the playlist).
```bash
./spotify/play <URI> [context URI]
```

#### pause
Pauses playback.
```bash
./spotify/pause
```

#### repeat/shuffle
Toggles the repeat or shuffle buttons.  By default they turn on when called but passing a `false` parameter disables them.
```bash
./spotify/repeat [enable=true]
./spotify/shuffle [enable=true] 
```
#### skipToSec
Skips a specified number of seconds into the current track.
```bash
./spotify/skipToSec [seconds=3]
```

## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.
