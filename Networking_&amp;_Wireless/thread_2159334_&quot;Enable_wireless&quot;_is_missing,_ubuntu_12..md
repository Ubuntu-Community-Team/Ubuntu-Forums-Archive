---
title: "&quot;Enable wireless&quot; is missing, ubuntu 12.04"
date: 2013-07-02
forum: Networking &amp; Wireless
---

### Post by pretty_whistle on 2013-07-02
I'm using an ethernet cable since I cant get the wireless to work.

The only thing it shows is "Enable networking".

I dont know how to fix this.

Thanks for any help :-)

---

### Post by Peptid on 2013-07-02
Hi,
Have you checked your wireless driver is installed?

---

### Post by pretty_whistle on 2013-07-02
No.
How do I do that anyway?

---

### Post by Peptid on 2013-07-02
You can go to 'additional drivers' from dashboard. I remember that you need to activate it through there.

---

### Post by pretty_whistle on 2013-07-02
It says "no proprietary drivers are in use on this system."

---

### Post by Peptid on 2013-07-02
hmm...

sudo apt-get install bcmwl-kernel-source

after this command, you should see drivers are available at 'additional drivers'. 

also you may want to check installed drivers, afaik, with `lswh` command.

---

### Post by pretty_whistle on 2013-07-02
> **Peptid said:**
> hmm...

sudo apt-get install bcmwl-kernel-source

after this command, you should see drivers are available at 'additional drivers'. 

also you may want to check installed drivers, afaik, with `lswh` command.

I got the same message.

lswh?  I will have to look that up since I dont know how.

---

### Post by ajgreeny on 2013-07-02
```
sudo apt-get install bcmwl-kernel-source
``` That will only help with a broadcom wireless adapter, and not even all of those!

We need to know what wireless chip your adapter contains in order to help you more, so let's see the output of ```
lspci
``` in terminal and then for more detail ```
sudo lshw -c network
```

---

### Post by grahammechanical on 2013-07-02
Do you actually have a wireless adapter in that machine? Perhaps it is a laptop with a keyboard combination that switches the wireless adapter off to safe battery power. Perhaps you are running Windows and have used Windows to switch off the wireless adapter. That will stop it being recongized in Ubuntu because Ubuntu cannot detect a wireless adapter that is not working.

Run

```
rfkill list
```

if the result is 

> 0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Then the issue may be a driver problem but if it is Soft blocked: yes then that means that the wireless adapter is switched off by software. But if it says Hard blocked: yes then that means that the wireless adapter is switch off by a hardware switch such as a keyboard combination.

Try this

```
rfkill unblock wifi
```

Regards.

---

### Post by varunendra on 2013-07-03
> **ajgreeny said:**
> ...We need to know what wireless chip your adapter contains in order to help you more, so let's see the output of ```
lspci
``` in terminal
..to be more precise -
```
lspci -nn
```
which will also give the chip ID, which determines exactly which driver is needed.

Sometimes, despite being internal, the wifi card can be attached to a USB bus. In that case, the above will not show the card and instead we'll need to see -
```
lsusb
```

Of course this will be needed only if what grahammechanical suggested does not solve the problem. :)

---

### Post by Irihapeti on 2013-07-03
*Thread moved to **Networking & Wireless**.*

---

### Post by pretty_whistle on 2013-07-03
> **varunendra said:**
> ..to be more precise -
```
lspci -nn
```
which will also give the chip ID, which determines exactly which driver is needed.

Sometimes, despite being internal, the wifi card can be attached to a USB bus. In that case, the above will not show the card and instead we'll need to see -
```
lsusb
```

Of course this will be needed only if what grahammechanical suggested does not solve the problem. :)

Here is the output of [COLOR=#000000][FONT=Ubuntu Mono]lspci -nn
[/FONT][/COLOR]
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation Panther Point MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation Panther Point High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.2 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 3 [8086:1e14] (rev c4)
00:1c.3 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 4 [8086:1e16] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation Panther Point LPC Controller [8086:1e5d] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Panther Point SMBus Controller [8086:1e22] (rev 04)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)
02:00.0 Network controller [0280]: Ralink corp. Device [1814:3290]
02:00.1 Bluetooth [0d11]: Ralink corp. Device [1814:3298]
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5229] (rev 01)

------------------------------------
I dont know what to do with this output though.

And here's the output of [COLOR=#000000][FONT=Ubuntu Mono]lsusb

[/FONT][/COLOR]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 064e:e263 Suyin Corp.

---

### Post by varunendra on 2013-07-03
> **pretty_whistle said:**
> ```
02:00.0 **Network controller [0280]: Ralink corp. Device** **[1814:[COLOR="#FF0000"]3290[/COLOR]]**
```
Hmm.. quite a new device it is. Please download the proprietary driver (**RT3290 PCIe**) from here : [http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501](http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501)

Install this driver as follows :
[INDENT]**1)** Copy the downloaded file (_2012_0508_RT3290_Linux_STA_v2.6.0.0.tar.bz2) to your Ubuntu desktop.

**2)** Right-click the file > Extract here. This will extract a folder "**DPO_RT3290_LinuxSTA_V2600_20120508**" from the archive.

**3)** Open the file "config.mk" located in the "os/linux" folder in the extracted directory, and change line #31 from "HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=**[COLOR="#FF0000"]n[/COLOR]**" to "HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=**[COLOR="#FF0000"]y[/COLOR]**". Save and close the file.

**4)** Now open a terminal (shortcut - Ctrl+Alt+T), and run the following commands in it -
```
cd ~/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508
make
sudo make install
```
[/INDENT]
Watch out for errors, and post back if there are any, especially during the "make" process. Exactly one error in the last (regarding "tftpboot") is normal and can be safely ignored. Post back the exact error message(s) if there are more.

You may have to reboot or do -
```
sudo modprobe -v rt3290sta
```..after this to activate the wireless (it will automatically work since next boot).

Let us all know how it goes :).

---

### Post by pretty_whistle on 2013-07-03
> **varunendra said:**
> Hmm.. quite a new device it is. Please download the proprietary driver (**RT3290 PCIe**) from here : [http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501](http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501)

Install this driver as follows :[INDENT]**1)** Copy the downloaded file (_2012_0508_RT3290_Linux_STA_v2.6.0.0.tar.bz2) to your Ubuntu desktop.

**2)** Right-click the file > Extract here. This will extract a folder "**DPO_RT3290_LinuxSTA_V2600_20120508**" from the archive.

**3)** Open the file "config.mk" located in the "os/linux" folder in the extracted directory, and change line #31 from "HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=**[COLOR=#FF0000]n[/COLOR]**" to "HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=**[COLOR=#FF0000]y[/COLOR]**". Save and close the file.

**4)** Now open a terminal (shortcut - Ctrl+Alt+T), and run the following commands in it -
```
cd ~/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508
make
sudo make install
```
[/INDENT]
Watch out for errors, and post back if there are any, especially during the "make" process. Exactly one error in the last (regarding "tftpboot") is normal and can be safely ignored. Post back the exact error message(s) if there are more.

You may have to reboot or do -
```
sudo modprobe -v rt3290sta
```..after this to activate the wireless (it will automatically work since next boot).

Let us all know how it goes :).

Hey!!  This worked!!! :D  :D

Can I delete the folder to it from my desktop?

---

### Post by varunendra on 2013-07-03
> **pretty_whistle said:**
> Hey!!  This worked!!! :D  :D
Great !! :D

> Can I delete the folder to it from my desktop?
Sure you can, but keep the downloaded file handy.

The downside of this fix is that you'll have to re-compile and re-install the driver everytime when the kernel is upgraded (make > make install). Let's hope the support for this chip gets included in the native driver soon (so you don't have to rely on the proprietary driver).

If things seem to be working nicely, please consider marking the thread as [Solved]. Thanks! :)

---

