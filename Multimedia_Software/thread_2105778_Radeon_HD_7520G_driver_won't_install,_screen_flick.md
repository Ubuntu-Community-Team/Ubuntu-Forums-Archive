---
title: "Radeon HD 7520G driver won't install, screen flickers and &quot;cracks&quot;"
date: 2013-01-17
forum: Multimedia Software
---

### Post by johnjanney on 2013-01-17
I just purchased an HP g7 2340dx laptop with a Radeon HD 7520G video card (AMD A6-4400M APU with Radeon(tm) HD Graphics × 2).

I installed Ubuntnu 12.10 64-bit and everything seems to work fine except the graphics. Sometimes the screen flickers or parts of the screen go gray. Sometimes it appears as if there are cracks in the screen (as if the actual glass cracked, but it's just the graphics going haywire). 

I tried installing the fglrx drivers, but when I reboot the system won't load Unity, just a terminal prompt. I have to run the following command just to get Unity loading again:

sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*

I tried installing fglrx via terminal, Ubuntu Software Center, and using the Additional Drivers application. I tried using AMD's amd-driver-installer-8.98-x86.x86_64.run but that also failed to install. 

the /var/log/jockey.log files give the following info after running the Additional Drivers application:

> 2013-01-16 23:22:06,173 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-01-16 23:22:06,174 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driverThe /usr/share/ati/fglrx-install.log gives the following info after running the amd-driver-installer from the AMD website:

> Package build failed!
Package build utility output:
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
./packages/Ubuntu/ati-packager.sh: 295: ./packages/Ubuntu/ati-packager.sh: dpkg-buildpackage: not found
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
./packages/Ubuntu/ati-packager.sh: 295: ./packages/Ubuntu/ati-packager.sh: dpkg-buildpackage: not found
[Error] Generate Package - error generating package : Ubuntu/quantalI'm hoping there is a solution for this. As it stands now, my screen is a mess with all the flickering, random gray blotches and graphical cracks. 

Your help is greatly appreciated.

---

### Post by johnjanney on 2013-01-19
Here is the certification page by Ubuntu. 
[http://www.ubuntu.com/certification/hardware/201209-11640/](http://www.ubuntu.com/certification/hardware/201209-11640/)

Nothing I tried on 12.04 (which wouldn't even load the GUI/Unity) or 12.10 (which kept flickering, blotching, "cracking" and twisting the on-screen graphics) worked. 

I had to reinstall Windows 8 and return the laptop. 

Lesson learned: If Canonical says "Certified (Pre-installed only)" then do not buy this machine. Chances are high that it's too much of a headache and a huge waste of time.

On another note, I looked around the web for a pre-installed Ubuntu laptop. Holy Cow! They are expensive. It's cheaper to pay for the Windows 8 license (and I hate Windows). If anyone knows of a reputable site that sells sub-$300 (heck, even sub-$500) Ubuntu laptops, please let me know. It's truly a shame that there are no "student-level" Ubuntu laptops on the market. Not everyone needs $1200-worth of computing power.

---

### Post by dibodabadibo on 2013-01-29
Same problem here! 
Same computer specs.
Any advice from anyone???

---

### Post by Mark Phelps on 2013-01-30
Laptops, especially HP, come with onboard graphics chips -- and while the model number may read HD 7520, that is no indication that the restricted AMD HD7500 drivers will work.  You nearly always need drivers written specifically for the Mobile series Radeon chipsets when using laptops.

So, you should search the AMD site for that specific Mobile Radeon graphics chipset.  Don't be surprised if it is NOT there.  OEMs provide their own graphic drivers and you would, in this case, need to go to HP to get them.

---

### Post by bfootdav on 2013-04-16
In case anyone comes across this again, I recently tried the 13.3 beta from AMD with Ubuntu 13.04 on my Toshiba Satellite with a 7520g and it works.  Not sure if it was Ubuntu, the newer beta, or a combination but the driver works and I'm getting full 3D (without tearing), much better battery management (4+ hours vs. 2 hours with the open-source driver), and can control screen brightness. My laptop finally works as it should.

---

