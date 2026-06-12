---
title: "Mythbuntu is installed correclty, and configured, but &quot;watch TV&quot; doesn't work, HELP!!"
date: 2008-06-29
forum: Mythbuntu
---

### Post by frojoe2004 on 2008-06-29
I've tryed mythdora, and mythbuntu, and mythdora had more problems but this one seems to be the same with both programes.

unlike mythdora, mythbuntu actualy recognises all my hardware, and its all installed and configured correctly. 

MythTV is also fully configured and recognises all associated hardware and software.

everything works, the schedualsdirect, the webTV, everything, eccept the most important. when I click "watch TV" or ty to watch something recorded, the screen goes black for a few secconds then it just returnes to the main menue. I don't understand what is causing this.

I'm very good with computer hardware, and am trained in windows support, but I'm new to linux. it seems to me like everything should be working.

any ideas on what I can do to fix this?




here are my PC scpecs.

ASUS M2N-VM DVI AM2 NVIDIA GeForce 7050PV Micro ATX AMD Motherboard 

AMD Athlon 64 LE-1600 2.2GHz Socket AM2 45W Single-Core Processor Model ADH1600DHBOX 

Seagate Barracuda 7200.11 ST3500320AS 500GB 7200 RPM SATA 3.0Gb/s Hard Drive 

WINTEC AMPX 2GB 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory Model 3AXT6400C5-4096K 

Hauppauge WinTV PVR 350 Video Recorder, TV/FM Tuner Card PCI Interface

---

### Post by funkydan2 on 2008-07-08
Have you checked your mythfrontend logs?  You should be able to find them in /var/log/mythtv/mythfrontend.log.

Have a look in there and post anything that looks relevant.

---

### Post by drifting on 2008-07-08
I had that problem, was driving me nuts, to this day I am not sure what it was, but what solved it was to do the proposed updates, so can only assume it was either a kernel or nvidia driver problem. I must admit I tend to think it was the Nvidia driver.

Regards Paul.

---

### Post by db260179 on 2008-07-08
Try my kernel first

I assume your machine is 64bit? - these packages are for 64bit kernel only, the link i supplyed is for i386 kernel.

I did another link, which you have downloaded as well - 64bit version (as shown by you post)

Anyway, you need to just install the following:-

If I386 - not 64bit -
[http://gallery.mulberry.towerhamlets...kerneltest.zip](http://gallery.mulberry.towerhamlets...kerneltest.zip)

In terminal shell, type as follows
sudo dpkg -i
linux-headers-2.6.24-19-mythtv_2.6.24-19.34_i386.deb
linux-image-2.6.24-19-mythtv_2.6.24-19.34_i386.deb
linux-restricted-modules-2.6.24-19-mythtv_2.6.24.13-19.42_i386.deb
linux-ubuntu-modules-2.6.24-19-mythtv_2.6.24-19.28_i386.deb


If you pc is 64bit - generic 64bit kernel
[http://gallery.mulberry.towerhamlets...nelgeneric.rar](http://gallery.mulberry.towerhamlets...nelgeneric.rar)

In terminal shell, type as follows

sudo dpkg -i
linux-headers-2.6.24-19-myth64_2.6.24-19.34_amd64.deb
linux-image-2.6.24-19-myth64_2.6.24-19.34_amd64.deb
linux-restricted-modules-2.6.24-19-myth64_2.6.24.13-19.42_amd64.deb
linux-ubuntu-modules-2.6.24-19-myth64_2.6.24-19.28_amd64.deb

Then still in the terminal, type
sudo gedit /boot/grub/menu.lst
Find the line # def_options=
add pci=routeirq
save,exit
Type, sudo update-grub
Reboot machine, select new kernel

For the log files, copy them like this

goto /var/, using a file manager

then create an archive of the log directory
send it here

I have a pvr-350 card, the latest .19 kernel doesnt work! - use my kernel.

You need to tune the card in properly - [http://hausheer.osola.com/docs/24](http://hausheer.osola.com/docs/24)

PLEASE SEND you logs here for analyse. will resolve the issue quicker!

> **frojoe2004 said:**
> I've tryed mythdora, and mythbuntu, and mythdora had more problems but this one seems to be the same with both programes.

unlike mythdora, mythbuntu actualy recognises all my hardware, and its all installed and configured correctly. 

MythTV is also fully configured and recognises all associated hardware and software.

everything works, the schedualsdirect, the webTV, everything, eccept the most important. when I click "watch TV" or ty to watch something recorded, the screen goes black for a few secconds then it just returnes to the main menue. I don't understand what is causing this.

I'm very good with computer hardware, and am trained in windows support, but I'm new to linux. it seems to me like everything should be working.

any ideas on what I can do to fix this?




here are my PC scpecs.

ASUS M2N-VM DVI AM2 NVIDIA GeForce 7050PV Micro ATX AMD Motherboard 

AMD Athlon 64 LE-1600 2.2GHz Socket AM2 45W Single-Core Processor Model ADH1600DHBOX 

Seagate Barracuda 7200.11 ST3500320AS 500GB 7200 RPM SATA 3.0Gb/s Hard Drive 

WINTEC AMPX 2GB 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory Model 3AXT6400C5-4096K 

Hauppauge WinTV PVR 350 Video Recorder, TV/FM Tuner Card PCI Interface

---

### Post by Tukcedo on 2008-07-08
It might have to do with the channel table in the database. I found that for where I live (Netherlands) I had to update the channel frequencies by hand according to a printed table that the cable provider publishes. Mythfilldatabase was simply not picking up the right channels and couldn't correlate with the program guide.

---

