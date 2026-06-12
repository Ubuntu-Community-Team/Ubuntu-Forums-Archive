---
title: "Atheros wifi issue."
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by NeT_DeMoN on 2009-04-08
Hi, I have a Toshiba A215 Satellite laptop with an Atheros wireless networking card with the lspci result of:
```
 Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```
 I've tried Madwifi and it worked until an update and then never again after that. Ndiswrapper worked at one time before I had to do a fresh install but I don't remember how I did it. Every thread I've looked through on this subject is outdated and when I try to run the wget commands it's returned 404'd. Any help would be greatly appreciated.

---

### Post by lisati on 2009-04-08
(mad scramble hooking up gear to check, distracted by smoke alarm set off by someone else's cooking)

I'm wondering if my checking of my gear was a waste of time: I have a Toshiba A100 with an Atheres 2413 adapter, hasn't needed ndiswrapper...

---

### Post by NeT_DeMoN on 2009-04-08
I'm using Ibex and Gutsy nor Hardy picked it up off the bat. I always have to use Madwifi or Ndiswrapper.

---

### Post by t0mppa on 2009-04-09
MadWifi changed their web address from madwifi.org to madwifi-project.org, so that's why all the old links fail. Here's a run down of how I got mine (same wireless card, different laptop) up and running.

Yesterday some Ubuntu update outdated my HAL driver and my WLAN was rendered useless as a result. So, I checked some guides and ended up downloading a snapshot from here: [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz]("http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz") to '~/MadWifi'. Doesn't really matter where it's put, that just seemed like a nice and easy place, where I'd find it later, if I had some trouble again.

Unpacked the tarball with ```
tar -xvf madwifi-hal-0.10.5.6-current.tar.gz
``` 
Of course you can navigate to madwifi-project.org and figure out a path for WGet or SVN too, if you want to use them. I just used the simple download, since I had navigated to that site already and it was just one click away.

Then it was just```
cd madwifi-hal-0.10.5.6-r3977-20090408
``` Will probably get a big different name for the directory as they built it again today. Next, I figured garbage cleaning wouldn't hurt: ```
make clean
``` Then the actual compiling of the data: ```
make
``` And root access was required to install it: ```
sudo make install
``` Then added 'ath_pci' to the list of modules automatically loaded at boot with: ```
gksudo gedit /etc/modules
``` After that it was just a reboot ahead (had to boot my system anyway at that point because of some other stuff), but this should get it up and running even without a boot: ```
sudo modprobe ath_pci
```

---

### Post by NeT_DeMoN on 2009-04-10
t0mppa, I love you... Because of you I finally got wireless on my Ubuntu box once again. :D

---

### Post by laffytaffy on 2009-04-10
Hi, 

Got my wireless working too. Thanks. I had to install wicd because it was they only way I could get hidden ssid and WPA working. Now when I rebooted the machine - Voodoo!

Nothing is there, nothing works...

lspci:
0b:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

Before Ath0 was there, I could iwconfig scan and all was working.

What in the world happened? It's like I never setup anything. I also haven't done any updates, or installed any other programs since.

Any help greatly appreciated.

---

### Post by laffytaffy on 2009-04-10
I also played around with my wireless button on the laptop, and that didn't make any difference either.

---

### Post by laffytaffy on 2009-04-10
Here is lshw:

 *-network               
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:1e:68:fc:ba:0f
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full ip=192.168.11.9 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=1GB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: aa:76:79:59:e3:cc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



/etc/network/interfaces

auto lo
iface lo inet loopback

Sorry to post all the info, but I hope it makes it easier for someone to help.

---

### Post by coutts99 on 2009-04-10
Works out the box on Jaunty

---

### Post by jdackle on 2009-04-10
There's a simpler way: [http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html)
Thanks to superprash2003 for pointing it out to me in another thread. :)

The howto is for intrepid but it worked fine for me by changing linux-backports-modules-intrepid to linux-backports-modules-**hardy**. Of course, you need the Backports repo enabled to get the package. ;)
Might work with other releases too.

---

### Post by laffytaffy on 2009-04-10
Hi Coutts,

Are you saying that after install of juanty you can just go to network manager and all the wifi networks are just there? Did you leave Atheros hardware driver installed?

Do you have a hidden ssid setup using WPA? Even if it's not hidden, can you use WPA1/2?

Thanks

---

### Post by j4k3y34g3r on 2009-04-18
Thanks t0mppa! 
I upgraded from Intrepid (which I had resolved wireless card problems with ndiswrapper) on my Toshiba L305.

NOTE: users coming from ndiswrapper and using t0mppas method; comment out ndiswrapper and blacklist ath_hal in /etc/modprobe.d/blacklist.conf with the ol' #.

```
#ndiswrapper
#blacklist ath_hal
```

Unfortunately, now that I have wireless again, I have no more excuses and have to get back to work...

---

### Post by rmayer32 on 2009-04-18
I have the same card in mine, with Intrepid I just had to install the backports and it worked.

Jaunty with a fresh install worked right out of the box. This card used to be a real bear back in Gutsy and Hardy. No more now. :)

---

### Post by t0mppa on 2009-04-19
Actually using the backports way installs ath5k, if I'm not mistaken. What I listed here is a way to install the older MadWifi driver.

And to make the mess perfect, users of different cards have reported that for some cards ath5k works, for some the older driver works and some need NDISwrapper. So, none of these options can be offered as the ultimate fix for users. They just have to find out which one works for their card.

---

### Post by rmayer32 on 2009-04-19
Yes, the backport does install ath5k. Hopefully nobody with this same card needs ndiswrapper anymore though at this point.

---

