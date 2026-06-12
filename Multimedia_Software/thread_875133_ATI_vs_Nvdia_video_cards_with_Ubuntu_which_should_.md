---
title: "ATI vs Nvdia video cards with Ubuntu: which should I go for ?"
date: 2008-07-30
forum: Multimedia Software
---

### Post by Browser_ice on 2008-07-30
I currently have an ATI card and on a few occasions I have seen mentions that on some Ubuntu softwares, ATI is not supported. I do not recall seeing the same mentions with Nvidia.

So since I am starting to think about replacing my video card and move further into Linux, which one should I go for in terms of having the lease amount of problems with Ubuntu (current and future versions) and Why ?

---

### Post by chalewa on 2008-07-30
what do you use your computer for?

---

### Post by Browser_ice on 2008-07-30
3d graphic designs, 3d softwares, creating textures and a bit of gaming

---

### Post by ilovelinux33467 on 2008-07-30
probably nvidia. Just make sure you install the restricted driver :)

---

### Post by Browser_ice on 2008-07-30
But why go with Nvidia ?

I mean, is it somehow forseen that ATI support on any/most Ubuntu softwares will not be done or unlikely done ?

If this is a trend due to better support on Nvidia vs Ubuntu, then a general statement should be made to advise the community.

---

### Post by chalewa on 2008-07-30
i have not used nvidia extensively under linux, but  my ati card (x600) sucks.

---

### Post by toolzen on 2008-07-30
Why use nvidia? Generally, from my experience and what I've read, nvidia generally works better on linux than ATI. Also, as a gamer, I have always had better "pretty" with nvidia. If you are going to be doing graphics design, you should really check this out:

[http://www.nvidia.com/object/tesla_computing_solutions.html](http://www.nvidia.com/object/tesla_computing_solutions.html)

---

### Post by Browser_ice on 2008-07-30
> **toolzen said:**
> If you are going to be doing graphics design, you should really check this out:

[http://www.nvidia.com/object/tesla_computing_solutions.html](http://www.nvidia.com/object/tesla_computing_solutions.html)

I'm just an average Joe like you. I don't have the money for this. Plus, my current MB is AGP. I do not have the money to do a full upgrade. So I have to consider in advance updradign little by little.

I do graphic designs as a hobby and building up a portfolio to maybe one day work in it.

---

### Post by toolzen on 2008-07-30
I bought a PCI nvidia 5500 256 meg card to play everquest 2 with - cost me 70 bucks new. It's a very good card for a PCI. You can get an AGP for around the same price I would guess - AGP is of course faster bandwidth than a PCI (non-express anyway). Since you're going AGP, it is safe to say you would be getting a card that is probably, by now, well supported - so as far as drivers go you would probably be safe with either ATI or Nvidia. I would still recommend nvidia - even if you can't afford a tesla, their chips are just good...

---

### Post by sloggerkhan on 2008-07-30
If you want more nuanced opinions, I'd say the place to ask is [http://www.phoronix.com](http://www.phoronix.com) . They specialize in Linux GPU stuff.

Off hand, as an individual who owns both a geforce 8600 gt and an x700 mobility and has plenty of experience with ATI's fglrx and the proprietary nvidia driver, I would tell you to go Ati at this point in time. 

My experience is that with new Ati cards you will probably have the card supported at or within a month of release, there's an updated driver every month, it's easy to install and makes its own *.deb files that can be installed like any other package, you have a choice of 1 or 2 open source drivers in addition to the proprietary one, if it's an older card, the open source driver may even have 3-D support, video playback is superb using open gl (this has more CPU load) or as good, if not a little better than the nvidia driver, using xv. In my opinion, Ati/AMD is clearly the company making linux support more of a priority and adding features. Further, they have a dev on the phoronix forums and I can attest from personal experience that if you have an actual bug/driver issue and bring it up, there is a good chance that it will be gone in the driver release 1 to 2 months from when you point it out.

My experience with nvidia is that it works, provides good 3-D, slightly worse video than Ati, has somewhat better modesetting support and related GUI, but is also trickier to install (without envy, anyhow, IMO), and clearly has less energy getting put into it. Plus there aren't really any fully functional open source drivers.

---

### Post by Vakman on 2008-07-30
I am finding I am having trouble with the ATI drivers on Linux distros currently. When this computer had a nVIDIA card, the drivers work without a problem really. I suggest nVIDIA, I will never buy an ATI card again.

---

### Post by sloggerkhan on 2008-07-30
> **Browser_ice said:**
> I'm just an average Joe like you. I don't have the money for this. Plus, my current MB is AGP. I do not have the money to do a full upgrade. So I have to consider in advance updradign little by little.

I do graphic designs as a hobby and building up a portfolio to maybe one day work in it.

Doing graphic design on linux using things such as gimp and inkscape, my experience is that more RAM will pay much more than your GPU in terms of benefit, particularly as you work with higher resolution images.

As to installing ati's fglrx, all you need to do is make sure the repo driver is purged, then run ati's installer with the build package for ubuntu option. It create 2 or 3 *.deb files that you install, and after they're installed, do a dpkg reconfigure of xorg, select fglrx, restart x (or reboot), and you should be good to go.

---

### Post by mrreality13 on 2008-07-30
I would go for Nvidia as they are a card with stronger support base Yes ati is starting to be more linux friendly but why deal with the headaches of a card that Could become time consumptive in its set up.
look at this for a reasonably priced alternative
[HTML]http://www.newegg.com/Product/Product.aspx?Item=N82E16814150107[/HTML]

---

### Post by SunnyRabbiera on 2008-07-30
Nvidia is a good bet, ATI is seriously behind in its linux support.

---

### Post by ModdTaco on 2008-07-30
All depends. My old ATI x600 was great for most games right up to and beyond Half-Life 2 Ep2. It would probably be just as good for 3d design. That would be your cheapest route. However for only about $200 your can go with a Nvidia 8800GT. I'm very pleased with mine and it worked right out of the box with Ubuntu. A 8800GT is a great buy if you only plan on doing 3d or 2d graphic designs more often. Still I think for you a x600 or something like it is your best choice. Remember RAM helps out alot in graphic design too. Mind you Linux has swap so low RAM is ok. I've custom built most of my computer and I've only spent about $900. Investing into something with a PCI Express x16 is a good future investment. Exp since there getting quite cheap.

---

### Post by ModdTaco on 2008-07-30
Oh the  ATI x600 worked out of the box with Ubuntu too.

---

