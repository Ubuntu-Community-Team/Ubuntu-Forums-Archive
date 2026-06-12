---
title: "Wireless problem after &quot;suspend&quot;"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by flyver on 2010-05-02
Hi, my wireless is working fine except after having suspended my session. It just won't start again (I can see no networks). My Sony has ha separate "wireless LAN" button and I put it off and then on again but it doesn't help.

I have Ubuntu 10.04 LTS.

I searched in the forums but didn't find any threads about problems only after having suspended a session...

Thank you.

---

### Post by flyver on 2011-01-12
I still have the very same problem, and I've done hours and hours of seaching this forum, Google, Launchpad... :(

I hate Intel® PRO/Wireless 3945ABG.

---

### Post by amsterdamharu on 2011-01-12
When you come back from suspend and switch the wireless on and off what are the outputs of the following commands?
```
iwconfig
```and
```
rfkill list
```

To execute the commands you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in &#91;code] &#91;/code] tags.

---

### Post by flyver on 2011-01-12
They are:

```
lo        no wireless extensions. 

eth1      no wireless extensions. 

wlan1     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          
vmnet1    no wireless extensions. 

vmnet8    no wireless extensions. 
```



and



```

0: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
```

---

### Post by amsterdamharu on 2011-01-12
Strange that iwconf gives you wlan[COLOR=Red]1[/COLOR] but rfkill shows a [COLOR=Red]0[/COLOR]: pho[COLOR=Red]0[/COLOR]:

Is there output for 
```
rfkill list 1
```

And just to make sure the make and model could you check:
```
lspci -k
lsusb
```

Depending on if it's usb or pci card.

---

### Post by flyver on 2011-01-12
No, there was no output for "rfkill list 1".

But for ```
lspci -k
``` I got this:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c) 
	Subsystem: Sony Corporation Device 902d 
	Kernel driver in use: agpgart-intel 
	Kernel modules: intel-agp 
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) 
	Subsystem: Sony Corporation Device 902d 
	Kernel driver in use: i915 
	Kernel modules: i915 
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) 
	Subsystem: Sony Corporation Device 902d 
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) 
	Subsystem: Sony Corporation Device 902d 
	Kernel driver in use: uhci_hcd 
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) 
	Subsystem: Sony Corporation Device 902d 
	Kernel driver in use: uhci_hcd 
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) 
	Subsystem: Sony Corporation Device 902d 
	Kernel driver in use: ehci_hcd 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03) 
	Subsystem: Sony Corporation Device 902d 
	Kernel driver in use: HDA Intel 
	Kernel modules: snd-hda-intel 
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) 
	Kernel driver in use: pcieport 
	Kernel modules: shpchp 
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) 
	Kernel driver in use: pcieport 
	Kernel modules: shpchp 
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) 
	Kernel driver in use: pcieport 
	Kernel modules: shpchp 
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) 
	Subsystem: Sony Corporation Device 902d 
	Kernel driver in use: uhci_hcd 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) 
	Subsystem: Sony Corporation Device 902d 
	Kernel driver in use: uhci_hcd 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) 
	Subsystem: Sony Corporation Device 902d 
	Kernel driver in use: uhci_hcd 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) 
	Subsystem: Sony Corporation Device 902d 
	Kernel driver in use: ehci_hcd 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) 
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03) 
	Subsystem: Sony Corporation Device 902d 
	Kernel modules: iTCO_wdt 
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) 
	Subsystem: Sony Corporation Device 902d 
	Kernel driver in use: ata_piix 
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) 
	Subsystem: Sony Corporation Device 902d 
	Kernel driver in use: ahci 
	Kernel modules: ahci 
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03) 
	Subsystem: Sony Corporation Device 902d 
	Kernel modules: i2c-i801 
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15) 
	Subsystem: Sony Corporation Device 902d 
	Kernel driver in use: sky2 
	Kernel modules: sky2 
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02) 
	Subsystem: Intel Corporation Device 1050 
	Kernel driver in use: iwl3945 
	Kernel modules: iwl3945 
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller 
	Subsystem: Sony Corporation Device 902d 
	Kernel driver in use: yenta_cardbus 
	Kernel modules: yenta_socket 
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller 
	Subsystem: Sony Corporation Device 902d 
	Kernel driver in use: firewire_ohci 
	Kernel modules: firewire-ohci, ohci1394 
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) 
	Subsystem: Sony Corporation Device 902d 
	Kernel driver in use: tifm_7xx1 
	Kernel modules: tifm_7xx1 
```

and for ```
lsusb
``` I got this:

```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 003: ID 046d:c50e Logitech, Inc. Cordless Mouse Receiver 
Bus 006 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by amsterdamharu on 2011-01-13
If you try the following commands does it come back on?
```
sudo rmmod iwl3945
sudo modprobe iwl3945
```

To execute the commands you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in &#91;code] &#91;/code] tags.

I found this bit where someone suggests making a script that is called on sleep and awake to this for you but if the above commands don't help there is no point in trying the script:
[http://ubuntuforums.org/archive/index.php/t-1313614.html](http://ubuntuforums.org/archive/index.php/t-1313614.html)

sudo nano /etc/pm/sleep.d/11_iwl3945

Then paste this text...

```
 #!/bin/sh

case "$1" in
    hibernate|suspend)
        rmmod iwl3945
        sleep 0
        ;;
    thaw|resume)
        modprobe iwl3945
        ;;
    *) exit $NA
        ;;
esac
```

Then click Ctrl-X, Y, and Enter.

Then reboot.

---

### Post by flyver on 2011-01-13
Hi, with those commands I wasn't able to turn it back on. I got this message after having typed "sudo modprobe iwl3945":
```
WARNING: All config files need .conf: /etc/modprobe.d/iwl3945, it will be ignored in a future release.
```

I somewhere, somehow made a script (well not me, I just followed the suggestions of someone else) in order to force the wireless (which is controlled by the power management or something?) to restart AFTER a whole bunch of other system restarts occur simultaneously after suspend... I somehow thought this would be the heart of the problem, but that didn't fix a thing (by the way I deleted that file afterwards).

Thanks for your suggestions and your time.

---

