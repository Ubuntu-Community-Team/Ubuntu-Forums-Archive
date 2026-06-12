---
title: "HIS Radeon HD4670 AGP + Apple DVI to S-video adapter - No picture"
date: 2010-06-17
forum: Multimedia Software
---

### Post by KingBongo on 2010-06-17
Can someone help me with this please! Recently I bought this AGP card [http://www.hisdigital.com/un/product2-448.shtml](http://www.hisdigital.com/un/product2-448.shtml) and this adapter (DVI to Video) [http://store.apple.com/us/product/M9...co=MTA4NDU1Mjc](http://store.apple.com/us/product/M9...co=MTA4NDU1Mjc) . 

The card itself has no S-Video output, but people told me that if I were able to find an adapter from DVI to S-Video it would probably work. However, I get no picture on my old CRT TV. The TV detects some signal because it changes mode, but no picture is to be seen. In the Monitor Preferences the Adapter+TV combo is detected as "Monitor: Apple Computer Inc 10" ". I have tried playing around with the resolution and the frequency (56Hz and 60Hz) in all possible configurations (only a few) but no luck. What can I do? Help!

My setup is the following:

Lucid Lynx
Kernel 2.6.35rc3-maverick
PPA-xorg-edgers repos added
updated and upgraded

I have also tried other Kernels (.32, .33, .34) but still no picture.

---

### Post by KingBongo on 2010-06-18
Here we go again. I newer got any kind of help with graphical problems, ever. If somebody would write at least something I would be happy.

I don't know if it still counts as S-Video or not since my signal is converted from DVI to S-Video, but according to this [http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature) , S-Video should work. So why isn't mine working then?

---

### Post by urbanus on 2010-06-19
Is it an old tv?

I had problems when connecting a computer via a native s-video port. The picture became black and white. Another computer connected to the same tv got colours.

Do you get a picture with the DVI when a normal monitor is connected? Have you tried the adapter with another TV, or another computer, or in Windows (the drivers are often more feature complete)?

---

### Post by KingBongo on 2010-06-26
urbanus:
Sorry! I completely missed your reply. I forgot to enable "email notification". Back to topic.

No, I did not try connecting it directly via the DVI port. The reason is that I am not that modern yet ;) I am still using old CRT monitors and an old (but good) CRT TV, that's why I bought the DVI-to-Video adapter from Apple. I am guessing that DVI works flawlessly though, it mostly does these days. And no, I did not try Windows and I don't want to, because I really hate it.

I haven't had any problems with S-Video on this TV before, using this computer and also the same software. I have an ages old Nvidia card (MX200) with a native S-Video output which works at once when I plug it in (Nvidia proprietary drivers). 

More ideas? Please. I really would like to get this to work! I do not want to buy a new TV just yet for two reasons: 1. Analog TV looks better on CRT TVs, haven't seen anything else. 2. If I were to upgrade I would like to buy an o-led TV, but they are still too expensive for my taste.

By the way. I have been looking for the "xorg.conf" file but as I understand it, it isn't used anymore by default. Can I edit some other file instead? Which one and how? Since the TV gets some signal (changes mode) it feels like there is only some minor tweaking necessary, changing "NTSC" to "PAL", activating "S-Video" or something like that. But what do I know.

---

### Post by KingBongo on 2010-06-27
Ok. This is almost too scary, but I am getting more help with this on a Mac forum than on the Ubuntu forum.

Anyway. How do I check the properties of the actual video signal that is being sent out of the DVI/VGA port? I need to know the resolution, frame rate and also if the picture is progressive or interlaced. How can I check that and how can I change that if needed? 

Help me pleeeeease!

---

### Post by KingBongo on 2010-06-28
Back again. Still hoping the get some help! 

Does anybody know how to use Framebuffer to manipulate the video output to the TV? I would like to be able to manipulate the resolution, frame rate and most importantly (I believe) if it is progressive or interlaced. It is my understanding that Frambuffer can be used for things like that.

---

### Post by urbanus on 2010-06-28
You are using the open source driver, right?
Have you tried the binary one? The Catalyst Control Panel is quite capable in many ways.

I mentioned Windows simply because it would reveal if it is a software issue, not because I meant you should use it. The open source driver should detect the s video automagicly, it does on my x600 card. But the adapter might screw it up a bit :-P

---

### Post by KingBongo on 2010-06-28
urbanus:
I am absolutely sure it IS the adapter that is screwing everything up :) Yes, I am using the open-source driver (adding xorg-edgers repos implies that). I tried installing the newest Catalyst as well, but it couldn't be installed because of xorg-server 1.8 which comes from xorg-edgers. I am perfectly sure that Catalyst wouldn't solve my problems anyway, so I gave up on that.

What I need help with now is to check and possibly alter the following video output: Resolution, frame rate, Progressive or Interlaced scan.

---

