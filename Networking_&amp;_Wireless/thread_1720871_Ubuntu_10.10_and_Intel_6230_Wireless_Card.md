---
title: "Ubuntu 10.10 and Intel 6230 Wireless Card"
date: 2011-04-03
forum: Networking &amp; Wireless
---

### Post by GeraldNunn on 2011-04-03
I just bought a new computer and it comes with the Intel 6230 wireless/bluetooth combo card. I'm trying to get wireless working on this laptop in Ubuntu 10.10 (64 bit) but am not having much success. I installed linux-backport-modules for Meerkat but that did not get the card working. Here is the output of lspci -k:

```

00:00.0 Host bridge: Intel Corporation Sandy Bridge DRAM Controller (rev 09)
	Subsystem: CLEVO/KAPOK Computer Device 5102
	Kernel modules: intel-agp
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
	Subsystem: CLEVO/KAPOK Computer Device 5102
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
	Subsystem: CLEVO/KAPOK Computer Device 5102
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
	Subsystem: CLEVO/KAPOK Computer Device 5102
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
	Subsystem: CLEVO/KAPOK Computer Device 5102
	Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge: Intel Corporation Cougar Point LPC Controller (rev 05)
	Subsystem: CLEVO/KAPOK Computer Device 5102
	Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)
	Subsystem: CLEVO/KAPOK Computer Device 5102
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
	Subsystem: CLEVO/KAPOK Computer Device 5102
	Kernel modules: i2c-i801
01:00.0 VGA compatible controller: nVidia Corporation Device 0dd1 (rev a1)
	Subsystem: CLEVO/KAPOK Computer Device 5102
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nouveau, nvidiafb
01:00.1 Audio device: nVidia Corporation Device 0be9 (rev a1)
	Subsystem: CLEVO/KAPOK Computer Device 5102
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
02:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
	Subsystem: CLEVO/KAPOK Computer Device 5102
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci-hcd
03:00.0 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 05)
	Subsystem: CLEVO/KAPOK Computer Device 5102
	Kernel driver in use: jme
	Kernel modules: jme
03:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 90)
	Subsystem: CLEVO/KAPOK Computer Device 5102
03:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 90)
	Subsystem: CLEVO/KAPOK Computer Device 5102
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci
03:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 90)
	Subsystem: CLEVO/KAPOK Computer Device 5102
04:00.0 Network controller: Intel Corporation Device 0091 (rev 34)
	Subsystem: Intel Corporation Device 5201
	Kernel modules: iwlagn
05:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (rev 30)
	Subsystem: CLEVO/KAPOK Computer Device 5102
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci, ohci1394

```

Here is the output of rfkill:

```

gnunn@gerald-laptop:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

Any ideas on how to get this going?

---

### Post by GeraldNunn on 2011-04-04
With the backport package installed, I see the following in dmesg:

```

[    7.608499] iwlagn 0000:04:00.0: request for firmware file 'iwlwifi-6000g2b-4.ucode' failed.
[    7.608555] iwlagn 0000:04:00.0: no suitable firmware found!

```

Anyone know where I can get this file as I'm having a hard time finding it.

---

### Post by GeraldNunn on 2011-04-05
I tried downloading the natty beta to see if it had the right firmware file but no luck. I know this works with Natty but I would prefer not to upgrade at this time so any help would be greatly appreciated.

---

### Post by jawilljr on 2011-04-05
You can normally download Intel wifi firmware from [Intel Linux Wireless]("http://intellinuxwireless.org/") but [they appear to be down]("http://www.downforeveryoneorjustme.com/http://intellinuxwireless.org/")

Jerry

---

### Post by GeraldNunn on 2011-04-05
Thanks, I had a look and problem is they have the version 5 firmware (iwlwifi-6000g2b-5.ucode) instead of version 4 (iwlwifi-6000g2b-4.ucode). I just did a quick check by downloading and renaming the file but the driver complains about the newer firmware version.

---

### Post by jawilljr on 2011-04-05
I couldn't find your firmware either...the only thing I would suggest doing is to download and install either the latest bleeding edge [compat-wireless drivers]("http://wireless.kernel.org/en/users/Download") or the latest stable drivers from compat-wireless.

They are easy to install... just untar the file and change to that directory and do a "make" the "sudo make install" the reboot.

Hope this helps.

Jerry

---

### Post by flash63 on 2011-04-05
Hello,
you can download the latest Firmware from Linux Firmware-Git
[http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=tree](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=tree)

Klick on "snapshot" in the upper left corner.

But the new driver from Compat-Wireless recently dont't work with Kernel 2.6.35-*. No Problem with Kernel 2.6.32-* and Lucid.

Reference article in german ubuntuusers forum:
[http://forum.ubuntuusers.de/post/2767012/](http://forum.ubuntuusers.de/post/2767012/)

---

### Post by jawilljr on 2011-04-05
> But the new driver from Compat-Wireless recently dont't work with Kernel 2.6.35-*. No Problem with Kernel 2.6.32-* and Lucid.Below is my uname -r

```
2.6.35-28-generic
```And the version of compat-wireless I am running is:

```
compat-wireless-2.6.38-3-ns
```I even downloaded and installed the latest bleeding edge last night...but reverted back to stable.

So yes they do work with Kernel 2.6.35-*.

Also compat-wireless was the only way  could get wireless N at 5ghz.

Jerry

---

### Post by flash63 on 2011-04-05
> So yes they do work with Kernel 2.6.35-*.
Great

Check in addition ...
```
cat /etc/modprobe.d/intel-5300-iwlagn11n.conf
```
Option should be
```
options iwlagn 11n_disable=[COLOR="Red"]0[/COLOR]
```

---

### Post by jawilljr on 2011-04-05
I actually commented that line out... got me wireless N but no 5 ghz... until I compailed and installed compat-wireless.

Below is my iwconfig on my laptop.

```
wlan0     IEEE 802.11abgn  ESSID:"KJAWJR"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: C0:C1:C0:38:4F:32   
          Bit Rate=144.4 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:197  Invalid misc:2   Missed beacon:0
```I just wish  could get the full 300 mbs...but I'm not complaining because it is a whole lot better than before.

Jerry

---

### Post by GeraldNunn on 2011-04-05
Thanks everyone, I got it working with the bleeding edge version and specifying the iwlagn driver before make. I tried the compat-wireless-2.6.38-2.2-ns version, which is what is available to download in stable releases, but it didn't seem to install the iwlagn.ko driver in the updates directory for some reason.

---

### Post by flash63 on 2011-04-06
> I just wish could get the full 300 mbs...but I'm not complaining because it is a whole lot better than before.
Both, Router and WLAN-Devive must support two transport streams (MIMO) to achieve this transfer rate. The Intel Card do, but your Router also?

The router must have at least two antennas as a first indication. Device-type and manufacturer of your WiFi-Router?

Do a scan to check out whether the radio channel is free
```
sudo iwlist wlan0 scan
```

---

### Post by jawilljr on 2011-04-06
> Device-type and manufacturer of your WiFi-Router?lspci:

```
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
```Router Linksys E3000.

---

### Post by flash63 on 2011-04-08
> Router Linksys E3000.
Your Router can. Three Transponder, and three Antennas are build in. Check the Channels as described.

---

