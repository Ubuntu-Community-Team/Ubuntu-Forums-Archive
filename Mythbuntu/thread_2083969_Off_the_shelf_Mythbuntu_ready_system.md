---
title: "Off the shelf Mythbuntu ready system"
date: 2012-11-14
forum: Mythbuntu
---

### Post by halibut on 2012-11-14
Can anyone recommend an off the shelf Mythbuntu ready system? Or as close to off the shelf as possible?

What I've got in mind is something that:
Runs very cool and quiet (lounge use. some atom based job? Perhaps with an air cooled external psu brick?)
Is fairly compact
Has at least 2x 3.5 internal drive bays (I want to use Raid 1 and also make them available as a basic home nas)
1080 HDMI output, and reasonable audio output
Gig NIC
Has at least one expansion card space for a tv tuner
Has enough grunt to record at least 2 Freeview HD streams and play back a third.

Any ideas?

---

### Post by halibut on 2012-11-14
just in case I was unclear...

I'm not expecting a Mythbuntu box to arrive in the post. I'm looking for a pre-built system that will work with Mythbuntu when I install it.

---

### Post by nickrout on 2012-11-15
> **halibut said:**
> just in case I was unclear...

I'm not expecting a Mythbuntu box to arrive in the post. I'm looking for a pre-built system that will work with Mythbuntu when I install it.Generaly this is fairly specialised and many people put their own machines together for that very reason. 

I assume you want a combined backend/frontend machine rather than going the way more experienced people tend to of having a more grunty, perhaps noisier machine as a backend in a backroom networked to quiet low power video oriented machines in the lounge, bedroom and whereever else you want to watch tv.

the parameters are: a backend machine needs IO power to pull/push data from/to disk. Ideally it has at least two disks - one small and fast for the OS and database. One (or more) large for TV and video data. It's cpu requirements depend on whether or not you want to commflag, trancode and use the services api for viewing on ipad/android etc. It needs slots for as many tuners as you can afford, the more the better, but the more tuners the more important the I/O capability is.

A frontend primarily needs low power, low noise and above all a good video card that will decode in hardware. Other people will say low power, low noise, and a cpu that will decode. Either option is good but I go the video card way and always buy nVidia video solutions, cos they just work with mythtv.

If you want a combined box you need all that in one box. It's not that easy to find, but there are many high powered low power cpu/motherboard combinations out there, with a slot for your nVidia card and plenty of sata ports. 

But if you separate the backend and frontend the options for each is wider. 

So sorry I can't point you to a box that does everything, but hope I have given you some stuff to think on.

---

### Post by jksj on 2012-11-15
Not off the shelf but close.
I recently bought a Zotac IonITX S series motherboard, with Nvidia Ion 2, wifi, gig ethernet, dual atom etc.
With a 2TB disc, 3 gig of ram, PCTV Nanostick (DVB-T2) and TBS 6920 (DVB-S2).
 This is setup to  record 4 HD channels while playing back one. Though In normal use there are only 3 things worth watching at the same time so I have only done limited testing on 4.
Works reliably with Ubuntu 12.04.01, mythtv 0.26.
If you want more specific build & configuration details ask.:)
Note - even a single core atom with first generation Nvidia Ion can record 2 HD streams and playback one. However I am finding the second generation Atom Ion combo much more reliable than the first which I think was running close to its limits.

---

### Post by halibut on 2012-11-15
How hot and noisy is that JKSJ?

---

### Post by jksj on 2012-11-16
Consumes 40 watts fully loaded.
The cpu & graphics chips on the motherboard are under a passive heatsink which only gets warm. The Nvidia Ion is running at about 70c when playing HD content. So the basic kit is silent.
I bought a "In Win case BP655 mini ITX case black with HD Audio 200W PSU". It has a case fan and a PSU fan.  Neither of which seem to be speed controlled. I am not using the case fan as the internals are not getting hot. But the PSU fan is still a bit noisy. You are aware of it when the TV is quiet. Its a nice case but I would see if you can get a lower noise one.

By the way I needed a PCI slot to support my DVB-S2 card but if you don't really need it, any nvidia based prebuilt netop  like the Zotac ones would meet your needs.

---

### Post by halibut on 2012-11-16
Thanks jksj.
 
It's looking more ane more like I'm not going to find what I'm looking for and I'll have to scratch build.
 
H.

---

### Post by lucgallant on 2012-11-17
jksk, I'm a little bit jealous of your setup. I just finished setting one up with the same case except the Asus AT5IONT-I which has an ATOM and onboard NVidia ION as well, and I consume about 75 - 85 W at full load. 

Anyway, I just wrote a post that outlines how to build one using the hardware I mentioned:

Might be of use to the OP - starting from scratch is fairly daunting. The hardware part is trivial to assembly, it's getting all the little details lined up in software.

[http://yetanothermythtvguide.blogspot.ca/](http://yetanothermythtvguide.blogspot.ca/)

---

### Post by jksj on 2012-11-17
High Lucgallant - I am suprised that your power consumption is that high, the only difference I can see between the two systems is that I am using a low power green disk but that should only account for say 5 watts. I will check my numbers and report.
Are you just measuring current and calculating power? I am using a cheap power meter.
The guide is interesting, I have been looking for a wireless rather than infra-red remote.

By the way :- In your description of how to implement automatic power up you mention [FONT=Arial]hwclock-save which prevents the software updating the harware clock before shutdown. I don't do this anymore as it caused problems. After a few months the hardware clock drifted off by 20 mins. At boot the system would start with the wrong time then jump to the correct one when time was updated by NTP. Mythtv got quite upset by this.
[/FONT]

---

### Post by lucgallant on 2012-11-17
> **jksj said:**
> High Lucgallant - I am suprised that your power consumption is that high, the only difference I can see between the two systems is that I am using a low power green disk but that should only account for say 5 watts. I will check my numbers and report.
Are you just measuring current and calculating power? I am using a cheap power meter.
The guide is interesting, I have been looking for a wireless rather than infra-red remote.

By the way :- In your description of how to implement automatic power up you mention [FONT=Arial]hwclock-save which prevents the software updating the harware clock before shutdown. I don't do this anymore as it caused problems. After a few months the hardware clock drifted off by 20 mins. At boot the system would start with the wrong time then jump to the correct one when time was updated by NTP. Mythtv got quite upset by this.
[/FONT]

I'm using my multimeter as an inline current meter and multiplying by 120 V to get VA... If I assume a < 1 power factor I might be looking at less watts actually consumed.

When I implemented the hwclock thing I thought about the exact problem you describe. I might disable it too in order to prevent what you're describing. Initially during troubleshooting I thought I'd do it to at least get things working. Whenever I change it I'll try re-enabling it I'll update the guide.

---

### Post by jksj on 2012-11-18
My power consumption data is not quite as good as I thought. But the numbers do look correct as the case is not even getting warm even when just using the PSU fan.
Power consumption data:-[INDENT]System shut down 1-2 watts
[/INDENT][INDENT]Recording - frontend showing mythwelcome 42 watts.
[/INDENT][INDENT]Recording & watching HD program 48 watts.
[/INDENT]Hardware [INDENT]Motherboard Zotac Ionitx-S-E, dual core atom
[/INDENT][INDENT]Memory 3 GB DDR3
[/INDENT][INDENT]DVB-T2 tuner PCTV Nanostick USB.
[/INDENT][INDENT]DVB-S2 tuner TBS 6920 PCIE card. 

Drive 2 TB SAMSUNG HD204UI
[/INDENT][INDENT]Case / PSU InWin BP655.
[/INDENT]

---

