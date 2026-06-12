---
title: "wireless goes belly up:  broadcom 4306 on dell latitude D610 under ubuntu 10.04"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by carltoews on 2010-09-12
I installed 10.04 a few months ago and although I initially had trouble getting the wireless up and running, I eventually figured it out with the help of this post:  

[http://linuxwireless.org/en/users/Drivers/b43#b43_and_b43legacy](http://linuxwireless.org/en/users/Drivers/b43#b43_and_b43legacy)

A few weeks ago, the wireless suddenly quit.  One hypothesis is that my card died, but I'm not sure about this and don't know how to check.  Another hypothesis is that automatic updates threw something out of wack (drivers, modules, etc.), but since working through the above post did not solve the issue this time around, I'm at a loss as to what the problem might be. 

Here's what information I know:

1.  Machine is a Dell Latitude D610; Wireless is Broadcom bcm4306 (rev 3) -- [14e4:4320]

2.  operating system is Ubuntu 10.04, kernel 2.6.32-24-generic.

3.  The b43 driver is installed (it shows up when I go to System --> administration --> Hardware drivers and is listed as active.

4.  The radio is on (indeed, I can turn it on and off via 'sudo iwconfig wlan0 txpower <on/off>

5.  Right-clicking on the network icon in the upper right hand corner reveals that wireless is 'enabled', but left clicking shows that it 'disconnected'.

6.  iwconfig gives the following:
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

If anyone has any thought on how to figure out if my card has gone belly up or I'm merely having a software issue, I would appreciate hearing them.

---

### Post by MaindotC on 2010-09-13
It's showing wlan0 and it usually doesn't show that unless you have a wireless card that it detects.  Do this to ensure your wireless driver is still there:```
lsmod | grep b43
```  If you see a few entries then it's still loaded.

Is NetworkManager still present in the top right of the screen?  Does it allow you to choose wireless networks?

---

### Post by carltoews on 2010-09-13
> **strAlan said:**
> It's showing wlan0 and it usually doesn't show that unless you have a wireless card that it detects.  Do this to ensure your wireless driver is still there:```
lsmod | grep b43
```  If you see a few entries then it's still loaded.

Is NetworkManager still present in the top right of the screen?  Does it allow you to choose wireless networks?

Thanks for the feedback.  The lsmod command shows that b43 is indeed loaded.  The network manager is still present, but it is no longer allowing me to choose any wireless networks.  If I right-click the manager, there is a checked box saying 'Enable Wireless', but if I left click the manager, there is a line under the 'Wireless Networks' line that says 'wireless network disconnected'.  Nor do I have the functionality to scan for networks:  when I type 

sudo iwlist scanning

I get a 'no networks detected' message (even though there are multiple networks available.)

---

### Post by MaindotC on 2010-09-13
NetworkManager controls the network connections as long as it's installed.  What you do with ifconfig or /etc/network/interfaces or iwconfig/iwlist is irrelevant because NetworkManager owns all.  I have had my own [unexplainable experience with NetworkManager](http://ubuntuforums.org/showthread.php?t=1573766) where it just "stopped working".  You are free to try the various methods, listed in the history of threads I provided, for stopping, starting, or restarting network-manager and nm-applet, but I didn't have any success.

I cannot give you a solution, but I can give you a work-around.  Open Synaptic and completely remove the packages "network-manager" and "gnome-network-manager".  Since you have a laptop I would imagine you will want to connect to various wireless networks in the future so I advise installing the package "wicd".  You can do it right during the removal of network-manager in Synaptic.  Reboot and we'll go from there.

---

### Post by utilitytrack on 2010-09-13
> **strAlan said:**
> I cannot give you a solution, but I can give you a work-around. Open Synaptic and completely remove the packages "network-manager" and "gnome-network-manager".

Awesome advice! Yes, really this is the first thing to do when network problems occurs. I propose to write it to NetworkTroubleshooting HowTo :)

---

### Post by MaindotC on 2010-09-13
> **utilitytrack said:**
> Awesome advice! Yes, really this is the first thing to do when network problems occurs. I propose to write it to NetworkTroubleshooting HowTo :)

I disagree - the problem with NetworkManager should be investigated because I'm not the only one that has had to remove it.  You shouldn't have to solve the failed operating of one application by installing another - that's not a solution.  I'm trying to find where I can file a bug report or something because no one is helping me with my thread either.

---

### Post by carltoews on 2010-09-13
> **strAlan said:**
> 
I cannot give you a solution, but I can give you a work-around.  Open Synaptic and completely remove the packages "network-manager" and "gnome-network-manager".  Since you have a laptop I would imagine you will want to connect to various wireless networks in the future so I advise installing the package "wicd".  You can do it right during the removal of network-manager in Synaptic.  Reboot and we'll go from there.

Hi strAlan,

OK, I've removed the network manager and the gnome-network manager, I've installed wicd, and I've rebooted.  The network manager icon in the upper right hand corner is now gone, and in its place is another icon which, when I click it, produces the wicd interface.  I can access the web via a wired connection, but there is no information about a wireless one.  

If that is the way things are supposed to be, great!  Where do we go from here?

Cheers,

Carl

---

### Post by MaindotC on 2010-09-13
Hi carl!  In the Wicd window, click "Preferences" and it should have a box to enter your wireless interface.  I never asked you which one it was so just do an "ifconfig" in a shell and it will probably be named wlan0 or eth1 or something other than eth0.

When you add that, go back to the main Wicd window and press "refresh" and then the wireless network should appear under your wired connection.  Click "connect" and you'll probably want to click "connect automatically" so you won't have to do this again.  For any future questions with Wicd feel free to consult the [Ubuntu Wicd Official Documentation](https://help.ubuntu.com/community/WICD).  Unfortunately that wiki hasn't been edited very well so I'll be sure to put in some pictures and make it a little more inviting.  Let me know how it goes.

---

### Post by carltoews on 2010-09-14
Well, the plot thickens:  I tried following your advice directly after work today, and seem to have run into a wall.  My wireless interface is wlan0, and it is listed under the Properties section.  Unfortunately, when I click 'refresh', I get the message 'no wireless networks detected.'  

I'm beginning to wonder if perhaps this is a hardware problem?  My laptop is about 5 years old, which is pretty old, by laptop standards.  Could my card have died?  Is there any way to check, short of buying a new card?  

Thanks again, I appreciate your help with all this.

Cheers,

Carl

---

### Post by MaindotC on 2010-09-14
Start with the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  There are commands it tells you to run like lspci, lsmod, and lshw -C network.  Those are the types of things that help determine where the problem lays.

---

### Post by MaindotC on 2010-09-14
Double post, my bad

---

### Post by carltoews on 2010-09-14
Yes, I know that page well--I've worked through it on several occasions, all to no avail.  

Anyway, I'll keep plugging away at this, but I have one last question that may or may illuminate things.  When I run the command "sudo lshw -C network", I get the following output:

 *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:11:43:48:ef:f4
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5751-v3.29a ip=192.168.2.2 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:16 memory:dfcf0000-dfcfffff

  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfbfe000-dfbfffff

  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0b:7d:15:2f:84
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


I would expect two network items, not three:  the first is clearly the wired interface, while the second two both seem to be the wireless.  What strikes me as weird (and this is doubtless a naive question) is that all the information about the card, its driver, etc. is in item 2, while the "logical name" wlan0 doesn't show up until item 3.  Why is this?  Could there be a disconnect between the card and the interface?  I tried establishing the interface manually (via the /etc/networks/interfaces file) to obviate this problem, but didn't have any luck.

---

### Post by MaindotC on 2010-09-15
Well it's likely not a hardware problem because it wouldn't show that output if the BCM4306 was inoperable.  There's no disconnect between the card and the interface but for further explanation of that output you'll have to contact [the developers of Hardware Lister](http://ezix.org/project/wiki/HardwareLiSter).  Perhaps if I have time I'll examine the source code but I rarely have that kind of time.

According to the [official Ubuntu documentation](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom) this card (version 3) should not work natively.  I'm not really sure why Hardware Drivers let you install that b43 driver in the first place.  According to this document you will need to use ndiswrapper and install the windows driver.  You may also want to continue trying the native drivers by following [this guide that was linked](http://caytin.wordpress.com/2009/07/21/how-to-broadcom-wireless-in-ubuntu-jaunty-jackalope/) to the official documentation.

---

### Post by bkratz on 2010-09-15
This page indicates that the version 3 is supported by b43.
[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

Supported chip types

BCM4303 (802.11b-only chips, uses b43legacy)
BCM4306 (Rev. 2 uses b43legacy, Rev. 3 uses b43)
BCM4309 (only the 2.4GHz part)

Might be something useful here.

---

### Post by MaindotC on 2010-09-15
> **bkratz said:**
> This page indicates that the version 3 is supported by b43.
[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

Supported chip types

BCM4303 (802.11b-only chips, uses b43legacy)
BCM4306 (Rev. 2 uses b43legacy, Rev. 3 uses b43)
BCM4309 (only the 2.4GHz part)

Might be something useful here.

Excellent find, kratz!  carltoews you are welcome to try the ndiswrapper route but kratz has found that the native driver should work.  Before you use ndiswrapper you may want to try a manual compiling and installation of the driver because it may be better configured for your system.  Also please check out the developer's [irc channel and other support](http://linuxwireless.org/en/users/Drivers/b43#support) just so you can eliminate the possibility that the driver is the issue.

---

### Post by carltoews on 2010-09-15
> **bkratz said:**
> This page indicates that the version 3 is supported by b43.
[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)


Thanks for the link, bkratz.  Actually, this was the link I referenced in my initial post (i.e. the one that started this thread.)  It does suggest that b43 should solve the problem, and since I had the card working before with exactly this driver, I'm baffled as to what could have gone wrong.  Sigh :-(

---

### Post by carltoews on 2010-09-15
> **strAlan said:**
> Excellent find, kratz!  carltoews you are welcome to try the ndiswrapper route but kratz has found that the native driver should work.  Before you use ndiswrapper you may want to try a manual compiling and installation of the driver because it may be better configured for your system.  Also please check out the developer's [irc channel and other support](http://linuxwireless.org/en/users/Drivers/b43#support) just so you can eliminate the possibility that the driver is the issue.

Thanks for the suggestions, strAlan.  I did in fact try compiling my own version of the driver, and it seemed to fare no better.  It looks like it's time to try ndiswrapper. (I've had success with ndiswrapper on the same machine under a Fedora distribution.  It may not work with this latest version of ubuntu, however: in the course of my quest for guidance on this issue, I recall seeing a page saying that ndiswrapper would not work with this card on this distribution of Ubuntu.)  Anyway, I'll give it a shot tonight, and report back with how things go.

All the best,

Carl

---

### Post by MaindotC on 2010-09-15
> **carltoews said:**
> Thanks for the link, bkratz.  Actually, this was the link I referenced in my initial post 

Sorry - I think I subscribe to too many threads - I'm off my game.  GL w/ ndis.

---

### Post by carltoews on 2010-09-19
As promised, a report on my latest misadventures with this wireless card:  ndiswrapper did not solve the problem.  After failing, I decided to reinstall Ubuntu 10.04 from scratch, to see if I could get back to where I was before, and it turns out that things have gotten worse.  My wireless card now has no power (as confirmed by iwconfig and the absence of the 'wireless power on' button on one of the laptop panels.) Since the bios are set to turn the card on at boot, I think what this means is that my card has in fact died.  

My next plan is to buy a new wireless card (ideally an internal one) and try to install it.  I've never opened a laptop in my life, so this will be a new adventure, details of which may materialize in a different thread.  But thanks again for trying to help me out here!  The problem wasn't resolved, but I learned something in the process, and appreciate your help.

Regards,

Carl

---

### Post by MaindotC on 2010-09-21
I'm sorry that happened and I wish I could physically be there to help you because I'm certain we could have gotten it resolved.  Please be wary of the "re-install solution" because typically if just 1 component is having an issue - the network adapters in this case - it's not really ideal to just wipe out everything and start over (that's how Winblows works).  You may have had to do that due to time constraints or frustration which I completely understand, but just wanted to give you my advice for the future.  Ubuntu is a very stable o/s once you get over the two main humps - wireless and video.

If you get a new network card I advise you look into the Intel or RealTek cards, or cards that use their chipsets.  Usually both chipsets are supported by late kernels, or if not then Intel typically provides Linux drivers.  I've been using the 3495 on my laptop for 4 years now and I've never had a problem.

---

### Post by carltoews on 2010-09-22
> **strAlan said:**
> 
If you get a new network card I advise you look into the Intel or RealTek cards, or cards that use their chipsets.  Usually both chipsets are supported by late kernels, or if not then Intel typically provides Linux drivers.  I've been using the 3495 on my laptop for 4 years now and I've never had a problem.

Thanks for the tips, I'll try to find one of these two brands.

Best,

Carl

---

### Post by carltoews on 2010-11-05
OK, it's been some time, but there have been developments:  I ended up reinstalling the OS and changing out my wireless card.  The new wireless card is an Intel 2200, and it works fine most of the time, though occassionally it exhibits the same behavior as the old Broadcom card, suggesting that I didn't really need to swap it out.  

The plot has thickened, however:  I have discovered that my machine will connect, and then immediately disconnect, from certain networks.  At my workplace, I have two neworks available, and to one it can connect without problem, to the other it won't stay connected.  The refusal to stay connected is new behavior, however:  for two weeks it worked beautifully, then abruptly ceased.  I have no idea what triggered the shift in behavior.

Any thoughts?

---

### Post by Roasted on 2010-11-05
> **carltoews said:**
> OK, it's been some time, but there have been developments:  I ended up reinstalling the OS and changing out my wireless card.  The new wireless card is an Intel 2200, and it works fine most of the time, though occassionally it exhibits the same behavior as the old Broadcom card, suggesting that I didn't really need to swap it out.  

The plot has thickened, however:  I have discovered that my machine will connect, and then immediately disconnect, from certain networks.  At my workplace, I have two neworks available, and to one it can connect without problem, to the other it won't stay connected.  The refusal to stay connected is new behavior, however:  for two weeks it worked beautifully, then abruptly ceased.  I have no idea what triggered the shift in behavior.

Any thoughts?

I cannot offer any help directly to your issue, but I would like to offer some insight from a fellow Ubuntu user with a Dell laptop.

I have a Dell Latitude E5500. It came with a Broadcom 4322 card. I had a slew of issues. It would connect on some networks, but not others. Yet each network was set up identically with WPA Personal, yet just a different SSID/PW to each one. It just wouldn't connect all of the time. Likewise, if I lost wireless due to being out of range, it would take a few minutes (8-10) just to re-initiate the connection. Extremely unacceptable.

The Intel 2200 is something else that was an issue. Intel itself is AWESOME with Linux wireless support, but the 2200 is the ONE Intel card that has exhibited issues. I put a 2200 in my mom's Toshiba laptop and it would connect just fine. After 20, 30, 40 minutes would pass, it would bomb out and lose its authentication with the router itself. It would NOT lose "connection" but it would just flat out stop responding. I did a little test, by opening 3 terminals and pinging 3 different web sites 5 seconds apart. As expected, I did not lose my wireless signal, it still said connected - but after a while it began to fail pings.

I ended up getting two new wireless cards for the laptops, both being Intel. I forget the exact models of the wireless cards, to be honest. What I did was I took off the panel of my laptop to see the exact form factor of the wireless card that I had. I then google image searched to find the exact name of it, since there's mini PCI, mini PCI express, mini PCI express half, etc...

I went on Google Shopping and scanned for "Intel mini PCI express half" or whatever form factor I had. I ended up getting a wireless N Intel card for less than 15 dollars! It has worked flawlessly with this E5500 ever since. All of the previous issues I had were gone. I connect in SECONDS now, instead of minutes. The Toshiba laptop is also working well now too with its new wireless card, which was even cheaper than the one I got for the E5500. Deals are out there, even wireless N cards can be had for cheap if you utilize Google Shopping to do the scanning of various web sites for you.

Moral of the story - avoid Broadcom. At. All. Costs. Sure, they have an "open source" driver now (about fricken time), but I just don't trust that company. Intel and Atheros is where it's at for Linux wireless support.

Before anybody fires out to me "avoiding Broadcom isn't fixing the issue with Linux support", here's some food for thought. I work in a school district, and two of our labs have desktops with Broadcom cards. These cards have exhibited issues in the past, and currently one lab is severely acting up and we are trying to troubleshoot it. Is it Broadcom? The driver? Our network? No idea at this point. But in the past there have even been direct issues with our Windows systems in regard to Broadcom cards. Just some food for thought that it doesn't matter what OS it is, sometimes problems arise with certain manufacturer's. It just seems to be a reoccuring pattern with Broadcom in this case...

Anyway, that's my story.

---

### Post by carltoews on 2010-11-05
Hey Roasted,

Thanks for the narrative--it may just be that I need to find yet another card (wish I'd read the story before I bought my Intel 2200, however... ;-)

Cheers,

Carl

---

