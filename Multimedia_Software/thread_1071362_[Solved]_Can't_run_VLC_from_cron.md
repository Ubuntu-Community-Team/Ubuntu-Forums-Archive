---
title: "[Solved] Can't run VLC from cron"
date: 2009-02-16
forum: Multimedia Software
---

### Post by Regenpak on 2009-02-16
I want to record (file dump) an MPEG4 webcam stream (Linksys WVC54GCA) with VLC. If I run it from a console (tty4 in my case) I get:
```
$ vlc http://192.168.0.28/img/video.asf --demux=dump --demuxdump-file="/TEMP/cam.asf"
VLC media player 0.8.6e Janus
[00000289] skins2 interface error: Cannot open display
[00000289] skins2 interface error: cannot initialize OSFactory
Remote control interface initialized. Type `help' for help.
status change: ( new input: http://192.168.0.28/img/video.asf )
status change: ( audio volume: 256 )
status change: ( play state: 1 )
[00000298] demuxdump demuxer: dumping raw stream to file `/TEMP/cam.asf'
```
In my console it waits for input, and if I type "quit" it exits. Now I want to run it with cron, and I can't figure out how to tell VLC not to open a control interface, which it can't do when run with cron as the output (>/var/log/vlc.log) shows:
```
VLC media player 0.8.6e Janus
[00000289] skins2 interface error: Cannot open display
[00000289] skins2 interface error: cannot initialize OSFactory
Error: Unable to initialize gtk, is DISPLAY set properly?
```

Edit: I have to use "--rc-fake-tty". VLC now runs without a hitch from crontab (and doesn't start a remote control interface):
```
0 7 * * * vlc http://192.168.0.28/img/video.asf --demux=dump --demuxdump-file="/TEMP/cam.asf" --rc-fake-tty >/dev/null 2>&1
```

---

