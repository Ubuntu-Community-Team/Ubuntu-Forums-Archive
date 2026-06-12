---
title: "ATI 7.11 install breaks fglrx"
date: 2007-11-23
forum: Multimedia &amp; Video
---

### Post by Mark Phelps on 2007-11-23
When I saw that ATI has released yet another new driver, and is now using the Catalyst numbering convention, I downloaded it, ran the "run" file, and chose automatic installation.  While that worked, when I opened a terminal and did fglrxinfo, I got the dreaded Mesa messages!!

I went through all the steps in the "Gutsy, Xgl, and ATI fglrx" instructions, checking the uname, the generic package versions, the kernel modume, and the kernel driver -- all were correct.Checked to see if the X driver is installed -- it is. Checked if the restricted drivers manager was installed and the ATI drivers were selected -- both true.

Since I saved the xorg.conf file before starting any of this, did a side-by-side comparison -- not much was different, and both had "fglrx" in the proper Device section.

The only thing that looked odd is that the xorg-driver version, instead of being 7.1.0-8.37.6xxx was 8.43xxxx.  

To fix it, I did an apt-get purge, and reinstall, of xorg-driver-fglrx.

The good news is that direct rendering is back.

Anyone else experience this, or am I the only one?

---

### Post by Yellow Pasque on 2007-11-24
> **Mark Phelps said:**
> The only thing that looked odd is that the xorg-driver version, instead of being 7.1.0-8.37.6xxx was 8.43xxxx.  
If you installed the latest ATI driver (8.43.2), why would that be odd?

---

### Post by Mark Phelps on 2007-11-24
It was odd because the driver did not beging with "7.1.0-".

Also, I spoke too soon -- the direct rendering is NOT back, but the Mesa problem IS!  I could have sworn that uninstalling the drivers and then reinstalling from apt-get restored the original 8.37, fglrx, and direct rendering -- at least, when I ran fglrxinfo and glxinfo, those appeared to be the case.  But in running fglrx now, I get the Mesa text, and in running glxinfo, I get NO direct rendering.

I have since tried everything in the ATI "Ubuntu Gutsy Installation Guide", Method 2 - Installing manually.  I generated the Ubuntu/gutsy debs from the downloaded 8.43.x.run file from AMD. I blacklisted the old fglrx module. I installed the three debs listed (except, for 8.43 instead of for 8.42). I even created the ati-module-fix file.

But after I rebooted, and did the post-installation fglrxinfo, I STILL get the Mesa text!

I removed the xserver-xorg-video-all package (as instructed), did the symbolic link, enabled the ATI restricted driver, rebooted ...  and STILL get the Mesa text!

This all started because I installed the latest AMD catalyst 7.11 drivers -- and now I can't figure out how to get back to having direct rendering work.

I'm at my wits end!!  Apart from a total Linux reinstall, I don't know what to do!

---

### Post by Melcar on 2007-11-24
One thing that always, and I mean always, caused the driver install to fail was not being in my home directory when attempting to compile the kernel module; I would always get errors about links not being made and/or broken and fglrx simply would not load.

---

### Post by tiachopvutru on 2007-11-24
The easier way to install the driver is

```
sudo sh driver_name
```

Replace driver_name with whatever the driver's name is, then follow the GUI instruction. I didn't get the Mesa problem on the latest install, but the one before it (8.42). When that happened, I just enable the driver from Restricted Driver Manager and it would work, lol (somehow enabling it doesn't install the old driver).

---

### Post by Lagos on 2007-11-25
i have the same problem. installed the new ati 7.11 driver. everything went well, but when i booted back up, it said i was still on the mesa driver.  anyone know a way to fix this?

---

### Post by tiachopvutru on 2007-11-25
> **Lagos said:**
> i have the same problem. installed the new ati 7.11 driver. everything went well, but when i booted back up, it said i was still on the mesa driver.  anyone know a way to fix this?

try enabling the driver in Restricted Driver Manager. It would still use the latest driver and it may fix the problem.

---

### Post by Lagos on 2007-11-25
> **tiachopvutru said:**
> try enabling the driver in Restricted Driver Manager. It would still use the latest driver and it may fix the problem.

tried it, but its still using the mesa driver.:confused:

---

### Post by Mark Phelps on 2007-11-25
From the reports, symptoms appear to be the same:
1) Install new Catalyst 7.11 driver from AMD
2) fglrxinfo shows ATI driver
3) glxinfo shows direct rendering
4) restriced drivers manager shows ATI driver as being loaded
5) reboot
6) fglrxinfo NOW shows Mesa driver
7) glxinfo NOW shows NO direct rendering
8) restricted drivers manager STILL shows ATI driver as being loaded

I alread tried uninstalling the drivers and using synaptic to reinstall them.  As with the initial update, that worked until reboot -- then, back to the Mesa, no-direct-rendering problem.  Didn't have this problem with Fisty, but then, I used Envy to install the ATI drivers.  Have also tried that.  Installs the 8.40 driver, but upon reboot, still b ack to the Mesa, no-direct-rendering problem.

I've spent HOURS reinstalling drivers --using every method I can find.  Nothing fixes this!!

It's this kind of updating-a-driver-breaks-the-machine crap that drove me away from Windows to Ubuntu in the first place!

Would be nice if someone knew how to fix this...

---

### Post by adent42 on 2007-11-28
found a fix to this problem:

sudo rmmod fglrx
cd /lib/modules/*/misc
sudo insmod fglrx.ko
modprobe fglrx

Found this here:
[http://www.phoronix.com/forums/showthread.php?t=6062&postcount=6](http://www.phoronix.com/forums/showthread.php?t=6062&postcount=6)

---

### Post by Mark Phelps on 2007-11-29
This was great!! Using the info in the link, I was finally able to figure out how to fix it.

I discovered that I too had the DRI initialization problem.  The fix involved the following:
1) Correcting the ati-module-fix script in the Ubuntu Gutsy Installation Guide -- to include "fglrx.ko" on the end of the "ln -sf" command in the script.
2) Detecting that the fglrx.ko link from /lib/modules/.../misc/ never got made correctly
3) Confirming that after remaking the link, it really did exist in the /lib/modules/.../volatile/ directory
4) Determining that there are two DISABLED_MODULES lines in the restrict-modules-common file and that the first is a comment line.  The "fglrx" needs to be added to the second DISABLED... line.

So now, on reboot, the script runs, does the CORRECT link, and fglrxinfo and glxinfo yield the correct result.

... Lot of work for something that was SUPPOSED to be a simple matter of clicking the ATI restricted driver button ...

---

### Post by megadave on 2007-11-30
First off, thanks to all the posters who find and post the useful information.  :guitar:

There must be a way to package or distribute these ATI updates which are very popular and the bane of most users existence in a way that it "just works".

Is Envy still considered evil, and does anyone know if it works w/ the newest drivers?

---

### Post by mick222 on 2007-11-30
used envy on linux mint installed latest ati drivers which seem to be working well.
with old drivers i couldn't play games or get compiz to work. seems god don't know if Envy works on gutsy but hopefully it should.

---

