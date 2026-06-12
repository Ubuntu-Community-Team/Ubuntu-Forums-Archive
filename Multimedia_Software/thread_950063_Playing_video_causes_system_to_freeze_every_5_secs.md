---
title: "Playing video causes system to freeze every 5 secs..."
date: 2008-10-16
forum: Multimedia Software
---

### Post by shaggy999 on 2008-10-16
I am having a really weird problem. I just got an old IBM eserver motherboard w/ a PIII 1.33 GHz processor on it. Ubuntu installed just fine on it and I've added ubuntu-restricted-extras as well as non-free-codecs (from medibuntu), libdvdcss2, and vlc.

My problem is that if I play ANY video (Flash, MPG, MOV, AVI, etc) in ANY player (totem, mplayer, vlc, firefox) my system will start freezing for like 5 seconds then it will work for 5 seconds and then freeze for 5 seconds and so on and so on (and this is the WHOLE system) all the way until I reboot my computer!! Even after I close a video it still does this! Not even the mouse will move when it freezes! So I can only work in 5 second intervals.

Anybody have any idea what could be causing this?

Here's the output from lspci for my video card and sound card (in case they might be related to the issue):

01:00.0 VGA compatible controller: Trident Microsystems 3DImage 9850 (rev f3)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)

No restricted drivers are in use on this system. I know someone w/ a spare nVidia card and he's going to bring it over hopefully tonight and we're gonna swap it in to see if it's the video card that's the problem.

---

### Post by Mattie03 on 2008-10-16
What is your video card. You may need a 152MB or 1G video card to play your videos. Also check the capacity of your RAM.

---

### Post by dagoth_pie on 2008-10-16
could be an issue with the IRQ, are there any pci devices plugged in, or are they all onboard?

---

### Post by shaggy999 on 2008-10-17
Things seem to be going ok now. I removed totem and all of a sudden things work ok now. Really weird. I have no idea how totem could be affecting other players.

---

