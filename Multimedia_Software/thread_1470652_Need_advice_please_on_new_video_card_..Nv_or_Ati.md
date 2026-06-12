---
title: "Need advice please on new video card ..Nv or Ati?"
date: 2010-05-03
forum: Multimedia Software
---

### Post by gordong11 on 2010-05-03
I have an old video card, Nvidia XFX 7800GT, which is now beginning to fail and I need to upgrade. I am not huge a gamer but I do play/buy games on regular basis. Right now I'm playing Eternal Lands on the Linux side. Looking to spend $100-$150 on a new card.

I have a Core2Duo Wolfdale 3.0, with 2ghz ram and run Lucid 32bit. Also run windows Vista64Ultimate on dual boot (rarely).

I would love to buy a new ATI 5770 or 5830, ATI budget cards seem to be much better for the buck over budget Nvidia cards, but I'm concerned with ATI drivers and long term with Ubuntu.

On the Nvidia side I'm considering the GTS 250. The only advantage I can find is lower power consumption with Nvidia and Ubuntu has always preferred Nvidia over ATI, as far as working drivers go.

As Far as Ubuntu and Lucid is concerned, which way is best, ATI or Nvidia? Has anything changed with ATI support, that could make theor cards more compatible now and in the future?

Thanks, :)

---

### Post by tsucol11 on 2010-05-03
> **gordong11 said:**
> I have an old video card, Nvidia XFX 7800GT, which is now beginning to fail and I need to upgrade. I am not huge a gamer but I do play/buy games on regular basis. Right now I'm playing Eternal Lands on the Linux side. Looking to spend $100-$150 on a new card.

I have a Core2Duo Wolfdale 3.0, with 2ghz ram and run Lucid 32bit. Also run windows Vista64Ultimate on dual boot (rarely).

I would love to buy a new ATI 5770 or 5830, ATI budget cards seem to be much better for the buck over budget Nvidia cards, but I'm concerned with ATI drivers and long term with Ubuntu.

On the Nvidia side I'm considering the GTS 250. The only advantage I can find is lower power consumption with Nvidia and Ubuntu has always preferred Nvidia over ATI, as far as working drivers go.

As Far as Ubuntu and Lucid is concerned, which way is best, ATI or Nvidia? Has anything changed with ATI support, that could make theor cards more compatible now and in the future?

Thanks, :)

ATI or Nvidia. That is up to you. I use an ATI 9600XT in one computer and a NV 9800GT in the other computer (don't let the numbers fool you). Both work fine. Ubuntu does seem to have better support for Nvidia drivers.
Why go for a GTS 250, You can get great value for the buck on slightly slower cards.

Brian

---

### Post by xzero1 on 2010-05-04
Consider that Nvidia is no longer supporting open source drivers.
see [http://www.phoronix.com/scan.php?page=article&item=nvidia_kills_nv&num=1]("http://www.phoronix.com/scan.php?page=article&item=nvidia_kills_nv&num=1")

ATI is supporting open source and has provided a good deal of source code to open source developers.

I currently use a radeon hd 4770 and (non flash) video playback is tearfree, compiz is fine, I can even play Nexuiz and OpenArena with no problems all with the default stock Radeon driver. I have had no lockups with xorg which I cannot say when using Karmic and the proprietary ati driver. Still, the fglrx driver is much faster and will probably be needed for wine games. The only real issue I have had with the driver is a nasty gamma bug when using a hdmi to analog dongle (which may have been fixed by now).

As to the future support this chart should give you a better idea:
[http://wiki.x.org/wiki/RadeonFeature]("http://wiki.x.org/wiki/RadeonFeature")

It should be noted here that not all cards have progressed equally.

I'm sure someone on the Nvidia side will chime in...:)

---

### Post by steveneddy on 2010-05-04
IMHO Nvidia is the way to go.

---

### Post by gordong11 on 2010-05-05
Thank you. Well I've decided to give ATI a Second chance, but that is only because they make a better budget card. Nvidia cards don't seem to be SLI capabable while 5670, and 5750 are crossfire ready. One reason I dont mind buying cheap is because i can always double up. Nvidia GT 240 and cheaper GTS 250 cards do nave SLI support. unless I go with older technology on Nv side...but why?

Ati I also get Dx11 support. I do like the XFX GTS 250, but it's $150, for the same price I can get a 5770 card!!

---

### Post by cascade9 on 2010-05-06
> **gordong11 said:**
>  Nvidia cards don't seem to be SLI capabable while 5670, and 5750 are crossfire ready. One reason I dont mind buying cheap is because i can always double up. Nvidia GT 240 and cheaper GTS 250 cards do nave SLI support. unless I go with older technology on Nv side...but why?


Only nVidia does SLI, all ATI cards that can be run in 2x mode are crossfire. The only way you can get the choice between SLI or Crossfire is with the newer Intel (iX) chipsets. 

As far as I know, all the GTS250s are SLI capable. None of the GT240s are. 

BTW...older technology, heh. The GTS250 is just a rebadged/worked over GT9800, which is just a rebadged/worked over 8800GT. 

ATI has got more bang for buck these days, so if your on a budget and want to get the highest FPS for your dollar then its probably the way to go.

---

### Post by cchhrriiss121212 on 2010-05-06
You should also consider that nvidia has vdpau hardware acceleration, which is great for 720/1080p video, and as far as I know ATI has no such feature with Ubuntu. I have a 9600gt which handles new games just fine, and can be bought fairly cheap.

---

### Post by frito on 2010-05-07
> **gordong11 said:**
> Thank you. Well I've decided to give ATI a Second chance, but that is only because they make a better budget card. Nvidia cards don't seem to be SLI capabable while 5670, and 5750 are crossfire ready. One reason I dont mind buying cheap is because i can always double up. Nvidia GT 240 and cheaper GTS 250 cards do nave SLI support. unless I go with older technology on Nv side...but why?

Ati I also get Dx11 support. I do like the XFX GTS 250, but it's $150, for the same price I can get a 5770 card!!

I hear mostly nightmares about ATI drivers. I use NVidia and its perfect, dual screen, flash everything, awesome.

Also 150$!!?!... on new egg there is a [MSI GTS 250 for 90$ after rebate]("http://www.newegg.ca/Product/Product.aspx?Item=N82E16814127495&cm_re=gts_250-_-14-127-495-_-Product")

>  currently use a radeon **hd 4770 and (non flash) video playback is tearfree**, compiz is fine, I can even play Nexuiz and OpenArena with no problems all with the default stock Radeon driver. I have had no lockups with xorg which I cannot say when using Karmic and the proprietary ati driver. Still, the fglrx driver is much faster and will probably be needed for wine games. The only real issue I have had with the driver is a nasty gamma bug when using a hdmi to analog dongle (which may have been fixed by now).

What happens when you try to see flash video? Thats pretty important?

---

### Post by xzero1 on 2010-05-07
I didn't install flash. I just use chrome and html 5. Being curious, I booted with the live cd, installed flash and tried a few youtube hd trailers and they played perfectly. There is still the mouse button problem though (it takes a bit of effort to make flash buttons respond). Be careful which card you pick if you expect similar results -- the 5xxx series support is not as complete as the 4xxx series which I have. Thats why I referenced this link:
[http://wiki.x.org/wiki/RadeonFeature]("http://wiki.x.org/wiki/RadeonFeature") in my post. Also I have a fairly 3Ghz Amd-64 quad system.

---

### Post by xzero1 on 2010-05-07
> **cchhrriiss121212 said:**
> You should also consider that nvidia has vdpau hardware acceleration, which is great for 720/1080p video, and as far as I know ATI has no such feature with Ubuntu. I have a 9600gt which handles new games just fine, and can be bought fairly cheap.

They do not have vdpau, but they do have XvBA accelerated video which I understand is supported by gnash (though I have not tried it). This is still beta and not all cards are supported. They are still behind here but are catching up.

See:
[http://ubuntuforums.org/showthread.php?t=1385896]("http://ubuntuforums.org/showthread.php?t=1385896")

---

### Post by lashram on 2010-05-07
**Well I think that this version of Ubuntu will support Nvidia and ATI graphics cards. I personally have an Nvidia chipset in my custom built laptop running Lucid 10.04. But i have used both Nvidia and ATI and have not had a problem with either one. So I guess it is a matter of your personal preference and which one is more in line with the amount of money that you are willing to invest in it. Now with my Nvidia graphics card it actually works great. Im using the development version of Wine to play my Windows games. Ive only tested my EA Sports games so far but they work just as they did under Windows. My Nvidia driver is the 195 series. I am very pleased with this distro so far. :guitar:**

---

### Post by drreed on 2010-05-14
Hi,

I'm in the same boat right now, trying to choose. In my case, I want the GPU for parallel stream processing. I'll need a card that's known to at least boot-up and give me a working desktop. My next criteria would be multiple GPU's (Crossfire or SLI). I note that several knowledgeable people have replied to this thread: Does anyone know if I can use 2 or 3 graphics cards? Google only shows articles from back around 2008, surely things have changed. Is there Crossfire support in Linux(Ubuntu) drivers?

**edit**
I'd prefer to work with open source tools such as OpenCL, and AMD/ATI - Crossfire would be my choice.

---

