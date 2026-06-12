---
title: "Mythtv cpu 100%"
date: 2009-02-21
forum: Multimedia Software
---

### Post by xsilvergs on 2009-02-21
Hi,

I've just installed Ubuntu 8.10 on the PC that is my PVR. For a few years now I've been using GBPVR which is a brilliant program but runs under windows.

So I thought I'd try mythtv which I've installed using this guide [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php) which installed ok, but my CPU is running at 100% nearly all the time.

Has anybody else seen this problem and where should I start looking, still quite new to Ubuntu, any help would be appreciated.

Thank you.

P.S.Memory:44% in use by programs, 38% in use as cache

---

### Post by punx45 on 2009-02-21
run top in console and see what is using up all the CPU

---

### Post by xsilvergs on 2009-02-22
punx45

Thanks for reply. Never tried top before but it shows 10% CPU activity until I run system monitor and then it jumps to 70%.

With firefox and tops running I get something like this: 

Cpu(s): 11us, 3.7%sy, 0.0%ni, 87%id, 0%wa, 1.0%hi, 0.0%si, 0.0%st
Mem: 773728k total, 737000k used, 37100k free, 71722k buffers
Swap: 1397612k total, 1764k used, 1395848k free, 317380k cached

If I try to run mythtv it's all very stuttery.

What should I look for next?

Tony

---

### Post by xsilvergs on 2009-02-22
More info.

After some fiddling I've got the CPU down and myth plays TV smoothly 

As I'm unlikely to play recorded programs on the PC but play the media via my Hauppauge MediaMVP I've installed it using this tutorial [https://help.ubuntu.com/community/MythTV/MediaMVP_Frontend](https://help.ubuntu.com/community/MythTV/MediaMVP_Frontend) but my MVP get stuck with "contacting servers". It finds the PC IP address but the PC name comes up as <unknown>, the PCs name is PVR, it then just sits there saying "Contacting Servers" with the blobs scrolling across the screen of the TV.

Any ideas.

---

### Post by punx45 on 2009-02-22
network problem maybe? not really sure. no experience with that device.

---

