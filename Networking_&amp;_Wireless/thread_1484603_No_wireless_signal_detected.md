---
title: "No wireless signal detected"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by pso2010 on 2010-05-15
I just installed the latest version of Linux on my Dell Mini 910 and it's now not picking up my wireless signal. The wireless card is enabled so I'm not sure what's going on. Btw, I tried entering the smb command that was given to the other member about 4 threads down as he had the same issue. Didn't work though.

---

### Post by pso2010 on 2010-05-15
Ok, now it says "device not ready".

---

### Post by cariboo on 2010-05-16
Which distribution and version of Linux did you install? We need to do a little troubleshooting in order to solve your problem. Open a terminal and type:

```
sudo lshw -C network
```

paste the output of the above command in your next post.

---

### Post by pso2010 on 2010-05-16
*-network               
         description: Network controller
         product: BCM4312 802.11b/g
         vendor: Broadcom Corporation
         physical id: 0
         bus info: pci@0000:03:00.0
         version: 01
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress bus_master cap_list
         configuration: driver=b43-pci-bridge latency=0
         resources: irq:17 memory:f0200000-f0203fff
    *-network
         description: Ethernet interface
         product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 0
         bus info: pci@0000:04:00.0
         logical name: eth0
         version: 02
         serial: 00:21:70:d4:4e:11
         size: 10MB/s
         capacity: 100MB/s
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
         resources: irq:27 ioport:2000(size=256) memory:f0610000-f0610fff(prefetchable) memory:f0600000-f060ffff(prefetchable) memory:f0620000-f063ffff(prefetchable)
    *-network DISABLED
         description: Wireless interface
         physical id: 2
         logical name: wlan0
         serial: 00:23:08:47:14:29
         capabilities: ethernet physical wireless
         configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  joe@joe-laptop:~$

---

### Post by purelinuxuser on 2010-05-16
If my hunch is right, you have a Broadcom BCM4312 wireless card.  I've had mixed success with this card- it works with the proper firmware, but wireless is SLOW and disconnects a lot.

To get yours working, you'll need to install the firmware.  The easiest way is to just plug your Mini into Ethernet and open Synaptic Package Manager.  Search for "b43-fwcutter," right-click, check install, and then click the "Apply" button in the toolbar.  You'll get a prompt with a checkbox that says "Automatically download and install firmware?," make sure it's checked.  Then reboot.

You can find more information at this page: [http://linuxwireless.org/en/users/Drivers/b43#device_firmware_installation](http://linuxwireless.org/en/users/Drivers/b43#device_firmware_installation).

---

### Post by pso2010 on 2010-05-16
Great, now it's not working wired either. It tries to connect and then prompts me that I'm now offline. When I try to reconnect the only thing to choose is ethO and it still doesn't connect.

---

### Post by NUboon2Age on 2010-05-16
Ouch, ethernet connectivity shouldn't have been impacted.  Hmm...  There are sooooo many posts on the Broadcom driver probs. I think possibly your solution may involve fiddling with ndiswrapper. That's what worked for me, although I have a 4318 instead of your 4312.

Here's a related bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203819](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203819)

It helps get developer attention if you report that the bug is effecting you too and if you subscribe to the bug.

This person had the same chip as you and got theirs to work:
[http://ubuntuforums.org/showpost.php?p=3961932&postcount=9](http://ubuntuforums.org/showpost.php?p=3961932&postcount=9)

This person apparently had the 4312 reports having gotten it to work;
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203819/comments/6](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203819/comments/6)

---

### Post by NUboon2Age on 2010-05-16
Also what happens when you run jockey (System->Administration->Hardware Drivers)?  Does it show the b43 (or b43legacy) drivers as available and active or enactive?  This is what is supposed to happen and is supposed to be the simple way to make them work, but with the Broadcom interfaces its hit and miss.

---

### Post by pso2010 on 2010-05-16
When I click on hardware drivers, it says no proprietary drivers exist.........

---

### Post by Bucky Ball on 2010-05-16
If you haven't already, plug in an ethernet cable and get updates. That card should be recognised pretty quickly and firmware etc should be offered. Follow your nose to get it set-up. 

Generally takes about five minutes BUT you need to get online with a cable first. Catch 22.

---

### Post by pso2010 on 2010-05-16
I'd try that but I can't connect wired either.

---

### Post by purelinuxuser on 2010-05-16
> **pso2010 said:**
> When I click on hardware drivers, it says no proprietary drivers exist.........

That's weird, the Broadcom "wl" proprietary driver should have been listed, even on a fresh installation.  As Bucky Ball said, you might have to install updates, but I'm not sure how you can do that without any connection to the Internet. :confused:

---

### Post by pso2010 on 2010-05-16
Should I just re-install the OS?

---

### Post by NUboon2Age on 2010-05-17
> **pso2010 said:**
> Should I just re-install the OS?

Maybe, to get the ethernet working again, that might be the easiest way to get back to only one problem. But you'll probably still need to solve the wireless issue even after a reinstall.  At least to get the ethernet going again you might be able to reload anything needed from your CD using Synaptic.  If you want to try to fix the ethernet without reinstalling you'd almost want to start a new thread just about that and [include all this info in it (ticket)]("http://ubuntuforums.org/showthread.php?p=6183681") in it, since you have a new set of symptoms.

---

### Post by NUboon2Age on 2010-05-17
> **pso2010 said:**
> 
    *-network DISABLED
         description: Wireless interface
         physical id: 2
         logical name: wlan0
         serial: 00:23:08:47:14:29
         capabilities: ethernet physical wireless
         configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  joe@joe-laptop:~$

I don't see a driver listed in configuration AND it says "DISABLED".  You probably need to repost this info since things have changed.

---

### Post by NUboon2Age on 2010-05-17
> **pso2010 said:**
> 
    *-network DISABLED
         description: Wireless interface
         physical id: 2
         logical name: wlan0
         serial: 00:23:08:47:14:29
         capabilities: ethernet physical wireless
         configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  joe@joe-laptop:~$

I don't see a driver listed in configuration AND it says "DISABLED".  You probably need to repost the ```
sudo lshw -C network
``` info since things have changed.

---

### Post by purelinuxuser on 2010-05-17
Post the output of```
lspci
``` too.  That way, we can find out EXACTLY what wireless card you have and what Ethernet card you have.

---

### Post by bkratz on 2010-05-17
> **pso2010 said:**
> I just installed the latest version of Linux on my Dell Mini 910 and it's now not picking up my wireless signal. The wireless card is enabled so I'm not sure what's going on. Btw, I tried entering the smb command that was given to the other member about 4 threads down as he had the same issue. Didn't work though.

You might want to check out this page;
[http://www.bauer-power.net/2009/11/getting-wireless-to-work-on-dell-mini-9.html](http://www.bauer-power.net/2009/11/getting-wireless-to-work-on-dell-mini-9.html)

See the last comment which says that it works for 10.04 also, although the initial page is talking about 9.10.

---

### Post by pso2010 on 2010-05-18
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
  00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
  00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
  00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
  00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
  00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
  00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
  00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
  00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
  00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
  00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
  00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
  00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
  00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
  00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
  00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
  02:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
  02:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
  02:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
  03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
  04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
  joe@joe-laptop:~$ sudo lshw -C network
  [sudo] password for joe:
    *-network               
         description: Network controller
         product: BCM4312 802.11b/g
         vendor: Broadcom Corporation
         physical id: 0
         bus info: pci@0000:03:00.0
         version: 01
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress bus_master cap_list
         configuration: driver=b43-pci-bridge latency=0
         resources: irq:17 memory:f0200000-f0203fff
    *-network
         description: Ethernet interface
         product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 0
         bus info: pci@0000:04:00.0
         logical name: eth0
         version: 02
         serial: 00:21:70:d4:4e:11
         size: 10MB/s
         capacity: 100MB/s
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
         resources: irq:27 ioport:2000(size=256) memory:f0610000-f0610fff(prefetchable) memory:f0600000-f060ffff(prefetchable) memory:f0620000-f063ffff(prefetchable)
    *-network DISABLED
         description: Wireless interface
         physical id: 2
         logical name: wlan0
         serial: 00:23:08:47:14:29
         capabilities: ethernet physical wireless
         configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by pso2010 on 2010-05-18
After re-installing the OS it still won't connect wired.........wtf......I'm gonna go outside and scream.

---

### Post by purelinuxuser on 2010-05-19
> **pso2010 said:**
> After re-installing the OS it still won't connect wired.........wtf......I'm gonna go outside and scream.

According to this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/534536](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/534536), you'll need to compile and install the latest drivers from Realtek.

They can be found here: [http://www.realtek.com/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false).

To install:

[LIST=1]
[*]Download the file to Downloads in your home folder.
[*]Navigate to the file in the File Browser and right-click, then hit "Extract."
[*]Open a Terminal (Applications > Accessories > Terminal).
[*]Type 'cd ~/Downloads/r8101-1.016.00' (without the quotes) and press Enter.
[*]Type 'sudo ./autorun.sh' (without the quotes) and press Enter.  You will be prompted for your "sudo" password- **just type in your regular one.  However, you will NOT see any characters, not even *s, as you type- this is normal, just keep typing.**
[*]Reboot, and hopefully the Ethernet will be working.
[/LIST]

---

