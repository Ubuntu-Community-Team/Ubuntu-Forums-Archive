---
title: "[SOLVED] Enable preinstalled wireless driver"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by baskcoder on 2008-12-21
Hi Guys,

I'm using **Ubuntu 8.10 Intrepid IBEX** on **Dell Studio 1537** laptop. Previously I was able to use wireless connection with the preinstalled driver. On my friends advice I installed Windows Vista Wireless driver for **Intel 5100** using NDISWrapper. It failed to work.

Now, I want to get back to using the previous(default) driver which was installed while installing Ubuntu. How do I do that? Right now, I've uninstalled the Windows Vista driver and ndiswrapper software.

Please help me in this regard.
Thank You.

---

### Post by untappedpilot2 on 2008-12-21
Take a look at this thread [http://ubuntuforums.org/showthread.php?t=906865]("http://ubuntuforums.org/showthread.php?t=906865") I assume you had to disable the default driver when you installed ndiswrapper, do you remember which driver that was? I'm curious as to why you would disable your working driver for ndiswrapper anyway? Ndiswrapper is usually the last resort or second choice. Please post your the results of:

```

sudo lshw -C network
lspci

```

---

### Post by baskcoder on 2008-12-21
I actually didn't disable the default driver. I used **ndisgtk** to install the windows driver. I don't know the default driver. I was advised that the windows driver works better than inbuilt generic driver. So, I tried installing it. Thereby, screwing up my wireless driver :)

I will post the output of the commands shortly. Thank you

---

### Post by baskcoder on 2008-12-21
Output of **sudo lshw -C network**

```

  *-network UNCLAIMED
       description: Network controller
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:21:70:83:64:1c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full ip=192.168.2.15 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 46:2a:6f:9d:a3:7d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by baskcoder on 2008-12-21
Output of the command: **lspci**

```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

---

### Post by untappedpilot2 on 2008-12-22
From looking around on the web and checking the drivers I had available on my system, I think the native driver for the Intel 5100 is the iwl3945 driver. Once ndiswrapper is completely removed / uninstalled / whatever do:
```
modprobe iwl3945
```
...and I think that should load the native driver for your card. Thought it should get it working I'm not sure the change will be permanent. (If you were to reboot or something.) Try that and let me know how it goes and if it still works on reboot or if you have to do the modprobe command again to load up the driver. I'll get back with how to make the change permanent if you need to. It's been awhile since I've had to play around with it. Good luck!

---

### Post by baskcoder on 2008-12-22
After executing the **sudo modprobe iwl3945** here is the output of** lsmod | grep iwl3945** command:

```

iwl3945                98804  0 
rfkill                 17176  1 iwl3945
mac80211              216820  1 iwl3945
led_class              12164  1 iwl3945
cfg80211               32392  2 iwl3945,mac80211

```


After this, wifi link LED didn't glow (i.e. Wireless was not enabled) as the module was not loaded. On restarting, I couldn't view the entry of iwl3945 on executing lsmod command.

Is there any way to add this permanently to the module list?

Thanks for the replies :)

---

### Post by baskcoder on 2008-12-22
It is solved. When I used the command **sudo modprobe iwl3945** wireless was not enabled. So, I tried the command **sudo modprobe iwlagn**. This enabled the wireless hardware.

So, [COLOR="Red"]iwlagn[/COLOR] can be used as the driver for **Intel Wireless WiFi Link 5100**.

In order to load the driver automatically during boot, add **iwlagn** to the [COLOR="Blue"]/etc/modules[/COLOR] file.

Thank you _**untappedpilot2**_ for all the help and guidance. Really grateful to you. :)

---

### Post by djenia on 2010-01-26
I had very similar problems, the above thread didn't help, this did
[http://ubuntuforums.org/showthread.php?t=1307396](http://ubuntuforums.org/showthread.php?t=1307396)

---

### Post by cantInstallUbu on 2010-02-03
> **baskcoder said:**
> It is solved. When I used the command **sudo modprobe iwl3945** wireless was not enabled. So, I tried the command **sudo modprobe iwlagn**. This enabled the wireless hardware.

So, [COLOR=Red]iwlagn[/COLOR] can be used as the driver for **Intel Wireless WiFi Link 5100**.

In order to load the driver automatically during boot, add **iwlagn** to the [COLOR=Blue]/etc/modules[/COLOR] file.


I had the same exact issue, and I tried this to resolve my issue, but found that this didn't help. However, when I did **sudo modprobe iwlcore**, my wireless started working. So anyone who doesn't have success with [COLOR=Red]iwlagn[/COLOR] might want to try [COLOR=Red]iwlcore[/COLOR] before trying that other thread.

Thanks for the help **baskcoder/untappedpilot2** !

---

