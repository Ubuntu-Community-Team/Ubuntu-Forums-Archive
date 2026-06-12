---
title: "Bigfoot Networks (Qualcomm Atheros) Killer Xeno Pro"
date: 2013-05-05
forum: Networking &amp; Wireless
---

### Post by PadreAdamo on 2013-05-05
[COLOR=#000000]I have the Killer Xeno Pro. The E2100 might be the other name for this. I have been completely unable to get this card working including using the E2200 fix on this forum as well. Any help, would be greatly appreciated for this new Linux user.

Cheers,
Padre

[/COLOR][HR][/HR][COLOR=#000000]
0a:00.0 Power PC [0b20]: Freescale Semiconductor Inc Device [1957:00b6] (rev 12)[/COLOR]
[COLOR=#000000]Subsystem: Bigfoot Networks, Inc. Device [1a56:1101][/COLOR]
[COLOR=#000000]Flags: bus master, fast devsel, latency 0, IRQ 255[/COLOR]
[COLOR=#000000]Memory at f2c00000 (32-bit, non-prefetchable) [size=1M][/COLOR]
[COLOR=#000000]Memory at f2dff000 (32-bit, non-prefetchable) [size=4K][/COLOR]
[COLOR=#000000]Memory at f1000000 (64-bit, prefetchable) [size=16M][/COLOR]
[COLOR=#000000]Memory at f2df8000 (64-bit, non-prefetchable) [size=16K][/COLOR]
[COLOR=#000000]Capabilities: <access denied>[/COLOR]

---

### Post by chili555 on 2013-05-05
I have done a lot of digging including downloading and extracting the LAN driver at Killer's site for your network card. Here is a snip from the .inf file with some highlighting:
> [BFOOT]
; DisplayName Section DeviceId
; ----------- ------- --------
;%Xeno831x.DRVDESC%=Xeno831x_Inst, PCI\VEN_1957&DEV_00B4&SUBSYS_11011A56
%Xeno831x.DRVDESC%=Xeno831x_Inst, PCI\VEN_1957&DEV_00B4 ;MPC8315E
%Xeno831x.DRVDESC%=Xeno831x_Inst, PCI\VEN_1957&DEV_00B5 ;MPC8315
%Xeno831x.DRVDESC%=Xeno831x_Inst, PCI\VEN_[COLOR="#FF0000"]1957[/COLOR]&DEV_[COLOR="#FF0000"]00B6[/COLOR] ;MPC8314E
%Xeno831x.DRVDESC%=Xeno831x_Inst, PCI\VEN_1957&DEV_00B7 ;MPC8314
%Xeno831x.DRVDESC%=Xeno831x_Inst, PCI\VEN_1957&DEV_C006 ;MPC8308
The name of the .inf file is XenoXP.inf.

I have Googled your pci.id and the others listed in the .inf file; 1957:00B4 for example, and found nothing. I am fairly confident this isn't an alx device and isn't an Atheros. I can find no Linux driver for any of these devices to adapt. Frankly, and I hate to say this ever, I have no further suggestions.

---

### Post by PadreAdamo on 2013-05-05
Wow! Thank you SOOO much for your reply and the time that you spent. That's amazing; thank you. I found the thread for the E2200 solution but unfortunately that one does not work for this card. It's very odd.

Thank you,
-Padre

---

### Post by chili555 on 2013-05-05
The E2200 in the other thread is a different chipset altogether. The driver discussed there, *alx*, is simply wrong for your device.

---

### Post by sauyon on 2013-05-05
Ok, I did some more digging, and it appears that the e2100 is based on the intel X79 chipset - [http://www.qualcomm.com/media/releases/2011/11/30/qualcomm-atheros-announces-availability-killer-e2100-game-networking](http://www.qualcomm.com/media/releases/2011/11/30/qualcomm-atheros-announces-availability-killer-e2100-game-networking).The X79 is an express chipset, and according to [http://lwn.net/Articles/278016/](http://lwn.net/Articles/278016/), you therefore want the e1000e drivers - [http://sourceforge.net/projects/e1000/files/e1000e%20stable/](http://sourceforge.net/projects/e1000/files/e1000e%20stable/).Since these should be pre-installed in your kernel, try a```
sudo modprobe e1000e
```and see if it works - check the output of```
dmesg | grep e1000e
```

---

### Post by chili555 on 2013-05-05
Please compare the aliases above to e1000e:> $ modinfo e1000e
filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/net/ethernet/intel/e1000e/e1000e.ko
version:        2.3.2-NAPI
license:        GPL
description:    Intel(R) PRO/1000 Network Driver
author:         Intel Corporation, <linux.nics@intel.com>
srcversion:     281F7CB2F8EDEC01E32F57F
alias:          pci:v00008086d00001559sv*sd*bc*sc*i*
alias:          pci:v00008086d0000155Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000153Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000153Asv*sd*bc*sc*i*
alias:          pci:v00008086d00001503sv*sd*bc*sc*i*
alias:          pci:v00008086d00001502sv*sd*bc*sc*i*
alias:          pci:v00008086d000010F0sv*sd*bc*sc*i*
alias:          pci:v00008086d000010EFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010EBsv*sd*bc*sc*i*
alias:          pci:v00008086d000010EAsv*sd*bc*sc*i*
alias:          pci:v00008086d00001525sv*sd*bc*sc*i*
alias:          pci:v00008086d000010DFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010DEsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CEsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CDsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CCsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CBsv*sd*bc*sc*i*
alias:          pci:v00008086d000010F5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010E5sv*sd*bc*sc*i*
alias:          pci:v00008086d0000294Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010BDsv*sd*bc*sc*i*
alias:          pci:v00008086d000010C3sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C2sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C0sv*sd*bc*sc*i*
alias:          pci:v00008086d00001501sv*sd*bc*sc*i*
alias:          pci:v00008086d00001049sv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Asv*sd*bc*sc*i*
alias:          pci:v00008086d000010C4sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C5sv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010BBsv*sd*bc*sc*i*
alias:          pci:v00008086d00001098sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BAsv*sd*bc*sc*i*
alias:          pci:v00008086d00001096sv*sd*bc*sc*i*
alias:          pci:v00008086d0000150Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010F6sv*sd*bc*sc*i*
alias:          pci:v00008086d000010D3sv*sd*bc*sc*i*
alias:          pci:v00008086d0000109Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000108Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000108Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Dsv*sd*bc*sc*i*
alias:          pci:v00008086d000010B9sv*sd*bc*sc*i*
alias:          pci:v00008086d000010D5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010DAsv*sd*bc*sc*i*
alias:          pci:v00008086d000010D9sv*sd*bc*sc*i*
alias:          pci:v00008086d00001060sv*sd*bc*sc*i*
alias:          pci:v00008086d000010A5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BCsv*sd*bc*sc*i*
alias:          pci:v00008086d000010A4sv*sd*bc*sc*i*
alias:          pci:v00008086d0000105Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000105Esv*sd*bc*sc*i*
Every, every and every one of them are 8086:something. This device is:> Freescale Semiconductor Inc Device [[COLOR="#FF0000"]1957:00b6[/COLOR]] (rev 12)In short, e1000e won't work.

---

### Post by PadreAdamo on 2013-05-06
Unfortunately there was no output for the modprobe command. I did get an output with dmesg | grep e1000e.

I'm currently using my onboard NIC though.
```

dmesg | grep e1000e
[    2.546813] e1000e: Intel(R) PRO/1000 Network Driver - 2.0.0-k
[    2.546815] e1000e: Copyright(c) 1999 - 2012 Intel Corporation.
[    2.546867] e1000e 0000:02:00.0: >Disabling ASPM L0s 
[    2.546968] e1000e 0000:02:00.0: >Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    2.547020] e1000e 0000:02:00.0: >irq 97 for MSI/MSI-X
[    2.651456] e1000e 0000:02:00.0: >eth0: (PCI Express:2.5GT/s:Width x1) 14:da:e9:43:34:43
[    2.651458] e1000e 0000:02:00.0: >eth0: Intel(R) PRO/1000 Network Connection
[    2.651538] e1000e 0000:02:00.0: >eth0: MAC: 4, PHY: 8, PBA No: FFFFFF-0FF
[   15.159571] e1000e 0000:02:00.0: >irq 97 for MSI/MSI-X
[   15.260511] e1000e 0000:02:00.0: >irq 97 for MSI/MSI-X
[   20.440210] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[ 1228.111039] e1000e 0000:02:00.0: >Disabling ASPM L0s 
[ 1228.111218] e1000e 0000:02:00.0: >irq 90 for MSI/MSI-X
[ 1238.492276] e1000e 0000:02:00.0: >irq 81 for MSI/MSI-X
[ 1238.593374] e1000e 0000:02:00.0: >irq 81 for MSI/MSI-X
[ 1241.785184] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[ 2269.909060] e1000e 0000:02:00.0: >Disabling ASPM L0s 
[ 2269.909226] e1000e 0000:02:00.0: >irq 97 for MSI/MSI-X
[ 2280.397771] e1000e 0000:02:00.0: >irq 97 for MSI/MSI-X
[ 2280.498869] e1000e 0000:02:00.0: >irq 97 for MSI/MSI-X
[ 2283.057273] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx

```

---

### Post by sauyon on 2013-05-08
PadreAdamo, is your ethernet working? it looks like it should be, judging from your dmesg output. I wouldn't really know though, I guess. (modprobe shouldn't have an output, I believe [my linux box is kind of dead right now :/])

Yeah, I do understand that e1000e wouldn't support by default the Xeno pro, but I would assume that it would be the closest that we can currently get to the correct drivers simply because it does state that the chip is based on Intel's X79 express chipset.

---

### Post by PadreAdamo on 2013-05-11
My onboard is working. I cannot get the Killer Xeno Pro working at all.

---

### Post by sauyon on 2013-05-11
Is there a specific reason that you want your Xeno to be working? I doubt that you would see any difference in internet connectivity from any other NIC.chili555, could there be any adverse effects if he added the card to the driver lists that couldn't be dealt with easily?

---

### Post by PadreAdamo on 2013-05-12
> **sauyon said:**
> Is there a specific reason that you want your Xeno to be working? I doubt that you would see any difference in internet connectivity from any other NIC.chili555, could there be any adverse effects if he added the card to the driver lists that couldn't be dealt with easily?

I have a previous (windows) configuration that utilized both of my cards. My goal is to get back to that. There's a number of reasons.

---

### Post by chili555 on 2013-05-12
At the present time, there is no way I am aware of, nor, apparently Google is aware of, to get this card working. I suggest you Google the device ID from time to time to see if there are any new developments.> Freescale Semiconductor Inc Device [[COLOR="#FF0000"]1957:00b6[/COLOR]] I am sorry I can't be of further help.

---

### Post by PadreAdamo on 2013-05-12
Thank you so much for taking the time to help me with this! Anyone else have any ideas?

---

### Post by sauyon on 2013-05-12
Well, you could always try adding the device to e1000e and seeing how well it works. :/

---

### Post by PadreAdamo on 2013-05-16
> **sauyon said:**
> Well, you could always try adding the device to e1000e and seeing how well it works. :/

How would I go about doing this? Sorry, I'm a linux newbie for the most part but I do not mind getting under the hood.

---

### Post by sauyon on 2013-05-16
> **PadreAdamo said:**
> How would I go about doing this? Sorry, I'm a linux newbie for the most part but I do not mind getting under the hood.

Go through the source and see if you can find the place where it lists the devices and try adding the id of your card to the list - keep in mind that there may be multiple lists and that you may need to edit some of the code to make sure that switch/cases or ifs are handled correctly.

---

### Post by PadreAdamo on 2013-05-24
Unfortunately I don't really know what I'm doing. I am going to have to wait until a solution becomes available to me. I don't suspect that will be anytime soon though!

---

