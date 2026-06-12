---
title: "wireless worked briefly then stopped"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by gyyl on 2009-08-18
Hi everyone.  

I installed Ubuntu on my Sony Vaio pcg-r505jsp laptop and the wireless (Linksys wpc54g) didn't work. When I clicked on the network configuration in the taskbar  a menu appeared and there was an option to enable wireless. That was checked. There was also a Wireless Network listing, but it was grayed out and no networks were listed.

I installed ndisgtk but when I tried to install the Windows driver it said it was invalid - even though it is definitely the correct driver.

I  connected the laptop to a wired network and several hours later a popup appeared from the Hardware Drivers utility asking me if I wanted to download and activate the driver for my wireless.  Of course I clicked yes.  But the wireless still didn't work.

I downloaded and installed a bunch of updates and when the updates were finished installing, the wireless miraculously worked.  Networks in range were detected and all listed in the menu, the previously grayed out option able to be selected.  I connected to my wireless network and everything worked fine.

However, when I restarted my computer (I was asked to do so to complete the install of the updates) the wireless no longer worked.  Furthermore, when I click on the Network icon in the taskbar the options I describe above are no longer there.  There is no checkbox to enable wireless networks and there is not even a grayed out Wireless Networks listing.  There are also a few other listings from the menu that are no longer there.

Can someone please help me solve this problem?

Thanks

---

### Post by SoftwareExplorer on 2009-08-19
When Ubuntu is first starting, I will say something like grub loading, press esc to enter menu. Press escape. It will have a list that Has something like
Ubuntu (version)
Ubuntu(version) recovery mode
Ubuntu (lesser version)
Ubuntu (lesser version) recovery mode 
etc.
Anyways try the one that is not the highest version number, but the second highest and doesn't have recovery after it. See if it works when you boot up in that.

---

### Post by SoftwareExplorer on 2009-08-19
By the way, [gyyl]("http://ubuntuforums.org/member.php?u=895962"), welcome to the Ubuntu forums.

---

### Post by gyyl on 2009-08-19
Thanks for your advice SE.  I tried booting the older version, but unfortunately it didn't solve the problem.  This seems very odd because installing the updates got the wireless to work, yet when I restarted the computer to complete the update installation, the wireless no longer worked.  And the network configuration menu is now missing options it had before the updates.  

What do you think it could be that caused the wireless to work for that brief period?

---

### Post by superprash2003 on 2009-08-19
when you boot ubuntu , try booting into the previous kernel version

---

### Post by SoftwareExplorer on 2009-08-19
> **gyyl said:**
> Thanks for your advice SE.  I tried booting the older version, but unfortunately it didn't solve the problem.  This seems very odd because installing the updates got the wireless to work, yet when I restarted the computer to complete the update installation, the wireless no longer worked.  And the network configuration menu is now missing options it had before the updates.  

What do you think it could be that caused the wireless to work for that brief period?
Probably some part of an update tried to automatically set stuff up and got it right until you restarted. Why I didn't work when you restarted is the question I'm wondering about. What if you go to the hardware drivers (System->Administration->Hardware Drivers) and try uninstalling the wireless driver and then reinstalling it. 
> **superprash2003 said:**
> when you boot ubuntu , try booting into the previous kernel version
We already tried that, do you have any other ideas?

---

### Post by gyyl on 2009-08-19
I went to Hardware Drivers and nothing is listed. It just says No propriety drivers are in use on this system.  Perhaps that's the problem?

The odd thing is that, like I stated earlier, the Hardware Drivers utility prompted me, asking if I wanted to download and activate the driver for my wireless. I said yes and it installed.  But nothing is listed.

---

### Post by SoftwareExplorer on 2009-08-19
can you post the output of ```
lspci
``` and ```
lsusb
```? Second, if you have windows, does it show up in windows?

---

### Post by SoftwareExplorer on 2009-08-19
This almost sounds like what my HP compaq presario did. It's wireless didn't work when I got it second hand. It didn't even show up. Then it showed up for ten minutes one day and I was ecstatic. Then it magically disappeared when I rebooted never to be found. I went to HP website and also did some googling and found out it was a bios and motherboard thing that was common with my model. Contacted hp and asked how much it would cost since it wasn't under warranty and they said if that was my problem that they had extended the warranty for that specific issue and that they would fix it for free. 
So, it could be a hardware issue, but I would be nice if it didn't take sending it in to get fixed.

---

### Post by gyyl on 2009-08-20
Yeah, it does sound similar to your situation.  below is the info you requested.  Do you think it might be different with kubuntu or xubuntu?  The lap top had XP on it and the wireless worked.  My friend put xubuntu on it and he got the wireless to work, though he can't remember what he did, just that he needed to fiddle with it.  I was thinking of putting Kubuntu on it, because the's also an issue with the screen resolution.  It only allows 800x600 as a choice and it should be at 1024x768.

btw, thanks for helping me out on this.

    yd@syd-laptop:~$ lspci
  00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
  00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 11)
  00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
  00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
  00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
  00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
  00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 03)
  00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
  00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 03)
  00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem Controller (rev 03)
  01:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AA22 IEEE-1394 Controller (PHY/Link Integrated) (rev 02)
  01:02.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 80)
  01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
  02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
   
  syd@syd-laptop:~$ lsusb
  Bus 002 Device 002: ID 054c:0056 Sony Corp. MG Memory Stick Reader/Writer
  Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 001 Device 002: ID 08ec:0008 M-Systems Flash Disk Pioneers TravelDrive 2C
  [FONT=&quot]Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]

---

### Post by SoftwareExplorer on 2009-08-20
Well, it looks like the computer can see the card from the software side. It sounds like your card has a native Linux driver, so in a perfect world you shouldn't have to mess with ndiswrapper. I somewhat doubt it would be different in K/Xubuntu, but if you were going to try that then you could also try a new ubuntu install. Consider yourself lucky so far, it doesn't look like you need to replace any hardware like I had to.

---

### Post by gyyl on 2009-08-20
Well, thanks for your help.  I guess I'll just try installing the other os's and see what happens.

---

