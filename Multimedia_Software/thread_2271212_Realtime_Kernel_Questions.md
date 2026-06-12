---
title: "Realtime Kernel Questions"
date: 2015-03-28
forum: Multimedia Software
---

### Post by Oliver_Evans on 2015-03-28
Hi all,

I'm interested in doing some audio recording, so I've got jack running and integrated with pulseaudio. It often works fine, but occasionally I'll have bursts of lots of xruns.

My understanding is that a realtime kernel, while not necessarily faster on average, will be much more consistent. So if I were to find jack settings that did not produce xruns, those settings would never randomly produce xruns. Please correct me if I'm wrong about any of this.

I've never installed another kernel, so I don't have a great idea of how it will affect my system.

So my questions are:

[LIST]
[*]Which kernel do you recommend? (rt/realtime/other) 
[*]Can I install another kernel without reinstalling my whole OS? 
[*]Once installed, will it be possible to choose which kernel to use on startup? (Through grub perhaps) 
[/LIST]

Thanks in advanced for the help!
Oliver

P.S. I'm running Kubuntu 14.04 on an [ASUS laptop]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834231548")

---

### Post by Bucky Ball on 2015-03-28
Welcome. The first step is to choose a kernel to suit what you want to do. I hope [this page]("https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel") can help you out. Ask if you get stuck. I use the low-latency personally, but am not running a dedicated DAW. Just do some recording with Audacity from time to time. 

That link has a warning:

> It is not recommended to use kernels from unknown or untested PPA's! You do not know what configuration were used or how it was built and an unstable (or unbootable) system could be the result. Use only trusted PPA's.

Keep this in mind and you'll be fine. And yes, at boot you can choose any kernel you have installed. This procedure WON'T replace your current kernel. Therefore you can also remove the kernel (or PPA) easily. And no, you don't need to reinstall. You can install any kernel you like into the current install (including ones that will break!). 

Good luck. ;)

---

### Post by dino99 on 2015-03-28
maybe UbuntuStudio is what you want/need
[https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel](https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel)

if you have some recent hardware, then a recent ubuntu release has to be used too. Vivid (15.04) which is already very stable will be released in a few weeks now.

---

### Post by Oliver_Evans on 2015-03-28
Wow, thanks so much for the quick and kind responses! :D

---

### Post by Bucky Ball on 2015-03-28
All good. Hey, I just noticed that the two links on the link I provided lead nowhere. Apologies. I had problems when I was trying to find the rt kernel a year and a half ago. I'll see if I can find the low-latency one I'm using in 14.04 LTS.

Update: And this is why I had trouble re. the -rt kernel some time ago, from [here]("http://askubuntu.com/questions/496403/ubuntu-14-04-realtime-kernels-3-13").

> sorry there isn't any, because linux-rt project was ended at Lucid(10.04)

The answer under that explains UStudio now uses the low-latency kernel. I couldn't find the -rt when I was looking back then, so I guess that's why I landed with the low-latency.

So, the low-latency kernel is in the repositories! I am using Synaptics, but should work ok in Software Centre. Look for 'linux-lowlatency' or 'linux-image-lowlatency' and install either. Should drag up the same kernel version as the one you have installed, but the lowlatency version. The latest 3.16 low-latency kernel's in there, too.

PS: Is this thread supposed to be marked solved? You can 'unsolve' it the same way. If you have solved it, please share how. ;)

---

### Post by Oliver_Evans on 2015-03-28
So I installed the lowlatency kernel using 

```
sudo apt-get install linux-lowlatency
sudo update-grub
```

And it worked! After a restart, uname -r returns

```
3.13.0-48-lowlatency
```

It doesn't seem to have changed much, though. I still have the same problem with occasional xruns. Is this because lowlatency is a soft RT kernel? Or was I wrong earlier when I asserted that xruns should be produced more consistently in a RT kernel?

Thanks again!
Oliver

---

### Post by DJonsson2008 on 2015-03-29
I'm using Xubuntu 14 LTS for a DAW.  This is a dedicated recording machine so did not need the full stack
of Ubuntu Studio. I'm simply using Audacity, post production editing takes place on another machine.

Finding the WIKIs on this confusing, checked in here.
Found that synaptic returns a long list of low latency items to be installed.

So finally like Oliver I installed from the command line, thanks Oliver.
Worked like a charm almost seemed to easy, machine booted up perfectly
uname -a shows low latency kernel is working.

Questions...

* Is in fact the lowlatency kernel loaded by Synaptic the same as that being used by Ubuntu Studio 14 ?

* Are there any other linux/ubuntu config switches to be thrown on a dedicated DAW?

Please advise

---

### Post by Bucky Ball on 2015-03-29
@ DJonsson2008: If you have questions other than the ones being asked by the OP here, suggest you start your own thread rather than jump on this one. You'll improve your chances of help and much less confusing.

@Oliver_Evans: What are you attempting to record at? 24bit/48? If so, try 16/44 and/or try tweaking the latency in the software a bit to get rid of some of the xruns (adjust sample rate). Most important: What hardware are you using for this and how much RAM is in the box?

---

### Post by DJonsson2008 on 2015-03-29
What is OP?

---

### Post by howefield on 2015-03-29
> **DJonsson2008 said:**
> What is OP?

OP = Original Post(er)

---

### Post by Oliver_Evans on 2015-03-29
Here are my qjackctl settings:
[IMG]http://i.imgur.com/wVE161E.png[/IMG]
Using these settings just to play music for the last few hours, I've gotten about 500 sporatic xruns. Definitely not optimal.

Also, the **RT** light in qjackctl goes off and on. It's not always lit up. Is this normal?

I have 6GB DDR3 RAM, a quad-core Intel i5 1.80GHz CPU, and a 7 Series Intel Audio Card.

More hardware info:

```
oliver@oliver-kubuntu:~$ sudo lshw -short
H/W path         Device      Class          Description
=======================================================
                             system         X450CA (ASUS-NotebookSKU)
/0                           bus            X450CA
/0/0                         memory         64KiB BIOS
/0/8                         memory         512KiB L2 cache
/0/9                         memory         128KiB L1 cache
/0/a                         memory         3MiB L3 cache
/0/b                         memory         6GiB System Memory
/0/b/0                       memory         2GiB SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
/0/b/1                       memory         DIMM [empty]
/0/b/2                       memory         4GiB SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
/0/b/3                       memory         DIMM [empty]
/0/c                         processor      Intel(R) Core(TM) i5-3337U CPU @ 1.80GHz
/0/100                       bridge         3rd Gen Core processor DRAM Controller
/0/100/2                     display        3rd Gen Core processor Graphics Controller
/0/100/14                    bus            7 Series/C210 Series Chipset Family USB xHCI Host Contr
/0/100/16                    communication  7 Series/C210 Series Chipset Family MEI Controller #1
/0/100/1a                    bus            7 Series/C210 Series Chipset Family USB Enhanced Host C
/0/100/1b                    multimedia     7 Series/C210 Series Chipset Family High Definition Aud
/0/100/1c                    bridge         7 Series/C210 Series Chipset Family PCI Express Root Po
/0/100/1c.1                  bridge         7 Series/C210 Series Chipset Family PCI Express Root Po
/0/100/1c.1/0    wlan0       network        AR9485 Wireless Network Adapter
/0/100/1c.3                  bridge         7 Series/C210 Series Chipset Family PCI Express Root Po
/0/100/1c.3/0                generic        Realtek Semiconductor Co., Ltd.
/0/100/1c.3/0.2  eth0        network        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controll
/0/100/1d                    bus            7 Series/C210 Series Chipset Family USB Enhanced Host C
/0/100/1f                    bridge         HM76 Express Chipset LPC Controller
/0/100/1f.2                  storage        7 Series Chipset Family 6-port SATA Controller [AHCI mo
/0/100/1f.3                  bus            7 Series/C210 Series Chipset Family SMBus Controller
/0/1             scsi0       storage        
/0/1/0.0.0       /dev/sda    disk           500GB HGST HTS725050A7
/0/1/0.0.0/1     /dev/sda1   volume         511MiB Windows FAT volume
/0/1/0.0.0/2     /dev/sda2   volume         459GiB EXT4 volume
/0/1/0.0.0/3     /dev/sda3   volume         6028MiB Linux swap volume
/0/2             scsi2       storage        
/0/2/0.0.0       /dev/cdrom  disk           DVD-RAM UJ8C2 S
/0/3             scsi6       storage        
/0/3/0.0.0       /dev/sdb    disk           1TB My Passport 0830
/0/3/0.0.0/1     /dev/sdb1   volume         931GiB Windows NTFS volume
/0/3/0.0.1                   generic        SES Device
```

Thanks again and again! :D

---

### Post by Oliver_Evans on 2015-04-12
I successfully compiled the RT-PREEMPT hard realtime kernel! Thanks for all the help. I posted my solution here: [http://ubuntuforums.org/showthread.php?t=2273355](http://ubuntuforums.org/showthread.php?t=2273355)

---

### Post by Bucky Ball on 2015-04-13
To help people along, avoid confusion and, rather than merging the threads as the other appears to encourage further discussion specific to the Pre-empt kernel, I've marked this thread as solved also. ;)

---

