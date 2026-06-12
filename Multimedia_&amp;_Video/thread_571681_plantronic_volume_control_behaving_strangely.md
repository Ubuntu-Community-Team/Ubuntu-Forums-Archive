---
title: "plantronic volume control behaving strangely"
date: 2007-10-09
forum: Multimedia &amp; Video
---

### Post by coulix on 2007-10-09
Hello ,
I am having some strange problems with a set of usb plantronic headphones + mic.
It get detected, appering as usb audio in the sound preferences.
I can get sound and mic working nicely.

However when i use the volume controls keyboard keys (controling pcm volume) it does not not increase the L and R chanel at the same time.

Firstly it diminushed the L chanel to 1, then the right in incremental steps.


[IMG]http://coulix.net/temp/platro_1.jpg[/IMG]


[IMG]http://coulix.net/temp/platro_2.jpg[/IMG]


All help is welcome

I am on gusty, using alsa 1.0.14

---

### Post by coulix on 2007-10-10
:(

---

### Post by james9876 on 2007-10-18
mmmmm.... sounds like the problem I'm having with my speakers unfortunately and it's driving me a little nuts :confused:

My setup though is Logitech V20 usb, again alsa,  With the device set at usb audio, and trying to change the volume I get the same odd result that you do, that of the channels splitting, the left one muting and the other going all over the place :(.

any takers for the problem? :):).

Oh yeah, gutsy too (I believe it happened when I first tried out the beta update).  a complete   format and install of the final product gives no joy either btw.

looks like this gentleman has the problem too?
[http://ubuntuforums.org/showthread.php?t=579722&highlight=usb+volume+problem](http://ubuntuforums.org/showthread.php?t=579722&highlight=usb+volume+problem)

---

### Post by oyvinst on 2007-10-19
Got problems with volume control on the Creative Xmod usb audio card. Channels split up and behave very odd. It's actually unusable.  This is in gnome-volume-control; the alsamixer console app works perferctly.

---

### Post by tipsqueal on 2007-10-20
I'm having exactly the same problem. I use a Plantronics DSP 500. Any help would be great. One thing that I did notice that was actually an awesome improvement was the fact that I can now have sound come from multiple sources/programs through my headset. Now if the volume control would work properly then I'd be all set.

Thanks,
Tipsqueal.

---

### Post by khughitt on 2007-10-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/155109](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/155109) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Same trouble with Plantronics .Audio 625 USB. There is now a[ launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/155109") on the issue, so if you are having same problem, it may be helpful to make a note of your device and settings there.

---

