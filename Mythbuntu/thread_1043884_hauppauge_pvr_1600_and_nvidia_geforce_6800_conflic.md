---
title: "hauppauge pvr 1600 and nvidia geforce 6800 conflict"
date: 2009-01-18
forum: Mythbuntu
---

### Post by Embiggens on 2009-01-18
I recently bought a hauppauge hvr 1600 tuner card, thinking I was all smart because it's supported in 8.10.  However, I am not smart because there is a previously characterized conflict in loading the hvr 1600 module ( cx18 ) in the presence of my nvidia agp card (geforce 6800).  I've tried most of the fixes proposed in the 2 or 3 other threads I've found on this, like changing the kernel boot vmalloc parameter and such ([link here]("http://http.download.nvidia.com/XFree86/Linux-x86/1.0-9629/README/appendix-l.html"))
What if none of those solutions work?  (specifically, the proprietary nvidia driver won't install- though it will install fine if I remove the tuner card; on the other hand, the hauppauge module ( cx18 ) and the hvr load fine).  Has anyone had any success with a more drastic change, or am I completely hosed?  For general info, here is some of the relevant output from dmesg:

"sudo dmesg|grep nvidia"
```
[  105.134346] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  105.134388] nvidia: probe of 0000:01:00.0 failed with error -1
[  853.500651] nvidia: probe of 0000:01:00.0 failed with error -1
```

"sudo dmesg|grep BAR" (not sure about the meaning of BAR, but this looks like an informative listing)
```
[    0.604536] pci 0000:01:00.0: BAR 1: can't allocate resource
[    0.648269] pci 0000:01:00.0: BAR 1: can't allocate mem resource [0xe0000000-0xe7ffffff]
[   10.952747] pci 0000:00:06.0: device not available because of BAR 0 [0xfecf0000-0xfecf0fff] collisions
[  105.134365] NVRM: BAR1 is 0M @ 0x00000000 (PCI:0001:00.0)
[  853.500621] NVRM: BAR1 is 0M @ 0x00000000 (PCI:0001:00.0)

```

here is the relevant output of lspci -vv
```
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6800 GS] (rev a2)
	Subsystem: XFX Pine Group Inc. Device 217e
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (1250ns min, 250ns max)
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f4000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at <ignored> (32-bit, prefetchable)
	Region 2: Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at d8000000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [44] AGP version 3.0
		Status: RQ=256 Iso- ArqSz=0 Cal=3 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
		Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>
	Kernel modules: nvidiafb


03:02.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
	Subsystem: Hauppauge computer works Inc. Device 7444
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (500ns min, 50000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 25
	Region 0: Memory at f0000000 (32-bit, non-prefetchable) [size=64M]
	Capabilities: [44] Vital Product Data <?>
	Capabilities: [4c] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: cx18
	Kernel modules: cx18

```

---

### Post by Embiggens on 2009-01-19
Well, I think I'm going to try either

(a) Compiling the cx18 driver into the kernel.  I don't think this will help because I'm getting the resource allocation error before the module loads.

(b) Figuring out how to manually allocate resources.  I understand this will be a one or multiple month project for me, but I think it will be fun to try - does anyone have a good link or recommended reference I could look into?

---

### Post by quill7111 on 2009-01-28
I have a similar problem with a hauppauge 1600 and my new geforce 9600gt. As soon as I installed the hauppauge card my nvidia driver broke. I tried both the 177 and 180 versions of the nvidia driver available through synaptic/hardware drivers manager, but neither would load with the tv card installed. One thread suggested compiling the nvidia drivers from source using this [[COLOR="Blue"]Howto[/COLOR]]("http://desiato.tinyplanet.ca/~lsorense/debian/debian-nvidia-dri-howto.html"), but the thread and howto are both a little old (ubuntu 7.10 ish). Could the problem have something to do with how Ubuntu installs the drivers vs. compiling them from source?

Because I got the Hauppauge card from Newegg, it probably wouldn't be a big deal to return it and get another, but I'm curious to know if this is a universal problem with the nvidia and hauppauge drivers. Can I get around this by finding a card that doesn't use cx18? I'd really hate to give up my shiny new graphics card and go back to the five year old radeon... Any help would be appreciated!

---

### Post by klc5555 on 2009-01-28
> **quill7111 said:**
> I have a similar problem with a hauppauge 1600 and my new geforce 9600gt. As soon as I installed the hauppauge card my nvidia driver broke. I tried both the 177 and 180 versions of the nvidia driver available through synaptic/hardware drivers manager, but neither would load with the tv card installed. One thread suggested compiling the nvidia drivers from source using this [[COLOR="Blue"]Howto[/COLOR]]("http://desiato.tinyplanet.ca/~lsorense/debian/debian-nvidia-dri-howto.html"), but the thread and howto are both a little old (ubuntu 7.10 ish). Could the problem have something to do with how Ubuntu installs the drivers vs. compiling them from source?

Because I got the Hauppauge card from Newegg, it probably wouldn't be a big deal to return it and get another, but I'm curious to know if this is a universal problem with the nvidia and hauppauge drivers. Can I get around this by finding a card that doesn't use cx18? I'd really hate to give up my shiny new graphics card and go back to the five year old radeon... Any help would be appreciated!

This is an issue with all versions of the nvidia driver and the cx18 driver module. Ubuntu per se has nothing really to do with it. The problem is there is insufficient virtual memory being allocated to the kernel for both drivers. The solution (in nearly all cases)is to pass more virtual memory to the kernel at boot by configuring Grub to pass the parameter vmalloc=256m to the kernel at boot.

This didn't work in a machine I recently put together, but upping the ante with vmalloc=512m did the trick and the GeForce 8600 and the Hauppauge 1600 began to play very nicely with each other.  

Cheers! :)

---

### Post by quill7111 on 2009-01-28
Thanks klc. I look forward to giving it a shot tonight when I get home.

---

### Post by quill7111 on 2009-01-28
So I tried the vmalloc fix, but it didn't seem to have any effect. I tried vmalloc=256MB, vmalloc=512MB and even vmalloc=1024MB, but none of them had any effect. There's a segment in the nvidia readme which talks about the "uppermem" parameter, but I didn't try that. 

One question I had was where to put the vmalloc parameter in my menu.lst file. I tried putting it both before and after the kernel list, but I got the same result. All the threads that I've seen that have mentioned the vmalloc parameter haven't been very specific about where to put it.

---

### Post by klc5555 on 2009-01-29
> **quill7111 said:**
> So I tried the vmalloc fix, but it didn't seem to have any effect. I tried vmalloc=256MB, vmalloc=512MB and even vmalloc=1024MB, but none of them had any effect. There's a segment in the nvidia readme which talks about the "uppermem" parameter, but I didn't try that. 

One question I had was where to put the vmalloc parameter in my menu.lst file. I tried putting it both before and after the kernel list, but I got the same result. All the threads that I've seen that have mentioned the vmalloc parameter haven't been very specific about where to put it.

Kernel parameters including vmalloc go on the kernel line in the menu.lst. After the root= statement and any other kernel parameters you may have operating. 

I'd recommend backing up the menu.lst file before editing it up, and if you feel uncomfortable, consult a tutorial like "Ubuntu - How to Edit Grub Boot Parameters" available here:
 [http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

Cheers! :)

---

### Post by movieman on 2009-01-29
Safest option is to boot into the Grub command line and edit the boot command there; it won't be saved to disk, so if you screw it up you'll still be able to boot next time :).

Once you have the correct command line you can go through the process of permanently updating the files on the disk.

---

### Post by klc5555 on 2009-01-29
> **movieman said:**
> Safest option is to boot into the Grub command line and edit the boot command there; it won't be saved to disk, so if you screw it up you'll still be able to boot next time :).

Once you have the correct command line you can go through the process of permanently updating the files on the disk.


Ah yes, much better. That's the trouble with being mostly a Slacker --I have this unnatural urge to just start editing config files that sometimes gets the best of me. #-o

---

### Post by elgreek84 on 2009-02-12
I'd love an answer to this, I had to leave Ubuntu for Windows XP because of this, I just couldn't take it anymore, my other option was to go back to 8.04.  Do you guys think 9.04 (JJ) will have this problem resolved?  If so, I might just be willing to wait until this is released.  Is it an ubuntu/kernel problem that JJ may  fix?
thanks

---

### Post by quill7111 on 2009-02-12
@ elgreek

Don't give up before trying the vmalloc modification mentioned above in the thread. That fixed it for me. Just make sure you read the other posts about where to put the vmalloc modifier. 

I've now got both analog and digital up and running in Mythtv, although apparently the digital half of the 1600 is really particular about signal strength and can't pick up more than a handful of the channels that are supposed to be there in my area. Keeping my eye out for a cheap digital only tuner...

---

### Post by klc5555 on 2009-02-12
> **quill7111 said:**
> @ elgreek

Don't give up before trying the vmalloc modification mentioned above in the thread. That fixed it for me. Just make sure you read the other posts about where to put the vmalloc modifier. 

I've now got both analog and digital up and running in Mythtv, although apparently the digital half of the 1600 is really particular about signal strength and can't pick up more than a handful of the channels that are supposed to be there in my area. Keeping my eye out for a cheap digital only tuner...

I went with a new-style stripped down AverMedia A180 (where they've eliminated all the obsolete analog connections, leaving only the digital coax input) to supplement my digitally deaf hauppauge 1600 on the same machine. I was lucky enough to get the A180 white-boxed for about $40. 

It took a while to figure out how to get the saa7134 module and related firware to load up properly, but since then it's been an outstanding performer of a card for me --as good as my pchdtv5500s that cost me 3 times as much.

Cheers! :)

---

### Post by elgreek84 on 2009-02-14
I should clarify, I'm definitely not giving up on Ubuntu, I'm just not going to deal with the issue right now.  I tried the vmalloc setting and it worked for a while, but then it crapped out again (although I think it may have been a Seagate 7200.11 issue).  In any case, I plan to go back after I finish my thesis (I just don't want any issues while I work on this). Aftereward, however, I plan to try out Jaunty Jackalope this time around.  Hpefully this resolves the prolbem.

On a side note, Nvidia just released an update to their drivers, will this help the issue?  What is the source of the problem? X? Nvidia? Kernel? HVR-1600? Who needs to provide the fix?
Thanks!


> **quill7111 said:**
> @ elgreek

Don't give up before trying the vmalloc modification mentioned above in the thread. That fixed it for me. Just make sure you read the other posts about where to put the vmalloc modifier. 

I've now got both analog and digital up and running in Mythtv, although apparently the digital half of the 1600 is really particular about signal strength and can't pick up more than a handful of the channels that are supposed to be there in my area. Keeping my eye out for a cheap digital only tuner...

---

### Post by 67GTA on 2009-02-21
It is actually vmalloc=XXXM, and not vmalloc=XXXMB. [http://ubuntuforums.org/showthread.php?t=1004660&highlight=cx18+nvidia](http://ubuntuforums.org/showthread.php?t=1004660&highlight=cx18+nvidia)

---

### Post by klc5555 on 2009-02-22
> **elgreek84 said:**
> 
On a side note, Nvidia just released an update to their drivers, will this help the issue?  What is the source of the problem? X? Nvidia? Kernel? HVR-1600? Who needs to provide the fix?
Thanks!

The newer Nvidia driver does not change anything. Insofar as the vmalloc=XXXm kernel parameter solves the problem, it would seem likely that neither side views the matter as a problem that needs to be bothered with. It's just that the documentation, as usual, sucks.

---

### Post by d2globalinc on 2009-04-01
Problem is still in Jaunty latest BETA... I just installed to a system and had the nvidia drivers working great with my 6800GT card in this machine.. Then installed the HVR-1600 - and POOF nvidia drivers fail to load.. Added - vmalloc=256M to the kernel options in the /grub/boot/menu.lst - and fixed issue.

This was tested with Jaunty Beta latest 4/1/09 - and latest nvidia drivers - 180.44 - From what I've seen and read - this is an issue with x86 only, not x86-64 kernels.

Shane Menshik
D2 GLOBAL INC

p.s. I should also add that this machine has a built in video card on the motherboard that I do not use at all - so this could be another reason why the vmalloc= fix is needed - too many video card resources needed..

---

### Post by cubdukat on 2009-05-02
I've also tried the vmalloc fix, and it's gotten the new restricted drivers to work, but it seems a side effect is that I no longer have a working HVR-1600 card. When I select the "Watch TV" option, the screen goes black as if it's tuning, then it kicks me right back to the menu. Also, I've noticed that when I go into the menu of recordings, I have several programs which I had not set up to record in the listing. It seems to me that the card is live from the minute Mythbuntu Jaunty starts. I haven't set up the analog portion of the card because I don't have any need of it, but could that be causing part of the conflict? 

Also, what log should I be looking in for problems? I've tried looking in the Mythbuntu logs, but I can't seem to find anything.

---

### Post by klc5555 on 2009-05-02
> **cubdukat said:**
> I've also tried the vmalloc fix, and it's gotten the new restricted drivers to work, but it seems a side effect is that I no longer have a working HVR-1600 card. When I select the "Watch TV" option, the screen goes black as if it's tuning, then it kicks me right back to the menu. Also, I've noticed that when I go into the menu of recordings, I have several programs which I had not set up to record in the listing. It seems to me that the card is live from the minute Mythbuntu Jaunty starts. I haven't set up the analog portion of the card because I don't have any need of it, but could that be causing part of the conflict? 

Also, what log should I be looking in for problems? I've tried looking in the Mythbuntu logs, but I can't seem to find anything.

I'm not sure what "when I go into the menu of recordings, I have several programs which I had not set up to record in the listing" means. You have actual viewable recordings made by the 1600? You can watch these recordings (or at least see their animated 'thumbnails' in the menu?) Then the 1600 card is loading the cx18 driver and working properly. 

You can also confirm the 1600's driver and firmware are loaded mostly correctly from the command:  dmesg | grep cx18
which should return output that looks something like:

cx18:  Start initialization, version 1.1.0
cx18-0: Initializing card 0
cx18-0: Autodetected Hauppauge card
cx18 0000:05:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
cx18-0: cx23418 revision 01010000 (B)
cx18-0: Autodetected Hauppauge HVR-1600
cx18-0: Simultaneous Digital and Analog TV capture supported
tuner 2-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
cs5345 1-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
cx18-0: Registered device video0 for encoder MPEG (64 x 32 kB)
DVB: registering new adapter (cx18)
cx18-0: DVB Frontend registered
cx18-0: Registered DVB adapter0 for TS (32 x 32 kB)
cx18-0: Registered device video32 for encoder YUV (16 x 128 kB)
cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
cx18-0: Registered device video24 for encoder PCM audio (256 x 4 kB)
cx18-0: Initialized card: Hauppauge HVR-1600
cx18:  End initialization
cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
  
If your 1600 is in fact loaded correctly and seems to be recording things, but livetv fails, then the culprit is most likely a display problem: the way you have your video card set up, the new video card drivers set up, or your myth frontend configuration. 

Also, 'mythtv' account is in charge of recording, but your user account is in charge of watching livetv tv, so if your user account has not been properly added to the mythtv group, or if your user doesn't have correct read/write permissions to every directory in the default storage group, livetv will fail and kick you back to the menu even though you can record programs and watch recordings.

---

### Post by quill7111 on 2009-07-16
Just wanted to add that the vmalloc solution did work for me in Hardy once I figured out where to put it. 

Recently, however, I upgraded to Jaunty and the same problem appeared when I enabled the nvidia drivers. But this time the vmalloc parameter resulted in an unbootable system (with a bunch of error messages including "invalid boot parameter" and my personal favorite "kernel panic!"). Since my Jaunty install is brand new, I think I'm just going to start over and try the 64bit version rather than figuring out another solution for the x86 one.

---

### Post by 67GTA on 2009-07-16
I can confirm the 64bit version doesn't suffer from this bug because the virtual memory is allocated differently. Did you try different memory values 128, 512, etc?

---

### Post by quill7111 on 2009-07-16
I didn't try anything lower than vmalloc=1024 because in Hardy I stepped up gradually starting at =128, and the first one that worked was =1024. If I get motivated I might try some of the lower values to see if they don't break things. I sort of assumed that the error message "invalid boot parameter" had to do with vmalloc in general, but I suppose it could have also been the value that I entered. Although I'm not sure how 1024 could break it. 

But I'll probably just install the 64bit version and save the hassle. I love the fact that installing this OS is so painless...

---

### Post by theteju on 2009-07-18
Hello,

I have similar problem with Hauppauge Pvr 1600 and Nvidia geforce 8200. I could not try "vmalloc=" trick because I could not find proper step by step information to do so.

Please help me out ..

thank you.

---

### Post by quill7111 on 2009-07-18
@theteju

yeah, I had a hard time finding the instructions as well, and when I found some, I didn't understand them at all the first time through. All you have to do is edit the menu.lst file and include the parameter "vmalloc=*M" where "*"= an appropriate number (256, 512, 1024, etc.)

[s]Keep in mind that this fix probably will not work with Jaunty!!
(at least it didn't for me)[/s]

Apparently my problem was leaving off the "M" after the number in the vmalloc parameter, and although I haven't tested it, the vmalloc fix should work with all versions. Thanks 67GTA!

Open a terminal and type:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```
(this makes a copy of the menu.lst file under menu.lst.bak. Always a good idea when you're messing around with boot parameters.)

then type
```
gksudo gedit /boot/grub/menu.lst
```

This will open your menu.lst file in gedit but with sudo authority, allowing you to edit it. Obviously feel free to use whatever text editor you like, but you will need to sudo/gksudo it. 

Find the kernel line you need in menu.lst, probably the first one. Here's my menu.lst from an older install on a different machine:

```
title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd0,4)
**kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=66c6ff95-8b70-4b6d-8504-b8da0801473d ro quiet splash**
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=66c6ff95-8b70-4b6d-8504-b8da0801473d ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=66c6ff95-8b70-4b6d-8504-b8da0801473d ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=66c6ff95-8b70-4b6d-8504-b8da0801473d ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

```

At the end of the line, simply add "vmalloc=256M" (or whatever number you want) to make it look like this:

```

kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=66c6ff95-8b70-4b6d-8504-b8da0801473d ro quiet splash vmalloc=512M
```

It's probably not a good idea to copy anything that I've posted here since this install is pretty ancient, but it should give you an idea of what you need to do. And if something goes horribly wrong, just get to a terminal somehow and go back to your original menu.lst.

```
sudo cp /boot/grub/menu.lst.bak /boot/grub/menu.lst
```

Hope this helps!!

---

### Post by 67GTA on 2009-07-18
You have to add a capitol "M" to it for it to work. It will be ```
vmalloc=256M
``` It will work with any version as long as it is spelled correctly.

---

### Post by quill7111 on 2009-07-18
Thanks! I was wondering what had changed with the jaunty that would break this fix, but apparently I just didn't remember it correctly. I've changed my post above to reflect your correction.

---

### Post by theteju on 2009-07-21
Thanks every one !!

My problem got fixed with "256M" value. for someone's reference, I am running 8.10.

By the way... even though its not my efforts.. its all your support. But when I got mine fixed, I felt like Genious !!

LOL

Thank you very much guys.. YOU people are great.

MY next challenge is to get Asus Xonar D2 sound card working with all its features. I just ordered it. waiting for it to knock the door !!!

thank you all.

Take care.

---

### Post by kkovary on 2010-02-20
Hey everyone,

So for the past day or so I've been trying this menu.1st fix and it never seemed to work right. I did a bit of research and found out that in Ubuntu 9.10 menu.1st fixes are a thing of the past due to Grub2. Does anyone know of a workaround for this conflict in 9.10? Thanks for any help or of anyone can refer me to another thread with some info!

---

### Post by 67GTA on 2010-02-21
It can still be edited. You have to edit /etc/default/grub and then run ```
update-grub
``` in a terminal. This will then update the /boot/grub/grub.cfg file (formerly menu.lst) with anything added to /etc/default/grub. Open /etc/default/grub as root and look for 
```
GRUB_CMDLINE_LINUX=""
``` Then add the boot options in between the quotations (" ") and save. Then run ```
update-grub
``` Then /boot/grub/grub.cfg should have the options added to it and be read when you boot.

---

### Post by DataTully on 2010-03-28
> **67GTA said:**
> It can still be edited. You have to edit /etc/default/grub and then run ```
update-grub
``` in a terminal. This will then update the /boot/grub/grub.cfg file (formerly menu.lst) with anything added to /etc/default/grub. Open /etc/default/grub as root and look for 
```
GRUB_CMDLINE_LINUX=""
``` Then add the boot options in between the quotations (" ") and save. Then run ```
update-grub
``` Then /boot/grub/grub.cfg should have the options added to it and be read when you boot.
I've been looking ALL over for this fix!  I'm a newb to this but I'm making progress!  Thanks!

---

### Post by Nausser on 2010-06-09
Thank you very much for this post. I was editing the "vmalloc=512MB" during each boot manually. Not that I was restarting the system much anyways. 
I had Mythbuntu 9.10 and just upgraded to 10.04. It was really quite painless. Once I had Mythbuntu 10.04 running, this was the last fix I needed to implement.

Thanks Again!!!

---

### Post by nacho32 on 2011-03-28
wow I'm so glad I found this thread, I have the 1600 tv card and Nvidia 430 gt card and the same thing the TV card would break the Nvidia driver conflict, I was running linux mint 10 then tried to install ubuntu 10.10 and same thing, I will try the 64 bit version since my system is still fresh. Update Installed 64 bit version works like a charm!
here is a video of the problem in case some one else has this problem
[http://vimeo.com/21606922](http://vimeo.com/21606922)

---

