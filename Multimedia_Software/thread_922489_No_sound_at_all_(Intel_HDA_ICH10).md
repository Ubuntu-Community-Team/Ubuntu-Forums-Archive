---
title: "No sound at all (Intel HDA ICH10)"
date: 2008-09-17
forum: Multimedia Software
---

### Post by desertoak on 2008-09-17
Hi

After installation the sound won't work 

Checked the alsamixer it says Intel HDA audio.
So ubuntu seems to recorgnize the device.

Still get no sound at all in headphones or via optical spdif.

Ubuntu version: 8.10 Alpha 5.

#lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller

#cat /proc/asound/card0/codec#* | grep Codec
Codec: IDT 92HD73E1X5

My motherboard is a new Intel DG45ID with G45 chipset.

I've tried disabled pulseAudio.

Anyone out there with a solution?

Thanks in advance!

---

### Post by wolfen69 on 2008-09-17
take a look at [this]("https://help.ubuntu.com/community/HdaIntelSoundHowto").

---

### Post by josephhitt on 2008-10-24
Sound does not work for me either, same motherboard.

---

### Post by maxim99 on 2009-05-09
I've been working for a while on this sound issue and stumbled across the solution.

First I started here:

[http://ubuntuforums.org/showthread.php?t=1104653](http://ubuntuforums.org/showthread.php?t=1104653)

That lead me to here:

[http://ubuntuforums.org/showthread.php?t=1104653](http://ubuntuforums.org/showthread.php?t=1104653) (This was a huge help since it fixed the problem.)

Then I reinstalled the OS. I redid everything just like I did before but this time I get no sound just like I did before.

This time I poked around for a while and did some different stuff I eventually stumbled upon the solution in alsamixer.

I have 5 loopback devices on the sound card displayed in alsamixer:
Analog Loopback
Analog Loopback 1
Analog Loopback 2
Analog Loopback 3
Analog Loopback 4

I'm not sure what the purpose of these devices are but I muted them and now the sound works, just like that.

Actually I just muted "Analog Loopback" the other made no difference at all from what I could see, but I muted them all for good measure. Hope this helps someone as it was very frustrating for me.

---

