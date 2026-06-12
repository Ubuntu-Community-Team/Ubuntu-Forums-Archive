---
title: "ATI or Nvidia? Help needed..."
date: 2009-11-22
forum: Mythbuntu
---

### Post by Man-O-Leisure on 2009-11-22
I have just built a new system, which i want to run Mythtv on. O only have an old TV so i need a graphics card with TV-out with svideo. I have always used ATI cards, but someone just told me that ATI doesnt work well with Linux and that i should get a Nvidia card.. Is this true?

I currently have an ATI HD4650 which i am using with Windows 7 Media centre, works fine but it is way too loud for my what was silent system befire using this card...

So, does anyone know of a cheapish video card i can get with svideo out that will be good enough for HDTV playback and Bluray, and silent is preferable..?

Thanks guys

---

### Post by ian dobson on 2009-11-23
Hi,

Have a look for a NVIDIA 9300/9400 passive cooled card. I'm currently running one in my dedicated frontend and can watch HD (1080p) without any problems thanks to VDPAU (hardware acceleration of video playback under linux). Even when watching HD video the CPU load is only 10-20% on an underclocked E5200 (1.2GHz).

Although ATI cards are not that bad the Linux drivers have been really bad in the past. Their getting better but their not up there with NVIDA.

You should be able to pickup such a card for about 50$ US.

Regards
Ian Dobson

---

### Post by wolfdale on 2009-11-23
From my experience, 9500GT and 9800GT (both passive) work flawlessly on Jaunty and Karmic using Nvidia driver. My HD4850 (ATI card) did not work well with Jaunty. ATI's video driver (fglrx) produced video tearing, compiz lockups and power saving mode that doesn't work correctly (monitor still on with black screen). I spent several months trying to get it to work. The open-source driver was a little better with my ATI card but didn't support 3D at that time (6 months ago). I went with Nvidia and now all my video problems are gone.

---

### Post by mmalone21 on 2009-11-23
I too have had many issues with ATI cards I would go for an NVIDIA video card for Ubuntu.

---

### Post by Dark_Stang on 2009-11-23
The new ATI hardware is flat out amazing and beats nVidia's hands down. But ATI's drivers still suck, so nVidia is still winning the practical race.

---

### Post by Man-O-Leisure on 2009-11-23
Thanks for all the replies.. Just one thing, do these cards you guys are mentioning have svideo? i seem to find a few different silent cards, but none seem to have svideo

---

### Post by efball3 on 2010-11-09
> **Man-O-Leisure said:**
> Thanks for all the replies.. Just one thing, do these cards you guys are mentioning have svideo? i seem to find a few different silent cards, but none seem to have svideo

Zotac ZT-94TEH2P-FSR 9400GT (with fan) or ZT-94TEH2P-FSL 9400GT (no fan). They have S-video and component video.  I use the model with the fan (it's lower profile and not that loud).

---

### Post by P4man on 2010-11-09
You can get an even cheaper solution buy buying something like a 8400GS on ebay (some places even sell them new still). Thats the lowest end card that supports VPDAU (video accelerated decoding, which you really need for bluray). Costs next to nothing and has s-video. Similar thread here:
[http://ubuntuforums.org/showthread.php?t=1601253&page=2](http://ubuntuforums.org/showthread.php?t=1601253&page=2)

anyway, your friend was right. AMD have good hardware, but their drivers are a mess, especially on linux. And GPU decode is all but impossible to get working.

---

### Post by LowSky on 2010-11-10
Dont get an 8400, yes it supports VDPAU but not as ell as a GT220 or 240 can. If you can go newer the newer the card the more features supported. My 8600 was ok but had issues with video failing to play due to VDPAU.

---

### Post by nickrout on 2010-11-10
I have a fanless low profile GT220 and it is the bees bloody knees. Takes up two slots with an enormous heatsink, but it fits in my SFF case and i am happy.

BUT the OP wants something with analogue out. AFAIK such things are not available in 220/240 range.

People who still want analogue but want a decent video card are very rapidly being left in the dust.

---

### Post by LowSky on 2010-11-10
S-video... ouch.. a bit tougher but still availible on some cards

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709+600026339+600030348&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=48&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709+600026339+600030348&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=48&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)

---

### Post by nickrout on 2010-11-10
And as i said, none are 220 or 240's

---

### Post by haiko2201 on 2010-11-10
> **Man-O-Leisure said:**
> I have just built a new system, which i want to run Mythtv on. O only have an old TV so i need a graphics card with TV-out with svideo. 


So, does anyone know of a cheapish video card i can get with svideo out that will be good enough for HDTV playback and Bluray, and silent is preferable..?



svideo and HDTV - no (HDMI or DVI needed)
Linux and Blueray -no (Win or MAC needed)


haiko2201

---

### Post by LowSky on 2010-11-10
> **haiko2201 said:**
> svideo and HDTV - no (HDMI or DVI needed)
Linux and Blueray -no (Win or MAC needed)

I think he meant for future upgrades. most newer card have DVI or HDMI and Bluray can work... but only through very no so legal ways in some cases


> **nickrout said:**
> And as i said, none are 220 or 240's

I was just listing cards with S-video, your right none of the 220 or 240 have s-video but the 250-260's do. And there seems to be a few 8xxx and 9xxx cards on that list too.

---

### Post by nickrout on 2010-11-10
> **haiko2201 said:**
> svideo and HDTV - no (HDMI or DVI needed)
Linux and Blueray -no (Win or MAC needed)


haiko2201

wrong, Bluray - yes, support in Mythtv 0.24

[http://www.gossamer-threads.com/lists/mythtv/users/443442#443442](http://www.gossamer-threads.com/lists/mythtv/users/443442#443442)

[http://www.mythtv.org/wiki/Release_Notes_-_0.24](http://www.mythtv.org/wiki/Release_Notes_-_0.24)

AND component does HD!

---

