---
title: "Setting Up Jury-Rigged WiFi with wired Ethernet card and WiFi router"
date: 2006-03-12
forum: Networking &amp; Wireless
---

### Post by lkvee on 2006-03-12
My previous Breezy installations failed to recognize my Belkin PCI 802.11b card (F5D6001).   I couldn't successfully install the ADM8211 drivers with the "make install" command (missing separator).   I was able to install ndiswrapper (and I even used the Realtek drivers), but had trouble with ndisgtk.

I decided to install Breezy once more with a 3Com wired Ethernet card and a Belkin 802.11b router (don't remember the model number offhand).   Breezy recognized the card.  The router seems to show WiFi activity.  I configured and activated Eth0, but I can't Internet up and running.

I'd like to use this jury-rigged setup (the 3Com card and the Belkin router) as if it were a typical run-of-the-mill PCI WiFi adapter.   I'm not sure if I have the appropriate packages installed.  I was thinking there's something that functions in the same way that a Windows WiFi utility does so - it would perform a site survey, choose a network, etc.

Any other thoughts?   :confused: 

Thanks for reading!

---

### Post by Sendervictorius on 2006-03-12
Please post the output of ifconfig eth0

Are you using static IP or DHCP? 
Is it just the internet you cannot connect to? Can you log onto your router?

I'm not sure I understand what you are trying to do inthe second part of your post. Perhaps you could elaborate?

---

### Post by lkvee on 2006-03-12
I'll reply again with the results of the ifconfig eth0 command when I get to the center.   I *do* know I tried to use DHCP.   I also didn't recall logging into the router, either.   I'll be happy to get more info, too, when I get there - I'll bring my WiFi laptop to relay the results.

Thanks for the reply! - Vincent

---

### Post by lkvee on 2006-03-13
In that second part of my post, I wanted to use the combination of an Ethernet card, Ethernet cable, and a WiFi router as if it were a PCI WiFi card.   I'm just trying to give the ubuntu machine WiFi access.

In the Networking section, I pulled this data:

eth0 active
hostname reuse-center
No entry under domain name, though
DNS 192.168.2.1

There was an entry called "Belkin" under the Search Domains section.

Here's the output from the ifconfig eth0 command.  I manually typed it here, realizing I probably could have piped the output to a text file, instead.  Oh well, here it is, just the same:

Link encap: Ethernet   HWaddr 00:60:97:C5:77:93
inet6 addr: fe80::260:97ff:kc5:7793/64 Scope: Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0  errors:0  dropped:0  overruns:0  frame:0
TX packets:0  errors:0  dropped:0  overruns:0  carrier:0
collisions:0 txqueuelen:1000
RX bytes:0  (0.0b)  TX bytes:0 (0.0b)
Interrupt: 10   Base address: 0xb000

I hope this can shed some light.   Thanks again. - Vincent

---

### Post by Sendervictorius on 2006-03-13
[QUOTE=lkvee]
Here's the output from the ifconfig eth0 command.  I manually typed it here, realizing I probably could have piped the output to a text file, instead.  Oh well, here it is, just the same:
[/QUOTE]
You can just highlight the text in terminal, Edit>copy, then paste into your browser.;) 

It looks to me that your router is not providing a DHCP ip address to your pc. I would suspect that it is not configured properly. First step is to get your PC talking successfully to the router, so you can get into the router's html configuration (if it has one)

I now think I understand what you are trying to do. You are trying to use two access points to create a wireless bridge. You have one network between your pc and the belkin router, and you want a wireless bridge to connect your mini-network to your main network via the host access point.. 

Now this may be hard (or impossible) to do - I'm not sufficiently savvy to know how. I think you may run into trouble - even at the start, because you want your belkin router to manage DHCP addresses from the access point you are trying to connect to. That means it must act as a DHCP client of the access point, and also a DHCP server for your pc. Possibly outside the capabilities of the router?
If it was me, I would hard-wire static ip addresses.

You need someone who knows how to configure wifi access points to help.

---

### Post by lkvee on 2006-03-14
I'm probably going to scrap the jury-rig with the router and just try to get the machine to recognize the Belkin WiFi card.  Would anything change if I used a wireless access point instead of a router?   

For the Belkin PCI card, I was able to configure ndiswrapper correctly for the Belkin card, based on the output of "ndiswrapper -l" but there's no mention of hardware.  I should see "net8180 driver present, hardware present" but I only see "net8180 driver present".

The ADM8211 driver set's what I needed for Ubuntu to recognize the Belkin card: [http://aluminum.sourmilk.net/adm8211/](http://aluminum.sourmilk.net/adm8211/) and I downloaded the 2.6.15
version (the very last line item as of this writing).  I'm having trouble installing the driver set.   I run the "make install" command and I get a "missing separator" message.

Here's the INSTALL file:
==============================================

Installing this driver should be fairly easy if you meet the prerequisites.

For 2.6:
1. Latest module-init-tools. Ok, you probably don't need the very latest, but I don't want to guess what the minimum version should be, so just make sure you have the latest.
2. Latest gcc 3.x or 2.95.x. Chances are, many many other versions also work - I'm just not supporting them. I do not actively test with 2.95.x, but I will fix any problems as soon as they are reported.
3. A kernel with the generic ieee80211 code. You can find patches to add the ieee80211 code at the same place you got this driver from. You must have your kernel tree installed and configured for kbuild to build your module. Generic IEEE 802.11 Networking Stack (CONFIG_IEEE80211) and WEP  (CONFIG_IEEE80211_CRYPT_WEP) must be compiled in or as modules or the driver will not work.
4. Wireless tools. Latest is prefered, but having slightly older versions are very unlikely to cause problems, at least compared to potential problems with the driver itself.
5. Latest hotplug scripts. This is somewhat optional, but it makes things easier.

To install, just run make install. You can also do make, then make modules_install, which uses the kernel build system to install the modules. However, if you do it the second way, you'll need to run depmod -a manually.

To put the driver inside the kernel source tree:
1. Apply kernel.patch
2. Copy the entire adm8211 directory into $(KERNEL_SOURCE)/drivers/net/wireless

Then you can configure/compile/install the driver like any other driver included with the kernel. Note that the driver is installed to a different place (as a module) than usual when compiled & installed inside the kernel tree, so be careful when upgrading.

To load the driver if it isn't automatically loaded, just run modprobe adm8211.
==============================================

I don't how to execute and verify Step 3.  The others I thought I had covered, but I'm not sure which packages come to mind for Step 4.

Any help's appreciated.   I'll be posting to at least one more list.  Thanks for reading just the same. - Vincent

---

