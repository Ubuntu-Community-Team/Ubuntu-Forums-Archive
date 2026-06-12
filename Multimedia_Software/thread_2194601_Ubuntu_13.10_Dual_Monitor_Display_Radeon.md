---
title: "Ubuntu 13.10 Dual Monitor Display Radeon"
date: 2013-12-19
forum: Multimedia Software
---

### Post by Belzika on 2013-12-19
[COLOR=#333333][FONT=UbuntuRegular]I recently purchased an external monitor to use with my laptop for a dual screen setup. My laptop is an HP Pavilion g6 and is running Ubuntu 13.10, along with the Radeon graphics driver. I plug in the VGA cable and then go to displays and my laptop detects the monitor as it should,however when I click Apply, my laptop screen goes black and only the external monitor shows the screen, and then after a while it will revert back to normal, where the external monitor is black and my laptop shows the main screen. How can I make it so that they both run at the same time? Thanks[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]also here is my line from doing lspci | grep VGA if it helps at all:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Sumo [Radeon HD 6480G][/FONT][/COLOR]

---

### Post by magicman1223 on 2013-12-19
Click on system settings from the search pannel. Open "displays" ,click detect displays then you should have the option to uncheck mirror displays. Uncheck that box position your secondary monitor in relation to your primary and select the resolution. Press apply and you should be set.

---

### Post by Belzika on 2013-12-20
This is what happens when I do that.
[IMG]https://24.media.tumblr.com/6d531228166819932d0c88aa9c032816/tumblr_my44cqRO2I1sgu3ufo1_1280.jpg[/IMG]

I also tried to do this with 2 other monitors and the same result happened. I achieved this before months ago but I was using Linux Mint or Pinguy OS, one of them. Is this an issue with Ubuntu 13.10? Or the open source video driver?

---

### Post by magicman1223 on 2013-12-20
Alright so do this...

```
lshw -C video (post your results to the forum)
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install fglrx

```

You will need to reboot after you do that lshw -C video (post results)
Then do a ```
sudo amdcccle
```

You should be able to configure your monitors from that pannel.

Best of luck.

---

### Post by Belzika on 2013-12-20
ok here is lshw -C video before installation of new drivers:
*-display               
       description: VGA compatible controller
       product: Sumo [Radeon HD 6480G]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:44 memory:e0000000-efffffff ioport:4000(size=256) memory:f0500000-f053ffff

I'll install the new drivers and reboot and see if it works

---

### Post by Belzika on 2013-12-20
Thank you very much!! As soon as I rebooted my machine after installing the new video driver both monitors turned on and work as they should now. Thanks again!

---

### Post by magicman1223 on 2013-12-21
Glad to hear it worked

---

### Post by whysisi on 2013-12-21
Man I could really use some help..I'm new to Linux, but I have a Linux class next semester and wanted a jump on playing with the kernel..hence began this adventure

So I just switched laptops from a Windows 8 system to 7 cause you guys know the problems with Ubuntu and 8. I reset the laptop to factory image and had to delete the HP Tools partition  to be able to shrink C for the Ubuntu install (HP sets four Primary partitions from start). After some forum browsing everything was set. Installed Ubuntu 13.04 from a Live Disk (used installer to partition 150gb logical partition into a swap, root, and home logical partitions) chose to set the boot loader to the option with windows boot loader..(I thought this was optimum choice from what I read..suspecting I was wrong).

Everything was perfect after install. I rebooted and got the grub asking me which OS to launch (had Ubuntu, Windows 7, and Windows recovery options) played around with the terminal got online, just to see if things were fine. I even restarted a couple times and I was still getting all the multiple boot options as before. I then tired plugging in a HP monitor and at first was only getting the laptop image but I opened up display settings, turned on the monitor, applied settings and I was fine both monitors working in sync. 

But at a later restart, (can't recall why I restarted), at boot the laptop monitor was black and once i realized I turned on the HP side monitor and there was my Ubuntu login screen. But the problem is I can see the laptop monitor in display settings but it still shows no image when I turn it on,even worse at boot I no longer get other boot options it just goes straight to Ubuntu. Plus if Im not plugged into the external monitor my laptop monitor won't work (doesn't work even being plugged up but with out the second monitor my laptop is basically useless)

I followed the steps in this thread, but upon restart the launcher is gone, so is the tool bar with date,time and all that info..Im soo lost, I cant even get the Windows 7 recovery disk to register (I was just gonna start all over)..Please someone help. What info do I need to post to the forum?

---

