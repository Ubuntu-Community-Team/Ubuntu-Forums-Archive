---
title: "Sound works in WinXP, earphones in Dapper, no speakers, nx6110 intel ICH"
date: 2006-09-22
forum: Multimedia &amp; Video
---

### Post by linuxbz on 2006-09-22
This one makes no sense to me. I have an HP nx6110 laptop with Kubuntu Dapper, all up to date. Somewhere along the line I lost speaker output.

Earphones and speakers work fine in WinXP. Earphones work in Kubuntu. But the built-in speakers do not.

I don't know whether it is related to the problems I've seen here or not.  Any ideas?

Thanks.

---

### Post by ermannobonifazi on 2006-09-23
Do you have some other USB sound device on you computer (like USB cam?)
Sometime happen that Ubuntu change the order of Audio device (is a bug) and as default is choosen a different audio device (like USB Cam).
to check the problem try this command (when you have working audio and when you have not working audio)

cat /proc/asound/modules

check default sound card (tagged with 0). Should be your ICH.

To avoid the problem in the future you can try

sudo gedit /etc/modprobe.d/alsa-base

and put the right index for the sound card (0 for you preferred, -2 for the rest). this method is not guaranteed.

To definitively avoid the problem you can (as me) blacklist the usb_audio sound module, but this wil prevent to use the Cam or other USB audio device.

sudo gedit /etc/modprobe.d/blacklist

add one row with:

blacklist snd_usb_audio

reboot and check.

---

