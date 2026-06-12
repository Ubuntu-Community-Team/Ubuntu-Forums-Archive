---
title: "DVB-T &amp; DVB-S   Tuners order changing every reboot under 18.4 Ubuntu Mythtv .29"
date: 2018-12-11
forum: Multimedia Software
---

### Post by drifting on 2018-12-11
Hi
Please bear with me on this as I am partially sighted.
I have spent hours following instructions on how to keep my tuner cards in the same order after each reboot. Both of my cards are TBS, one is a 6281SE the other 6982.
Read that I could add a dvb.conf to modprobe.d which I tried.
options tbsecp3 adapter_nr=0,1
options saa716x_tbs-dvb adapter_nr=2,3
Which did nothing? so either I have the driver names wrong? or something else?
Started to read about Udev, but there was so much confusing contrary information, that after nearly 6hrs of on and off reading when my eyes allowed, I just had to give up.

So where do I go from here? I am at a complete loss. Any help would really be appreciated.

Paul.

---

### Post by vidtek on 2018-12-11
> **drifting said:**
> Hi
Please bear with me on this as I am partially sighted.
I have spent hours following instructions on how to keep my tuner cards in the same order after each reboot. Both of my cards are TBS, one is a 6281SE the other 6982.
Read that I could add a dvb.conf to modprobe.d which I tried.
options tbsecp3 adapter_nr=0,1
options saa716x_tbs-dvb adapter_nr=2,3
Which did nothing? so either I have the driver names wrong? or something else?
Started to read about Udev, but there was so much confusing contrary information, that after nearly 6hrs of on and off reading when my eyes allowed, I just had to give up.

So where do I go from here? I am at a complete loss. Any help would really be appreciated.

Paul.

Paul-
Mythtv provides an answer here: [https://www.mythtv.org/wiki/Device_Filenames_and_udev]("https://www.mythtv.org/wiki/Device_Filenames_and_udev")

The best way is to write your own udev rules, as that is the "new" way of doing things, so is likely to last for a while until they drop it and come up with some even more complicated way of doing stuff.](*,)

I must admit, some of this stuff just makes your eyes roll up inside your head, write this rule here, do another one there and don't forget to make it writable with all the correct file permissions-it just goes on and on.   But we have to remember it is all done by volunteers who give their time freely, so who are we to complain when we just grab their free stuff and use it?

Cheers, Tony

---

### Post by drifting on 2018-12-12
Oh I get the free part, and appreciate the developers. Wish Myhtbuntu was still around, made a dire documented product workable.
What grates with me is the conflicting information. Had to laugh at the link you sent, they even say its dependent on the phases of the moon!

Will go have a read of the link you sent, and see if I can make any more sense of it. Was not a sympathy kick re the eyes, more a case of sheer frustration at another thumping headache and none the wiser with the problem :-)

Thanks Paul

---

### Post by drifting on 2018-12-13
OMG! Is a normal human being supposed to understand the udev rules? That has to be one of the most confusing, and contrary information I have ever read!

That being said, I am now stuck with two tuners and not the brain power to understand how to implement udev, or the eyesight to attempt to read it for the 40th time.

If I supplied the udev info, would some please be so kind as to help me create the right rule?

looking at parent device '/devices/pci0000:00/0000:00:1c.1/0000:30:00.0':
    KERNELS=="0000:30:00.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="TBSECP3 driver"
    ATTRS{broken_parity_status}=="0"
    ATTRS{class}=="0x048000"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{current_link_speed}=="2.5 GT/s"
    ATTRS{current_link_width}=="1"
    ATTRS{d3cold_allowed}=="1"
    ATTRS{device}=="0x6178"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{driver_override}=="(null)"
    ATTRS{enable}=="1"
    ATTRS{irq}=="31"
    ATTRS{local_cpulist}=="0-1"
    ATTRS{local_cpus}=="3"
    ATTRS{max_link_speed}=="2.5 GT/s"
    ATTRS{max_link_width}=="1"
    ATTRS{msi_bus}=="1"
    ATTRS{numa_node}=="-1"
    ATTRS{revision}=="0x00"
    ATTRS{subsystem_device}=="0x0002"
    ATTRS{subsystem_vendor}=="0x6281"
    ATTRS{vendor}=="0x544d"

looking at parent device '/devices/pci0000:00/0000:00:1c.0/0000:20:00.0':
    KERNELS=="0000:20:00.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="SAA716x Budget"
    ATTRS{broken_parity_status}=="0"
    ATTRS{class}=="0x048000"
    ATTRS{consistent_dma_mask_bits}=="64"
    ATTRS{current_link_speed}=="2.5 GT/s"
    ATTRS{current_link_width}=="1"
    ATTRS{d3cold_allowed}=="1"
    ATTRS{device}=="0x7160"
    ATTRS{dma_mask_bits}=="64"
    ATTRS{driver_override}=="(null)"
    ATTRS{enable}=="1"
    ATTRS{irq}=="16"
    ATTRS{local_cpulist}=="0-1"
    ATTRS{local_cpus}=="3"
    ATTRS{max_link_speed}=="2.5 GT/s"
    ATTRS{max_link_width}=="1"
    ATTRS{msi_bus}=="1"
    ATTRS{numa_node}=="-1"
    ATTRS{revision}=="0x03"
    ATTRS{subsystem_device}=="0x0002"
    ATTRS{subsystem_vendor}=="0x6982"
    ATTRS{vendor}=="0x1131"


Thanks guys, would not ask if I could even get my head round it.

Paul.

---

### Post by vidtek on 2018-12-13
> **drifting said:**
> OMG! Is a normal human being supposed to understand the udev rules? That has to be one of the most confusing, and contrary information I have ever read!

That being said, I am now stuck with two tuners and not the brain power to understand how to implement udev, or the eyesight to attempt to read it for the 40th time.

If I supplied the udev info, would some please be so kind as to help me create the right rule?

looking at parent device '/devices/pci0000:00/0000:00:1c.1/0000:30:00.0':
    KERNELS=="0000:30:00.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="TBSECP3 driver"
    ATTRS{broken_parity_status}=="0"
    ATTRS{class}=="0x048000"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{current_link_speed}=="2.5 GT/s"
    ATTRS{current_link_width}=="1"
    ATTRS{d3cold_allowed}=="1"
    ATTRS{device}=="0x6178"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{driver_override}=="(null)"
    ATTRS{enable}=="1"
    ATTRS{irq}=="31"
    ATTRS{local_cpulist}=="0-1"
    ATTRS{local_cpus}=="3"
    ATTRS{max_link_speed}=="2.5 GT/s"
    ATTRS{max_link_width}=="1"
    ATTRS{msi_bus}=="1"
    ATTRS{numa_node}=="-1"
    ATTRS{revision}=="0x00"
    ATTRS{subsystem_device}=="0x0002"
    ATTRS{subsystem_vendor}=="0x6281"
    ATTRS{vendor}=="0x544d"

looking at parent device '/devices/pci0000:00/0000:00:1c.0/0000:20:00.0':
    KERNELS=="0000:20:00.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="SAA716x Budget"
    ATTRS{broken_parity_status}=="0"
    ATTRS{class}=="0x048000"
    ATTRS{consistent_dma_mask_bits}=="64"
    ATTRS{current_link_speed}=="2.5 GT/s"
    ATTRS{current_link_width}=="1"
    ATTRS{d3cold_allowed}=="1"
    ATTRS{device}=="0x7160"
    ATTRS{dma_mask_bits}=="64"
    ATTRS{driver_override}=="(null)"
    ATTRS{enable}=="1"
    ATTRS{irq}=="16"
    ATTRS{local_cpulist}=="0-1"
    ATTRS{local_cpus}=="3"
    ATTRS{max_link_speed}=="2.5 GT/s"
    ATTRS{max_link_width}=="1"
    ATTRS{msi_bus}=="1"
    ATTRS{numa_node}=="-1"
    ATTRS{revision}=="0x03"
    ATTRS{subsystem_device}=="0x0002"
    ATTRS{subsystem_vendor}=="0x6982"
    ATTRS{vendor}=="0x1131"


Thanks guys, would not ask if I could even get my head round it.

Paul.

Paul now you understand why I sent you that link and said best of luck!  I had great difficulty in working out the rules required for my tuners-I think I spent about 2 days on it, and I still didn't have a clear understanding of udev at the end of it.  In the end I cheated and put a 4-tuner card in the master backend and put the other tuner in the slave.  Problem solved.  With the 4 tuners in the master, the slave rarely turns on now, and I still have the 2 tuner HD homerun to watch live tv if I want.
Tony

---

### Post by drifting on 2018-12-14
Thanks Tony, think at my time in life this has become the straw that broke the back of Mythtv for me. I have spent upward of 4 months upgrading from a working 14.04 with .25 Myth, have surmounted dozens of random problems.
Anyway, as they say, if you do not have the skill to change it, be grateful for those who gave up their time to write it. Really annoying no Myth over Xmas, can see the wife forcing my hand to get Sky TV.

Have a great Xmas.

Paul.

---

### Post by vidtek on 2018-12-14
> **drifting said:**
> Thanks Tony, think at my time in life this has become the straw that broke the back of Mythtv for me. I have spent upward of 4 months upgrading from a working 14.04 with .25 Myth, have surmounted dozens of random problems.
Anyway, as they say, if you do not have the skill to change it, be grateful for those who gave up their time to write it. Really annoying no Myth over Xmas, can see the wife forcing my hand to get Sky TV.

Have a great Xmas.

Paul.

Paul-
I understand the frustration, been there myself.  Before you totally give up, I just had a thought, give the guys at TBS a shout, they are very willing to help and may just provide the scrips you need.  When I was stuck in the past, I just emailed them and they replied with a solution within a day.
Cheers Tony.

---

### Post by viewera on 2018-12-14
There should be symlinks to your capture cards in /dev/v4l/by-path/ .
Mine look like this, yours will probably be different.

pci-0000:03:06.0-video-index0 
pci-0000:03:06.0-video-index2 
pci-0000:03:06.0-video-index1
pci-0000:03:06.0-video-index3
pci-0000:03:07.0-video-index0
pci-0000:03:07.0-video-index1
 
For me those links always point to the same card no matter how /dev/video0,
/dev/video1 ... swap places.

If you run a command like this on the links in /dev/v4l/by-path/

```
file /dev/v4l/by-path/(your links)
```

It will tell you what that symlink is currently pointing to ( /dev/video0, /dev/video1 ...)
For example if I run:

```
file /dev/v4l/by-path/pci-0000:03:06.0-video-index0
```

it returns the following, telling  me pci-0000:03:06.0-video-index0 is currently pointing to /dev/video0

```
/dev/v4l/by-path/pci-0000:03:06.0-video-index0: symbolic link to ../../video0
```

Next time I reboot it may tell me /dev/v4l/by-path/pci-0000:03:06.0-video-index0 is pointing at /dev/video1 , but it doesn't matter it will always be the same card.

I don't know anything about setting up Mythtv, but if you can point Mythtv at the appropriate link in /dev/v4l/by-path/ it should solve your swapping problem.

---

### Post by drifting on 2018-12-23
Hi, thank you so much for replying, no idea why I did not get a notification. Had resigned  myself to no MythTV over Xmas .
Had a look at my MythBox (Ubuntu 18, Myth .29) And I do not have a /dev/v4l/ directory !
Cards are all there, but under DVB.... Sorry at the extent of my knowledge with this card problem, and think udev is the work of satan :-)

Regards Paul.

---

### Post by RedDirtDog on 2019-04-07
Hey Drifty,

did you end up getting this sorted?  I just spent a day figuring it out, and can help if needed.

---

### Post by drifting on 2019-04-08
Hi Scumhook

Yes, in the end I did, some guys over on the TBS forum helped.

Thanks for replying

---

### Post by drifting on 2019-04-24
Just panicked, did some updates and the order changed again! Relieved to report that a cold boot sorted it. Just in case anyone else gets the same issue.

Paul

---

