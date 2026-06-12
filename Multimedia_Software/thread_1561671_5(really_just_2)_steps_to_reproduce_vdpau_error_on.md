---
title: "5(really just 2) steps to reproduce vdpau error on &gt;= 3 flavors of 2.6.32-24"
date: 2010-08-26
forum: Multimedia Software
---

### Post by denverdad on 2010-08-26
1.(opt) Clean install (From ubuntu.com - 64 bit, 64bit server, and netbook remix will all work(break))

2.(opt) Update, restart

3.(opt? I know it works (breaks) for 195.36.24 and for 256.44) activate nvidia current through Hardware Drivers Gui, restart

4. install vdpauinfo:
sudo add-apt-repository ppa:nvidia-vdpau/ppa
then using Synaptic, reload packages, install libvdpau1 and vdpauinfo (will also work (break) with more recent driver from x-swat ppa as shown in below output))

5. export VDPAU_NVIDIA_DEBUG=3 && export VDPAU_TRACE=1 && vdpauinfo

walla!
blah blah blah
VDPAU nvidia: Version: NVIDIA VDPAU Driver Shared Library  256.44  Thu Jul 29 01:51:58 PDT 2010
VDPAU nvidia: Error detected 0 3956 
VDPAU nvidia: Backtrace:
--: /usr/lib/vdpau/libvdpau_nvidia.so.1 [0x7f993e3c5000] DSO load base
00: /usr/lib/vdpau/libvdpau_nvidia.so.1 [0x7f993e3cb1b7] 
01: /usr/lib/vdpau/libvdpau_nvidia.so.1 [0x7f993e3cb5ae] 
 repeat. etc, etc ([full report]("http://pastebin.com/4dsrz09i"))

Now here is the cool part. This is on a 1 year old quad core with nvidia 8600GT, now turn on your nvidia ion netbook (Asus 1201n) that is running 32 bit netbook remix and follow steps 4 and 5 and walla! same error!

In fact, I would like to know if this happens on your machine if you run steps 4 and 5.

I have reproduced this with Ubuntu server clean install as well.

Apologies - Linux is not my first language and posting does not come naturally to me. I have been working on this for 3 days straight with very little sleep.

There are a number of old bug reports of similar issues related to ldconfig. I tried manually creating the symlinks, but it did not resolve the problem.

I stumbled across this problem because I have been trying to switch my life over to Ubuntu from Vista, and that means replacing my SageTV/XBMC life over to MythTV/XBMC. Without VDPAU, I can not watch any HDPVR recordings. WAF is at an all time low.

On the plus side, Ubuntu is incredible and I love it.

Thanks for your help and/or suggestions.
Randy

---

### Post by denverdad on 2010-08-26
Here are a couple people having a very similar problem:
[Re: Lucid upgrade: Nvidia or Nouveau I don't care...]("http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9312776#post9312776")

I tried the solution proposed in post#30 - didn't work. 
I skipped the line:
**"First if using 64 bit you want to install the driver using the 2.6.32-21 kernel NOT the -22 kernel."** b/c I don't have the -21 kernel. I have -22 and -24. This post led me to try a clean install of ubuntu server, which also didn't help, but did take a long time. In hindsight, perhaps I should try to do a clean install of the -21 server and see if that would work?

Here is an old bug that sounds related (read the comments):
[nvidia-vdpau-driver: bad /usr/lib/libvdpau_nvidia.so symlink]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=566518")

Here is another bug where the discussion is about these symlinks:
[nvidia-180-libvdpau packages both libvdpau and libvdpau_nvidia]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/432172")

---

