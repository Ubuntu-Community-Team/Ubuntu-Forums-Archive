---
title: "Same problem with Totem with video hesitation on a different laptop"
date: 2018-05-22
forum: Multimedia Software
---

### Post by jeo7 on 2018-05-22
After having this problem with Ubuntu 18.04 on a laptop running an AMD processor with integrated Radeon R7 series graphics, I eventually gave up and installed Linux Mint based on Ubuntu 16.04. I was convinced that it was the graphic driver that was at fault.

So fast forward to yesterday. I installed Ubuntu 18.04 on a laptop running an i5 core Intel processor with Intel graphics and also NVIDIA graphics. Not sure why two graphics, but that's what it has. There is an NVIDIA driver for this video card.

Lo and behold, the same problem with Totem exists on this laptop as well. The video plays in stops and starts with hesitations, especially with mp4s. Since the problem exists on two laptops with completely different graphics and processors, I doubt that it has anything to do with video drivers.

Has no one else noticed this? Is there any solution to this? I know a work around would be to use a different video player, but it still bothers me that I can't use Totem and knowing that this problem exists without resolution kind of spoils the Linux experience for me. Incidently, the problem appears to be on Dragon Player as well.

Any insight would be greatly appreciated!

EDIT: I have installed ubuntu-restricted-extras.

---

### Post by Autodave on 2018-05-23
Have you tried VLC to see if it has the same condition/problem?

---

### Post by monkeybrain20122 on 2018-05-23
The first thing I do after installing Ubuntu is getting rid of Totem and use a better player like mpv+ Smplayer or vlc. Totem has always been kind of a piece of crap, buggy and lacking in features (maybe even less features now the way gnome is going) Totem != Linux experience, only gnome experience.

---

### Post by jeo7 on 2018-05-23
> **Autodave said:**
> Have you tried VLC to see if it has the same condition/problem?

Yes, I know the problem doesn't exist with either VLC or Kaffeine.

> Totem != Linux experience, only gnome experience. 		 

Since Gnome is my (much) preferred environment to work in, whatever is a Gnome experience for me is pretty much a Linux experience for me. But I get where you are coming from. I just can't believe that this problem exists and more people have not complained about it.

---

### Post by mc4man on 2018-05-23
Install inxi then run & post results
```
inxi -GC
```

---

### Post by jeo7 on 2018-05-25
> **mc4man said:**
> Install inxi then run & post results
```
inxi -GC
```
```
CPU:       Dual core Intel Core i5-7200U (-MT-MCP-) cache: 3072 KB
           clock speeds: max: 3100 MHz 1: 1374 MHz 2: 868 MHz 3: 906 MHz
           4: 881 MHz
```

---

### Post by Yellow Pasque on 2018-05-25
```
sudo apt-get install vainfo
vainfo
```

1. Totem uses gstreamer
2. gstreamer uses VA-API for hardware decode
3. gstreamer-vaapi modules sometimes has its own issues (crazy colors etc.)
4. open-source radeon driver tends to work better with VDPAU (mesa-vdpau-drivers pacakge) than VA-API (mesa-va-drivers package) in my experience

---

### Post by jeo7 on 2018-05-25
> **Temüjin said:**
> 
4. open-source radeon driver tends to work better with VDPAU (mesa-vdpau-drivers pacakge) than VA-API (mesa-va-drivers package) in my experience

I thought this for a very long time when I was using just an AMD/Radeon laptop, but now the same thing is happening with an Intel i core 5 with Intel graphics. So I am thinking that the problem is not a driver problem, but some kind of a problem with Totem.

I just tried Totem again with an .mp4 file, and believe it or not, it appears to be working now. I can't say for sure because I need to play with it for a while to see if it really is working. But it appears to be working. I wonder if that has anything to do with a bunch of updates I did last night.

I am attaching the output of vainfo for the Intel laptop.

---

### Post by mc4man on 2018-05-25
> **jeo7 said:**
> I thought this for a very long time when I was using just an AMD/Radeon laptop, but now the same thing is happening with an Intel i core 5 with Intel graphics. So I am thinking that the problem is not a driver problem, but some kind of a problem with Totem.

I just tried Totem again with an .mp4 file, and believe it or not, it appears to be working now. I can't say for sure because I need to play with it for a while to see if it really is working. But it appears to be working. I wonder if that has anything to do with a bunch of updates I did last night.

I am attaching the output of vainfo for the Intel laptop.
With the intel graphics machine you've got pretty good support for vaapi. The only downside of totem is there isn't any way to disable hwdec on any particular file (or any easy way), so if you have an occasional file that doesn't work well via vaapi then you could just try another player rather than removing the gst-vaapi plugin.
Honestly a large number of vid's don't really need hwdec, maybe useful for high bitrate hevc & vp9 or for some power saving? on battery operated devices. (also maybe more helpful on dual core machines..

---

### Post by jeo7 on 2018-05-26
It's not just an occasional video ... it's a problem with all my .mp4's. Do you think it would be useful to remove the gst-vaapi plugin on the AMD machine?

I don't know why inxi returned that this machine is a dual core machine, but the Intel i5 core has 4 cores.

---

### Post by jeo7 on 2018-05-26
By the way, I need to correct something I wrote earlier. Totem still is not working.

---

### Post by kazakore on 2018-05-26
> **jeo7 said:**
> I don't know why inxi returned that this machine is a dual core machine, but the Intel i5 core has 4 cores.

No it's not, it has two physical processor cores and four threads. Hence why it calls it dual core yet reports four different current core speeds. It's called HypreThreading (but different to the technology with the same name from the days of the P4.)

[https://ark.intel.com/products/95443/Intel-Core-i5-7200U-Processor-3M-Cache-up-to-3_10-GHz](https://ark.intel.com/products/95443/Intel-Core-i5-7200U-Processor-3M-Cache-up-to-3_10-GHz)

---

### Post by mc4man on 2018-05-26
As far as the amd machine try removing the gst-vaapi  plugin (which get installed from restricted-extras > restricted-addons
Did inxi report anything on your graphics on the Intel machine ? ( the -G option

---

### Post by jeo7 on 2018-05-26
Is the gst-vaapi plugin called gst-vaapi? I'm asking because I can't seem to find it. Or should I try removing all the restricted extras?
  
I posted everything that inxi reported on the intel machine using -CC option.

---

### Post by Yellow Pasque on 2018-05-26
gstreamer1.0-vaapi

For better understanding of the graphics:
```
lspci -nn | grep '\[03'
```

---

### Post by mc4man on 2018-05-26
> **jeo7 said:**
> Is the gst-vaapi plugin called gst-vaapi? I'm asking because I can't seem to find it. Or should I try removing all the restricted extras?
  
I posted everything that inxi reported on the intel machine using -CC option.
It was -GC not -CC

---

### Post by jeo7 on 2018-05-26
> **Temüjin said:**
> gstreamer1.0-vaapi

For better understanding of the graphics:
```
lspci -nn | grep '\[03'
```

This is for the AMD machine:

```
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Wani [Radeon R5/R6/R7 Graphics] [1002:9874] (rev c8)
 
```

---

### Post by jeo7 on 2018-05-26
> **mc4man said:**
> It was -GC not -CC

Oops, sorry. My eyes must be failing.

Here is the result for the _**AMD machine**_:

```
~> inxi -GC
Resuming in non X mode: xdpyinfo not found. For package install advice run: inxi --recommends
CPU:       Quad core AMD A12-9720P RADEON R7 12 COMPUTE CORES 4C+8G (-MCP-) 
           cache: 4096 KB
           clock speeds: max: 2700 MHz 1: 1390 MHz 2: 1388 MHz 3: 1573 MHz
           4: 1449 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Wani [Radeon R5/R6/R7 Graphics]
           Display Server: x11 (X.org 1.19.6 )
           drivers: ati,amdgpu (unloaded: modesetting,fbdev,vesa,radeon)
           tty size: 80x24
  
```

---

