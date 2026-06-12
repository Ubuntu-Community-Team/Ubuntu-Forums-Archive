---
title: "How to get Flash GPU Accelleration - but BBC iPlayer?"
date: 2011-01-04
forum: Multimedia Software
---

### Post by spidermagicat on 2011-01-04
After a spell on windows 7 I'm back with ubuntu :-)

the main reason for my stay away was GPU acceleration in flash ( I have a tiny intel atom processor but a reasonable GeF. 9300M GS so it's a big thing :-D )

Now it's here on linux for NVidia with vdpau and highly recommended. Simply install vdpau and the latest flash beta (10.2). Assuming your card supports it and your using the proprietary drivers

sudo apt-get install vdpau-va-driver

The flash is available here [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

download the linux version and extract the libflashplayer.so to /usr/lib/mozilla/plugins/ for firefox 

Now right clicking on a flash video and clicking "about adobe flash player" should show the version as 10.2......

You should also be able to view youtube videos in 1080p without your CPU breaking a sweat. :-D

That's the how to, next post for the question.

---

### Post by spidermagicat on 2011-01-04
BBC iPlayer is not currently using the GPU. Something similar happened in windows where the beta 1 of flash 10.1 would use the gpu but the rc1 of 10.1 did not. I simply stuck with the beta

In this case I think it's because the H.264 codec used incorrectly flagged as interpolated when the check was introduced.

Has anyone got any ideas to force GPU acceleration, stop that check, or in fact have a version of flash which is working properly with iplayer.

You should be able to play the HD content no problem

If it's working for you could you post your exact flash version, maybe even your libflashplayer.so

My version is 10,2,151,49 and it's not working :-(

---

### Post by Yellow Pasque on 2011-01-04
Report the bug to Adobe (homewever futile that may seem). It seems like you have a good grasp on the technical part, so that's a big plus.

---

### Post by sosasami on 2011-01-29
I've filed a request on the BBC Iplayer discussion forum to support the new hardware acceleration features of Flash 10.2
[http://www.bbc.co.uk/dna/mbiplayer/F7331806?thread=8030330&post=105762061#p105762061](http://www.bbc.co.uk/dna/mbiplayer/F7331806?thread=8030330&post=105762061#p105762061)

Please add your heat to that thread if you want to see this happen.

Cheers.

---

### Post by onemanclapping on 2011-02-10
I did all this and my flash is still not accelerated, any idea why?

I downloaded the new flash (10.2.152.27) and I have an ION graphics card.

---

### Post by barefootdave on 2011-09-15
As a new linux convert, I am thinking of going back to Windows because of this. I cannot run bbc iplayer as it is jumpy and often the video and audio sync poorly. 

I have been all over the forums today, after starting in the latest Ubuntu, I also tried mint 11, 9 and 8 to see if using earlier distros avoided the issue. 

I have tried various flash updates, tried manually inserting realplayer files into their correct places in the mozilla plugins, tried linux and nvidia drivers... 

My gut feeling is that linux is not using the graphic card properly, along the lines of the initial post in the thread. Can anyone point me to a discussion on this? or suggest a fix?

the vdpau code didn't work for me, currently on the mint 8 distro (which according to the release notes is based on the ubuntu 9.10 distro)

I also have a NVIDIA GEforce 9300M GS graphics card

Please help if you can!

---

### Post by hrdbavg on 2011-09-25
I have the opposite problem. After running update manager recently, Iplayer now runs double speed with no sound - so its impossible to watch anything. I don't have any issues when I use windows 7 for iplayer. Tried playing bbc HD to see if that made any difference, but it doesn't. I'm using flash version 10,3,183,10
Any ideas how I can fix this?

---

### Post by Russ_H on 2011-10-31
> **hrdbavg said:**
> I have the opposite problem. After running update manager recently, Iplayer now runs double speed with no sound - so its impossible to watch anything. I don't have any issues when I use windows 7 for iplayer. Tried playing bbc HD to see if that made any difference, but it doesn't. I'm using flash version 10,3,183,10
Any ideas how I can fix this?

Yes, I would like to know what is going on with iplayer. I have 11.0.1.152 of flash on 10.04 LTS and have not seen HW acceleration on iplayer since flash 10.1 beta. Youtube 1080p no problem, this is getting ridiculous.

---

### Post by alexcckll on 2011-11-04
> **Russ_H said:**
> Yes, I would like to know what is going on with iplayer. I have 11.0.1.152 of flash on 10.04 LTS and have not seen HW acceleration on iplayer since flash 10.1 beta. Youtube 1080p no problem, this is getting ridiculous.
It gets worse - on an Intel Atom N270+NVIDIA ION - iPlayer loses video - or freezes a short way in.

Basically - it looks as though the Beeb have broken iPlayer completely for Ubuntu+NVIDIA by relying on Stage3D code that Adobe have removed entirely.  Flash 10.1 is also the minimum bversion they will support.

I've asked for 10.3 to be packaged as a backwards-support version, as the only current older version available is 10.0.42...

Here's the bug link.. [https://bugs.launchpad.net/ubuntu/+bug/886302](https://bugs.launchpad.net/ubuntu/+bug/886302)

10.3 IIRC was the last release version that contained experimental GPU accel code for VDPAU under Linux...

---

### Post by Russ_H on 2011-11-08
> **alexcckll said:**
> It gets worse - on an Intel Atom N270+NVIDIA ION - iPlayer loses video - or freezes a short way in.

Basically - it looks as though the Beeb have broken iPlayer completely for Ubuntu+NVIDIA by relying on Stage3D code that Adobe have removed entirely.  Flash 10.1 is also the minimum bversion they will support.

I've asked for 10.3 to be packaged as a backwards-support version, as the only current older version available is 10.0.42...

Here's the bug link.. [https://bugs.launchpad.net/ubuntu/+bug/886302](https://bugs.launchpad.net/ubuntu/+bug/886302)

10.3 IIRC was the last release version that contained experimental GPU accel code for VDPAU under Linux...

I can just about run standard video on a n330 on iplayer, might try [Old versions of flash]("http://kb2.adobe.com/cps/142/tn_14266.html#main_Switching_between_versions_") at the weekend, will report back if I have any luck.

---

### Post by Russ_H on 2011-11-09
[http://gigaom.com/video/bbc-iplayer-html5/](http://gigaom.com/video/bbc-iplayer-html5/)

Ah well I guess that is why flash is so bad, they are moving to HTML5

---

