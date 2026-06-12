---
title: "can't hear sound from any media player"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by kasemodz on 2006-07-24
Alright, this problem has happened ever since I installed Dapper and day by day I'm getting more frustrated with Dapper. Breezy never had any problems like these. Alright, most of the times, just randomly when I try to play a song from xmms or something it gives me this error.

Can't open audio
Please check that.
Your soundcard is configured properly
You have the correct output plugin selected
No other program is blocking the soundcard

Well I went to top and tried to see other media players running, and to my knowledge there are no other media players running. When I lougout and log back in the sound comes back sometimes. IF it doesn't I have to reboot before I can hear audio again. I tried installing alsa-oss, then using aoss xmms. It says

> libmikmod.so.2: cannot open shared object file: No such file or directory
Message: device: default

** WARNING **: alsa_setup(): Failed to open pcm device (default): Device or resource busy


---

### Post by senior on 2006-07-24
> **kasemodz said:**
> Alright, this problem has happened ever since I installed Dapper and day by day I'm getting more frustrated with Dapper. Breezy never had any problems like these. Alright, most of the times, just randomly when I try to play a song from xmms or something it gives me this error.

Can't open audio
Please check that.
Your soundcard is configured properly
You have the correct output plugin selected
No other program is blocking the soundcard

Well I went to top and tried to see other media players running, and to my knowledge there are no other media players running. When I lougout and log back in the sound comes back sometimes. IF it doesn't I have to reboot before I can hear audio again. I tried installing alsa-oss, then using aoss xmms. It says
L.S.,
Try to solve this problem by:

Open terminal

$ sudo bash
# killall esd

start a mediaplayer.

---

### Post by John Jason Jordan on 2006-07-25
> **senior said:**
> L.S.,
Try to solve this problem by:

Open terminal

$ sudo bash
# killall esd

start a mediaplayer.
Perfect!

I have been trying for days to get this resolved. My sound was working fine, except in media players. That is, logging in I hear the Ubuntu theme, etc. The computer beeps and snorts at me appropriately. But when I opened RealPlayer it gave me an error message "cannot open the audio device, another application may be using it."

Reading the forums I found a lot of suggestions, but this is the one that finally worked.

Now, is there something I can uninstall or install to make this fix permanent?

---

