# webm.py

Yet another bikeshed to encode WebM videos from CLI.

## Features

* Encodes input video to WebM container with VP9 and Opus
* Uses 2-pass encoding, has optional VP8/Vorbis and album art modes
* Fits output file to the size limit by default
* Allows to select video/audio streams and external audio track
* Can burn subtitles into the video
* Flexible set of options and ability to pass raw flags to FFmpeg
* [Interactive mode](#interactive-mode) to cut/crop input video with mpv

## Requirements

* [Python](https://www.python.org/downloads/) 2.7+ or 3.2+
* [FFmpeg](https://ffmpeg.org/download.html) 2+ compiled with libvpx and libopus
* [mpv](http://mpv.io/installation/) 0.17+ compiled with Lua support, *for interactive mode only*

## Installation

Just save <https://raw.githubusercontent.com/Kagami/webm.py/master/webm.py>

Optionally put it somewhere in your `PATH`:
```bash
[sudo] wget https://github.com/Kagami/webm.py/raw/master/webm.py -O /usr/local/bin/webm
[sudo] chmod +x /usr/local/bin/webm
```

Or with pip:
```bash
[sudo] pip install webm
```

## Usage

**NOTE:** Windows users may want to add Python executable to the `PATH`. See
[Setting environment variables](https://docs.python.org/3/using/windows.html#excursus-setting-environment-variables>)
for details. Otherwise just type the full path to your `python.exe` location
instead of `python`.

Use `webm` instead of `python webm.py` if you installed it with pip.

Show help:
```bash
python webm.py -h
```

Examples:
```bash
# Fit video to default limit
python webm.py -i in.mkv

# Fit video to 6 MiB
python webm.py -i in.mkv -l 6

# Set video bitrate to 600k
python webm.py -i in.mkv -vb 600

# Constrained quality
python webm.py -i in.mkv -crf 20

# Constant quality
python webm.py -i in.mkv -crf 20 -vb 0

# Encode with VP8 & Vorbis
python webm.py -i in.mkv -vp8

# Make album art video
python webm.py -cover -i pic.png -aa song.flac
```

### Interactive mode

Pass `-p` flag to interactively select cut frargment/crop area with mpv. Demo:

[![](https://i.imgur.com/JIogF33.png)](https://i.imgur.com/GjDWq3X.png)

Show help on interactive mode:
```bash
python webm.py -hi
```

## Windows, Python 2 and non-ASCII filenames

Unicode filenames won't work on Windows with Python 2 due to Python bugs. Use
Python 3 if you can but if not an option set `PYTHONIOENCODING` environment
variable to `utf-8` and run:

```bash
pip install subprocessww
```

## Related links

[webm.py wiki](https://github.com/Kagami/webm.py/wiki) contains some encoding tricks and links to documentation on WebM/VPx.

## License

webm.py is licensed under [CC0](COPYING).
