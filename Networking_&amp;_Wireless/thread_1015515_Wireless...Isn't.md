---
title: "Wireless...Isn't"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by yennik on 2008-12-18
I am having the same issues as some of the other folks trying to get my Sony Vaio to connect with a wireless card.. I have tried all the suggestions from ndiswrapper, to madwifi, and still my Sony Vaio VG-NR220E will not find or load the driver for my card. It is a Lan Express AS IEEE 802.11g PCI Express Card by Atheros COmmunications. I am a total newbie to Ubuntu. I like it first because it is free, and secondly because it is faster and more reliable than Gateows.  It will work with my cat 5 cord. I just can't seem to understand how to get it to work with the wireless card. Can someone give me some simple, easy to follow instructions?
Card works with windows.  Router is a Belkin N1 wireless.

---

### Post by IQRules on 2008-12-18
Check this out,
[http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/](http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/)

search backport ath5k apt-get atheros, hope this help

---

### Post by acreech on 2008-12-18
Can you post the output of these commands?

```
 lspci 
```

```
 sudo lshw -C network 
```

```
 sudo ifconfig 
```

---

### Post by yennik on 2008-12-20
acreech,
     Here are the output files.
lspci:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

sudo lshw -c network:
 *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:1a:80:b3:c9:d7
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9e:64:3d:03:bc:af
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

sudo ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:1a:80:b3:c9:d7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3592 (3.5 KB)  TX bytes:3592 (3.5 KB)

Thanks for your help.

---

### Post by trubshac on 2008-12-20
Hi

Here's the good news part 1: My wife recently had a Sony Vaio VGN-NR38E which has EXACTLY the same wifi hardware as you have, and after a little work, I can assure you that it CAN work well with Ubuntu.

Here's the bad news part 1:  I can't remember EXACTLY what I did to get it working.  This is what I do remember: I didn't need ndsiwrapper.  I installed Ubuntu 8.10 and (using a physical ethernet cable) did all the updates.  I think I then just selected System-Administrator-Hardware Devices - which suggested two device drivers - I just chose "Support for 5xxx series of Atheros 802.11 wireless LAN cards", and I think that it just worked!

Here's the bad news part 2: It occasionally looses all wireless connections, and when you click on the network icon on the top panel, it doesn't offer any wifi options.  I haven't yet figured out what causes this, or why it happens.

Here's the good new part 2: I have a work around for the bad news part2 - I just boot backtrack 3 ([http://www.remote-exploit.org/backtrack.html](http://www.remote-exploit.org/backtrack.html)) from a USB stick (live CD would do too), select the 3rd display option, wait for it to finish booting, then shutdown.  When I next boot up Ubuntu, all the wifi options magically re-appear!  I don't know why yet, but I did read somewhere that it may be some software switch within the Sony BIOS.  Please let me know if you know more about this!

So good luck, and keep trying - you can succeed with a little persistence!

---

### Post by acreech on 2008-12-21
This is the same card that I have too. I would suggest adding the backports through the synaptec package manager as suggested in the thread below (post #21). If that does not work I use the ndiswrapper as suggest in post #4. I never have issues of losing my wireless using the suggestion in post #4. 

Good luck and I hope that one of these ways are useful to you. 

[http://ubuntuforums.org/showthread.php?t=1007434&page=3]("http://ubuntuforums.org/showthread.php?t=1007434&page=3")

---

### Post by trubshac on 2008-12-21
Yes  - acreech is right - I now remember installing the backports.  I currently have linux-backports-modules-2.6.27.9-generic and linux-backports-modules-intrepid-generic installed.  
Sorry I didn't remember before.

---

### Post by yennik on 2008-12-23
O.K. folks, I am really slow at this linux stuff.  I may have messed up but I have switched to Kubuntu.  At least for the time being I can see using the network edit program my wireless network name and type.  I can still not connect with the wireless card so is there something different with Kubuntu I need to do to get the card to work?  Sorry to be such a pain, but this looks more like a OS I can learn to use easier.  Thanks in advance to all of you for your help.

I went to the Kubuntu forum and found the following.
   1.
      sudo apt-get install linux-backports-modules-intrepid-generic  

sudo apt-get install linux-backports-modules-intrepid-generic

After above install completes, reboot, then open up the Hardware Drivers manager (jockey-gtk or jockey-kde) and disable &#8220;Support for Atheros 802.11 wireless LAN cards&#8221; and make sure that &#8220;Support for 5xxx series of Atheros 802.11 wireless LAN cards&#8221; is enabled then reboot. You may need to reboot to see both drivers in the Hardware Drivers manager.

I did all the steps.  I can see my WlanO information listed as the name of my network and the security.  What looks like an lock icon in blue with about 10 blue boxes.  On my panel the icon that looks like a wheel turns and then stop.  I am getting closer so can someone tell me what to do from here?

---

### Post by acreech on 2008-12-23
> **yennik said:**
>  I can see my WlanO information listed as the name of my network and the security.  What looks like an lock icon in blue with about 10 blue boxes.  On my panel the icon that looks like a wheel turns and then stop.  I am getting closer so can someone tell me what to do from here?

I am not sure what you are looking at, can you give us a screen shot of that?

If this is your wireless network, left click on it and see if you can see your wireless network router. Click on your router and enter you network key when the window pops up. I am not sure if this is the stage you are at. 

If you can see your network, but can't connect then check your router settings for "Mac Filtering". This only allows listed computers to connect to it.

---

### Post by yennik on 2008-12-23
I am opening what I think is called network manager.  From the task bar at the bottom of the screen I show an icon of what I think is a cat 5 cable showing at the present I have a wired internet connection.   If I click on this icon it brings up Etho, Wlan, and some other options.  Under the Wlan it shows the name of my network, Kinney Farm, and out beside it (WPA) my security and futher to the right of that if has the blue icon that looks like a lock and the blue boxes.  I am not sure how to include a screen shot of this section.  Kubuntu seems to work a little different from Ubuntu.

---

### Post by acreech on 2008-12-27
> **yennik said:**
> I am opening what I think is called network manager.  From the task bar at the bottom of the screen I show an icon of what I think is a cat 5 cable showing at the present I have a wired internet connection.   If I click on this icon it brings up Etho, Wlan, and some other options.  Under the Wlan it shows the name of my network, Kinney Farm, and out beside it (WPA) my security and futher to the right of that if has the blue icon that looks like a lock and the blue boxes.  I am not sure how to include a screen shot of this section.  Kubuntu seems to work a little different from Ubuntu.


Sorry it took me so long to reply to you. There have been suggestions to set your router to WPA or WPA2 specifically. Sometimes they sent out to two different types of security. So you might look at the router settings and see if that changes anything. It looks like you are close to having it working.

---

### Post by yennik on 2009-01-05
aaaaaahhhhhhhhhhhhhhh!  This stuff is driving me back to windows.  O.K. at least a dual boot.
At this time I have lost everything except for wired access.  I have downloaded Madwifi, Auto-Nidswrapper, and Nidswrapper.  Nothing seems to work.  I am unable to to get any of these programs to load.  I know that my card is the Athersos Ar5006EG with an AR2424 chip set.  Can someone point me in the right direction as to which of the three programs I should use and how to use it.  My search of the forums and the web have left me frustrated and confused.  At least this forum is idiot friendly.  Some of the others are really abusive to newbies.:confused:

---

