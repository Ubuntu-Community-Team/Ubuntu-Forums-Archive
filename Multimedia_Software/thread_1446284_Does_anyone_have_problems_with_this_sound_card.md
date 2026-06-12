---
title: "Does anyone have problems with this sound card?"
date: 2010-04-03
forum: Multimedia Software
---

### Post by listerdl on 2010-04-03
Hi this is my sound card:

card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]

I have no sound and I am using Karmic Kola.

I have a dual boot Windows 7 that worked straight out of the box. Wish Ubutnu was the same.....

Anyone have any advice please? Maybe this sound card simply isnt supported?

Thansk

---

### Post by themusicalduck on 2010-04-03
I can't find much information about your particular card and Ubuntu. I don't see why it shouldn't work though.

Your first steps would be check sound preferences and see if the card is detected properly by Pulseaudio and listed under hardware and output. Also, it's worth typing ```
alsamixer
``` into a terminal, to see if you can change any volume levels in there that might be down to 0.

---

### Post by lidex on 2010-04-04
There are some generic issues with audio in karmic that should be ruled out. Work through this page:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

---

### Post by listerdl on 2010-04-04
thanks - in fact i solved it by another unconnected method - the problem was more complicated but thanks all the same

---

### Post by lidex on 2010-04-06
Care to enlighten us? ;)

---

### Post by listerdl on 2010-04-06
> **lidex said:**
> Care to enlighten us? ;)

Yes! Sorry about that!

Basically I had to trick Alsa into thinking that I am using a netbook.....

in this file /etc/modprobe.d/alsa-base.conf I had to add something like laptop='netbook' or something along those lines.

I am not using a laptop, i am using a panasonic CF toughbook that sems to work by tricking also into thinking it is a netbook - if that makes sense. I was following another thread on this issue as well....

If anyone has an issue with above soundcard please PM me - happy to help

I would post the exact code but i am using a different machine and currently travelling

---

