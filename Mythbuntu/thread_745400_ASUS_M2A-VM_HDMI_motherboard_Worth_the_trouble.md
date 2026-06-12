---
title: "ASUS M2A-VM HDMI motherboard: Worth the trouble?"
date: 2008-04-04
forum: Mythbuntu
---

### Post by dsbw on 2008-04-04
I've been trying to find the "perfect" motherboard for my mythtv set up and the "asus m2a-vm hdmi" looks great on paper. But I've read that a lot of people have had trouble with it.

As always, there's a sort of archeology that goes along with figuring out whether something will work or not. In one case it seemed to be a physical hardware problem, in another case a newer driver, and [this one implies]("http://ubuntuforums.org/showthread.php?t=595081") you need to do a little hacking....

So...can anyone enlighten me? Is this thing really going to work and give me my choice of TV-out, HDMI out, DVI out...

And is 64-bit mandatory or just supported? (Looks like the latter.)

---

### Post by daviding on 2008-04-05
This doesn't necessarily answer your question, but I've got an Asus P5E-VM HDMI working with Mythbuntu.

We had some problems installing the board into the case -- we eventually had tech support at Canada Computers do the installation -- but that could be due to our inexperience rather than anything with the board.  (There was something about not installing risers properly, so that that board was shorting out).

---

### Post by majoridiot on 2008-04-05
> **dsbw said:**
> I've been trying to find the "perfect" motherboard for my mythtv set up and the "asus m2a-vm hdmi" looks great on paper. But I've read that a lot of people have had trouble with it.

As always, there's a sort of archeology that goes along with figuring out whether something will work or not. In one case it seemed to be a physical hardware problem, in another case a newer driver, and [this one implies]("http://ubuntuforums.org/showthread.php?t=595081") you need to do a little hacking....

So...can anyone enlighten me? Is this thing really going to work and give me my choice of TV-out, HDMI out, DVI out...

And is 64-bit mandatory or just supported? (Looks like the latter.)

although not a technical consideration, i thought i would express my opinion- on asus in general.

after building literally a hundred or more computers over the last decade using nothing but asus
mobos, i turned my back on them last year after a series of sad and ridiculous issues with a bios 
update.

i got next to *zero* actual support from their tech support- and the info i did get was wholly
incorrect.  they jerked me around for two weeks, bouncing me back and forth between
departments before i finally had to send them back the mobo for replacement...
getting stuck for shipping costs on an IN-WARRANTY board mind you.

the replacement was DOA and a total POS.  asus' reaction was more or less "Meh. 
send it back and we'll try sending another".

at that point, i more or less told the customer "service" rep where he could stick their
remaining stock and went out and bought a gigabye board... which i have been
building with exclusively since and could not be happier.

just wanted to give you a heads-up that asus may not be the best choice- especially
if there are known technical/driver considerations going into it.  asus support is horrible
and (at least in my experience) their position was "linux is not supported, so yer on yer own."

hope you find the perfect mobo for the build!

---

### Post by dsbw on 2008-04-07
Well, I might be able to dismiss a single claim (no matter how bad) as a fluke, but it looks like you're not alone. There are a lot of ASUS (in general) complaints floating around the MythTV universe.

A shame. I really was hoping to find a motherboard with both digital and analog video/audio out.

---

### Post by Trollslayer on 2008-04-11
> **dsbw said:**
> Well, I might be able to dismiss a single claim (no matter how bad) as a fluke, but it looks like you're not alone. There are a lot of ASUS (in general) complaints floating around the MythTV universe.

A shame. I really was hoping to find a motherboard with both digital and analog video/audio out.

Abit I-90F, it is Intel CPU but works great (once I get the HDMI sound working...)

---

### Post by seapahn on 2008-04-19
ATI now has pretty decent suport for the x1250 video chipset on the m2a-vm. That combined with decent support for audio through the ALSA drivers make the m2a-vm a decent choice given the price point and the features it comes with (I am using it as home theater application). The way I have it set up is have primary video output through HDMI on my 42" LCD tv and secondary (dual head) video on a 19" LCD through DVI. 

64-bit is the way I went though I am running 32-bit firefox mainly due to some plug-ins and java (not m2a-vm related). 

If you were asking this question in 2007, I would have said stay faaaaaaaaar away from this board but now, it works fine (under Gutsy at least).  The only thing I don't have working is audio through HDMI but it's a non issue since I am running audio through the digital SPDIF connection directly to my amp. That bug seems to be something that is currently being addressed by ALSA but I haven't tried the latest latest developmental drivers ... I'll probably wait for their next stable release (I did try a driver back in mid february but that still didn't get the hdmi audio to work).

---

### Post by the plague on 2008-05-19
> **seapahn said:**
> ATI now has pretty decent suport for the x1250 video chipset on the m2a-vm. That combined with decent support for audio through the ALSA drivers make the m2a-vm a decent choice given the price point and the features it comes with (I am using it as home theater application). The way I have it set up is have primary video output through HDMI on my 42" LCD tv and secondary (dual head) video on a 19" LCD through DVI. 

64-bit is the way I went though I am running 32-bit firefox mainly due to some plug-ins and java (not m2a-vm related). 

If you were asking this question in 2007, I would have said stay faaaaaaaaar away from this board but now, it works fine (under Gutsy at least).  The only thing I don't have working is audio through HDMI but it's a non issue since I am running audio through the digital SPDIF connection directly to my amp. That bug seems to be something that is currently being addressed by ALSA but I haven't tried the latest latest developmental drivers ... I'll probably wait for their next stable release (I did try a driver back in mid february but that still didn't get the hdmi audio to work).

could you please explain your xorg.conf file to me ..i am running the same MB in mythbuntu and can not get it to work out the TV out put...please help i would love to get this board working ...

---

### Post by saarbuntu on 2008-05-20
> **seapahn said:**
> ATI now has pretty decent suport for the x1250 video chipset on the m2a-vm. 

What driver version are you refering to? 

Do you get those weird diagonal lines every once in a while during video playback?

Cheers

---

### Post by uncle hammy on 2008-05-20
I'll second majoridiot with having built a lot of systems over the years using ASUS boards, and having nothing but trouble with them recently. I have gone to Gigabyte as well, and am rather pelased.

---

