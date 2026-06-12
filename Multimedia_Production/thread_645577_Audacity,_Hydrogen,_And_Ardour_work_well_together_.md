---
title: "Audacity, Hydrogen, And Ardour work well together under Jack"
date: 2007-12-20
forum: Multimedia Production
---

### Post by theorganloft on 2007-12-20
The trick is to get the applications to connect together to the audio interface. If you set Audacity to connect directly to the sound card, other applications cannot use the sound card resources.

Basically, you have to send all request for the sound card through Jack. ALSA has the drivers and Jack controls the connections. Setting Audacity fixed this problem.

In my Ubuntu Studio (US) hardware I use one Delta Revolution 7.1 sound card. The internal or motherboard (mobo) sound interface is off in the BIOS. My goal was to only use the Delta and so far I am proving my theory because it performs excellent under long complicated recording sessions.

With 2 Gb of Memory and plenty of Hard Disk Space, the programs ran together with no problem. I just did a couple of loops and recorded audion directly from my synth. This would have killed my Windows machine. US handled it quite well. The only noticible latency was when I decided to hit record in Audacity to see if Audacity and Ardour could record at the same time. This was extreme and I thought that something would crash. Well...nothing happened! They both were recording! It slowed down for a second then the system caught up. I was impressed. I would never try this with Windoze. I may try it with a MAC but never Windows. However it was an extreme condition and I woul not do this again.

I do advise as they suggest in the forums that you use two harddrives on separate controllers. I do not recommend using RAID SATA or other RAID internal or external devices. Audio needs to have full attention of the drive and controller.

The other question in funtionality has to do with fragmentation and drive maintenance. All of my studies indicate that the drive format EXT3 does not need to be defraged. I have been working on several complicated Podcasts with Loop recordings built in Audacity and the system never glitched. I keep my archives on DVD medium therefore, I keep the space on my drive for production. I do not do complicated video on this machine. I am curious to know how things will be over time. I will keep notes on that progress. Images are forthcoming on the BLOG for the audio connections with Jack.:guitar:

---

### Post by Em-Buntu on 2007-12-25
Thanks.
I'll try these suggests. I have yet to get pass JACK giving me Timer resolution errors when I try to connect.

---

### Post by theorganloft on 2007-12-27
Please be more specific.  I am guessing that you may have a latency problem where there is simply not enough resources or they are configured incorrecty?

---

