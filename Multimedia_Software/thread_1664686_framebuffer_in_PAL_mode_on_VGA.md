---
title: "framebuffer in PAL mode on VGA"
date: 2011-01-11
forum: Multimedia Software
---

### Post by bamboosso on 2011-01-11
Hello,

I have ad724 chip from analog devices that converts VGA signal to composite video, but it requires input in PAL standart. Is it possible to change framebuffer resolution and synchronisation to achive PAL on RGB output?

I have try to change this using fbset but there is no change of resolution. Grub runs kernel with framebuffer of 640x480 resolution and i'm able to watch videos using mplayer on cli ubuntu version, but i have problems with setting it up to PAL.

Is it possible?
Why fbset does not affect to current display?
Maybe I will have to use x11?

Thank you for your help.

Best regards
 Maciej &#321;aski

PS. I have Intel Atom CPU with intel integrated graphics (maybe problem is here?)

---

### Post by BicyclerBoy on 2011-01-11
I only know how to do this with X server.
And you probably already know this..

/etc/X11/xorg.conf

Section "Monitor"
	Identifier  "TV"
	Option      "TV Format" "PAL"
EndSection

The intel driver works quite well on atom GMA950 945 netbooks..

You could run a very simple desktop manager.

KMS witchcraft..
[http://www.linuxquestions.org/questions/slackware-14/kernel-mode-setting-on-slack-current-736017/](http://www.linuxquestions.org/questions/slackware-14/kernel-mode-setting-on-slack-current-736017/)

---

