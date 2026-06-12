---
title: "Creative X-Fi Xmod Ubuntu problems..."
date: 2007-06-08
forum: Multimedia &amp; Video
---

### Post by t.achim on 2007-06-08
Hi,
I've recently purchased a Creative X-Fi Xmod external sound card, and have encountered problems while trying to use it in ubuntu,

First of all, it just wasn't detected. After googling a bit, I found out that I should comment out the ```
options snd-usb-audio index=-2
``` in /etc/modprobe.d/alsa-base.

After doing that and rebooting, it still didn't work for sound output, even though kmix found it. For a while I could turn the volume knob and it would SHOW that it was controlling the volume (it wasn't actually changing anything). Then, after about a minute, it only controlled the volume in broken intervals (where controlling means showing changes but not actually modifying the volume. same as before).

I can't figure out what else to try, as most of the google results are in foreign languages. Can anybody help?

Thanks

---

### Post by t.achim on 2007-06-09
bump

---

### Post by perimere on 2007-08-08
Hi,

I've just attached an Xmod to my Feisty laptop install. I've only just started trying to get sound working, but I've got Amarok playing audio, and the knob successfully controls the audio.

I had the same issue as you with the knob displaying a visual change on the screen, but not actually doing anything. After a reboot it appears to be behaving now.

I left this on another post that details how I got Amarok working. I hope this helps you as a starter?
[http://ubuntuforums.org/showthread.php?p=3155391#post3155391](http://ubuntuforums.org/showthread.php?p=3155391#post3155391)

Cheers

Adam

---

### Post by perimere on 2007-08-08
Ok, on the thread listed above, I just added the very brief solution I followed to get everything working for the Xmod.

HTH

Cheers

Adam

---

### Post by koolcracker on 2008-07-16
I have used the asoundconf set-default-card to Xmod, I've used the system>preferences>sound devices and set them to USB, and when I tested it the sound came out of my Xmod, but anything but Amarok will play out of my laptop speakers. What have i missed?

---

