---
title: "No wireless in 9.10 with Broadcom BCM4312"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by gubbi.fisk on 2009-11-01
Hi

I just upgraded from 9.04 -> 9.10 and that made me loose my wireless connection. I'm running the 32-bit version. In "Hardware drivers" the "Broadcom STA wireless driver" states that it's activated and currently in use. When I try to connect it does all the things, but fails on getting the IP-address (there is a long time-out, or some thing). My laptop is Acer Extensa 5220. As the title says I'm using a Broadcom BCM4312 wireless card.

I tried:
Reinstalling the driver package

In WICD I tried:
Changing from wext to hostap, madwifi, atmel, ndiswrapper ect.
Changing from external to ioctl

But no luck.

In terminal "lspci -v" outputs:

04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
	Subsystem: Foxconn International, Inc. Device e003
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f8000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl, ssb

Please help!!

---

### Post by gubbi.fisk on 2009-11-01
**"sudo lshw -C network" output:**

  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:e1:16:46:06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f8000000-f8003fff

**"lsmod | grep wl" output:**
wl                   1272936  0 
lib80211                6432  2 lib80211_crypt_tkip,wl

I noticed that the driver loaded is **wl**, but the driver in use is **wl0** does this mean anything?

---

### Post by gubbi.fisk on 2009-11-01
Wireless now working. (Hopefully for good)

All I did was:
```

sudo apt-get upgrade
sudo aptitude reinstall bcmwl-kernel-source

```

I don't know if i'll work for any body else, or me for long. But feel free to try!

---

### Post by Serpher on 2009-11-01
Didn't work for me

Lenovo G530 with the same chipset BCM4312.

---

### Post by endorphine44 on 2009-11-01
I've tried the same with 9.10 on a Dell Inspiron 1720, 4312 b/g wireless. Did not work for me. I've tried the hybrid drivers from Broadcom @ [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
I've tried the b43 driver, and the STA driver from Ubuntu restricted drivers. Just can't get the thing to even show up.

---

### Post by cen on 2009-11-01
Same here with the Broadcom STA driver. I previously had the 9.10 Koala netbook remix version installed and it worked great in that. Now that I've installed the desktop/laptop version (prefer the classic desktop look) it pops up that the driver is available but when I go to activate it, after giving my password for permission, it shows the keys symbol at the top taskbar for a brief second then it (keys symbol) just disappears and it never activates the driver. 
Does the same thing when I find the driver by going to System->Administration->Hardware Drivers

Must be a bug somewhere since it is working fine on the netbook remix version, like I said.

Everything else and the installation itself went fine. It's even running on my wired connection just fine and I've downloaded several apps from the repos already. Wireless connection is the only issue I can see.

---

### Post by gypsybee on 2009-11-02
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

I was having exactly the same issues. I tried handling it on my own at first using the drivers the 64bit 9.10 located, obviously that failed. Gubbi's ideas did not work for me either. I am running a Dell XPS M1530 with the BCM4312 wireless card. The link above did work for me however. The important thing about using the broadcom link is to ensure you read the wonderful notepad that you can download too. Especially if like me you are still pretty new at Ubuntu/linux. 
Stay Safe!

---

### Post by gonefortheday on 2009-11-02
Doesn't work for me on an HP Mini 1033 (1000 series) with a BCM4312 on 9.10.
Why was 9.10 released with SO MANY notebooks regressed to not working?

If I install the proprietary drivers using the Hardware Drivers tool, my system locks up and never boots again (kernel panic w/ no output on module load).  The native drivers don't work, but they worked OUT OF THE BOX on 9.04!

[   61.875158] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   61.920173] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 6, Type 5, Revision 1)

---

### Post by doixanh on 2009-11-02
You guys should try switching to ndiswrapper and follow this post. it's a bit annoying but it still works for me. I also have BCM4312.

[http://ubuntuforums.org/showpost.php?p=8082022&postcount=4](http://ubuntuforums.org/showpost.php?p=8082022&postcount=4)

---

### Post by endorphine44 on 2009-11-02
> **doixanh said:**
> You guys should try switching to ndiswrapper and follow this post. it's a bit annoying but it still works for me. I also have BCM4312.

[http://ubuntuforums.org/showpost.php?p=8082022&postcount=4](http://ubuntuforums.org/showpost.php?p=8082022&postcount=4)

I may try that tonight, I also ordered a new Dell 1490 wireless card today so I'll see if that plays any better with 9.10.
I also tried several Live CD's from Fedora and OpenSuse, all seemed to have the same problem with the 4312 card.

---

### Post by samasat on 2009-11-02
Combination of above Worked for me ... However, I had a wired connection to download.

1) Connect wired connection using NIC ethernet

2) do update and upgrade:
   ```
sudo apt-get install update
```3) System>>Administrator >>Hardware Drivers 
select Broadcom STA and BoadCom fwcutter and activate and restart

-Samasat

---

### Post by DapperMe17 on 2009-11-02
Try here...it works with the BCM4306(rev2) card.

It's worth the try, however, I haven't tried it with any other Broadcom cards.


[http://ubuntuforums.org/showthread.php?t=939658](http://ubuntuforums.org/showthread.php?t=939658)

---

### Post by corfitz on 2009-11-02
It is still not working for me. I cant even see the driver under hardware drivers.
It worked perfectly on 9.04 but not in 9.10 ive tried a fresh reinstall twice and ending up with same problem.

---

### Post by opengonzo on 2009-11-21
don't go for me also (hp 700 el)

---

### Post by ublintu on 2009-11-21
Hi,
(If it`s still not working) After a clean install, I followed this(the first post): [http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)
4 me it`s fine now.

---

### Post by Erki82 on 2009-11-21
I got HP nx6325 with Broadcom BCM4312. I installed a Ubuntu 9.10 on one partition. After booting up, OS didnt give me option to chouse restricted wifi drivers, like in 9.04. I tried:

sudo apt-get install --reinstall bcmwl-kernel-source

but after that, Wireless Networks form that small wifi logo next to clock disappeared. After I made again new install with format that 9.10 partition. I looked under Synaptic, what bcmwl packages are installed and I found this: bcmwl-modaliases. Then I removed it:

 sudo apt-get remove bcmwl-modaliases

And installed bcmwl-kernel-source again:

sudo apt-get install --reinstall bcmwl-kernel-source

And after restart wifi works.

---

### Post by Sabayenda on 2009-11-25
Okay,
I don't know if I'm reading this thread wrong, but I don't understand how this is solved when nothing I try works.  

I've tried all of the suggestions, and the only thing that seems to even allow my wifi to detect networks is if I make sure the broadcomm STA driver is uninstalled and that the fwcutter driver is installed (which disappears  entirely from time to time if I have had the SAT installed before it or if the bcmwl-kernel-source is installed).

Also, I'm having problems with the bcmwl-kernel-source itself... I had only the fwcutter driver installed through the hardware drives program and the bcmwl-kernel-source uninstalled, but the bcmwl-modaliases installed.  This configuration made it possible for me to access the drop down wireless menu and choose my wireless network, though it wasn't asking for a password at all and just dropping it after trying to connect for a minute or so.  I went into Network Connections and put the password in there under the security tab, and it would try to connect again, but would fail after a minute and not try to reconnect.  

My system is fully up to date with Ubuntu updates, and I can't think of anything else that's wrong.  I've tried Wicd, it didn't work either. Even though this is the newest version of Ubuntu, it's the toughest to get the stupid wireless working.  It used to be super simple, as long as I could find a wired internet connection.  

There used to be awesome step by step instructions on how to get wireless working, but those are for older versions and I think it stopped working for me on the last version (9.04).  Again, I'm probably just not reading this thread correctly, but if someone could point me in the right direction with a clear roadmap of what I need to do, I'd be most grateful. The only foolproof "solution" I can find is the "sudo apt-get upgrade
sudo aptitude reinstall bcmwl-kernel-source" solution, which does not work at all in my case.
"lspc -v" outputs:
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
	Subsystem: Dell Device 000c
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at f6cfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: ssb, wl

My output is a little bit different from the OP, so I don't know if it's what's causing the problem or not.

Thanks in advance if you're able to help!

---

### Post by MirzaD on 2009-12-04
I managed to fix my wifi problem. I am not sure what exactly what helped. However I want to share what I did in hopes it may help someone.

I did this:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/)

I finished all the steps from this site:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
I downloaded archive and read README file on site.

I allso did this:
sudo apt-get upgrade
sudo aptitude reinstall bcmwl-kernel-source

After each step i restarted system but it did not help, my device did not show in ifconfig.

In the end I opened Hardware Drivers and enabled STA wireless driver. System froze but after restart i had my WiFi working :D:D:D

For the record I am using Lenovo G550 with Kubuntu 9.10 Karmic.

---

### Post by mlitty on 2009-12-08
> **gypsybee said:**
> [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

I was having exactly the same issues. I tried handling it on my own at first using the drivers the 64bit 9.10 located, obviously that failed. Gubbi's ideas did not work for me either. I am running a Dell XPS M1530 with the BCM4312 wireless card. The link above did work for me however. The important thing about using the broadcom link is to ensure you read the wonderful notepad that you can download too. Especially if like me you are still pretty new at Ubuntu/linux. 
Stay Safe!

Confirmed.  This worked for me also, but only AFTER reading and following the README.txt file that is available on the same page from which the driver is downloaded.  There are a few things in there I didn't catch the first time I tried this.  The second time worked flawlessly.

---

### Post by wamukota on 2009-12-09
@Erki82

As I own a HP nx6325 I thank you very much for having posted your solution here.

Alain

---

### Post by gabbar_singh on 2009-12-14
Thanks Eric82. Worked for me after I put the restricted repo in the /etc/apt/sources.list
I have a HP Pavilion dv4

---

### Post by imahussey on 2010-01-21
samasat your awesome, After a fresh install I updated the machine first with a wired connection. Then went to system>admin>hardware drivers. It found the fwcutter and STA wireless drivers. Since I don't want to mess with the winblows driver, I'm using the STA driver, which works perfectly. All I had to do was activate it, and reboot, then setup my wireless settings. 
By the way I have an HP dv2000 with a a broadcom wireless card (bcm4312)and i'm running 9.10 Karmic Kola.

---

### Post by Sephenon on 2010-01-23
> **gubbi.fisk said:**
> Wireless now working. (Hopefully for good)

All I did was:
```

sudo apt-get upgrade
sudo aptitude reinstall bcmwl-kernel-source

```I don't know if i'll work for any body else, or me for long. But feel free to try!


sephenon@MattsLaptop:~$ sudo apt-get upgrade
[sudo] password for sephenon: 
Sorry, try again.
[sudo] password for sephenon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sephenon@MattsLaptop:~$ sudo aptitude reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "bcmwl-kernel-source"
Couldn't find any package whose name or description matched "bcmwl-kernel-source"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

sephenon@MattsLaptop:~$ 

yeahhhh...anyone make any sense of this?

---

### Post by bkratz on 2010-01-23
Here is a pretty good description of what to do, it can be done from the install CD. 

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by zviangi on 2010-03-14
You need just to install kernel-headers of respective kernel version you have and then reinstall bcmwl-kernel-source and everything will work!

---

### Post by MasterOfTheHat on 2010-07-06
> **gubbi.fisk said:**
> Wireless now working. (Hopefully for good)

All I did was:
```

sudo apt-get upgrade
sudo aptitude reinstall bcmwl-kernel-source

```

I don't know if i'll work for any body else, or me for long. But feel free to try!
Also worked for Lucid (10.04) with a BCM4312:
```
$ lspci | grep Network
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

---

