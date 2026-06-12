---
title: "Unable to install Broadcom STA wireless driver"
date: 2011-01-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by onemanclapping on 2011-01-17
Hi! I just tested Natty in a USB stick but couldn't pass the installation of the wireless drivers.

It asks me if I want to install the proprietary drivers, I select the "Broadcom STA wireless driver" and while installing it gives me the following error:



Any ideas? I can't even "report" the error as I don't have a connection. If no one knows what this is, I'll try to get an Ethernet cable and see if I can report it properly.

I'm using a HP Mini 311.

---

### Post by cariboo on 2011-01-17
To make things easier on yourself, connect an ethernet cable to install the drivers. If you don't have a cable, mount whatever you used to install to your usb device, to /cdrom, then open System->Administration->Synaptic and click the update button, and make sure your source is being read. Once the sources list has been updated you should be able to install the driver.

---

### Post by onemanclapping on 2011-01-17
Thanks. I tried connecting the Ethernet cable and I got a connection. The error persisted.

What doesn't persist is my USB stick and I guess that's why I'm getting this error, so I posted the new problem on this thread: [http://ubuntuforums.org/showthread.php?p=10369343#post10369343](http://ubuntuforums.org/showthread.php?p=10369343#post10369343)

Damn this blue Monday!

---

### Post by cariboo on 2011-01-17
If you can't install the driver via Additional Drivers, Open up Synaptic, and install bcmwl-kernel-source.

---

### Post by donniezazen on 2011-01-17
I was able to install the driver but the wireless card is still disabled and hardware switch is not working.

I have a Dell Inspiron 6400/E1505.

---

### Post by onemanclapping on 2011-01-18
After resolving the persistence issue, I was able to install it from the Additional Drivers section.

But nothing happened. Rebooted. Now the wireless adapter was gone from network manager - before it only said (firmware not present).

Uninstalled the drivers and rebooted: the "firmware not present" was back.

Installed them through synaptic, rebooted, same problem...

Any thoughts?

---

### Post by teh603 on 2011-01-18
I had the same problem on my Inspiron 1564. I believe I fixed it by uninstalling the modaliases file, and then reinstalling it with a new copy.

---

### Post by onemanclapping on 2011-01-18
> **teh603 said:**
> I had the same problem on my Inspiron 1564. I believe I fixed it by uninstalling the modaliases file, and then reinstalling it with a new copy.

Well, I'm talking about a fresh Ubuntu, with nothing installed in it, so reinstalling parts of it seems kind of useless, but I'll try that!

The problem is I don't really know what you're talking about and a search for "modaliases" didn't help me very much, can you explain me what should I do?

Thanks!

---

### Post by cariboo on 2011-01-18
Depending on what wireless chipsset you have, you may need the b43 driver, we found during the last testing cycle that some bcm4312 chipset worked better with the b43 driver.

On my netbook, the b43 driver works, but won't connect to one of my routers when wpa2 is enabled.

I would suggest you remove the sta driver and try b43 cutter and firmware-b43-lpphy-installer, to see if that works.

One other thing to note, this morning after coming out of sleep, my system connected to one of my routers, but when I try to connect to the router sitting 4 ft away from me, network-manager disappears from the top panel, even after a reboot, so there may be a problem there, as there was an update to network-manager-gnome yesterday.

---

### Post by onemanclapping on 2011-01-18
> **cariboo907 said:**
> Depending on what wireless chipsset you have, you may need the b43 driver, we found during the last testing cycle that some bcm4312 chipset worked better with the b43 driver.

Yeah, I have the BCM4312, but right now I'm at maverick using the STA drivers. I'll try to install b43 then, as I also wanted to try aircrack which seems impossible with STA.

I'll get back to you, thanks!

---

### Post by cariboo on 2011-01-18
Aircrack won't work with broadcom devices without a lot of extra work

---

### Post by onemanclapping on 2011-01-18
> **cariboo907 said:**
> Aircrack won't work with broadcom devices without a lot of extra work

[http://www.aircrack-ng.org/doku.php?id=b43](http://www.aircrack-ng.org/doku.php?id=b43)

They say I (14e4:4315) have to blacklist wl... I'll give it a shot this weekend!

---

### Post by onemanclapping on 2011-01-18
> **cariboo907 said:**
> Aircrack won't work with broadcom devices without a lot of extra work

[http://www.aircrack-ng.org/doku.php?id=b43](http://www.aircrack-ng.org/doku.php?id=b43)

They say I (14e4:4315) have to blacklist wl... I'll give it a shot this weekend!

---

### Post by onemanclapping on 2011-01-18
> **cariboo907 said:**
> Aircrack won't work with broadcom devices without a lot of extra work

[http://www.aircrack-ng.org/doku.php?id=b43](http://www.aircrack-ng.org/doku.php?id=b43)

They say I (14e4:4315) have to blacklist wl... I'll give it a shot this weekend!

---

### Post by donniezazen on 2011-01-19
I have tried both b43 and STA, together and separately, none of them works. My wifi is still not working. What happened to bcmwl-modaliases, its not in repo and when i install it from maverick it is removed if i install bcmwl-kernel-source. I am getting number of errors like firmware missing or disabled by hardware switch or wireless is greyed out or not available.

Can anybody please help me pin point the problem so a bug report can be filed? I have not been able to use natty for 2-3 weeks because of wifi problem which sucks.

Thanks.

---

### Post by TBABill on 2011-01-19
Broadcoms are a pain in 10.10. What I ended up having to do for my BCM4312 is ```
sudo rfkill list
``` and if either soft or hard are marked YES, then ```
sudo rfkill unblock all
``` BUT this only works AFTER you have the STA driver installed correctly. For some reason it blocks upon initial install of the driver, but this fixes it for some users.

---

### Post by nm_geo on 2011-01-19
> **soham_1207 said:**
> I have tried both b43 and STA, together and separately, none of them works. My wifi is still not working. What happened to bcmwl-modaliases, its not in repo and when i install it from maverick it is removed if i install bcmwl-kernel-source. I am getting number of errors like firmware missing or disabled by hardware switch or wireless is greyed out or not available.

Can anybody please help me pin point the problem so a bug report can be filed? I have not been able to use natty for 2-3 weeks because of wifi problem which sucks.

Thanks.

I also had problems installing the STA driver after one of the recent upgrades and I am now running the following.

```
  ~$ sudo lshw -C network

  *-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:c1:24:e5
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.115 firmware=5752-v3.19 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:40 memory:efcf0000-efcfffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7d:c5:67:29
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.37-12-generic firmware=410.2160 ip=192.168.1.102 link=yes multicast=yes wireless=IEEE 802.11bg

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu natty (development branch)"

```After I finally got my Natty working I have been researching the wireless drivers and found this string of troubleshooting wireless commands on launchpad answers. You might try them too and post here or in Launchpad, Answers Wireless.

```
sudo apt-get update; sudo apt-get install hwinfo grep; sudo lshw -C network; rfkill list; sudo iwlist scanning; cat /etc/network/interfaces; cat /etc/lsb-release; lspci -nn; lsusb; sudo lshw -short; uname -a; dmesg | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|ound|p54|prism|rtl|rt2|rt3|rt6|rt7|usb|witch|wl';  iwconfig; cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl'; sudo hwinfo --netcard ; cat /var/lib/NetworkManager/NetworkManager.state; sudo lsmod
 
```

---

### Post by donniezazen on 2011-01-24
I was able to install bcmwl-kernel-source without any problem. rfkill list shows all 'no'.

Network manager is not showing any wireless connection, it just have a wired connection.

/etc/network/interfaces file is empty with only
auto lo
iface lo inet loopback

sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.

sudo rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

---

### Post by nm_geo on 2011-01-24
> **soham_1207 said:**
> I was able to install bcmwl-kernel-source without any problem. rfkill list shows all 'no'.

Network manager is not showing any wireless connection, it just have a wired connection.

/etc/network/interfaces file is empty with only
auto lo
iface lo inet loopback

sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.

sudo rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

That was where I was with the STA driver too. :
Try these:  
```
sudo apt-get update; sudo apt-get install hwinfo grep; sudo hwinfo --netcard 
```

---

### Post by donniezazen on 2011-01-25
> **nm_geo said:**
> That was where I was with the STA driver too. :
Try these:  
```
sudo apt-get update; sudo apt-get install hwinfo grep; sudo hwinfo --netcard 
```

THis is what i get.

> hal.1: read hal dataprocess 2090: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
23: PCI b00.0: 0280 Network controller                          
  [Created at pci.318]
  Unique ID: IluS.AUabv0M9SM3
  Parent ID: z8Q3.2EHfjazND95
  SysFS ID: /devices/pci0000:00/0000:00:1c.0/0000:0b:00.0
  SysFS BusID: 0000:0b:00.0
  Hardware Class: network
  Model: "Dell Wireless 1390 WLAN Mini-Card"
  Vendor: pci 0x14e4 "Broadcom"
  Device: pci 0x4311 "BCM4311 802.11b/g WLAN"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x0007 "Wireless 1390 WLAN Mini-Card"
  Revision: 0x01
  Driver: "b43-pci-bridge"
  Driver Modules: "ssb"
  Memory Range: 0xecffc000-0xecffffff (rw,non-prefetchable)
  IRQ: 16 (12 events)
  Module Alias: "pci:v000014E4d00004311sv00001028sd00000007bc02sc80i00"
  Driver Info #0:
    Driver Status: ssb is active
    Driver Activation Cmd: "modprobe ssb"
  Driver Info #1:
    Driver Status: wl is active
    Driver Activation Cmd: "modprobe wl"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #11 (PCI bridge)

24: PCI 300.0: 0200 Ethernet controller
  [Created at pci.318]
  Unique ID: rBUF.BCnMZHQFpUF
  Parent ID: 6NW+.Wj0NIVYGM5E
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:03:00.0
  SysFS BusID: 0000:03:00.0
  Hardware Class: network
  Model: "Dell Inspiron 6400"
  Vendor: pci 0x14e4 "Broadcom"
  Device: pci 0x170c "BCM4401-B0 100Base-TX"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x01af "Inspiron 6400"
  Revision: 0x02
  Driver: "b44"
  Driver Modules: "ssb", "b44"
  Device File: eth0
  Memory Range: 0xecbfe000-0xecbfffff (rw,non-prefetchable)
  IRQ: 17 (5516 events)
  HW Address: 00:19:b9:6e:e2:1e
  Link detected: yes
  Module Alias: "pci:v000014E4d0000170Csv00001028sd000001AFbc02sc00i00"
  Driver Info #0:
    Driver Status: b44 is active
    Driver Activation Cmd: "modprobe b44"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #18 (PCI bridge)

---

### Post by nm_geo on 2011-01-25
Driver Info #0:
    Driver Status: ssb is active
    Driver Activation Cmd: "modprobe ssb"
  Driver Info #1:
    Driver Status: wl is active
    Driver Activation Cmd: "modprobe wl"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #11 (PCI bridge)

Looks like a driver conflict to me.  I am sure the ssb module creates the B43 driver so I would try to :

Go to Synaptic and remove any package that has STA in it. You might need to 
```
rmmod wl
```and will need to blacklist wl.  It will not hurt anything for sure.  

I have two Nattys installed on this same laptop and I am still trying to find the correct way to run the STA driver with this BCB4312 card. Like you before the kernel upgrade the STA driver worked okay.  We shall prevail q;o)

---

### Post by donniezazen on 2011-01-28
> **nm_geo said:**
> Driver Info #0:
    Driver Status: ssb is active
    Driver Activation Cmd: "modprobe ssb"
  Driver Info #1:
    Driver Status: wl is active
    Driver Activation Cmd: "modprobe wl"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #11 (PCI bridge)

Looks like a driver conflict to me.  I am sure the ssb module creates the B43 driver so I would try to :

Go to Synaptic and remove any package that has STA in it. You might need to 
```
rmmod wl
```and will need to blacklist wl.  It will not hurt anything for sure.  

I have two Nattys installed on this same laptop and I am still trying to find the correct way to run the STA driver with this BCB4312 card. Like you before the kernel upgrade the STA driver worked okay.  We shall prevail q;o)

Thanks,

Sorry for this delay but it did not help i am still not able to use Natty because of no wifi.

---

### Post by nm_geo on 2011-01-29
> **soham_1207 said:**
> Thanks,

Sorry for this delay but it did not help i am still not able to use Natty because of no wifi.

Have you un-installed the STA Broadcom driver? wl?  
bcmwl-kernal-source, broadcom-sta-common & broadcom-sta-source..

The wl and ssb modules conflict with each other according to the broadcom webpage. Maybe this will help.

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

I just never got the STA driver working so I went back to the B43. I still have another Natty installed in another partition that I am trying to get going with the STA driver, but I have not found an effective way to stop the ssb module from causing conflicts.  I have done nearly everything including rmmod ssb in the rc.local and blacklisting ssb.. Still working on it.. Maybe I will rename/remover the module next.. q;o)

---

### Post by nm_geo on 2011-01-29
Okay, I finally got tired of messing with the STA driver (at least for now).  Decided to get the B43 driver running on my dual Nattys.. So i remove ssb from the blacklist and the rmmod ssb from rc.local and now I have both installs working with B43 on my laptop.. STA maybe later not giving up just yet.

---

### Post by donniezazen on 2011-01-29
OK for sure STA is not working.

I suspect it to be related to kernel problem. I get this error inserting crc32c_intel with 2.6.37-12, i just install 2.6.38.1, so far kernel panic and wifi worked smoothly with b43-fwcutter and firmware b43 installer. I have previously tried b43 liphy installer which did not work. I blacklisted ssb and remod wl b43 b44 but i just removed ssb from blacklist and wifi does not have any problems.

Thanks all i am back to natty.

update:it disconnects every once in a while.

---

### Post by nm_geo on 2011-01-29
> **soham_1207 said:**
> OK for sure STA is not working.

I suspect it to be related to kernel problem. I get this error inserting crc32c_intel with 2.6.37-12, i just install 2.6.38.1, so far kernel panic and wifi worked smoothly with b43-fwcutter and firmware b43 installer. I have previously tried b43 liphy installer which did not work. I blacklisted ssb and remod wl b43 b44 but i just removed ssb from blacklist and wifi does not have any problems.

Thanks all i am back to natty.

update:it disconnects every once in a while.

Glad you finally got your Natty working again.  Your previous kernel problem might have been the big issue after all.  I am still working on getting the STA driver to work with my wireless chipsets and having little luck, but it is good to have working wireless to test any way and the B43 works well here.

---

### Post by donniezazen on 2011-01-30
> **nm_geo said:**
> Glad you finally got your Natty working again.  Your previous kernel problem might have been the big issue after all.  I am still working on getting the STA driver to work with my wireless chipsets and having little luck, but it is good to have working wireless to test any way and the B43 works well here.

b43 has disconnection problems. It is not stable it disconnects 3-4 times in an hour. Hope STA is fixed soon.

---

### Post by donniezazen on 2011-01-31
I am unable to block ssb as it is used by b44. If i removed b44 it closes network manager and there is no wired or wireless connection. Any idea what it is? So ideally i should remove all b44, ssb, and b43 module to run STA without any problems.

---

