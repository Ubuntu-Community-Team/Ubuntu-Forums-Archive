---
title: "UShare streaming problem with HD Video"
date: 2009-04-07
forum: Multimedia Software
---

### Post by blaise69 on 2009-04-07
Hi guys,

I'm having some problems with UShare that I'm having difficulty debugging.

I use it to stream video from my Desktop to my Xbox via a router, my Desktop is wired to the router, and my Xbox connects via Wifi.

UShare runs flawlessly with standard definition video, or file sizes of about 700MB say. But anything that's High Definition video, for example a 720p TV episode that I have at about 1GB will more often than not freeze once during playback.

I say freeze, but what actually happens is that the XBox loses connection to my UShare.

I try and restart it, the same way that I start my service.
```
sudo /etc/init.d/ushare restart
```
It reports that stopping and starting has been [OK], but in actual fact it hasn't stopped the service.

I try and use my web browser to view my shares but this times out, and system monitor fails to kill the process.

The only way I've found to get going again is to reboot my machine, and I don't like doing this.

Can anyone offer any suggestions or solutions for this?

Cheers,

Blaise.

---

### Post by billzeeabob on 2010-02-06
I am having the same problem. Did you find a solution?

---

### Post by shwerm601 on 2010-02-27
I just setup ushare and can stream videos of any size 100mb - 3Gbs or so.  Although none are true 720p streams but did want to at least comment that any file size worked fine streaming.

---

### Post by cbarnesro on 2010-05-25
I am having this problem now as well.  I had not experienced it before.  I have recently upgraded to ubuntu 10.04 and I've also started using handbrake to rip my own DVD's.  Wondering which one is the culprit.

---

### Post by jakerosoft on 2010-08-24
EDIT: Fixed, the problem was not related with ushare at all.  I was running everything on an 802.11b/g wireless connection.  Physically cabling the xbox and my laptop to the router fixed a problem.  Also, I saw a recommendation on the xbox that they recommend using 802.11n, I don't have an 802.11n router available so I am unable to test.

Summary: 802.11g can't handle streaming 720p, use ethernet.

------
I believe this is a problem with ushare. I have the exact same situation on my MacBook pro. I'm running ushare from macports. The xbox is connected via wifi and exact same results if the laptop is connected wirelessly or wired.
When I try to play a 720p video. The video on the xbox frequently stalls, freezes, stops and will sometimes loose connection to the laptop.   I also tried running ushare with nice -20 and I couldn't really tell if there was any improvement. 
No problems with lower quality video.

---

