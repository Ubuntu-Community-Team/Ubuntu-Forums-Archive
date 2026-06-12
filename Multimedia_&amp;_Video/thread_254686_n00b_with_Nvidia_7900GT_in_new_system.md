---
title: "n00b with Nvidia 7900GT in new system"
date: 2006-09-10
forum: Multimedia &amp; Video
---

### Post by RunsWithScissors on 2006-09-10
Ok here is the situation I have a new systems that I want to have Ubuntu 6.06 DD installed on. 

I tried to install it as soon as I got the system about a month ago but no luck. eveytime I installed 

the Nvidia driver, after I restarted the xserver I got a black screen., an dmy monitor said "out of 

range" I tryied everything I could find but all methods resulted in "out of range"
I could hit alt+ctrl+backspace and I could see the command line for  a sec but the xserver always 

tried to restart.and when it did ....... you guessed it "out of range" and thien the monitor would 

shut off. I tried Suse 10. Enterprise Desktop and had pretty much the same luck.

Now I have read about all of these pitfalls  with getting the nvidia driver running. I was wondering 

if someone can give a walk through to get this running. I need maximum Nvidia OpenGL acceleration. 

I will be running 3D animation programs on this system.



the system is as follows
CPU                     Intel(R) Pentium(R) D CPU 3.00GHz   MMX, SSE, SSE2, SSE3, EM64T
Motherboard             ASUS P5N32-SLI Deluxe Nforce 4 x16 Intel
Chipset                 nVidia nForce4 SLI Intel Edition rev. A3
Audio                   nVidia nForce4 MCP rev. A4 
Memory Type		DDR2
Memory Size		2048 MBytes
Video                   Nvidia Geforce 7900 GT OC 256MB PCI-X
monitor                 Viewsonic WS LCD VX2025 @1680x1050
Hard Drive              WD 250GB SATA
DVD                     LG DVDRW DL 16X

---

### Post by tseliot on 2006-09-10
post the output of this command:
```
lspci -n | grep 300
```

---

### Post by RunsWithScissors on 2006-09-10
ok let me reistall ubuntu first. btw should install from the boot screen or from the live cd desktop icon? or does it make a difference?

---

### Post by RunsWithScissors on 2006-09-10
ok I have now installed ubuntu 6.06 and run the update thing that poped up as soon as I logged in

here is what I got when I ran the command from the terminal

runswithscissors@mohawk:~$ lspci -n | grep 300
0000:01:00.0 0300: 10de:0291 (rev a1)
runswithscissors@mohawk:~$

---

### Post by tseliot on 2006-09-10
Ok, try Method 1 of my guide:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

---

### Post by RunsWithScissors on 2006-09-10
Will the envy script not work?

and it says to make sure that I have the universe and multiverse repositories enabled how do I check for that?

---

### Post by RunsWithScissors on 2006-09-10
well Method 1 didn't work.

I got the same thing. When I hit ctrl+alt+Backspace the X server restarted then I got a black screen and in the center it said "Out of Range"

any suggestions?

---

### Post by RunsWithScissors on 2006-09-11
Ok got it working it was a a setting in the xorg.conf that I needed to over ride the edid information and specify a refresh rate.

---

