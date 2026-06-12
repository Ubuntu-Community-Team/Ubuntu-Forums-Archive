---
title: "run from CF card"
date: 2008-07-12
forum: Mythbuntu
---

### Post by leeko on 2008-07-12
Hi all,

I'm in the process of setting up my (v. low budget) HTPC. I've replaced all the fans with low-noise fans, and the HDD is now the noisiest component. 

What I'd like to do is install a CF-to-IDE converter, and run the OS (Mythbuntu) from a 2GB CF card. This would let me set the 500GB IDE HDD to spin down for the most part, and keep my system quieter when watching TV. 

The minimum requirements state 2GB for the frontend and 20GB for the backend. Would my setup work, or is there anything I'm missing? 

Are there any other potential problems I haven't thought of? On other OS's running from solid-state media, it's best to disable swap to prolong the life of the card. Is this possible for mythbuntu, or is the swap essential? 

Thanks for taking the time to answer my questions, and any other hints/tips for this project would be much appreciated!

Regards,

Leea

---

### Post by nickrout on 2008-07-13
Firstly your hard drive will not spin down when you are watching tv, because in Myth everything is stored on the drive and the drive must be active when you are watching live Tv or recordings.

Secondly whether you need swap depends on how much RAM you have. If you go ahead I would recommend putting a 1G swap partition on the 500G drive. Try running the system without it, if it works thats fine. If it doesn't you can turn it on and you don't need to repartition that drive.

---

### Post by laga on 2008-07-13
Is it really the hard disk itself that is noisy or is the noise caused by vibrations in the drive cage? If it's caused by vibrations, you can always soft-mount or suspend your HDD.. google will probably have some howtos or products. But be careful - some also claim that it can affect performance and cause your disks to die early. I'll leave it to you to ask the intarwebs about that ;)

---

### Post by ian dobson on 2008-07-13
Hi,

To reduce the noise from my frontend system I went over to using a 2 1/2 inch harddisk and mounted it using rubber "grumits" so that the vibration from the drive doesn't go into case.

The biggest difference for me in terms of noise was to use fancontrol to control the speed to the fans bsed on the CPU temperture and changing the fans to low noise ones and reversing them so that all the fans are sucking air out of the case.

Regards
Ian Dobson

---

### Post by leeko on 2008-07-13
Dang!

That's a shame, but I thought it might be the case...

So, in order for my system to work, I would need a bigger CF card (say 8 or 16GB) and house the swap/storage on there. That way, although the drive wouldn't idle, it's a CF card and wouldn't make any noise while it's working. 

Any idea what that would do to the life-cycle of the card? I'm guessing it wouldn't be very long...

Re: Drive noise - that's all on my to-do list, and will certainly make a noise difference. But, I kinda like the idea of running the system from solid-state (I love my EeePC!), and I think I just like a challenge! :P  

Thanks for getting back to me :)

Lee

---

### Post by nickrout on 2008-07-13
Is this designed to be a frontend or a combined front and backend? If its just a front end you can easily netboot it. And you still haven't bothered to tell us how much ram you have.

---

### Post by leeko on 2008-07-13
If I understand the terminology correctly, the backend is what houses the capture card? In that case, it will be a combined frontend/backend which will be "always-on". I'd like it to go into standby/low-power mode when I'm not watching tv/movies/music. 

Re: Ram - The machine is in various bits at the moment. To hand, I have 384Mb Ram, but it's no problem to add more. That's why I didn't mention it.

Other specs:

AMD athlon XP 3200+
384MB ram (will probably upgrade)
500GB IDE disk
2x 2GB CF Card (on CF-to-IDE converter cards)
WUG2400 USB wifi (working via ndiswrapper) - will probably change this, due to problems with ndiswrapper surviving a standby.
NVIDIA GF2mx 440 w/ Svid-out (old, but does the job)
MSI digivox mini 2 v3.0 USB DTV stick
IR remote

It's a machine I have little use for after upgrade, so I thought I would put it to good use. At present, it's running debian etch, but I've been finding it tricky to set up mythTV. I figured I might start from scratch with mythbuntu and see how it runs... 

If it doesn't work, I'll probably sell or donate it, and use my new machine for the purpose instead (E6300 dual-core, 3GB ram, 500GB disk) and maybe run a web-server in the background.

Thanks,

Lee

---

### Post by laga on 2008-07-13
Well, from your first post: > 
What I'd like to do is install a CF-to-IDE converter, and run the OS (Mythbuntu) from a 2GB CF card. This would let me set the 500GB IDE HDD to spin down for the most part, and keep my system quieter when watching TV.

When you are watching LiveTV, MythTV is recording. I think you can put LiveTV recordings into a separate directory, i.e. your CF card. But you'll probably have to be careful not to fill up that file system.

Just my 0.02€..

---

### Post by leeko on 2008-07-13
> **laga said:**
> Well, from your first post: 

When you are watching LiveTV, MythTV is recording. I think you can put LiveTV recordings into a separate directory, i.e. your CF card. But you'll probably have to be careful not to fill up that file system.

Just my 0.02€..

Thanks for clarifying.

So, does anyone know if this could be adequate:

Mythbuntu installed on a 2GB CFcard; Recording directory on a separate 2GB CFcard (I have a lot of unused CFcards!); swap file on IDE HDD (disabled to start with, as suggested above). 

I guess what I'm asking is: how much of a "buffer" does mythtv use for live TV? Is 2GB enough? And if that 2GB filesystem becomes filled, presumably mythtv will just stop working (as opposed to bringing the OS down, as it'll be separate from the root filesystem)? 

Thanks,

Lee

---

### Post by nickrout on 2008-07-13
No that won't work as there just isn't enough space. 2G will only allow about an hour (or 2) of recording, you should either:

(a) install the whole thing on the hard drive; or

(b) install myth to the CF and use the hard drive for recording; or

(c) install myth to CF and store your recordings on a server away from the lounge, enabling you to keep the noisy hard drives out of the room.

On the other hand if you only want liveTV, mythtv is not the solution for you.

---

### Post by leeko on 2008-07-13
hi,

no, I want it to do more than just livetv, although that is what it will be doing for most of the time... Just looking for a neat solution :)

Can I ask, though: why does mythtv need to store more than an hour (or 2) of video for livetv? Doesn't it just use the stored video as a "buffer" (in which case a couple of minutes should suffice)?

Re: storing the video on a server - would a 802.11g wifi connection be sufficient to stream video for that purpose? I do have a (wired) network lan disk that could be put to that purpose, but my htpc box uses a wifi connection... 

Thanks again,

Lee

---

### Post by nickrout on 2008-07-13
By default mythtv keeps liveTV for a day (or maybe 2) before it expires it. Thats a lot of G if you watch tv for a few hours a day. It also stores liveTV in exactly the same way as recorded programmes, so you need the storage anyway.

I wouldn't recommend recording over 802.11. Put it on your wired network and you won't have to worrry about bandwidth.

By the way your machine is perfectly powerful enough for Std Def tv, not sure if it is enough for Hi Def, possibly not. If you want to run without swap I would say put 1-2G of RAM, but I am no expert.

But if you are just starting out, suck it and see with the hard drive in the lounge. Turn the volume up on the TV and you won't hear them!

---

