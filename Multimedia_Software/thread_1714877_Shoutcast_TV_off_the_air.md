---
title: "Shoutcast TV off the air?"
date: 2011-03-26
forum: Multimedia Software
---

### Post by fpgdu on 2011-03-26
This [http://sonic-lux.de/home/projekte/software/shoutcast_tv_lists/web/index.html](http://sonic-lux.de/home/projekte/software/shoutcast_tv_lists/web/index.html) is supposed to be a listing of the shoutcast channels. it worked well for at least a month or more but for the last 3 days or so, it just comes up blank on both firefox and chrome. There are other similar sites that don't bring up the listings. What is going on exactly?

---

### Post by perezomail on 2011-03-28
found the same issue here [http://sonic-lux.de/home/projekte/software/shoutcast_tv_lists/web/index.html](http://sonic-lux.de/home/projekte/software/shoutcast_tv_lists/web/index.html) was saved as a prism shortcut loved it I know shoutcast has been going through some changes for example in rhytmbox I had to install a new shoutcast plugin since the one I had no longer had much of a choice.

---

### Post by fpgdu on 2011-03-30
> **perezomail said:**
> found the same issue here [http://sonic-lux.de/home/projekte/software/shoutcast_tv_lists/web/index.html](http://sonic-lux.de/home/projekte/software/shoutcast_tv_lists/web/index.html) was saved as a prism shortcut loved it I know shoutcast has been going through some changes for example in rhytmbox I had to install a new shoutcast plugin since the one I had no longer had much of a choice.


What exactly is prism for?

---

### Post by fpgdu on 2011-04-01
Still down it appears. Has anyone been able to access the listings from Winamp in Windows?

---

### Post by waynefoutz on 2011-04-03
> **fpgdu said:**
> Still down it appears. Has anyone been able to access the listings from Winamp in Windows?

It works in WinAmp. This has me yanking my hair out. I Winamp will NOT play the video player in a virtual machine, the only way I can get my Shoutcast TV is to boot into Windows and run it natively. Tunapie, my usual way of watching in Ubuntu, will not load any streams. I think AOL, who owns BOTH Shoutcast and WinAmp, are behind this.

---

### Post by perezomail on 2011-04-05
this link

[http://sonic-lux.de/home/projekte/software/shoutcast_tv_lists/web/index.html](http://sonic-lux.de/home/projekte/software/shoutcast_tv_lists/web/index.html)

now produces 

not working, shoutcast don't support this anymore :(

looks as if Shoutcast is leaving Linux users out much like Netflix has been with there Windows and Mac only version of Silverlight or Moonlight to us.

guess they figure we will _buy_ into other than Linux as far as watching TV programs

---

### Post by dixonstalbert on 2011-04-05
shoutcast which is owned by AOL changed their licencing agreement

last summer. see this thread 

[https://bugs.launchpad.net/ubuntu/+source/tunapie/+bug/696573](https://bugs.launchpad.net/ubuntu/+source/tunapie/+bug/696573)

there is no legal way to access shoutcast tv directory except through Winamp.

I got shoutcastTV/Winamp to run  in Vmplayer running Windows 2000 with DirectX installed, but I have not been able to reproduce how I did it with a fresh windows 2000 install. It seems dependent on the order you install vmtools, DirectX9, winamp and you apparently cannot just try a new order as the previous attempts prevents successful installation. 

Also have had no luck running shoutcasttv/winamp in my virtualbox installs of windows 2000 and windows 7 64

---

### Post by waynefoutz on 2011-04-06
> **dixonstalbert said:**
> shoutcast which is owned by AOL changed their licencing agreement

last summer. see this thread 

[https://bugs.launchpad.net/ubuntu/+source/tunapie/+bug/696573](https://bugs.launchpad.net/ubuntu/+source/tunapie/+bug/696573)

there is no legal way to access shoutcast tv directory except through Winamp.

I got shoutcastTV/Winamp to run  in Vmplayer running Windows 2000 with DirectX installed, but I have not been able to reproduce how I did it with a fresh windows 2000 install. It seems dependent on the order you install vmtools, DirectX9, winamp and you apparently cannot just try a new order as the previous attempts prevents successful installation. 

Also have had no luck running shoutcasttv/winamp in my virtualbox installs of windows 2000 and windows 7 64

Tunapie was working until about a week ago. This really blows, because I'm a huge fan of Shoutcast TV. I often sleep with Comsmostv.org in the background. I've made several attempts to run it in Winamp on an XP VM,but have had no luck whatsoever either.  I thought I saw a glimmer of hope when I saw WinAmp in the android market, that I'll just watch it on a tablet, but no, it only does the radio, and not very well, I might add.

---

