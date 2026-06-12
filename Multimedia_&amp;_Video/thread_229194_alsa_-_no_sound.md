---
title: "alsa - no sound"
date: 2006-08-04
forum: Multimedia &amp; Video
---

### Post by dcer on 2006-08-04
Hi all,

I have a weird problem with sound, I hope someone will be willing to help me.

Even though I had Ubuntu for a year now, I'm still a linux newbie, so forgive me if I write something stupid :)

The problem is OSS works fine while alsa doesn't. I have two sound devices, one is a built-in speaker, the others is usb. It's a laptop. I have usb audio set as default sound device. I have the sound working for system sounds and videolan. But amarok and pretty much everything else (games etc.) doesn't work. I would like to listen to music once in a while on ubuntu and now the only way to do this is thru vlc.

Another weird thing is under valume control I have three cards listed:

Intel 82801DB-ICH4 (Alsa mixer)
USB Audio (Alsa mixer)
Cirrus Logic CS4229 rev 4 (OSS mixer)

Under sounds there are two to select for the defaul one: Intel and USB
Neither works for amarok.

My sound used to work fine on Breezy. After the upgrade that wasn't the case anymore. I thought it was a problem with the upgrade, so I reinstalled ubuntu from scratch. It didn't make any difference. Then I tried

following the sticky on sound problems

[http://www.ubuntuforums.org/showthread.php?t=76978](http://www.ubuntuforums.org/showthread.php?t=76978)

Setting up card order thru alsa-base

Playing around with Media systems Selector (only oss makes sound), but even if that is selected the problem persists)

Turning off system sounds because of possible problems with sound mixing.

Checking volume

In amarok, trying to set it to use different sound systems. Even if I set it to OSS it has no effect.

I didn't check bios cause there was no bios upgrade in this time.

Thanks!

---

### Post by aquasync on 2006-08-04
I think I had a similar problem with my sound card.
If you open the audio mixer, do you have an "External Amplifier" option?

---

### Post by dcer on 2006-08-05
hi!

thanks you for your reply.

Yes external amplifier is listed, but it can't be set to anything. Seems turned off. I read another thread someone has a problem with sound skiping. That is exactly what happens in amarok. It doesn't throw an error or anything just zooms thru the songs without actualy playing them. There wasn't a solution posted yet though.

---

