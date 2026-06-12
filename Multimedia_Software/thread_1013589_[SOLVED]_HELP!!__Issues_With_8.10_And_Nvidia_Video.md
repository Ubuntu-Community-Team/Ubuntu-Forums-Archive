---
title: "[SOLVED] HELP!!  Issues With 8.10 And Nvidia Video Drivers"
date: 2008-12-17
forum: Multimedia Software
---

### Post by HotDogBunToo on 2008-12-17
Went with upgrading to Ubuntu Server since it'd utilize tapping into my 4GB upgrade without going 64bit.

However my issues with my integrated Nvidia videocard (nforce 630i / GeForce 7100) is rendering me to a 800 x 600 screen. So far I tried installing the headers for this kernel then installing the video drivers from Nvidia themselves as well as installing the same propitiatory video drivers from the Synaptic and in System -> Hardware Drivers. Sadly all I'm getting for my efforts is a message before login screen that says "(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!". Also worth noting is that my sound also isn't coming back up.

I had issues with Ubuntu Server before yet went to desktop route after giving up, now that I'm up to 4gigs RAM I'm moreso stuck with this issue until things are figured out (no way am I wasting 1gig of RAM) so any help would be GREATLY appreciated :(

---

### Post by Sam Lars on 2008-12-17
I also had issues with Nvidia drivers going to 8.10.  I ended up using Envy, and it seemed to work.  But then I think the card died.  I'm hoping it was unrelated.

---

### Post by HotDogBunToo on 2008-12-18
Hey  Sam Lars   

Thanks for the help.  I tried Envy after completely removing the nvidia stuff for a clean install and I'm still getting the same error message. Both the 177 and 173 drivers are giving me hell right now when trying to install either one :(

---

### Post by Sam Lars on 2008-12-18
When I was trying to compile the drivers, I thought my problems were because I had kernel -10 installed but the latest headers and source were -9... probably due to the Proposed repo... any chance you have that going on?

---

### Post by adam_kimber on 2008-12-18
Whilst I do not know much about the server edition. This is how i got the nVidia drivers working before 8.10 and for 8.10. 

Before 8.10

Enable universe and the other "restricted" repos. Install restricted drivers for your current kernel. uname -r will give you the current version of your kernel and ```
apt-cache search | grep <the kernel number>
```. Change a line in the xorg.conf from nv to nvidia and it should work.

8.10

Go to restricted drivers window and enable the restricted drivers. In one of my upgrades this did not work... But on a vanilla install this works perfectly. Best way to install the drivers IMO as they can be updated by the updates system. With Envy and other third party programs these updates, like security patches etc might not work. 


Otherwise its troubleshooting time...... 

The system will have recorded what the actual error is in teh messages log. You can access this by typing dmesg or going to the System Log window. If you could paste the last few lines which should have at least one (EE) then we will be able to work out what is wrong. It might be a resolution issue, a keyboard issue, a number, speech mark etc missing from the file......

---

### Post by Sam Lars on 2008-12-18
The error is that the kernel module could not be loaded.
You can try the hardware drivers window, but that didn't do anything for me.

---

### Post by HotDogBunToo on 2008-12-18
Thanks Adam & Sam,

I actually tried the various methods of installing the drivers whether it was through downloading the driver from Nvidia's website (which then prompted me to reinstall Linux thinking doing it cleanly via "cleaner" driver installs would do the trick), synaptic, the "Hardware Drivers" window, and last EnvyNG all of which is still taking me back to the original error message.  I even tried explicitly referring to the BusID in the xorg.conf file and nothing is working.  So below is the long list of things I found in the log file output that seems to be related to my Nvidia hiccups.

```

[   11.903859] nvidia 0000:00:10.0: PCI INT A -> Link[SGRU] -> GSI 22 (level, low) -> IRQ 22
[   11.903867] NVRM: This PCI I/O region assigned to your NVIDIA device is invalid:
[   11.903868] NVRM: BAR1 is 256M @ 0x00000000 (PCI:30000000:01.0)
[   11.903873] NVRM: This is a 64-bit BAR mapped above 4GB by the system BIOS or
[   11.903874] NVRM: Linux kernel. The NVIDIA Linux graphics driver and other
[   11.903875] NVRM: system software do not currently support this configuration
[   11.903877] NVRM: reliably.
[   11.903893] nvidia: probe of 0000:00:10.0 failed with error -1
[   11.903951] NVRM: The NVIDIA probe routine failed for 1 device(s).
[   11.903954] NVRM: None of the NVIDIA graphics adapters were initialized!
[   12.768374] loop: module loaded
[   12.779559] lp0: using parport0 (interrupt-driven).
[   13.090183] NVRM: This PCI I/O region assigned to your NVIDIA device is invalid:
[   13.090185] NVRM: BAR1 is 256M @ 0x00000000 (PCI:30000000:01.0)
[   13.090189] NVRM: This is a 64-bit BAR mapped above 4GB by the system BIOS or
[   13.090191] NVRM: Linux kernel. The NVIDIA Linux graphics driver and other
[   13.090192] NVRM: system software do not currently support this configuration
[   13.090193] NVRM: reliably.
[   13.090200] nvidia: probe of 0000:00:10.0 failed with error -1
[   13.090227] NVRM: The NVIDIA probe routine failed for 1 device(s).
[   13.090230] NVRM: None of the NVIDIA graphics adapters were initialized!

[  882.741281] NVRM: This PCI I/O region assigned to your NVIDIA device is invalid:
[  882.741284] NVRM: BAR1 is 256M @ 0x00000000 (PCI:30000000:01.0)
[  882.741295] NVRM: This is a 64-bit BAR mapped above 4GB by the system BIOS or
[  882.741299] NVRM: Linux kernel. The NVIDIA Linux graphics driver and other
[  882.741306] NVRM: system software do not currently support this configuration
[  882.741313] NVRM: reliably.
[  882.741326] nvidia: probe of 0000:00:10.0 failed with error -1
[  882.741355] NVRM: The NVIDIA probe routine failed for 1 device(s).
[  882.741359] NVRM: None of the NVIDIA graphics adapters were initialized!
[  886.187825] NVRM: This PCI I/O region assigned to your NVIDIA device is invalid:
[  886.187828] NVRM: BAR1 is 256M @ 0x00000000 (PCI:30000000:01.0)
[  886.187840] NVRM: This is a 64-bit BAR mapped above 4GB by the system BIOS or
[  886.187843] NVRM: Linux kernel. The NVIDIA Linux graphics driver and other
[  886.187850] NVRM: system software do not currently support this configuration
[  886.187857] NVRM: reliably.
[  886.187872] nvidia: probe of 0000:00:10.0 failed with error -1
[  886.187914] NVRM: The NVIDIA probe routine failed for 1 device(s).
[  886.187915] NVRM: None of the NVIDIA graphics adapters were initialized!
[  889.632646] NVRM: This PCI I/O region assigned to your NVIDIA device is invalid:
[  889.632649] NVRM: BAR1 is 256M @ 0x00000000 (PCI:30000000:01.0)
[  889.632656] NVRM: This is a 64-bit BAR mapped above 4GB by the system BIOS or
[  889.632657] NVRM: Linux kernel. The NVIDIA Linux graphics driver and other
[  889.632659] NVRM: system software do not currently support this configuration
[  889.632660] NVRM: reliably.
[  889.632667] nvidia: probe of 0000:00:10.0 failed with error -1
[  889.632691] NVRM: The NVIDIA probe routine failed for 1 device(s).
[  889.632694] NVRM: None of the NVIDIA graphics adapters were initialized!



```

Much appreciation for the looks in this matter thus far since I'm being driven crazy about this whole thing :confused:

---

### Post by HotDogBunToo on 2008-12-18
AH HA!!!

I FIXES IT I FIXES IT!!! YEAAAAAAAAAAAAAA I FIXES IT!! WOOOOOOOO HOOOOOOOOOOOOOOOOOOO!!!

Well, after reading that error code I pasted up... I googled & seen folks refer to how the BAR memory is mapped out of range.  Even tho me running Ubuntu Server has advantage over Ubuntu Desktop edition in seeing all 4GB of RAM in upgrade, seems Nvidia still hits a roadblock in addressing this.  

So seeing how picky my OS is and getting hint of "..This is a 64-bit BAR mapped above 4GB by the system BIOS.." I finally fix things by just going into BIOS and changing my "Top Of Memory under 4GB" option to 1.75GB (I'm guessing any value under 2GB works) and PRESTO!!!  Full resolution baby!!!!  

So in my case... things wasn't much about installing Nvidia drivers properly, but an issue regarding RAM upgrade from last week (since I had same errors when on Desktop version of Ubuntu).  Thanks for everyone's help tho since that lead me to printing up error messages essential for me tracking this down! :D

---

### Post by ivanhoe75 on 2008-12-22
My way 2 fix video nv 7600gs under 8.10 is that: install nvidia-common and proprientary driver installer automaticaly finds card and install (my case - nvidia-glx-177 driver)

---

### Post by alexcuervo on 2009-09-12
I am having the same problem.
However I can not use HotDogBunToo work around of changing the "Top Of Memory under 4GB" option to 1.75GB in the BIOS, because my bios does not allow me to do so.
Is there the same can be achieved by passing a kernel boot parameter?

I am running 9.04 64 bit.

Thanks

---

