---
title: "oss with alsa seems not to work"
date: 2005-11-11
forum: Multimedia &amp; Video
---

### Post by Jabone on 2005-11-11
I have ubuntu breezy installed on my computer.
When playing games that use oss seems to be problem. Quake3 sais "/dev/dsp no device" or something like that. 

I have Sound Blaster Live soundcard and I've installed oss-emulation. 
How to create needed devices so that sound is working through games?

I tried Beep media player and choose oss plugin but it says check plugins and sound card is configured correctly blaa blaa. 

Oss plugin option let me choose which devices to use.
In mixer device it says that default is Sigmatel stac9721,23. I have no Sigmatel soundcard. I have sigmatel irda dongle, but it's not connected. 

I have also dxr3 mpeg decoder card which isn't configured.

---

### Post by marcus_brodi on 2005-11-22
Hi,

I was looking at the exact same bug here. Seeing your message reminded me I also have a DXR3 card. I know that this card has a sound chip (the sigmatel you see is your dxr3) but this is not a sound card (you can't use it to play regular sound). Simply blacklisting the module em8300 will fix the problem for the sb live (but you won't have any dxr3 support anymore... but I guess you didn't know you had it already).

See this bug: [https://launchpad.net/distros/ubuntu/+source/udev/+bug/4729](https://launchpad.net/distros/ubuntu/+source/udev/+bug/4729)

HTH,
Marc

---

