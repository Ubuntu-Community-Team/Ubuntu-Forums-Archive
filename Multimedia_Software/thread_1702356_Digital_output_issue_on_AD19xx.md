---
title: "Digital output issue on AD19xx"
date: 2011-03-07
forum: Multimedia Software
---

### Post by bupe on 2011-03-07
Dear All,

I'm having an issue with the following motherboard:
 [M3A32-MVP Deluxe/WiFi-AP]("http://www.asus.com/product.aspx?P_ID=KC8yHOfBMCe9SlrP")

It has the following onboard audio:
ADI® AD1988 8 -Channel High Definition Audio CODEC
Coaxial / Optical S/PDIF out ports at back I/O 

I'm using both the coaxial and optical digital out ports to connect to my digital receivers - this setup works perfectly fine in Windows 7 64bit.

However under Ubuntu 10.10 32bit PAE I'm not getting any sound on these digital interfaces - I'm only getting sound from the analog jack connectors.

I opened a Launchpad bug report (there hasn't been too much activity so far):

[[Analog Devices AD1988B] ALSA test tone not correctly played back - no sound on coaxial digital out.]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/725639").

I searched the forums and Google for a solution but couldn't find anything that would help.

Please let me know if I'm missing something or this is never going to work.

Best regards,
Peter

---

### Post by bupe on 2011-03-08
I found the following topic:

[Sound doesn't work anymore in 10.10]("http://ubuntuforums.org/showthread.php?t=1652696")

Lidex's suggestions in the 2nd post solved the issue for me. I added the following line to /etc/modprobe.d/alsa-base.conf

> options snd-hda-intel model=6stack-dig

After reboot I have stereo sound on my external receiver.

Next mission is to enable 5.1 throughput - I'll start with VLC.

Primary issue resolved.

---

### Post by bupe on 2011-03-09
Well, looks likeI was too tired yesterday to realize that the issue is still present on the coaxial output - it seems that the optical out is working fine however... - does anyone have any idea how to initialize both spdif outputs? I have two receivers - one at my desk using the optical out and one at the TV using the coaxial output - the latter still does not work (of course under Windows both work at the same time).

Any and all suggestions are welcome!

Best regards,
Peter

---

