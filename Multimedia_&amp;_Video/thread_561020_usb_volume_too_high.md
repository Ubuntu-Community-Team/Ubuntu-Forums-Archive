---
title: "usb volume too high"
date: 2007-09-27
forum: Multimedia &amp; Video
---

### Post by Mujaheiden on 2007-09-27
dear all,

I was finally able to make my USB audio (C-Media USB headphone set, which is actually a microphone with a headphone-out) work by default.

To get here, I compiled alsa-driver-1.0.15rc2 with only usb-audio - before I had a horribly difficult internal sound card.

So now it works, only the volume is WAY TOO LOUD. I have put all the controls on the lowest, it is still too much for a little background music, in the Volume contorl & in XMMS

When I run alsamixer, the volume is also at the lowest level.

My USB device doesn't have volume control.

What to do?

---

### Post by LinuxNewb_22 on 2007-09-27
Hi,

I don't have a solution for you as I'm quite wet behind the ears wrt Ubuntu...

BUT... would you please tell me how exactly you > **Mujaheiden said:**
>  compiled alsa-driver-1.0.15rc2 with only usb-audio ?

I have no sound at all!

My motherboard has onboard sound but, for some reason, the sound device is detected as a USB sound device. I had been trying to figure out how to get the sound running with no luck so far ... I have a feeling that what you did will work for me.

(Aside: I will have no problem with the volume being > **Mujaheiden said:**
>  WAY TOO LOUD as I have a volume control on my speaker system)

Look forward to hearing from you! Thanks!

---

### Post by Mujaheiden on 2007-09-28
Hm, thats no good for me. And do you have a microphone? My microphone doesn't work in my new install, so I hope your not waiting for that :(

But what I did: I went to the [SoundTroubleShooting]("https://help.ubuntu.com/community/SoundTroubleshooting#head-008f283a208cd8e708d33a0e9c8ba222e30faca0")-page

and although they advice v. 1.0.12, I took the 1.0.15rc2 anyway.

When you go to [step four]("https://help.ubuntu.com/community/SoundTroubleshooting#head-2dce7ad2a91ebb32cef4de93c06b197e7af45263") I used 
[INDENT]./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=**usb-audio** --with-oss=yes[/INDENT]
for selecting only the usb-audio.

nb. for using alsamixer later, i had to give "alsamixer -c 1", maybe you need to fiddle around with the number of the card too.

---

