---
title: "(K)Ubuntu 11.04: allround bad 2D performance"
date: 2011-05-25
forum: Multimedia Software
---

### Post by Rikva on 2011-05-25
Hi! I've been running Kubuntu since the first stable release. 
Since a few weeks I'm running Kubuntu 11.04 on a Lenovo Thinkpad Edge 13. 

The problem is the video performance which is really bad. Not just 720p videos on YouTube that are choppy, but every HD file I open in VLC is plain unwatchable - very choppy video and sound. 

VLC and Xorg eat up all my CPU and sometimes I get a kernel panic.

I'm using the default Intel drivers.

Now here's the interesting part. On a different partition I'm running Arch Linux, also with X11, KDE, VLC. No problems there at all.

So every time I want to watch a movie I reboot to Arch. This is obviously not perfect since I'd like to keep using Ubuntu.

Any tips?

---

### Post by johanPO on 2011-05-31
Interesting. I have one as well, and I have the same issue. I do not have arch linux, but Windows 7. I know, but it was on the machine and I can use it to check performance. For this, windows beats 11.04. Under Windows I can play youtube 1080p without problems, and under ubuntu 360 is choppy...

We need to find some solution to this. Arch linux sounds like one solution... Maybe it is worth a try

---

### Post by Yellow Pasque on 2011-05-31
What GPU do you have?:
```
lspci
```

---

### Post by johanPO on 2011-06-01
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)


or from lshw


 *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:42 memory:f0000000-f03fffff memory:d0000000-dfffffff ioport:1800(size=8)


from glxinfo

client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:


Could it be that I do not have the right "driver"?

---

### Post by johanPO on 2011-06-01
I found the following

[http://ubuntuforums.org/showpost.php?p=10482298&postcount=4](http://ubuntuforums.org/showpost.php?p=10482298&postcount=4) 

and that seems to have improved things a lot. I think 
sudo adduser YourUserName video
sudo adduser YourUserName audio

were the biggest improvements
 
I now have

OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile GEM 20100330 DEVELOPMENT 
OpenGL version string: 2.1 Mesa 7.10.2
OpenGL shading language version string: 1.20
OpenGL extensions:

It still looks like the audio is slightly out of sync, but much better then before.

The CPU usage is also a lot higher 

playing a 1080p in totem is still choppy but in VLC it is OK, but I have a cpu load of 100%. Under windows, playing the same video is hardly noticeable on the CPU...
I don't think that is normal on an iCore3 380UM.

---

