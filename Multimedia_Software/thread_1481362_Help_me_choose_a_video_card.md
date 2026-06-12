---
title: "Help me choose a video card"
date: 2010-05-12
forum: Multimedia Software
---

### Post by gap on 2010-05-12
I need a video card that should have no compatibility problems with Ubuntu. I hear that Lucid has switched to a different driver for nVidia, which has incomplete support for some card features. I’m not sure what to choose anymore.

My needs are simple: the card should work (fully) out of the box, accelerate HD video, and work well with Compiz. I don’t care about games, so I don’t want an expensive card. Preferably, the card would have passive cooling.

Does anybody here use Asus Radeon HD4350 Silent with Ubuntu 10.04? Is it well supported?

Thanks in advance.

---

### Post by Paradoxfox93 on 2010-05-12
I'm gonna wager you mean ATI Radeon HD 4350.  On the off chance your thinking about an ASUS mobo with that as integrated or something I wouldn't recommend it personally.  ASUS offers a lot of features with their mobos & BIOS but have read about a lot people having frustrations with them, DOA's, shoddy manufacturing and otherwise generally unreliable products and customer service.  I might be wrong as I'm only basing it on Newegg reviews tbh but I won't be buying one of their mobos for the system I'm building.

I've been researching HD capabilities myself for my own HTPC and it seems that ATI has come leaps and bound from where it used to be in offering Linux compatibility over the last few years but I've not found any reports of success with this card.

I'd go with this product for a few extra bucks if you want guaranteed compatibility with quality performance and are on a budget that doesn't need to consider gaming purposes.

[http://www.phoronix.com/scan.php?page=article&item=sparkle_9500gt&num=1](http://www.phoronix.com/scan.php?page=article&item=sparkle_9500gt&num=1)

---

### Post by gap on 2010-05-12
There’s a video card by Asus with that ATI chipset (not integrated with the mobo) that fits my needs, I just don’t know how well it’s supported by Ubuntu.

Thanks for your opinion and suggestion, Paradoxfox93.

---

### Post by Paradoxfox93 on 2010-05-12
Twice the price but you can have native linux support with:

[http://pchdtv.com/](http://pchdtv.com/)

---

### Post by Objekt on 2010-05-12
I don't think that's quite what the OP wanted.  The pcHDTV card is not a video card, but a TV capture card.  It merely captures HDTV signals, either broadcast or cable (provided it's unencrypted cable), so that you can either record it or watch it on your computer.  You'd still need a video card.

What does "HD acceleration" mean exactly?

I have a slightly old video card (see signature).  I don't know that it does "HD acceleration," though it does have an HDMI output and does HDCP over the DVI link.  I have no trouble at all watching HD content under Windows XP/7 or Ubuntu 9.10, using the Nvidia drivers.  I have even watched a movie, "Gamer," in all the glory of full 1080p HD.

---

### Post by Paradoxfox93 on 2010-05-12
You're right, I had a brain fart there thanks for check..

I also may have goofed on the sparkle.  If you need HDMI output the sparkle doesn't offer this.

---

### Post by cchhrriiss121212 on 2010-05-12
I installed an Ubuntu system the other week with an Asus silent 4350 which went OK, but I did not try out any HD video. ATI cards now have hardware acceleration but it seems [more complicated]("http://ubuntuforums.org/showthread.php?t=1385896") than with nvidia now that vdpau is working out of the box in lucid. 
I would look for an nvidia 8600/9600 series which can be had for a similar price to the 4350 and will handle all you need with less fiddling.

---

### Post by VastOne on 2010-05-12
I build machines for ppl daily and I exclusively use a nVidia 9500 chipset 1 gig card and newegg has those from 55-65 US dollars all the time.  [_[COLOR="Red"]Here[/COLOR]_]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130395")

I am now installing Lucid on everything and the restricted driver that is installed with Lucid is the most current supported driver, 195.36.24. It is the same driver I have had the most stable sytems with, in other words, no issues.

I will not install anything but these for the same type of sytem you described. Work, school, church and home and no big game needs.

Hope this helps

---

### Post by ratcheer on 2010-05-12
> **VastOne said:**
> 
I am now installing Lucid on everything and the restricted driver that is installed with Lucid is the most current supported driver, 195.36.24. It is the same driver I have had the most stable sytems with, in other words, no issues.



I have been waiting for the 195.36.24 driver since last week and it is not coming to me from the repos. Are you installing it manually, or do I need to do something else to get it from the repos?

Thanks,
Tim

---

### Post by Yellow Pasque on 2010-05-12
Get an nvidia G210 or GT220/240. Those are the best cards for HD video playback: [http://en.wikipedia.org/wiki/Nvidia_PureVideo#Table_of_PureVideo_.28HD.29_GPUs](http://en.wikipedia.org/wiki/Nvidia_PureVideo#Table_of_PureVideo_.28HD.29_GPUs)

---

### Post by gap on 2010-05-12
Many thanks to all for the generous advice.

---

### Post by VastOne on 2010-05-12
> **ratcheer said:**
> I have been waiting for the 195.36.24 driver since last week and it is not coming to me from the repos. Are you installing it manually, or do I need to do something else to get it from the repos?

Thanks,
Tim

I am sorry Tim, I was just able to check at home and the drivers from restricted that are loaded and working perfectly for me is 195.36.15

---

### Post by WinterRain on 2010-05-12
> **VastOne said:**
> I exclusively use a nVidia 9500 chipset 1 gig card and newegg has those from 55-65 US dollars all the time.

That exactly what I use. Works great. It will actually handle 3D gaming pretty well.

---

### Post by Paradoxfox93 on 2010-05-13
> **vastone said:**
> 
i will not install anything but these for the same type of sytem you described. Work, school, church and home and no big game needs.

Hope this helps

hd?

---

### Post by VastOne on 2010-05-13
> **Paradoxfox93 said:**
> hd?

Yes

---

### Post by ratcheer on 2010-05-13
> **VastOne said:**
> I am sorry Tim, I was just able to check at home and the drivers from restricted that are loaded and working perfectly for me is 195.36.15

Thanks for replying. That is the version I have, now. I have downloaded ~.24 from nvidia, but I am hesitant to try a manual installation on Lucid because of reading all the threads where people have so much trouble doing it.

Tim

---

### Post by cascade9 on 2010-05-13
> **Temüjin said:**
> Get an nvidia G210 or GT220/240. Those are the best cards for HD video playback: [http://en.wikipedia.org/wiki/Nvidia_PureVideo#Table_of_PureVideo_.28HD.29_GPUs](http://en.wikipedia.org/wiki/Nvidia_PureVideo#Table_of_PureVideo_.28HD.29_GPUs)

I'd get the GT220 myself. Unless you cant afford the GT220, then just a 9500/9400/8400 would be fine. 

> **ratcheer said:**
> Thanks for replying. That is the version I have, now. I have downloaded ~.24 from nvidia, but I am hesitant to try a manual installation on Lucid because of reading all the threads where people have so much trouble doing it.

Tim

Unless the 195.36.24 drive offers you something that the 195.36.15 driver doesnt, its not worth the effort to upgrade the drivers IMO.

---

### Post by gap on 2010-05-18
So in case somebody else stumbles upon this thread with the same needs as mine, here are my thoughts post-purchase.

I was going to get an ATI card, based on the assumption that they&#8217;re more Linux-friendly. However, based on the advice provided by the helpful people on this forum, I got this card:

[http://www.gigabyte.com.tw/Products/VGA/Products_Overview.aspx?ProductID=3188](http://www.gigabyte.com.tw/Products/VGA/Products_Overview.aspx?ProductID=3188)

I picked it because it has the GT220 processor, which supports PureVideo/VDPAU for accelerating HD video.

HD video plays very well on my system, no instance yet of jittering or such. However, I&#8217;m not sure this is necessarily because of the video card. I have a Core i7 CPU, and even with the default non-proprietary driver installed by Ubuntu (which presumably does not support the card acceleration features), HD video was smooth.

My other requirement, that the video card should be silent, was not met. The cooler on this card was by far the noisiest part in my system. I have detached the cooler and rely on the card&#8217;s heat sink.

With respect to Linux compatibility, the card is well supported. The default driver installed with Ubuntu is functional, but there&#8217;s no support for Compiz. There&#8217;s a proprietary driver from nVidia, which does support Compiz. Just remember to manually reinstall the driver after each kernel update.

As a conclusion, since I&#8217;m not interested in gaming, I think the card is overkill. If I were to buy today, I would probably get a cheaper passively cooled card.

Thanks again to everyone here for their advice.

---

### Post by kevin.jones on 2010-05-28
Ok. I am kind of new to Ubuntu. I have played with it in the past, but I am now trying to replace my Windows 7 machine with Ubuntu 10.4. The problem is I have an older motherboard/video card setup. I have a Biostar M7NCD and a GeForce MX4000 video card. I am having trouble with the card. I can either have accelerated graphics at 800x600, or 1024x760 and no acceleration. It is an 8x agp card. basically, I want a new card, and I am trying to find the most "Ubuntu Friendly" one out there. What 8x AGP could someone recommend?

---

### Post by gap on 2010-05-30
Kevin, my recently bought video card is only Ubuntu-friendly because there is a driver from nVidia for it (which Ubuntu does not install by default).

Rather than looking for another old video card in the same category, I would recommend that you look for the right driver for the one you already have. Start here:

    [http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)

There does appear to be a driver for GeForce4 MX 4000. I would download that and run the installer.

---

