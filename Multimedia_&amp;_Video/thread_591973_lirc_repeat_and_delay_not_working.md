---
title: "lirc repeat and delay not working"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by timgrin on 2007-10-25
I have installed lirc in Gutsy and have installed the correct hardware.conf and lircd.conf for the remote setup and it works well in mythtv, vlc and irexec - all except one option in lircrc for the power button on my remote - the delay option doesn't work for some reason.

[http://www.lirc.org/html/configure.html](http://www.lirc.org/html/configure.html) states: 
> delay
[INDENT]tells the program to ignore the specified number of key repeats before using the "repeat" configuration directive above. This is used to prevent double triggers of events when using a fast repeat rate. A value of zero, which also is the default, will disable the delay function.[/INDENT]

my .lircrc section in question :

```
# Power Button
begin
  [INDENT]prog = irexec
  button = POWER
  repeat = 1
  delay = 20
  config = /usr/local/bin/mythpowerbutton.sh[/INDENT]
end
```

Neither repeat = 0 or repeat = 1 works I want the power button to work only after 20 key responses from the remote however it executes after the first keypress as IRW shows:
```
0000000000000120c 00 POWER Technisat_TTS35AI.conf

```

If I disable the above lircrc section then irw does report the remote getting to 20 keypresses - so i am confused:
```
000000000000120c 00 POWER Technisat_TTS35AI.conf
000000000000120c 01 POWER Technisat_TTS35AI.conf
000000000000120c 02 POWER Technisat_TTS35AI.conf
000000000000120c 03 POWER Technisat_TTS35AI.conf
000000000000120c 04 POWER Technisat_TTS35AI.conf
000000000000120c 05 POWER Technisat_TTS35AI.conf
000000000000120c 06 POWER Technisat_TTS35AI.conf
000000000000120c 07 POWER Technisat_TTS35AI.conf
000000000000120c 08 POWER Technisat_TTS35AI.conf
000000000000120c 09 POWER Technisat_TTS35AI.conf
000000000000120c 0a POWER Technisat_TTS35AI.conf
000000000000120c 0b POWER Technisat_TTS35AI.conf
000000000000120c 0c POWER Technisat_TTS35AI.conf
000000000000120c 0d POWER Technisat_TTS35AI.conf
000000000000120c 0e POWER Technisat_TTS35AI.conf
000000000000120c 0f POWER Technisat_TTS35AI.conf
000000000000120c 10 POWER Technisat_TTS35AI.conf
000000000000120c 11 POWER Technisat_TTS35AI.conf
000000000000120c 12 POWER Technisat_TTS35AI.conf
000000000000120c 13 POWER Technisat_TTS35AI.conf
000000000000120c 14 POWER Technisat_TTS35AI.conf
000000000000120c 15 POWER Technisat_TTS35AI.conf
000000000000120c 16 POWER Technisat_TTS35AI.conf
000000000000120c 17 POWER Technisat_TTS35AI.conf
000000000000120c 18 POWER Technisat_TTS35AI.conf
000000000000120c 19 POWER Technisat_TTS35AI.conf
000000000000120c 1a POWER Technisat_TTS35AI.conf
000000000000120c 1b POWER Technisat_TTS35AI.conf
000000000000120c 1c POWER Technisat_TTS35AI.conf
000000000000120c 1d POWER Technisat_TTS35AI.conf
000000000000120c 1e POWER Technisat_TTS35AI.conf
000000000000120c 1f POWER Technisat_TTS35AI.conf
000000000000120c 20 POWER Technisat_TTS35AI.conf

```


I have managed to get it to work how I want (pausing before executing) by doing this:

```
# Power Button
begin
[INDENT]  prog = irexec
  button = POWER
  repeat = 2
  config = echo '' > /dev/null
  config = echo '' > /dev/null
  config = echo '' > /dev/null
  config = echo '' > /dev/null
  config = echo '' > /dev/null
  config = echo '' > /dev/null
  config = echo '' > /dev/null
  config = echo '' > /dev/null
  config = echo '' > /dev/null
  config = echo '' > /dev/null
  config = echo '' > /dev/null
  config = echo '' > /dev/null
  config = echo '' > /dev/null
  config = echo '' > /dev/null
  config = echo '' > /dev/null
  config = /usr/local/bin/mythpowerbutton.sh
end[/INDENT]
```

Just for interest sake why does the delay not work?

---

