---
title: "no HDMI audio device, no spdif sound to TV"
date: 2010-09-30
forum: Multimedia Software
---

### Post by beermotor on 2010-09-30
I have a 9400GT, which did play audio to the TV (a budget Sharp that sorta sucks) through WindowsXP until very recently (think an update fried the driver; will have to check cable connection).

Aplay doesn't show the HDMI audio device, though.  All I get is my onboard audio chip (a Realtek ALC662).  Tried every tutorial I could the other night, and nothing worked.  Alsa's upgraded to latest version.  I can see the SPDIF in alsamixer and they aren't muted but there's no volume indicator (like it's at 0) and you can't raise or lower it.  I'm hoping that maybe 10.10 will resolve my issue.  But does anyone else have any ideas?  All of the tutorials out there seem to assume that you actually get an HDMI audio device in aplay; I don't.  But I know it'll output audio because I was listening to it in WindowsXP.

Thanks in advance...

---

### Post by lidex on 2010-09-30
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by beermotor on 2010-09-30
[http://www.alsa-project.org/db/?f=8849dd84db4eff877e603374a1df54dcc08ec216](http://www.alsa-project.org/db/?f=8849dd84db4eff877e603374a1df54dcc08ec216)

---

### Post by lidex on 2010-09-30
Remove this options line in alsa-base.conf:
```
options snd-hda-intel probe_mask=1 model=3stack-6ch-dig
```
Replace with this:
```
options snd-hda-intel model=ecs
```
Reboot

---

### Post by beermotor on 2010-09-30
Thanks for the replies - I fixed that line but it still isn't playing any audio through the TV, checked with XBMC and MoviePlayer.  I confirmed that it is working, though, in WinXP.
:confused:

---

### Post by beermotor on 2010-10-01
Any other ideas?  I've poked through the things in your sig block, but I think my problem is different than most since I don't see any HDMI audio device in aplay.  SPDIF ought to "just play" though, since it's not really a device, right?  At least, that's what it does in WinXP.

When I originally followed your instructions, then fired up XBMC to test, it gave me a "failed to initialize sound device" error - so I had to switch it to IEC958... it was set to something like that with a whole big long string of garbage characters with it.  Not sure what that was all about.

I have a new set of physical speakers coming from Newegg right now so I'll be able to confirm that model=ecs works with the mobo outputs soon.  In (I think) 8.04 I had to use the 3-stack option to get it to work.

---

### Post by lidex on 2010-10-01
So you've tried this:
[http://ubuntuforums.org/showthread.php?t=877811](http://ubuntuforums.org/showthread.php?t=877811)

---

### Post by beermotor on 2011-04-12
Still nothing. If aplay -l doesn't show the device, there doesn't seem to be any recourse. It's like Linux just doesn't recognize the card. Sad panda...

---

### Post by lidex on 2011-04-12
Welcome back. Check out this thread:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)

---

### Post by beermotor on 2011-04-13
> **lidex said:**
> Welcome back. Check out this thread:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)

Thanks, lidex - I've skimmed through that thread and it seems like it might have some useful ideas to try. I think I'll probably end up upgrading my TV and media box (to an ion-based nettop or similar) before I ever get this hacked together to work right, heh. :)

---

