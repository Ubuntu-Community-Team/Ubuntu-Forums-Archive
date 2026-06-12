---
title: "Help picking the best video card for my system"
date: 2015-05-30
forum: Mythbuntu
---

### Post by benlyboy on 2015-05-30
Hi I am after some help and advice on what is the best video card to buy for my mythbuntu 14.04 system. The system I am looking to upgrade is at present using on board nvidia 8200, this has worked well for about 5 years. but I have just completed a system overhaul, in which i changed out the 4 analog tuner and replaced them with 2 HDhomerun primes, which mean I now have at least some HD content. I find that the play back of HD isn't as good as it should be and with the extra load on the system of 2 more tuners I think it is time to update  the video.


So this is what I’m looking for a card that has the following.

PCI express or PCI express 2.0.

Something quiet( maybe not silent but quiet )

Something that isn't going to be a pain to install.(driver support)

Finely something that has enough processor and memory to take as much of the load off the CPU as I can.

Would be grateful for any ideas thanks

---

### Post by SeijiSensei on 2015-05-30
Pretty much [any recent NVIDIA card]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%208000%20600030348&IsNodeId=1&bop=And&ActiveSearchResult=True") should do the trick, especially if you're primarily interested in video rather than gaming.  The proprietary driver includes support for VDPAU, NVIDIA's method for off-loading video decoding to specialized circuitry in the graphics chip.

---

### Post by benlyboy on 2015-05-30
thanks SeijiSensei for the reply
this seems like a good buy, what your toughts on it
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814500368](http://www.newegg.com/Product/Product.aspx?Item=N82E16814500368)

---

### Post by SeijiSensei on 2015-05-30
Looks like a pretty good deal, especially with 4 GB and silent running.  I don't have a monitor that uses DisplayPort, and I'm unlikely to own one any time soon, so HDMI is fine with me.  The last card I bought was an NVIDIA 9500GT from XTX, a step up from the 8200 you have onboard now.  That worked fine, but the machine it was in died.  Now I have an i5 with standard Intel HD graphics.  It plays 1080p files in 10-bit H.264 and streams from places like Netflix as well.  

Before investing in a new card, though, I'd play a couple of your most demanding files with a terminal window open running the "top" command.  Watch and see what happens to your load average.  On my all-Intel machine a 1080p Blu-ray rip pushed the load average up from 0.3 to 1.3, but that is still well below the level where you'd start to see performance degradation.  

I assume you're using the proprietary NVIDIA driver now, yes?  And using a player that knows how to take advantage of VDPAU?  I don't know much about myth, so I don't really know what it uses to play files.  I've used SMPlayer for years now, with mplayer and now mpv as the player engine.

---

### Post by benlyboy on 2015-05-30
ok thanks SeijiSensei
what about driver support, am I going to have to stand on my head to get this to work in my system?

---

### Post by SeijiSensei on 2015-05-30
You should be using the proprietary driver already with your 8200.  As I said, if you're not using it now, you should install it on your current machine before investing in new hardware.  Find the "Driver Manager" application.  It's inside System Settings on my Kubuntu machine, but it could be somewhere else on other flavors.  Or just install the driver from the command prompt with:
```

sudo apt-get update
sudo apt-get install nvidia-current

```
That will install the driver; you'll need to reboot to activate it.

NVIDIA has always provided excellent support for Linux.  I only use AMD/ATI hardware when I have no other option available.

---

### Post by benlyboy on 2015-05-30
hay SeijiSensei thanks for the good advice.

i will go ahead and order the card...thanks again

---

### Post by khPWXxF on 2015-06-01
[SIZE=3][COLOR=#000000][FONT=Calibri]A comment on 8x00 cards:
[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Calibri]I found the later nvidia drivers to be totally unstable with  both 8300 and 8400 graphics and I imagine 8200 to be the same.  I understood that they considered these to be obsolete and no longer supported.  Downgrading to 304 restored stability.[/FONT][/COLOR][/SIZE]

[[FONT=Calibri][SIZE=3][COLOR=#0000ff]http://ubuntuforums.org/showthread.php?t=2220827[/COLOR][/SIZE][/FONT]]("http://ubuntuforums.org/showthread.php?t=2220827")

[SIZE=3][COLOR=#000000][FONT=Calibri]hth[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Calibri]Phil[/FONT][/COLOR][/SIZE]

---

### Post by SeijiSensei on 2015-06-01
You can install the 304 driver with:
```

sudo apt-get install nvidia-304

```
rather than nvidia-current.  I now recall having to do that for an netbook with an NVIDIA ION processor, akin to a 9500.

---

### Post by benlyboy on 2015-06-07
Yes with my current 8200 video I had to install 304 To stop it a problem with it crashing when ever I tried to play video, I had a post on it.

---

