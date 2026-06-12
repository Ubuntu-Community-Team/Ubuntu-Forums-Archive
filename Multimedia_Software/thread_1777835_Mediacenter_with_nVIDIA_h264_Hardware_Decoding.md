---
title: "Mediacenter with nVIDIA h264 Hardware Decoding"
date: 2011-06-08
forum: Multimedia Software
---

### Post by Phkillah on 2011-06-08
Hi there,

I've setup a EEEBox 1501P exclusively to work as a Media Center.

So i've picked up Ubuntu 11.04 x64, and Boxee x64 (latest), and installed the nVIDIA drivers directly from site.

The problem is that video playback at 720p is a bit sloppy! I've tried on VLC player for example, and the CPU cores are at 10%. But when i use Boxee, one core gets stuck at 100%, and the others at 10%.

So this means that currently, boxee, cannot handle hardware acceleration in x86_64 Linux!

My question is: 
- ***What software can I use to set-up my Ubuntu-based Media Center?***

Thanks in advance

---

### Post by BicyclerBoy on 2011-06-08
VLC does not make a media centre IMO.

VLC has h/w decode presentation support thru' VA-API. This is not compiled into the stock VLC.

No comment on Boxee..

XBMC is the best media centre app...& it supports VDPAU (Nvidia purevideo API) & VA-API.

The VA-API is a GPU independent API but is not as capable as VDPAU directly.
VDPAU can only be used with nvidia GPU h/w. GT220 or better recommended.

XBMC, MythTV & mplayer support VDPAU directly.

---

### Post by Phkillah on 2011-06-08
Thanks for the Reply.

Not only i prefer Boxee, but also I've concluded that the entire hardware runs faster on Windows 7 than on 11.04...

It seems that the drivers supporting ION 2 chipsets under x86_64 Ubuntu Linux are sloppy.

Even with "Composite" disabled on xorg.conf, the performance boosts, but it isn't like Win7 running on this HW.
Also, the IR Remote Controller from this Asus EEE Box EB1501P does not work as expected. Not with VLC, boxee, or XBMC.

I'd love to run Linux on my EEEBox, but right now i'm stuck to a clean Win7 install, with Boxee and a Firewall.

Maybe sometime later it the IR Remote is supported on Linux. I'll make the change then.

Oh, and just FTR, yes, VLC and XBMC can hardware-decode x264 perfectly on Ubuntu x64.

Thanks,
Phk

---

### Post by BicyclerBoy on 2011-06-09
Fair enough.
Do what you have to make it work..

AFAIK VLC does not support h/w video decode (XvBA, VDPAU, Intel?) without using VA-API thru' a custom build or ppa.

Your cpu utilisation figures could suggest CPU decode.
Did you configure XBMC to use VDPAU ?
You run this to check driver vdpau fn:
vdpauinfo

A middle range core2-duo can decode broadcast h264 1080 on 50% (of both cores).

Composite/compiz etc on or off makes no difference to current VDPAU (from my expts).

---

### Post by Phkillah on 2011-06-09
> **BicyclerBoy said:**
> Fair enough.
Do what you have to make it work..

Exactly! Altough I prefer Linux over Win7, if for example I'm talking about a gaming computer, i most certainly will install Windows 7. What mean here is: I totaly agree with your sentence :)

> **BicyclerBoy said:**
> AFAIK VLC does not support h/w video decode (XvBA, VDPAU, Intel?) without using VA-API thru' a custom build or ppa.

Yes it can.
Just go to Option and enable "Hardware Decoding Experimental" and you'll see all cores dropping do 10% (in my case)

> **BicyclerBoy said:**
> Did you configure XBMC to use VDPAU ?
You run this to check driver vdpau fn:
vdpauinfo
Composite/compiz etc on or off makes no difference to current VDPAU (from my expts).

Well, yes, XBMC automatically does VDPAU and so the video decoding is hardware and smooth.

About the Composite, here's the strange behaviour:
```
- Turn **ON **composite on xOrg.conf
- Login to X
- Open gnome-system-monitor and leave it open
- Enter Boxee (no VDPAU support)
- Play 720p x264 for a minute
- Exit Boxee

```
RESULT: Video is Sloppy. On a Quad-Core, 1 core was 100%, other were asleep


Now the phenomenom:
```
- Turn OFF composite on xOrg.conf
- Login to X
- Open gnome-system-monitor and leave it open
- Enter Boxee (no VDPAU support)
- Play 720p x264 for a minute
- Exit Boxee
```

RESULT: Video is good, almost like HW decoding. On a Quad-Core, all cores are in use, about 40% each.


:: So it seems that somehow when Composite is enabled, Multi-threading is affected! This IS weird, but it could prove why games run 200% faster if you disable this.
Ideas?

---

### Post by BicyclerBoy on 2011-06-10
I did not know VLC had progressed that far with h/w decode support..
Sorry but 10% of 4 cores on an i5/i7 processor is not h/w decode..I guess it should be 1-2%.

VDPAU is not the same as openGL performance (games).
Video decode is done in bit stream processor (part of GPU). This is either fast enough & with the correct capabilities or it just does not work.
Post decode filters run in the shaders (de-interlace etc).
Historically composite & VDPAU did not work together. 

Maybe the threading is the key..have no idea what composite has to do with that.

---

### Post by beew on 2011-06-10
> **BicyclerBoy said:**
> 

XBMC, MythTV & mplayer support VDPAU directly.


Which version of mplayer? I am surprised to find that mplayer from the  often recommended MOTU ppa apparently doesn't work with vdpau.

[http://ubuntuforums.org/showthread.php?t=1778720](http://ubuntuforums.org/showthread.php?t=1778720)

---

### Post by beew on 2011-06-10
VLC from this ppa [https://launchpad.net/~ed10vi86/+archive/ppa]("https://launchpad.net/%7Eed10vi86/+archive/ppa") sort of works with VDPAU through VAAPI, performance is better than the stock VLC but still way worse than mplayer (version with VDPAU support) and XBMC in terms of cpu usage.

---

### Post by Yellow Pasque on 2011-06-10
> **beew said:**
> VLC from this ppa [https://launchpad.net/~ed10vi86/+archive/ppa]("https://launchpad.net/%7Eed10vi86/+archive/ppa") sort of works with VDPAU through VAAPI, performance is better than the stock VLC but still way worse than mplayer (version with VDPAU support) and XBMC in terms of cpu usage.
That PPA doesn't have the necessary stuff for va-api on vdpau. I've put the necessary stuff in my ppa, but no one with an nvidia card ever let me know if it works: [https://launchpad.net/~dtl131/+archive/catalysthacks](https://launchpad.net/~dtl131/+archive/catalysthacks)
I have managed to make ati/xvba work in vlc, though I have to repackage libva because the dependencies conflict with the stock libva.

---

### Post by beew on 2011-06-10
> **Temüjin said:**
> That PPA doesn't have the necessary stuff for va-api on vdpau. I've put the necessary stuff in my ppa, but no one with an nvidia card ever let me know if it works: [https://launchpad.net/~dtl131/+archive/catalysthacks]("https://launchpad.net/%7Edtl131/+archive/catalysthacks")
I have managed to make ati/xvba work in vlc, though I have to repackage libva because the dependencies conflict with the stock libva.

I know, I have installed from your ppa because of your advise and it works, though understandably not as good as mplayer since as you explained, VLC uses vdpau indirectly through VAAPI. See this thread [http://ubuntuforums.org/showthread.php?t=1677477](http://ubuntuforums.org/showthread.php?t=1677477)  So let me thank you again for the good job.

But it seems that ObZen's works just as well (but honestly I have only been testing ObZen's ppa on my test install from an external drive which runs Natty)

Now my main machine is on Maverick and I plan to keep it at least til Dec (or perhaps April) but your ppa hasn't updated for Maverick since Jan (VLC still in version 1.14) I read on another thread that you are not planning to, so I am looking for other alternatives(some guy requested a version for Lucid and you went on complaining  how Ubuntu's release cycle makes it hard for packagers,--which I agree,--and said that you won't be upgrading for Maverick either, which I can understand) I am planning to look at Andrew.46's guide eventually for compiling VLC myself, but it has to wait til I have the time.

---

### Post by Yellow Pasque on 2011-06-10
> **beew said:**
>  I am planning to look at Andrew.46's guide eventually for compiling VLC myself, but it has to wait til I have the time.
Sorry for my laziness, but having so many VM's is a pain, and then there are dependency issues. I also wonder how many people actually use that PPA and are still on Maverick, so that putting time/effort into backporting VLC isn't compelling. If only a handful of people want it, it's better that they learn how to compile their own anyway..

---

### Post by beew on 2011-06-14
> **Temüjin said:**
> That PPA doesn't have the necessary stuff for va-api on vdpau. I've put the necessary stuff in my ppa, but no one with an nvidia card ever let me know if it works: [https://launchpad.net/~dtl131/+archive/catalysthacks]("https://launchpad.net/%7Edtl131/+archive/catalysthacks")
I have managed to make ati/xvba work in vlc, though I have to repackage libva because the dependencies conflict with the stock libva.

Yes, you are right. I tried Obzen's version in Natty and it was working good but in Mav it is just like the others. So maybe it is something else. In the mean time I am not upgrading VLC yet, seems that your version does work better even though it is a bit dated.

---

