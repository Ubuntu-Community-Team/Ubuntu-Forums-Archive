---
title: "RealTek ALC850 &amp; Ubuntu 6.06 32bit Not Working?"
date: 2006-09-15
forum: Multimedia &amp; Video
---

### Post by onioneater36 on 2006-09-15
I am new to Ubuntu and so far am excited that I finally have a Linux distro I can do things with.  I had tried the Ubuntu 6.06 AMD64 distro and my audio worked, but being that I could not get Opera web browser or Wine to work I decided to go to the 32bit distro.  I installed it last night and my audio does not seem to work.  I downloaded the driver from ASUS website for my audio but it is in source code form.  I added the gcc and cpp packages and was going to try and compile and get this installed, but I feel like a fish out of water.  Does anyone have instructions on how I do this?  When I added gcc and cpp packages, it did not add them to the PATH environment variable so that is the first thing the ASUS ALC850 driver complained about when I followed their instructions.  I was going to try to proceed and try things but if someone has some guidance, it would be sincerely appreciated.  TIA.

---

### Post by x64Jimbo on 2006-09-15
open synaptic and install this package
build-essential

---

### Post by onioneater36 on 2006-09-15
I successfully added the build-essential package and made it a little further.  The instructions from the drivers off of ASUS' website were...

> Step 1. unzip source code
        tar xfvj alcsound.tar.bz2
Step 2. Turn on sound support (soundcore module, default turn on)
Step 3. Complied source code
	a. ./configure
	b. make
	c. make install
	d. ./snddevices
Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
 	(Please refer to the attached modules.conf)
Step 5. reboot your machine

After installing the build-essential I was able to execute the ./configure command in step 3, but it gave me the warning...

> Please, install the package with full kernel sources for your distribution or use --with-kernel=dir option to specify another directory with kernel sources (default is /usr/src/linux).

I assume this means I need to install some sort of source code for the kernel of the distro I am running.  Any kind of clue what that package may be called?  I am going to start scouring synaptic to see if I can figure it out.

Thanks for your help so far!

---

### Post by onioneater36 on 2006-09-18
My thread here seems to have gone stagnant.  Anyone with additional advice?  Is there anyone that has on board Realtek ALC850 sound that works in Ubuntu?  Do you have 32bit or 64bit and what version?  

When I look at...

[https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html]("https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html")

They don't even have a section for audio drivers.

When I look at...

[https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards]("https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards")

They don't have the Realtek ALC850 listed as being compatible.  Am I to assume that it will not work in Ubuntu then?  The ASUS A8N32 motherboard is very popular so I would be a little surprised if Ubuntu did not support this audio.

Any help is appreciated.

---

### Post by onioneater36 on 2006-09-18
A little more info to add.  I tried to reinstall the 32bit distro of Ubuntu 6.06 this evening and to my shock and awe, when booting off of the LiveCD, my audio works perfectly.  Then, once installation is complete and you I booted Ubuntu off of the hard drive install, NO SOUND!!!  ARGH!!!

But since I knew the LiveCD played perfect sound I concluded that Ubuntu 6.06 32bit WOULD support the Realtek ALC850 built into my mobo and I was doing something totally stupid.

I WAS CORRECT...

When I went to SYSTEM > PREFERENCES > SOUND...

The default sound card selected was USB Device blah blah blah and in ALSA mixer, only a microphone showed up.  I concluded that this was my stupid little logitech webcam.  I hit the dropdown and selected "nVidia CK804" and rebooted and voila...  SOUND!!!  Ubuntu was selecting the microphone of my webcam as the default sound in ALSA mixer.  Can't believe it took me 2 days to figure this out (putzing here and there, not dedicated work).  Even thought I felt stupid, I have seen other posts with people having the same problem so I figured I'd own up to my ditziness in case other people were missing this setting too.  

I figured it had to be something simple and my suspicions were confirmed.:biggrin:

CASE CLOSED

---

### Post by x64Jimbo on 2006-09-21
With that said, are you going back to x64 now? ;)

---

### Post by onioneater36 on 2006-09-21
I will most likely consider it.  I did think the AMD64 was a little peppier.  I am still most frustrated with Ubuntu that I cannot get plugins to work right with web browsers.  Tried Automatix and got real close...  Tried Easy Ubuntu and it was a mess.  Most scripts didn't work or errored along the way after doing a half install.  Next efforts will be learning how to manually install these plugins which will probably teach me more about linux anyway.

For now I will stick with the 32bit distro so I can use Opera web browser if I want to and I can also use WINE, although now that I know how to setup WINE, I think it may actually work on the 64bit distro.

---

### Post by reticencias on 2006-12-04
Hi, I hope this is usefull to you!!

I have a Asus MB, K8N, with Realtek Alc850, I'm using ubuntu Edgy Eft (6.10) and I have full sound but only in 2.1 (2 channels), My MB works with 6 channels (I know that because it works in windows with my 5.1 sound system) but in ubuntu it onley gives me 2 channels...

---

