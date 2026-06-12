---
title: "Xubuntu 12.04 flash problems"
date: 2012-12-01
forum: Multimedia Software
---

### Post by andypearce on 2012-12-01
Hi,
I am having problems streaming flash on iplayer and youtube, jerky sound/picture out of synch...it is worse on full screen and only happens on my laptop with xubuntu 12.04.  I use two laptops one with xubuntu 12.04 and the other with ubuntu 10.04. Here are details of the two laptops I use.

Toshiba satellite pro L100 with Xubuntu 12.04
System monitor tells me:
Release ubuntu 12.04 (presice) 32 bit
Kernel linux 3.2.0-33-generic (as I write I am being asked to upgrade to 3.2.0-34generic)
Gnome 3.4.2

Hardware
Memory 463.1 MiB
Processor Intel celeron ® M processor 1.60GHZ
Available disk space 30GiB

Additional information
Adobe flash 11.2.202.251 with firefox 17.0
Medibuntu added
Xubuntu restricted extras added
flash aid added 
disabled hardware acceleration
adblock plus disabled on iplayer

Toshiba Satellite Pro A120 with Ubuntu 10.04
System monitor tells me:
Release Ubuntu 10.04
Kernel linux 2.6.32-45-generic
Gnome 2.30.2

Hardware
Memory 489.0MiB
Processor Intel core T1350 @ 1.86GHZ
Available disk space 45.5 GiB

Additional information
Adobe flash 11.2.202.251 with firefox 17.0
Medibuntu added
I use adblock plus and it is enabled on youtube and iplayer
hardware acceleration enabled

Wireless connection both have ath5k driver, both had speed of 1mb/s, Xubuntu 12.04 laptop had connection of 60% but Ubuntu 10.04 laptop had 80% in exactly the same position.

So after all this information... I looked for a light weight os to replace Ubuntu 10.04 on the satellite pro L100, it worked OK with 10.04 but had become slow after an update so I thought it was time for a change.  After taking advice (here) I decided to go for Xubuntu 12.04. I downloaded it, copied it to cd and installed it wiping ubuntu 10.04 as it went (I assume). However, when you play flash like BBC iplayer of youtube the sound and video are out of sync, it is worse and jerky on full screen. I can only use this laptop connected to the internet with an ethernet cable not the wifi and accessing ordinary web pages etc is fine. (I have included some wifi details above). I cannot access much using the wifi at all. In total contrast, the other old Toshiba satellite pro laptop with Ubuntu 10.04 works absolutely perfectly with wifi only, streaming is perfect full screen (except when busy, but you expect that...buffering up takes place or very rarely there is not enough bandwidth). I know from searching about that others are having this problem as well but why with the same flash player will one work (Ubuntu 10.04) and the other even when hard wired (Xubuntu 12.04) drive you absolutely mad with the flash problem of the sound and video being out of sync. I have looked all over for a solution... older versions of flash are suggested, but both are using the same version, the laptop cannot get the information quick enough to stream it properly (which I do not think can be true as the faulty one is hard wired and the good one uses wifi and works even at 64%) and so on. 

From the information about the two laptops, can anyone tell me what the difference in the hardware or software that might be causing this.... I kind of thought that the Xubuntu 12.04 would be better than the Ubuntu 10.04.  
Any answers will be much appreciated as they will enhance my understanding and help me work out what is going on.
Thanks Andy

---

### Post by Yellow Pasque on 2012-12-01
The Linux Flash plugin is a CPU hog, and it's probably bringing the Celeron M to its knees. The only thing I can suggest is trying to turn off pulse timer scheduling: [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

---

### Post by andypearce on 2012-12-02
Thanks Temüjin for your reply and pointing me toward the CPU. So what you are saying is that the celeron m is not a big enough processor to do the work required by modern standards such as streaming video even when connected to the modem by an ethernet cable, but the intel core is. 
I have now searched information about the celeron m processor and I am now informed it is a budget processor, but beyond that I am a bit lost.

This is something I am going to have to learn about.

I also assume then that this is the difference in the wifi perfomance of the two laptops, The celeron m laptop cannot process the information from the wifi fast enough whereas the intel core laptop can. Yes or no anybody?

So the idea that you can use older machines to do modern, up to date, computer applications, using light weight linux OS is ok if you do not want to stream video or use wifi unless you have a cpu of a certain and minimum quality?
A

---

### Post by andypearce on 2012-12-02
I will also follow up the pulse timer scheduling. Thanks.

---

### Post by Yellow Pasque on 2012-12-02
> So the idea that you can use older machines to do modern, up to date, computer applications, using light weight linux OS is ok if you do not want to stream video or use wifi unless you have a cpu of a certain and minimum quality?

The Linux Flash plugin is to blame. It uses a lot more CPU on Linux than on Windows. You may want to try Google Chrome, as the Flash plugin is built in and updated.

> So what you are saying is that the celeron m is not a big enough processor to do the work required by (the Flash plugin), but the intel core is. 
Yeah, the Core is a faster CPU, uses faster RAM, faster FSB, etc. than Pentium/Celeron M. It's very possible the Core can keep up while the Celeron can't.

---

### Post by andypearce on 2012-12-02
Thank you for the clarification and direction. I still have much to learn. I have seen that Google chrome includes supported flash but was a bit reluctant to join the google monopoly...maybe I will give it a go.
All the information you have given me seems very reasonable so will mark the thread solved. Thanks again...
Andy

---

### Post by alfu on 2012-12-18
I am also having flash (gnash) plugin problems with Xubuntu 12.04:  At one point, everything worked, and I thought the situation was resolved, but no flash content will play at all.  Before switching over from Ubuntu 12.04, all flash content played fine on this HP dv2-1030us. I wanted to go back to using swfdec-mozilla, the plugin I was using with Ubuntu 12.04, but Synaptic refuses to install it.

Installing Flash-Aid did nothing but wipe out 2 browser windows with a lot of tabs I will have to rebuild from scratch.
______________________
Edit 121217: Googled 'Xubuntu flash problems' and found a link to [http://www.youtube.com/watch?v=3HAgUCh5qoM](http://www.youtube.com/watch?v=3HAgUCh5qoM), installing Adobe Flash on Xubuntu 12.04. Amazingly, the video played on my computer! Without the tips presented there, I would have come to a dead end on Adobe's site. So far, following these instructions looks like it has enabled Flash content to play. :)

---

