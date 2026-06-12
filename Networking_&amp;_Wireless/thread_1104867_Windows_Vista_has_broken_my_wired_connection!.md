---
title: "Windows Vista has broken my wired connection!"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by rdasilva451 on 2009-03-24
Greetings,

I have a brand new HP laptop running ubuntu 8.1

I finally had everything working... graphics card, wireless etc. and it was working perfectly for about a month. Then I needed to boot into vista to download a particular app for my job. As soon as I was finished I rebooted into trusty ubuntu and my wired internet connection (that had been working just fine moments earlier when I was in vista and also on ubuntu before I booted into vista) no longer was working. Looking at the available networks list the wired network connection ( Auto eth0) is grayed out.

My wireless card still works just fine.

Please help... don't let vista win and force me to go back to using windows!

Thanks
rdasilva451

---

### Post by ThatGuyOverThere on 2009-03-24
You could try opening up the properties of your NIC in Vista's Device Manager and enabling the Advanced property that resets the PHY of the network interface.  I have found this to temporarily clear up the problem I had, which was that Ubuntu leaves the NIC link always on, even when the machine is asleep or off.  Maybe Ubuntu isn't resetting the PHY on the HP machines.

That wouldn't be an nForce NIC on the HP laptop, would it?  Ubuntu uses the forcedeth driver on those, and I'm trying to track down a fix for it myself.

---

### Post by rdasilva451 on 2009-03-24
do you mean the auto disable PHY (power saver feature)?

My wired network card is a Realtek RTL8102E family PCI-E fast ethernet NIC

---

### Post by rdasilva451 on 2009-03-24
After doing a lot of research I ended up fixing my problem. If you have this or a similar issue I suggest doing the following:

1) turn off your computer and leave it off for a little while then try again
2) boot into vista (::shudder::) and go to device manager. Find your wireless card and make sure that under power management that the box that says something like "allow the computer to turn this device off to save power" is unchecked.

It seems this issue centers on vista tinkered with the powersaver settings of your driver.

---

### Post by Anthon on 2009-03-24
In these cases you definately want try and turn the computer completely off before booting. 
It seems Linux does not (are maybe cannot properly reset the hardware before trying to load some firmware). I have seen this with wireless adapters and also with some graphics boards (but the latter not recently).

---

### Post by DerHesse on 2009-03-24
Have you tried removing the battery pack for a little while? This should solve it.

---

### Post by ThatGuyOverThere on 2009-03-24
The Advanced properties tab, appearing probably right after the first properties tab if your driver in Vista has one, is a list of stuff, and a dropdown box to pick the setting for whatever in the list is selected.  If there's an entry that mentions resetting the PHY, you want that Enabled.

Power management options are another tab on my NVIDIA nForce NIC driver, and that's not the one that resets the PHY.  That setting didn't help me.

I don't even see the Realtek RTL8102E NIC in my system's manually selected (even incompatible) driver choices.  Realtek makes the wired PHY interface on some HP equipment, but the driver for the NIC is sometimes nForce, handled through the system chipset, so I'm told.  If you have a different chipset, your NIC may be a standalone device on the system board.

The HP laptop I was working on the other day had a wired NIC and a wireless NIC.  I just had the wireless physically switched off, and didn't mess with any of its settings.  But the wired NIC had a PHY reset advanced property setting.

That PHY reset is what Ubuntu should be doing in several circumstances, but appears not to do.  Your mileage may vary.

In Ubuntu, open up a command prompt from Accessories, and type:

sudo lshw -C network

(sudo will give a bit more info, but not required)

Look at what your NIC hardware is detected as, and the configuration line will show what driver is in use.

Maybe we can triangulate the problem if we have different hardware, or verify that the forcedeth driver is at fault.

---

### Post by rdasilva451 on 2009-03-24
It appears that a simple extended power cycling of my laptop did the trick. 

Thanks everyone for your help!

---

### Post by rdasilva451 on 2009-03-24
My hardware is 

description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:2a:8b:4d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s

---

### Post by chili555 on 2009-03-24
Perhaps this will be helpful:  [http://linux.derkeiler.com/Mailing-Lists/Debian/2008-02/msg00168.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2008-02/msg00168.html)

Particularly, check this:> "As of 27 May 2007, in kernel 2.6.21.3, you may experience the issues
with the r8169 driver if you dual boot Windows on some systems. Windows
by defaults disables the NIC at Windows shutdown time in order to
disable Wake-On-Lan, and this NIC will remain disabled until the next
time Windows turns it on. The r8169 driver in the kernel does not know
how to turn the NIC on from this disabled state; therefore, the device
will not respond, even if the driver loads and reports that the device
is up. To work around this problem, simply enable the feature
"Wake-on-lan after shutdown." You can set this options through Windows'
device manager."

---

