---
title: "Is it possible to play bbc radio programmes with get_iplayer outside of the UK?"
date: 2010-02-11
forum: Multimedia Software
---

### Post by sup on 2010-02-11
Hello,
I would like to listen to BBC radio online, I tried get_iplayer (it is in the repositories). But no matter what I try, it does not work (i.e. no sound is player). The command I use (from the documentation of get_iplayer) is ```
get_iplayer --stream --pid='bbc_radio_one' | mplayer -cache 64 -

``` output goes like this ```
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing -.
Reading from stdin...
Cache fill:  0.00% (0 bytes)   get_iplayer v2.41, Copyright (C) 2009 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.

Cache fill:  0.00% (0 bytes)   INFO Trying to stream pid using type tv
Cache fill:  0.00% (0 bytes)   INFO: pid not found in tv cache
Cache fill:  0.00% (0 bytes)   Matches:
Cache fill:  0.00% (0 bytes)   :	 - , , , 
Cache fill:  0.00% (0 bytes)   
INFO: 1 Matching Programmes
Cache fill:  0.00% (0 bytes)   INFO: Checking existence of default version
Cache fill:  0.00% (0 bytes) 
```
Is there anybody from the UK who could verify whether it works for them or not? Also I use 64bit, I od not know whether that is important?

---

### Post by sup on 2010-02-11
Apparently the issue is with me using 64bit and mplayer not being compiled with support for windows codecs or something. Luckily, there is a solution, use real media streams that mplayer should be able to handle (I use mplayer from medibuntu, so not sure about the official one).

[http://www.listenlive.eu/uk.html]("http://www.listenlive.eu/uk.html") are the urls and here is the command
```
mplayer -playlist http://www.bbc.co.uk/worldservice/meta/tx/nb/live/eneuk.ram
```
(that is for World Service).

---

