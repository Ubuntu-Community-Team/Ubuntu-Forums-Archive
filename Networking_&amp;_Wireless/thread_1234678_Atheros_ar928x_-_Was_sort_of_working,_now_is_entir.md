---
title: "Atheros ar928x - Was sort of working, now is entirely gone"
date: 2009-08-08
forum: Networking &amp; Wireless
---

### Post by Legolover64 on 2009-08-08
Hi everyone,

I have a Gigabyte Touchnote T1028 tablet netbook. I recently put Ubuntu on it, and I've been having some problems with the networking...

Initially, the WiFi would not work. It would show the status as "disabled" and manually entering an SSID would not work. So, I searched the forums (obvious) and found this page:
[http://ubuntuforums.org/showthread.php?p=7699456](http://ubuntuforums.org/showthread.php?p=7699456)

I followed these instructions:

wget [http://burnthesorbonne.com/files/compat-wireless-ath9k-20080916.tar.gz](http://burnthesorbonne.com/files/compat-wireless-ath9k-20080916.tar.gz)
tar -xzvf compat-wireless-ath9k-20080916.tar.gz 
sudo ./compat-wireless-ath9k-20080916.sh

sudo dpkg --install compat*deb

Now, unfortunately, the actual interface has disappeared! ifconfig yields no wlan found: just eth0 and loopback. I'm not sure of what to do at this point: I'd really like wireless networking on my computer.

Can anybody help?

---

### Post by Legolover64 on 2009-08-09
After working with some very intelligent users on IRC, I have the card showing up again in ifconfig. Here are the results of some commands that may be useful:

```
~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
02:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
```

```
~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

```

```

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

```

~$ dmesg | grep -e wlan -e ath
[   10.652871] device-mapper: multipath: version 1.0.5 loaded
[   10.652877] device-mapper: multipath round-robin: version 1.0.0 loaded
[   13.422938] ath9k: 0.1
[   13.423034] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.423059] ath9k 0000:02:00.0: setting latency timer to 64
[   13.902622] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   14.108431] Registered led device: ath9k-phy0:radio
[   14.108495] Registered led device: ath9k-phy0:assoc
[   14.108548] Registered led device: ath9k-phy0:tx
[   14.108600] Registered led device: ath9k-phy0:rx
[   25.188488] ADDRCONF(NETDEV_UP): wlan0: link is not ready


```

```

~$ sudo lshw -C Network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:17:50:a6
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:43:6a:fd:6c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 62:75:72:8e:05:0a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```
```

~$ uname -rm
2.6.28-14-generic i686

```

Any and all help with my issue would be greatly appreciated! I would really like to get this card working so I can use this computer at college!

---

### Post by pytheas22 on 2009-08-10
I'm a bit puzzled because I don't see anything in the output you posted that would indicate a problem.  Everything looks like it should be working, but scanning returns no results, which is strange.

One possible explanation is that the network you want to connect to is in a different mode than your wireless card, or on a channel that it can't see.  Do you know what the settings for your wireless network are?  You can usually view and change these by logging into your router from a computer that's connected to it (type 192.168.1.1 or 192.168.0.1 in a web browser and it should connect you to the router; if you don't know the password, check the outside of the router for the defaults, which are usually something like 'admin' and 'password').

If you could please check your the settings and let me know, that would be helpful.  The mode will be either 802.11a, 802.11b, 802.11g, 802.11n or a combination of these.  The channel should be a number between 1 and 13 inclusive.

Also, can you normally see many networks (like your neighbors') from the place where you're scanning, or just one?

Another thing to check is that the wireless card is turned on.  On many laptops you can turn the wireless card off to save power either with a physical switch on the outside of the computer, or a hotkey like function+F2.  Please make sure the card is not disabled this way.  (Usually it would be clear from your 'dmesg' output that this is the problem, but it's worth checking anyway if you haven't already.)

---

### Post by Legolover64 on 2009-08-11
> **pytheas22 said:**
> I'm a bit puzzled because I don't see anything in the output you posted that would indicate a problem.  Everything looks like it should be working, but scanning returns no results, which is strange.

One possible explanation is that the network you want to connect to is in a different mode than your wireless card, or on a channel that it can't see.  Do you know what the settings for your wireless network are?  You can usually view and change these by logging into your router from a computer that's connected to it (type 192.168.1.1 or 192.168.0.1 in a web browser and it should connect you to the router; if you don't know the password, check the outside of the router for the defaults, which are usually something like 'admin' and 'password').

If you could please check your the settings and let me know, that would be helpful.  The mode will be either 802.11a, 802.11b, 802.11g, 802.11n or a combination of these.  The channel should be a number between 1 and 13 inclusive.

Also, can you normally see many networks (like your neighbors') from the place where you're scanning, or just one?

Another thing to check is that the wireless card is turned on.  On many laptops you can turn the wireless card off to save power either with a physical switch on the outside of the computer, or a hotkey like function+F2.  Please make sure the card is not disabled this way.  (Usually it would be clear from your 'dmesg' output that this is the problem, but it's worth checking anyway if you haven't already.)

I am pretty frustrated with this card :/. It sucks that it hasn't worked yet. Oh well, I'm going to keep at it!

Here is the information on my wireless network:

WPA/WPA2 Personal encryption
Channel 6 (Automatically selected)
Broadcasting on 802.11n (802.11b/g compatible)

From where I am right now, I can only see this access point. I went to another part of the house, where an 802.11g access point is visible. Unfortunately, there is nothing there either.

I have tried the hardware toggle keyboard combination. It does not appear to do anything, no lights turn on, and the computer still has no scan results.

---

### Post by pytheas22 on 2009-08-11
It sounds like Ubuntu should be able to see your wireless router, since the settings look pretty normal.  It might not hurt to try switching to G mode only just to see if N broadcasting is part of the problem (some of the Linux wireless drivers still have flaky support for N mode), but I don't really think it is.

I did some googling and found [this thread]("http://www.linuxquestions.org/questions/linux-newbie-8/ar928x-detected-by-ubuntu-but-no-access-points-are-visible.-694984/"), which sounds a lot like your situation (same hardware, same failure to see networks).  In post 3 of that page there are instructions for compiling a specific version of the madwifi driver that seemed to work for the poster there.  If you could please give that a try, I think it might help.

The one addition that you'll need to make to those instructions is that, after recompiling the madwifi driver and rebooting, you'll need to run these commands so that the system will use the madwifi driver (whose module is named "ath_pci") rather than the madwifi-ng driver (named "ath9k", which you're currently using):
```

sudo rmmod ath9k
sudo rmmod ath_pci
sudo modprobe ath_pci
```

After that, the card should be brought up under ath_pci, so see if you can see networks then.

If you have any trouble following the instructions on that other page for compiling madwifi, let me know.

---

### Post by Legolover64 on 2009-08-11
Thank you so much for your response!

I was unable to checkout from svn.madwifi.org, but I followed the instructions and modified my hostfile. Sadly, here is what happened when I then tried to checkout:

```
$ svn co http://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6
svn: Server sent unexpected return value (405 Method Not Allowed) in response to PROPFIND request for '/madwifi/branches/madwifi-hal-0.10.5.6'

```

Do you know of any way to get it to checkout? Perhaps I'm checking out the wrong thing, or it's old?

Thanks again!

---

### Post by pytheas22 on 2009-08-13
Sorry the download didn't work.  I tried it as well and had the same problem.  Unfortunately the madwifi people have had problems because their domain was hijacked a while ago (if you go to [http://madwifi.org/](http://madwifi.org/) now, it's not a legitimate site; the new domain is madwifi-project.org); this may be related to why subversion doesn't work, even with the IP address of the server specified in /etc/hosts.

In any case, I found [this page]("http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/"), which offers snapshots of the code you need.  Please try downloading the madwifi-hal-0.10.5.6-r4068-20090705.tar.gz file, save it to your desktop and run these commands to compile and install:
```

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xzvf madwifi-hal*tar.gz
cd madwifi-hal*
make
sudo make install
```

Then reboot and let me know if there's any difference.  This should be the same code you would have gotten from subversion, so hopefully it will do the trick.

---

### Post by Legolover64 on 2009-08-13
Thanks for the response! It sucks that the madwifi domain got hijacked. The site did seem a little dodgy. I'll have to read up about the domain hijacking...

Anyways, I followed your instructions. Thanks for posting them! I ran wget to grab the code, untarred it, and compiled. There were functions that put up warnings, but no errors (from what I saw). I'm assuming make is like gcc and will throw up things if they error. Either way, I did make install and it seemed to have worked! I rebooted, and then ran the rmmod commands you specified earlier. Here is where the problems started to happen:

 - ath9k removed without headaches. ath_pci, however, was not found as a module in the kernel. I decided to move along.
 - After modprobing the ath_pci, the interface did not show up in sudo iwlist scan or ifconfig (just eth0 and loopback.) So, I thought that rebooting would be a good idea. I ran the dmesg command that you specified, and was shocked to see that the card came back with ath9k! I did an rmmod again of ath9k. It seems that that module is loaded on boot, every time I boot. How do I fix this issue? Is there some script that's running in the background that starts this up?

Thanks again for all your help!

---

### Post by pytheas22 on 2009-08-13
So when you typed:
```

sudo modprobe ath_pci
```

it returned with a "module not found" error?  That's strange.  ath_pci should definitely exist on your system.  What is the output of:
```

uname -r
sudo updatedb
locate ath_pci
```

Also, when you want to remove ath9k, try typing:
```

sudo rmmod ath9k
sudo rmmod ath_hal
```

Sometimes the ath_hal module will stick around and prevent other drivers from claiming the wireless card, even if ath9k has been removed. The commands above should take care of this.

As for ath9k loading on boot, it's probably because it's in your /etc/modules file--this is a list of modules that the kernel loads at boot regardless of whether it thinks they're necessary.  So try removing ath9k from that list.

---

### Post by Legolover64 on 2009-08-15
> **pytheas22 said:**
> So when you typed:
```

sudo modprobe ath_pci
```

it returned with a "module not found" error?  That's strange.  ath_pci should definitely exist on your system.  What is the output of:
```

uname -r
sudo updatedb
locate ath_pci
```

Also, when you want to remove ath9k, try typing:
```

sudo rmmod ath9k
sudo rmmod ath_hal
```

Sometimes the ath_hal module will stick around and prevent other drivers from claiming the wireless card, even if ath9k has been removed. The commands above should take care of this.

As for ath9k loading on boot, it's probably because it's in your /etc/modules file--this is a list of modules that the kernel loads at boot regardless of whether it thinks they're necessary.  So try removing ath9k from that list.
...
Hmm, weird. Now it seems ath_pci is there. Perhaps I misread the output last time? My apologies.

I did rmmod on both ath9k and ath_hal, but unfortunately that did not solve the problem. It still popped up on boot! So, I went into /etc/modules with vim, to look for these modules. They weren't mentioned at all in the file. Sadly, it still looks like ath9k gets loaded on boot, and that means that I cannot get on the internet still.

I don't know how orthodox this would be, but perhaps we can try something? I was thinking we could set up a screen session on the box, and have you SSH into it. There's currently nothing important on the computer, so it wouldn't bother me if you were poking around as root. Then, we could post what we found on the forums for future people with this card/computer. If this isn't appropriate, please let me know, but it seemed like an interesting idea...

Thanks again for all your help pytheas22!

---

### Post by djchandler on 2009-08-15
@legolover64:
See this thread.
[http://ubuntuforums.org/showthread.php?t=1238766](http://ubuntuforums.org/showthread.php?t=1238766)

It helped me solve my problem. It seems jockey is blacklisting atheros drivers if you try using proprietary driver then switching back.

I also think I found another source for downloading a .deb package for your madwifi driver. Problem is I need to go to another installation to see if the history is still there from getting it a week ago.

I'll repost later.

---

### Post by pytheas22 on 2009-08-15
> I don't know how orthodox this would be, but perhaps we can try something? I was thinking we could set up a screen session on the box, and have you SSH into it. There's currently nothing important on the computer, so it wouldn't bother me if you were poking around as root. Then, we could post what we found on the forums for future people with this card/computer. If this isn't appropriate, please let me know, but it seemed like an interesting idea...

The thread mentioned by djchandler above seems worth looking into to (I noticed that strange /etc/modprobe.d/blacklist-ath_pci.conf file the other day; I didn't realize it was there before), but if that doesn't help, I'm happy to try ssh'ing in and see if I can figure anything out.  Just send me the IP address and login credentials by private message, and please make sure port forwarding on your router is set up appropriately if applicable.

---

### Post by djchandler on 2009-08-15
[http://madwifi-project.org/](http://madwifi-project.org/) just has source code. I must have downloaded the .deb of compiled code from the site that is down now (madwifi.org).

---

### Post by Legolover64 on 2009-08-16
> **pytheas22 said:**
> The thread mentioned by djchandler above seems worth looking into to (I noticed that strange /etc/modprobe.d/blacklist-ath_pci.conf file the other day; I didn't realize it was there before), but if that doesn't help, I'm happy to try ssh'ing in and see if I can figure anything out.  Just send me the IP address and login credentials by private message, and please make sure port forwarding on your router is set up appropriately if applicable.

Thanks for the thread djchandler! And, thanks again pytheas22 for walking me through everything.

Unfortunately, after adding ath_pci, ath_hal and ath9k, still no dice. I tried removing ath_pci from the excluded list, but it unfortunately does not work :/. In either of those configurations, there is no wireless interface within ifconfig, leaving the system to only work on ethernet for the network.

I am going to hook up the machine to SSH later tonight, and forward 22 through to the computer. I will PM you with the details, pytheas22. Thanks again for all your help!

---

### Post by beke on 2009-09-26
I don't know if this is helpful, but I have no problem with the wifi of my T1028M with Karmic Koala Netbook Remix. 
Although it did not work in live-cd mode, it worked after installation & updating via ethernet (before the update, nm-applet would crash while connecting). 
See also
[http://ubuntuforums.org/showthread.php?t=1275975](http://ubuntuforums.org/showthread.php?t=1275975)

---

### Post by djchandler on 2009-09-28
Finally got an answer from launchpad on the Jockey bug that is blacklisting the driver.

> OK, thanks. Jockey should look into this file as a special case, unless
it's a conffile (I have to check).

** Changed in: jockey (Ubuntu)
   Importance: Undecided => Low

** Changed in: jockey (Ubuntu)
       Status: Incomplete => Triaged

-- 
jockey not restoring ath5k driver from blacklist
[https://bugs.launchpad.net/bugs/413781](https://bugs.launchpad.net/bugs/413781)
You received this bug notification because you are a direct subscriber
of the bug.
Stay tuned.

@beke,
When you combined threads, it dragged all the subscribers of those threads into the new combined thread. I suggest you use that feature sparingly. Somehow I don't think that's supposed to happen. If you are doing this to try to cross-post, it is contrary to the terms of service.
See:
[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

If you're trying to avoid cross-posting, I don't think it worked correctly.

I don't think I have seen this occur on this forum before. Suggest you contact the moderators to see how it is supposed to work.

djc

---

