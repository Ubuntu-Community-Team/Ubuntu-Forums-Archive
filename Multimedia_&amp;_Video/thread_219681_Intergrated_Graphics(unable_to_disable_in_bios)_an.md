---
title: "Intergrated Graphics(unable to disable in bios) and PCI Graphics conflict"
date: 2006-07-20
forum: Multimedia &amp; Video
---

### Post by Bcell on 2006-07-20
Hi, I am currently trying to convert an 'old' dell 4500S to a mythTV box using Ubuntu.  I have been able to get a working install on the computer *without* the PCI FX5200 and have gotten Ubuntu running like a dream.  Unfortunately I have spent the last month trying to figure out why the FX5200 would make the system hang each time I tried to install it. I know Ubuntu has had notorious issues with Nvidia, so I have installed the drivers (and ALL versions) in almost every method possible, but alas no luck.

I read while forum crawling that I need to disable my 'intel intergrated graphics' when trying to use the PCI FX5200.  So I went into the bios and I get only two options: 'onboard' and 'auto' (no 'disable onboard'). I tried finding a more updated BIOS but there hasn't been one since 2002. After a few more weeks of reinstalling drivers etc... I came to the conclusion that I NEED to somehow disable this 'intergrated graphics' through Ubuntu.  I heard a rumor that someone had compiled a kernel that basically either a) disable the intergrated graphics or b) set the graphics memory of the intergrated graphics to 0 effectively disabling it. 

Can anyone suggest a method of going about this besides physically ripping the intergrated graphics side of my mother board off? I am going out of my mind.

Side Note: I had windows running on this machine with the PCI FX5200 card working like a charm.  I am also fairly new to Ubuntu (be kind ;) ) but semi-computer savy.

---

### Post by tseliot on 2006-07-20
> **Bcell said:**
> I know Ubuntu has had notorious issues with Nvidia
Unfortunately all distros can have problems with the Nvidia Drivers (it does depend of course)

> **Bcell said:**
> I read while forum crawling that I need to disable my 'intel intergrated graphics' when trying to use the PCI FX5200.  So I went into the bios and I get only two options: 'onboard' and 'auto' (no 'disable onboard'). I tried finding a more updated BIOS but there hasn't been one since 2002. After a few more weeks of reinstalling drivers etc... I came to the conclusion that I NEED to somehow disable this 'intergrated graphics' through Ubuntu.  I heard a rumor that someone had compiled a kernel that basically either a) disable the intergrated graphics or b) set the graphics memory of the intergrated graphics to 0 effectively disabling it. 

Can anyone suggest a method of going about this besides physically ripping the intergrated graphics side of my mother board off? I am going out of my mind.

Side Note: I had windows running on this machine with the PCI FX5200 card working like a charm.  I am also fairly new to Ubuntu (be kind ;) ) but semi-computer savy.

1) Set the graphic card in the BIOS to "auto". Then turn off your computer

2) Plug in your Nvidia card and connect your monitor to it.

3) Boot in Recovery Mode (you can boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer)

4) type:
```
lspci | grep VGA
```

and write down the output on a piece of paper (there's no need to post it right now).

OR (if you don't want to use a piece of paper)
```
lspci | grep VGA > /home/your_username/videolist.txt
```

OF COURSE replace "your_username" with your username.

You will find the output of that command in /home/your_username/videolist.txt

You might need that output later

5) Type: 
```
sudo nano -w /etc/X11/xorg.conf
```

Put a # before the BUSID in the section Device
Set the driver to "vesa"

CTRL+X to exit

6) reboot:
```
sudo reboot
```

and boot as usual.

If that doesn't work (explain me what happens) please post the output you got in step 5

---

### Post by Bcell on 2006-07-20
Thanks so much for the quick response. I did as you said and booted in (recoverymode) with the FX5200 and unfortunately the computer hangs (freezes) after trying to load restricted drivers...  

I am going to include the output that I could read when it froze (the previous errors flashed too fast for my eyes):

[17179674.33200] EIP is at smp_apic_timer_interupt+0x32/0x100
[17179674.33200] eax: c16c32e0 ebx: 00000000 ecx:00000000 edx: dfeb8000
[17179674.33200] esi: 012c7f60 edi:dfeb9fbc ebp: bff6d5b8 esp:dfeb9fa0
[17179674.33200] ds: 007b es:007b ss:0068
[17179674.33200] Process S10udev (pid: 2118, threadinfo=dfeb8000 task=eed95030)
[17179674.33200] Stack: dfeb9fbc 00000008 b7f2aadc bff6d6e8 bff6d5a8 bff6d5b8 c0103fb4 b7f2aadc
[17179674.33200] 00000000 bff6d664 bff6d6e8 bff6d5a8 bff6d5b8 0000000b 0000007b 0000007b
[17179674.33200] ffffffef b7e6b9de 00000073 00000202 bff6d47c 0000007b cccccccc cccccccc
[17179674.33200] Call Trace:
[17179674.33200] [<c0103fb4>] apic_timer_interrupt+0x1c/0x24
[17179674.33200] Code: ff 89 5c 24 08 31 db 89 74 24 0c 89 7c 24 10 89 c7 b8 80 b3 3f c0 89 6c 24 14 21 e2 8b 34 8d 20 10 40 c0 01 f0 ff 40 0c <89> 1d b0 d0 ff ff bb cc b7 3f c0 81 42 14 00 00 01 00 8b 72 10
[17179674.33200] *HANG* 

Also I tried your suggestion with the 'onboard' in the BIOS (allowing boot and get to terminal):

command: lspci | grep VGA
0000:00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Intergrated Graphics Device (rev 01)
0000:01:08.0 VGA compatible controller: nVidia Corporation NV34 {GeForce FX 5200] (rev a1)

I also edited my xorg.config file as you said and rebooted with 'auto' in BIOS. Got a similar hang situation to the one above. :( 

I attached my xorg.config as well for reference.

---

### Post by tseliot on 2006-07-20
Try this and tell me what happens:

1) Type:
```
sudo nano -w /etc/X11/xorg.conf
```

Remove the "#" before the BUSID and set the BUSID like the following example:

```
BusID		"PCI:1:8:0"
```

CTRL+X to exit (save the file)

Then turn off your computer.

2) Set the graphic card in the BIOS to "auto". Then turn off your computer

3) Plug in your Nvidia card and connect your monitor to it.

4) Boot Ubuntu as usual


Then report to me. If that doesn't work we'll try another way

---

### Post by Bcell on 2006-07-20
Yeah this method seemed to produce the same result...

The computer once again booted and hung after trying to load restricted drivers. :(

---

### Post by christhemonkey on 2006-07-20
Sounds like your graphics card might be a tad ga-shmungled!

if you type:
```
dmesg | less 
```
Then you will be able to scroll through the output of dmesg, which will be useful for telling us the earlier errors.

---

### Post by Bcell on 2006-07-20
Are you suggesting that I boot with the 'onboard' in BIOS enabled and then try```
 dmesg | ls 
```? Because that is the only way I am able to enter the terminal or boot Ubuntu.

Side Note: As previously stated, the FX 5200 worked fine under my Windows XP operating system.

---

### Post by tseliot on 2006-07-20
Read (or print) the part of the guide below which begins with:
> OTHERWISE

b) If you have installed Ubuntu...

[http://www.ubuntuforums.org/showthread.php?t=75281](http://www.ubuntuforums.org/showthread.php?t=75281)

[B]
Then[/B] try this:

1) Put the "#" back in your xorg.conf before BUSID

2) Set the graphic card in the BIOS to "auto". Then turn off your computer

3) Plug in your Nvidia card and connect your monitor to it.

4) Try the part of the guide below which begins with:
> OTHERWISE

b) If you have installed Ubuntu...

[http://www.ubuntuforums.org/showthread.php?t=75281](http://www.ubuntuforums.org/showthread.php?t=75281)

Try all the boot parameters suggested in the guide

---

### Post by Bcell on 2006-07-21
Not good news... tried to your guide (btw there is an duplicated step 3 and 6) and the computer still hangs everytime.

---

### Post by tseliot on 2006-07-21
Can you try this guide?
[http://www.ubuntuforums.org/showthread.php?t=192677&highlight=nvidia+intel](http://www.ubuntuforums.org/showthread.php?t=192677&highlight=nvidia+intel)


Please, tell me if it works for you.

---

### Post by Bcell on 2006-07-21
Wow.  I can't thank you enough. The guide you suggested partially worked for me.  Here is what I did:

1: Turned BIOS to 'onboard'
2: In terminal typed
```
sudo nano /etc/modprobe.d/blacklist
```
3: Added the following to the end of the file:
```

[B]blacklist agpgart
blacklist intel_agp[/B]

```
4: Ran latest Nvidia driver package (8762 I think)
5: Restarted computer with 'auto' enabled in BIOS

And the graphics card is SO much faster... now for TV out.

Thanks again. Hopefully won't be back with anymore issues as my MythTV box! :smile:

---

### Post by tseliot on 2006-07-22
> **Bcell said:**
> Wow.  I can't thank you enough. The guide you suggested partially worked for me.  Here is what I did:

1: Turned BIOS to 'onboard'
2: In terminal typed
```
sudo nano /etc/modprobe.d/blacklist
```
3: Added the following to the end of the file:
```

[B]blacklist agpgart
blacklist intel_agp[/B]

```
4: Ran latest Nvidia driver package (8762 I think)
5: Restarted computer with 'auto' enabled in BIOS

And the graphics card is SO much faster... now for TV out.

Thanks again. Hopefully won't be back with anymore issues as my MythTV box! :smile:
I will add it to my guide then

---

### Post by tseliot on 2006-07-22
I have written a guide about it and given credits to you (Bcell) and to the ones who posted the original guide.

It's here:
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

---

### Post by Bcell on 2006-07-25
Bad news tseliot... wanted to ammend that post. Although I did get the graphics driver working before restart (used latest driver 8762 I think), on restart it crashed my computer and I had to fresh install ubuntu which I didn't get on the internet until today.  Crossing my fingers, going to try this install process with other driver (nvidia-settings package) and see if that works.  Will keep you updated.

But atleast blacklisting got the comp working before restart...

---

### Post by Bcell on 2006-07-27
Hey,

Just tried to install my card again and YAY!

All I had to do was use the steps I said above and then use 'vesa' as the driver instead of installing, the newest nvidia graphics drivers.

boots up and everything. trying different drivers, will tell you how is goes.

---

### Post by starfire1983 on 2006-10-17
When I tried to boot the Dapper install CD on my roommate's computer, I got the same error message and a kernel panic message the second time. Mostly the same situation. Can't disable the onboard chip through the BIOS and it is set to use the PCI bus for the main grapihcs card but theres a kernel panic each boot. Intel chip and a NVidia GeForce FX 5500.

---

### Post by sadaraine on 2007-05-08
The blacklist steps above worked like a charm for my Dell workstation that I had a PCI Nvidia 5200 configured for dual-monitors.  It had worked for about 2 boots fine, then started being weird.  I'm glad these forums are here!

---

