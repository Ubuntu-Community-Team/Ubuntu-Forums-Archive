---
title: "mozplugger silent for Windows Media Audio"
date: 2009-05-24
forum: Multimedia Software
---

### Post by celem on 2009-05-24
FYI: Posted just to help anyone else struggling with this issue:

I couldn't get Windows streaming media to work with mozplugger/mplayer as distributed. To obtain more diagnostic data I compiled and installed from source with DEBUG on. I then reported the bug to mozilla's mozdev bugzilla. Then when I recompiled mozplugger without DEBUG and reinstalled, the Problem mysteriously went away. I can now play the audio track. Please note, however, that mozplugger as distributed in ubuntu 9.04 did not work which is why I went down this path in the first place.

```
I use Ubuntu 9.04 on an AMD64 machine. uname -a output is:
Linux ubu-squirrel 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux
mplayer version is 2:1.0~rc2-0ubuntu19+medibuntu1 (jaunty)

I am trying to figure out why mozplugger won't play a Windows Media streaming sound of type video/x-ms-asf that I can play directly from mplayer with the command: 
  mplayer http://live.wsqlradio.com/wsql

mozplugger attempts to play with:
  mplayer -really-quiet -nojoystick -nofs -zoom -vo xv,x11 -ao esd,alsa,oss,arts,null -osdlevel 0 -xy $width -wid $window "$file" </dev/null
but it looks like the fork fails with PID12755: NewStream() exiting process already running

I compliled mozplugger with the DEBUG option so that I could see what was happening. Admittedly, I don't understand why it fails. Can anyone help?


Partial output of mozdebug:
------------
PID12755: GetMIMEDescription
PID12755: do_read_config
PID12755: find_helper_file 'mozpluggerrc'
PID12755: READ_CONFIG(/home/ecomer/.netscape/mozpluggerrc)
PID12755: READ_CONFIG(/home/ecomer/.mozilla/mozpluggerrc)
PID12755: READ_CONFIG(/home/ecomer/.opera/mozpluggerrc)
PID12755: READ_CONFIG(/etc/mozpluggerrc)
PID12755: read_config
PID12755: ::: # Configure file for MozPlugger 1.12.1
PID12755: ::: # Version: April 16, 2009
...
PID12755: GET Plugin name
PID12755: GET Plugin description
PID12755: Initialize - API versions plugin=0.11 Browser=0.19
PID12755: Static Pool used=10831, free=54705
PID12755: NEW (application/x-mplayer2) - instance=0x2961450
PID12755: VAR_pluginspage=http://www.microsoft.com/Windows/MediaPlayer/
PID12755: VAR_type=application/x-mplayer2
PID12755: VAR_src=http://live.wsqlradio.com/wsql
PID12755: VAR_id=WMP1
PID12755: New finished
PID12755: GET Plugin 'needs XEmbed', returned false
PID12755: SetWindow() - instance=0x2961450
PID12755: GET Plugin value 15 not implemented
PID12755: GET Plugin value 11 not implemented
PID12755: SetWindow() - instance=0x2961450
PID12755: GET Plugin value 15 not implemented
PID12755: GET Plugin value 11 not implemented
PID12755: NewStream() - instance=0x2961450
PID12755: Mime type video/x-ms-asf
PID12755: Url is http://live.wsqlradio.com/wsql (seekable=0)
PID12755: Mismatching mimetype reported, originally was 'application/x-mplayer2' now 'video/x-ms-asf' for url http://live.wsqlradio.com/wsql
PID12755: find_command...
PID12755: -------------------------------------------
PID12755: Commands for this handle at (0x7ff6643c2d88):
PID12755: Checking 'video/mpeg' ?= 'video/x-ms-asf'
PID12755: Not Same
PID12755: Checking 'video/x-mpeg' ?= 'video/x-ms-asf'
PID12755: Not Same
PID12755: Checking 'video/x-mpeg2' ?= 'video/x-ms-asf'
PID12755: Not Same
PID12755: -------------------------------------------
PID12755: Commands for this handle at (0x7ff6643c3290):
PID12755: Checking 'video/mp4' ?= 'video/x-ms-asf'
PID12755: Not Same
PID12755: -------------------------------------------
PID12755: Commands for this handle at (0x7ff6643c3798):
PID12755: Checking 'video/msvideo' ?= 'video/x-ms-asf'
PID12755: Not Same
PID12755: Checking 'video/x-msvideo' ?= 'video/x-ms-asf'
PID12755: Not Same
PID12755: Checking 'video/fli' ?= 'video/x-ms-asf'
PID12755: Not Same
PID12755: Checking 'video/x-fli' ?= 'video/x-ms-asf'
PID12755: Not Same
PID12755: -------------------------------------------
PID12755: Commands for this handle at (0x7ff6643c3ca0):
PID12755: Checking 'application/x-mplayer2' ?= 'video/x-ms-asf'
PID12755: Not Same
PID12755: Checking 'video/x-ms-asf' ?= 'video/x-ms-asf'
PID12755: Same.
PID12755: Checking command: mplayer -really-quiet -nojoystick -nofs -zoom -vo xv,x11 -ao esd,alsa,oss,arts,null -osdlevel 0 -xy $width -wid $window -playlist "$file" </dev/null
PID12755: fmatch mismatch: url 'http://live.wsqlradio.com/wsql' doesnt have '%.asx'
PID12755: Checking command: mplayer -really-quiet -nojoystick -nofs -zoom -vo xv,x11 -ao esd,alsa,oss,arts,null -osdlevel 0 -playlist "$file" </dev/null
PID12755: Flag mismatch: mode different 20 != 40
PID12755: Checking command: mplayer -really-quiet -nojoystick -nofs -zoom -vo xv,x11 -ao esd,alsa,oss,arts,null -osdlevel 0 -xy $width -wid $window "$file" </dev/null
PID12755: Match found!
PID12755: Command found.
PID12755: NEW_CHILD(http://live.wsqlradio.com/wsql)
PID12755: >>>>>>>>Forking<<<<<<<<,
------------
PID12786: Closing up to 1024 Fds
PID12755: Child running with pid=12786
PID12755: WriteReady() - instance=0x2961450
PID12755: DestroyStream() - instance=0x2961450
------------
PID12786: Helper started.....
PID12786: HELPER: mozplugger-helper 172,1,63,58720257,674,261,240,200 http://live.wsqlradio.com/wsql mplayer -really-quiet -nojoystick -nofs -zoom -vo xv,x11 -ao esd,alsa,oss,arts,null -osdlevel 0 -xy $width -wid $window "$file" </dev/null
PID12786: setup_display(:0.0)
PID12786: display=1a75250
PID12786: WINDOW=3800001
PID12786: rootwin=1a7
PID12786: setup_display() done
PID12787: Running mplayer -really-quiet -nojoystick -nofs -zoom -vo xv,x11 -ao esd,alsa,oss,arts,null -osdlevel 0 -xy $width -wid $window "$file" </dev/null
PID12787: Redirecting stdout and stderr
PID12786: Waiting for pid=12787
PID12755: NewStream() - instance=0x2961450
PID12755: NewStream() exiting process already running
PID12786: Signal 17 routed to pipe
PID12786: Exited OK!
PID12786: Wait done (repeats=1, loops=1)
...

```

---

