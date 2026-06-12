---
title: "Nvidia 8200 &amp; Ubuntu 8.04 - Can't see entire screen.."
date: 2008-08-30
forum: Multimedia Software
---

### Post by MattUK on 2008-08-30
Hi all,

I'm setting up a linux media center, it has an integrated nvidia 8200 chipset and I'm running ubuntu 8.04.

I've managed to install the latest nvidia drivers using Envy, but no matter what resolution I choose, I can't see the top or bottom 50 or so pixels, I'm not sure about the sides if there's any missing there or not.

This is on a 40" Samsung LCD using a HDMI cable.

If I don't use the accelerated graphics driver from Nvidia, it works fine and I can see the whole thing, just with no effects which means I can't run Entertainer, which is more or less the whole point of the computer in the first place, that also forces me to use 1024x768 resolution or similar (everything is huge).

Any ideas what's wrong? If you need any other info let me know and I'll get it for you, I'm not a linux guru though so you'll have to supply the commands ;)

Thanks,
Matt

---

### Post by MattUK on 2008-08-30
I've looked up the native resolution for my samsung lcd, which is 1366x768. Just tried a VGA cable instead of HDMI and it auto adjusts to that resolution, and everything works fine.

I would preferably like to get the HDMI working too though, as thats sound as well, and the colours seem a bit dull on VGA..

Any ideas? Is it a ubuntu HDMI issue?

---

### Post by u!mp3 on 2008-09-14
Support for the 8200 GeForce MOBOs is not very good at this moment, the upcoming intrepid ibex release should work better for you...

i was using an asus 8200 geforce mobo with the same problem, after a couple of weeks of trying, i read that in someplace and i just order a abit GeForce 7050PV  and now my sistem is working like a charm, and the HDMI is good too...

best regards

---

### Post by jasonkordecki on 2008-09-17
On Samsung TV's changing the input name of HDMI 1 to PC under the menu will change the processing of the line.  I did this on my Samsung DLP 46" and the screen now fits properly.  I am using an old radeon card not supported by the binary drivers.

Try that to see if it works.

---

### Post by mehturt on 2009-12-28
Same for me with 9.10.

---

### Post by arvati on 2010-08-10
I use ubuntu lucid with Geforce 8200 and Samsung TV and have the same problem.
With resolution 1920x1080 i got both screens but with borders cutted. The TV only shows until 1440x900 resolution screen with a black screen and no signal. Above that signal is ok but with edges cutted.

---

