---
title: "TV Tuner: IO-DATA GV-MVP/RX3"
date: 2008-06-30
forum: Multimedia Software
---

### Post by osarusan on 2008-06-30
I run Windows Vista and Ubuntu on my PC. Recently I got a IO-DATA GV-MVP/RX3 TV Tuner card, and I was wondering if I might be able to set it up in Ubuntu. Searching around I was able to find some websites about using the RX2 model in linux, however a) they're using Fedora and Vine linux, of which I know nothing, and b) it's all in Japanese.

[http://www.h5.dion.ne.jp/~tangos/HomeServer/mbrtv/ivtv.html](http://www.h5.dion.ne.jp/~tangos/HomeServer/mbrtv/ivtv.html)
[http://shino.pos.to/linux/rx2w.html](http://shino.pos.to/linux/rx2w.html)

Apparantly there's a way to do it with ivtv, but only barely being able to read the Japanese and not knowing enough about linux, I was wondering if anyone else might be able to look at this and figure it out. Of course, these pages are for the RX2, but maybe my model works in the same way?

Any help would be greatly appreciated. Thanks!

---

### Post by osarusan on 2008-07-27
*Bump*

I guess it's a long shot afterall... does anyone else have this hardware?

---

### Post by cariboo on 2008-07-27
if you run:

```
lspci
```

in a terminal and post the output in your next post, it might tell us what chip set it is using, if we know that I'm sure we can help you get your tv tuner card working. If there are instructions to get it running in Fedora, it should work in Ubuntu.

Jim

---

### Post by osarusan on 2008-08-13
> 00:00.0 Host bridge: Intel Corporation 82925X/XE Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82925X/XE PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7950 GT] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
04:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
04:01.0 Multimedia audio controller: Creative Labs SB Audigy LS
04:02.0 Multimedia video controller: NEC Corporation Dual Tuner/MPEG Encoder (rev 0c)

Thanks for the tip. :-) Here is my lspci output. I guess the card is the final entry: 04:02.0 Multimedia video controller: NEC Corporation Dual Tuner/MPEG Encoder (rev 0c)

Do you have any suggestions?

Thank you.

---

### Post by osarusan on 2008-08-31
*bump*

Any ideas?

---

### Post by Cresho on 2008-08-31
if it is a analog, try tvtime.  It is in add remove.

if it is digital, I recommend me-tv  high definition tv  player and recorder.

if you ask kindly, i can show you how to record television shows through tvtime.

in tv time, f is for fullscreen or not
it works with right clicks.

---

### Post by osarusan on 2008-09-04
Thanks for the reply, Cresho.

I installed both tvtime and me-tv, but I can't get either to work with the card. It appears that the driver isn't installed or configured correctly; tvtime connects only to my webcam, and when I try to change the video source there are no other options.

me-tv errors on load saying there is no tuner device.

Is there anyone who could help me set up the tuner to work? I'm completely new to drivers in linux.

---

### Post by saedelaere on 2008-09-10
Please post the ouput of

dmesg | grep ivtv

If there is no output, you could try 

sudo modprobe ivtv


Regards 

Saedelaere

---

### Post by osarusan on 2008-09-14
```
osarusan@gorilla:~$ dmesg | grep ivtv
[ 2428.670339] ivtv:  Start initialization, version 1.1.0
[ 2428.670403] ivtv:  End initialization

```

It did nothing at first, so I did the modprobe command you said. I got this message. Any idea what it means?

---

### Post by osarusan on 2008-09-16
Just for reference, here is the card's page: [http://www.iodata.jp/product/tv/analog/gv-mvprx3/index.htm](http://www.iodata.jp/product/tv/analog/gv-mvprx3/index.htm)

And here is another website that seems to have something: [http://wiki.livedoor.jp/rockie33jp/d/Ubuntu%207.04%20Feisty%A4%C7GV-MVP/RX%A4%F2%C6%B0%A4%AB%A4%B9](http://wiki.livedoor.jp/rockie33jp/d/Ubuntu%207.04%20Feisty%A4%C7GV-MVP/RX%A4%F2%C6%B0%A4%AB%A4%B9)

My problem is that the Japanese makes more sense to me than the instructions... in other words, none at all. I am really a beginner linux user, so I have no idea what to do or how to do it, whether in English or not. Can anyone look at the pasted commands on these websites and figure out what it means and how to do it Ubuntu?

---

### Post by saedelaere on 2008-09-18
Hi,

I thought I found something on the ivtv wiki about your card. But they are referring to the MVP/RX2. 

Perhaps 

lspci -v 

could give us some more infos. I would recommend to ask your questions in the [ivtv mailing list]("http://ivtvdriver.org/index.php/Asking_for_help").

The guys there are capable and friendly :)

If you managed to get your card working you could try [TV-Viewer]("http://home.arcor.de/saedelaere/index_eng.html").

Regards

---

### Post by osarusan on 2008-09-20
Hi, thanks for the reply.

```
04:02.0 Multimedia video controller: NEC Corporation Dual Tuner/MPEG Encoder (rev 0c)
	Subsystem: I-O Data Device, Inc. Unknown device d03f
	Flags: bus master, medium devsel, latency 64, IRQ 3
	Memory at dcdfe000 (32-bit, non-prefetchable) [size=8K]
	Memory at dcdfbff0 (32-bit, non-prefetchable) [size=16]
	Capabilities: [40] Power Management version 2

```

There's the output of lspci -v. It's kind of Greek to me. I'll look at the ivtv wiki in the meantime and see if the RX2 solution might work for me... If you have any other suggestions please let me know!

---

### Post by osarusan on 2008-12-16
Sorry to bump... it's been a few months and still I have no idea. I mailed the ivtv help list, but received no responses at all.

Can anyone else help me please?

---

