---
title: "[SOLVED] Intel HDA No Sound on Ubuntu 8.04"
date: 2008-06-15
forum: Multimedia Software
---

### Post by zincoxide1979 on 2008-06-15
Hello,

I've done a search around and can't seem to find a definitive guide on how to get my audio working on my Alienware M9700i.

I've checked all the volume controls for every device and maxxed them out.

Still nothing - so I've typed in lspci and got:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GHM (ICH7-M DH) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 PCI bridge: nVidia Corporation Unknown device 01b3 (rev a3)
02:00.0 PCI bridge: nVidia Corporation Unknown device 01b3 (rev a3)
02:01.0 PCI bridge: nVidia Corporation Unknown device 01b3 (rev a3)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8700M GT (rev a1)
04:00.0 3D controller: nVidia Corporation GeForce 8700M GT (rev a1)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
0a:07.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
0a:07.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0a:07.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
0a:07.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev ff)


Now I am a complete newbie to Ubuntu - please tell me what I need to do in plain english or if anyone has a step-by-step guide?

I've done a search on the forums and through google but everything I tried didn't work - it's back to Microsoft for me if I can't get my speakers working! - Save me from that pain!!

---

### Post by Pjotr123 on 2008-06-15
Try this:
[http://ubuntutip.googlepages.com/sound](http://ubuntutip.googlepages.com/sound)
(number 6 )

---

### Post by zincoxide1979 on 2008-06-15
I've tried that, but get this error message at the last hurdle...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules

---

### Post by prshah on 2008-06-15
> **zincoxide1979 said:**
>  how to get my audio working on my Alienware M9700i.

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)



Open a terminal (Applications-Accessories-Terminal), then give the following commands and post the output here. ```

sudo modprobe snd_hda_intel
dmesg | tail

```

---

### Post by zincoxide1979 on 2008-06-15
> **prshah said:**
> Open a terminal (Applications-Accessories-Terminal), then give the following commands and post the output here. ```

sudo modprobe snd_hda_intel
dmesg | tail

```

It doesn't do anything when I type that in terminal and hit enter - it just goes back to the prompt?

---

### Post by zincoxide1979 on 2008-06-15
sudo modprobe snd_hda_intel doesn't do anything but I get this for dmesg | tail
dmesg | tail
[   65.097716] NET: Registered protocol family 17
[   66.893626] wlan0: Initial auth_alg=0
[   66.893631] wlan0: authenticate with AP 00:19:e0:10:12:fa
[   66.895391] wlan0: RX authentication from 00:19:e0:10:12:fa (alg=0 transaction=2 status=0)
[   66.895393] wlan0: authenticated
[   66.895395] wlan0: associate with AP 00:19:e0:10:12:fa
[   66.897585] wlan0: RX AssocResp from 00:19:e0:10:12:fa (capab=0x431 status=0 aid=1)
[   66.897587] wlan0: associated
[   66.899168] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   73.343252] wlan0: no IPv6 routers present

---

### Post by prshah on 2008-06-15
> **zincoxide1979 said:**
> sudo modprobe snd_hda_intel doesn't do anything 

OK, Another request: open a terminal (Applications-Accessories-Terminal), then give the following commands and post the output here. ```

dmesg | grep -i -A 3 -B 3 "1b.0"

```

---

### Post by zincoxide1979 on 2008-06-15
This is all I get

$ dmesg | grep -i -A 3 -B 3 "1b.0"
[   37.420220] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   37.420228] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   37.420238] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   37.420264] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 19 (level, low) -> IRQ 20
[   37.420275] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   37.523465] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   37.523476] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   37.523636] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17


I have NO idea what that all means!

---

### Post by cotcot on 2008-06-15
If you upgraded from an former version to 8.04 then it might help to delete the .asound* files in your user directory. (happened 2 times by me)

---

### Post by prshah on 2008-06-16
> **zincoxide1979 said:**
> 
$ dmesg | grep -i -A 3 -B 3 "1b.0"
[   37.420220] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   37.420228] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   37.420238] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   37.420264] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 19 (level, low) -> IRQ 20
[   37.420275] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   37.523465] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   37.523476] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   37.523636] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17



I suspect (but cannot be sure) that your wireless is interfering with sound. To confirm, give the command```

sudo modprobe -r iwl4965
``` WARNING! You will lose wireless (temporary, until next boot).

After the above command, check if sound is working? If so, post back for information on how to make the change permanent _and_ keep wireless. If you get any errors, post those. Otherwise, I have no idea.

---

### Post by zincoxide1979 on 2008-06-16
I found this elsewhere and ran it

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

Success!! But now my wireless isn't working?

---

### Post by zincoxide1979 on 2008-06-16
Managed to get the wireless working - I just had to reboot 3 times for some bizarre reason. 

Anyone got any ideas on how to increase the volume, when it's up full it sounds just as normal?

---

