---
title: "Hauppauge 1800"
date: 2010-11-16
forum: Mythbuntu
---

### Post by Tagged on 2010-11-16
Hey all!

Really trying to be an ubuntu guy for my HTPC. I have MC7 running out of the box and love it. We stopped paying for cable over a year ago and use the internet, torrents, and hulu to watch anything we cannot watch with OTA broadcasts.

CPU: AMD Athlon 64 x2 (ordered a AMD Phenom II x4 3.0GHz, should be installing this in the next couple of days)
TV Card: Hauppauge 1800
Video: EVGA 640-P2-N825-AR GeForce 8800GTS 640MB 320-bit GDDR3 PCI Express x16 HDCP Ready SLI Supported Video Card
MOTHERBOARD: ASUS M2N32-SLI Deluxe Wireless Edition AM2 NVIDIA nForce 590 SLI MCP ATX AMD Motherboard
RAM: 6GB DDR2 800 (PC26400)


Installed Mythbuntu 10.10 64 bit, could not detect any channels. Reinstalled Ubuntu 10.10 64 Bit and installed mythtv over that. Could not detect channels. Loaded the 10.04 kernal. Got card to detect channels, guide to work. No video.

I am not a linux guy. I want to be but time will not allow me to be an expert.  Is there a card I can buy that will pretty much work out of the box or has very easy copy and past instructions to get to work?

Also, is the 64 bit preventing me from using the Hauppauge 1800 card or the fact that it is pcie?

I really want to get away from windows (got my laptop over to Ubuntu 10.10, getting my wife to sign up for 10.10 on her new computer, really want to get my Media Center PC switched over!!!)

I love how windows works with our 2TB library of music, movies, and tv shows.  I would like to get something as easy to use (my wife uses this mostly, has to be wife approved and easy!).

Thanks for all of your help / recommendations!!  

Bryan

---

### Post by LowSky on 2010-11-17
If you were using Windows with out a problem, why switch? I'm not one of the Linux is awesome people. I generally tell people "use what works best for you."
I use Ubuntu and MythTv because I don't like DRM on my recorded files.


Now According to [_this _]("http://www.mythtv.org/wiki/Analog_Hardware_Encoder_Cards")your card does not work


[PCHDTV HD-5500]("http://www.pchdtv.com/") is actual designed for working with MythTV
[DViCO FusionHDTV7 ]("http://www.sundialmicro.com/dvico-fusion-hdtv-7-dual-express-tv-tuner-card_2047_1369.html")Dual Express is supprted really well
[Haupauge HVR-2250 ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815116037")is the card I use and support is a bit more involved but runs great. There is a very good tutorial on these forums (I wrote it, LOL).

---

### Post by David Grigor on 2010-11-18
If you can detect channels but cannot see video, can you clarify, are you trying to watch a recorded one or livetv. 

If your trying Livetv, you likely need to play around with the playback settings until you find one that works perhaps trying the different types of vdpau settings and cpu+, cpu++. Then try to go from there. There is a post about it a few weeks back but don't have it handy. 

I know there is a known bug for some hauppauge video cards with 10.10 ( I use the 1250 card ) where when trying to detect channels it will hang. There is a work around for that if your experience that issue to use a higher level kernel that is not currently available through updates. Here is the thread: [http://ubuntuforums.org/showthread.php?t=1593695](http://ubuntuforums.org/showthread.php?t=1593695) There isn't an official fix for it yet but has been stable for me for about 3 weeks.

---

