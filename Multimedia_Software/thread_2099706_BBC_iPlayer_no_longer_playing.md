---
title: "BBC iPlayer no longer playing"
date: 2012-12-30
forum: Multimedia Software
---

### Post by engine on 2012-12-30
Firefox 17.0.1 on Ubuntu 10.04 LTS, everything up to date as far as I know … and since the last time I used it, the BBC iPlayer isn't working. The standard "listen now" link gives me a neat white oblong where the player should be, and "listen in pop-out player" gets stuck on 'loading'.

Any hints/tips on what's going on and how to listen to BBC content? Thanks in advance.

---

### Post by haqking on 2012-12-30
> **engine said:**
> Firefox 17.0.1 on Ubuntu 10.04 LTS, everything up to date as far as I know … and since the last time I used it, the BBC iPlayer isn't working. The standard "listen now" link gives me a neat white oblong where the player should be, and "listen in pop-out player" gets stuck on 'loading'.

Any hints/tips on what's going on and how to listen to BBC content? Thanks in advance.

Do you have any extensions such as NoScript or ADBlock running ?

it is working fine for me in FF 17 though I am not in Ubuntu but I suspect it is flash related or script blocking of some type.

Peace

---

### Post by ajgreeny on 2012-12-30
What graphic card do you have and what version of flash are you using?

If you have only just updated your 10.04 you will probably now have the latest flash 11.2.202-258, which refuses to work on some ATI cards such as my ATI 9200SE;  I have to install the older 11.1.102-63 version for any success.

BBC iPlayer is fine here, --well, as fine as it ever is, which is never great, being flash based.

Try **get-iplayer** from the repos which allows you to download the programmes you want and play them in totem, mplayer or VLC, whichever you prefer.

---

### Post by engine on 2013-01-13
Results of first experiments with get-iplayer &#8230; lots here not to understand! so if someone can patiently talk me through the error messages, that's already something. If someone can tell me how to achieve the desired result &#8210; downloading a radio programme &#8210; that would be even better!

> get-iplayer --get 12674 --output "home/Music/"
get_iplayer v2.66, Copyright (C) 2008-2010 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.

Matches:
12674:	radio, The Early Music Show - Baroque Instruments, BBC Radio 3, Classical,Early Music,Music,Radio

INFO: 1 Matching Programmes
INFO: Checking existence of default version
INFO: flashaaclow1 modes will be tried for version default
INFO: Trying flashaaclow1 mode to record radio: The Early Music Show - Baroque Instruments

WARNING: ffmpeg does not exist - not converting flv file
INFO: File name prefix = The_Early_Music_Show_-_Baroque_Instruments_b01ppvzp_default                 
FLVStreamer v1.9
(c) 2009 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Failed to open file! /The_Early_Music_Show_-_Baroque_Instruments_b01ppvzp_default.partial.flv
INFO: Command exit code 1 (raw code = 256)
WARNING: Failed to stream file /The_Early_Music_Show_-_Baroque_Instruments_b01ppvzp_default.partial.flv via RTMP
INFO: skipping flashaaclow1 mode
ERROR: Failed to record 'The Early Music Show - Baroque Instruments (b01ppvzp)'


---

### Post by shantiq on 2013-01-13
---------------  

see Ron below for a fix

**PS**


if you then want mp3 instead of aac   use  [number will be different now]


> get-iplayer -o  ~/Music --mode=flashaacstd --aactomp3 --mp3vbr 0 --get 12674

---

### Post by ron999 on 2013-01-13
> **engine said:**
>  patiently talk me through the error messages...

> get-iplayer --get 12674 --output "home/Music/"
get_iplayer [COLOR="Red"]v2.66[/COLOR], Copyright (C) 2008-2010 Phil Lewis
This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
This is free software, and you are welcome to redistribute it under certain
conditions; use --conditions for details.

Hi
You need to upgrade to get_iplayer v**2.82**.
(Google for "Jon Davies PPA").
Then use a command like this:-
```
get_iplayer --type=radio --pid=b01ppvzp
```

For low-bitrate version use a command like this:-
```
get_iplayer --type=radio --pid=b01ppvzp --mode=flashaaclow
```

---

