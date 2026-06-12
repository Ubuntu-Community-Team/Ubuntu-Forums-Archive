---
title: "GeForce 9800 GT - Good Card to get?"
date: 2010-06-26
forum: Mythbuntu
---

### Post by usererror on 2010-06-26
I am looking to replace my ATI 4350 radeon card.  I am tired of the tearing in videos for my myth front end.  I've tried serveral fixes having to do with vsync's and other things.

I'm looking at this video card at NewEgg:

EVGA 01G-P3-N988-TR GeForce 9800 GT HDMI 1GB

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130534](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130534)

Has anyone had success with it?  I'd hate to get it and find out tearing issues. :)

Thanks in advance!

---

### Post by cascade9 on 2010-06-26
If its just for a mythTv box, dont get a 9800GT. They are good cards, but they are 'gamers' cards- high clock speeds, power use and heat output. 

You would better off with a GT220/GT240. Not as fast for gaming, but better VDPAU features, etc. 9800, feature set 'a', GT220/240, feature set 'c'. 

[http://en.wikipedia.org/wiki/Nvidia_PureVideo](http://en.wikipedia.org/wiki/Nvidia_PureVideo)

---

### Post by ian dobson on 2010-06-26
Hi,

9800gt is abit too much (if it's what you can get then why not). I have an underclocked 9600gt (bios hack for 450MHz clock) and it's more than enough for h264 video playback (BBC HD) on my underclocked c2d (e5200 @ 1GHz).

The most important thing is to get a passive cooled card, fan noise when watching TV can really **** you off.

Regards
Ian Dobson

---

### Post by usererror on 2010-06-26
Thanks for the input.  The GT240 is only $70 after a rebate here:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814125305&cm_re=gt240_1gb-_-14-125-305-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16814125305&cm_re=gt240_1gb-_-14-125-305-_-Product)

I'm not worried about active vs passive cooling.  The actual front end box is in a hidden closet that I ran HDMI and powered USB repeaters to the room where the TV screen actually is.

So this brings the next question.  Does Nvidia's HDMI Sound out work out of the box?  I had to do some tweaking that was listed on a blog out there to get the HDMI sound to work on the ATI card I'm using now.

---

### Post by epi 1:10,000 on 2010-06-26
The gt240 hdmi sound will be supported in ubuntu 10.10.  Until then you have to install the new alsa drivers.  
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)
[http://www.mythtv.org/wiki/NVidiaProprietaryDriver#HDMI_audio_on_GT210_and_GT220_cards](http://www.mythtv.org/wiki/NVidiaProprietaryDriver#HDMI_audio_on_GT210_and_GT220_cards)

---

### Post by pootle1 on 2010-06-27
I have a GT220 and it works very well with Mythtv and copes well with Blu-ray HD data rates. (although I don't use sound over HDMI at the moment.)

There have been problems with sound over HDMI though with the nvidia drivers / alsa, so you will need to get some later versions than are standard in latest ubuntu.

Loads more info is available on the nvnews website - try [this thread]("http://www.nvnews.net/vbulletin/showthread.php?t=143610") for starters.

---

### Post by BigSilly on 2010-06-27
I have a 9800GT and have to say it's been fantastic on Ubuntu. No tearing videos (though I did have to tweak some settings - search the forums for help), and lovely Compiz/AWN effects and the games run fine. I also run Windows though and it's great for gaming there too.

---

### Post by Detonate on 2010-06-27
I have an EVGA Nvidia GeForce 9500.  I has onboard cooling.  It has handles every thing I throw at it flawlessly.  It idles at about 60 Centigrade and only climbs slightly when I am working it hard.  I'm not a gamer, but I do a lot of video editing.  It has the SLI feature but I only have one card, so I am not using it.

---

### Post by novellahub on 2010-06-28
> **usererror said:**
> Thanks for the input.  The GT240 is only $70 after a rebate here:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814125305&cm_re=gt240_1gb-_-14-125-305-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16814125305&cm_re=gt240_1gb-_-14-125-305-_-Product)

I'm not worried about active vs passive cooling.  The actual front end box is in a hidden closet that I ran HDMI and powered USB repeaters to the room where the TV screen actually is.

So this brings the next question.  Does Nvidia's HDMI Sound out work out of the box?  I had to do some tweaking that was listed on a blog out there to get the HDMI sound to work on the ATI card I'm using now.

I have this GT 240 card:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130533](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130533)


It took me a bit to figure out getting HDMI audio to work but I got it going.  I had to upgrade ALSA and set up a asound.conf file. I documented on getting it working in my Mythtv blog.

---

### Post by usererror on 2010-07-06
I just picked up the GT220.  It was on Tiger Direct via SlickDeals for $20 after rebates. w00t!

---

