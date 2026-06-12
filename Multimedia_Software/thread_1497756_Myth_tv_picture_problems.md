---
title: "Myth tv picture problems"
date: 2010-05-31
forum: Multimedia Software
---

### Post by s3019293 on 2010-05-31
Hi All,

I set up MythTV this weekend and am really excited about it. I am running ubuntu 9.10 and the latest version of MythTV (although I don't know exactly what version that is or how to find out).

So far I have Live TV and recordings working however I am not 100% happy with the quality of my Live TV. It is a bit hard to describe but I am getting background flickering in my picture and when I look closely at my screen I can see that the pixels on my screen are really noticeable. The flickering is particularly bad when MythTV shows the name of the program currently showing at the bottom of the screen. The text which MythTV displays flickers quite a bit. 

I have been trying to look up if there is anything I can tweak to fix my picture problems which lead me to download and installing nvidia drivers for my graphics card to see if that would make a difference but it didn't seem to. 

In doing research I've also found many notes on changing xorg.conf and changing bob2 de-interlacing but I haven't touched these as I have yet to find anything substantial to convince me that changing these would improve my picture quality.

I'm starting to think that my graphics card is just not good enough. Can anyone please give me some advice on what I should be looking at. My system specs are below...


CPU - Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
Graphics Card - nVidia Corporation G71 [GeForce 7900 GS] (rev a1)
        	Subsystem: Giga-byte Technology Device 342e
        	Flags: bus master, fast devsel, latency 0, IRQ 12
RAM - 2GiB
Resolution - 1280x800
TV-Tuner - DVICO dual digital 4

I am using a VGA cable to connect my Ubuntu box to my samsung LED TV. (I've also read a lot of conflicting forums on whether component is better than VGA or vice versa)

Thank you for your help

---

### Post by s3019293 on 2010-06-03
Looks as if no one is sure about what might be causing my picture problems. Will getting a better graphics card improve my picture? Should I get one with a hdmi out cable?

---

### Post by madverb on 2010-06-05
I have a fairly similar setup and no problems. I have an 8600GT instead. I'm thinking the problem may be the connection to the TV.
I have a 1080p monitor connected and it works fantastically. The Dvico is 1080i but I don't think it would make much difference if it was 1080p.

---

### Post by s3019293 on 2010-06-13
hI,

Yes the problem was the connection to the tv. After doing some reading i decided to buy a dvi to hdmi cable and that fixed the picture totally. 

I still have a slight problem where there seems to be some borders around my Myth TV screen at the top and bottom of the picture but this is a different issue I think.

---

