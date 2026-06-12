---
title: "Help with Wireless"
date: 2012-06-28
forum: Networking &amp; Wireless
---

### Post by kf7kiu on 2012-06-28
Hello. I am fairly new to Ubuntu, and have been having problems with my wireless networking. I don't know what is wrong, one day it is working and the nest it is not, But it works fine on windows. Any ideas?

---

### Post by mikewhatever on 2012-06-28
Hi, and welcome to the forums. You should start by identifying the wireless hardware, which can be done by looking at the output of the following from a terminal window:
```
lspci -nnk | grep -iA2 net
```

...to open a terminal windows, hit ctrl-alt-t.

---

### Post by kf7kiu on 2012-06-28
Okay. This is what I have. 

joshua@ubuntu:~$ lspci -nnk|grep -ia2net
1:00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
2:    Subsystem: Lenovo Device [17aa:3975]
3:    Kernel driver in use: agpgart-intel
4:00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0106] (rev 09)
5:    Subsystem: Lenovo Device [17aa:3975]
6-    Kernel driver in use: i915
7-    Kernel modules: i915
8:00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
9:    Subsystem: Lenovo Device [17aa:3975]
10-    Kernel driver in use: mei
11-    Kernel modules: mei
12:00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
13:    Subsystem: Lenovo Device [17aa:3975]
14-    Kernel driver in use: ehci_hcd
15:00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
16:    Subsystem: Lenovo Device [17aa:3975]
17:    Kernel driver in use: HDA Intel
18:    Kernel modules: snd-hda-intel
19:00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5)
20:    Kernel driver in use: pcieport
21-    Kernel modules: shpchp
22:00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b5)
23:    Kernel driver in use: pcieport
24-    Kernel modules: shpchp
25:00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
26:    Subsystem: Lenovo Device [17aa:3975]
27-    Kernel driver in use: ehci_hcd
28:00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 05)
29:    Subsystem: Lenovo Device [17aa:3975]
30:    Kernel modules: iTCO_wdt
31:00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 05)
32:    Subsystem: Lenovo Device [17aa:3975]
33-    Kernel driver in use: ahci
34-    Kernel modules: ahci
35:00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
36:    Subsystem: Lenovo Device [17aa:3975]
37-    Kernel modules: i2c-i801
38:01:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
39:    Subsystem: Lenovo Device [17aa:3979]
40:    Kernel driver in use: atl1c
41:    Kernel modules: atl1c
42:02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
43:    Subsystem: Lenovo Device [17aa:f101]
44:    Kernel driver in use: rt2800pci
45:    Kernel modules: rt2800pci

---

### Post by lz1dsb on 2012-06-28
Hmm... the output says you're using this wifi card:
Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
Just a quick search shows that there're a lot of issues under Linux with this particular model. I'm not sure if it's at all supported.

---

### Post by lz1dsb on 2012-06-28
Correction!
There's an interesting link. The author gives detailed instructions. So there are Linux drivers for this wifi card after all.
[http://soad1982.blogspot.com/](http://soad1982.blogspot.com/)

Enjoy!

---

### Post by wildmanne39 on 2012-06-28
Hi, you already have the driver you need if you are using 12.04, please do:
```
echo "options rt2800pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci 
sudo modprobe -v rt2800pci 

```
I apologize for getting involved I just did not want to see you compile a driver if you did not have too, now I turn you back over to mikewhatever who is good with wireless issues.
Thanks

---

### Post by kf7kiu on 2012-06-28
Okay. I tried doing it without compiling the driver and got this message.        tee: invalid option -- 'r'
Try `tee --help' for more information.

I then tried to compile the drive and kept getting a tar error.

---

### Post by wildmanne39 on 2012-06-28
Hi, just copy and paste the commands one at a time, you have a typo I believe.
Thanks

---

### Post by kf7kiu on 2012-06-29
Okay. i will give it a try.

---

### Post by madvinegar on 2012-06-29
Wildmane39, I think that there might be a typo in your instructions.
In the 1st line i.e.:
```
echo "options rt2800pci  nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci .conf
```

there is an unecessary space in the end: "```
/rt2800pci .conf
```" should be "```
/rt2800pci.conf
```"

Is thar right? Sorry for getting involved.

---

### Post by kf7kiu on 2012-06-29
Okay. I tried it both ways and I still get this message at the end.FATAL: Error inserting rt2800pci (/lib/modules/3.0.0-15-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

I also get tones of WARNINGS in the second and third lines.

---

### Post by madvinegar on 2012-06-29
Ok lets see dmesg...

```
dmesg | grep rt2800
```

Is it Ubuntu  12.04 you are using?

---

### Post by kf7kiu on 2012-06-29
I am running 11.10

---

### Post by wildmanne39 on 2012-06-29
Hi madvinegar, thank you I do not know how that command got the extra space because I just copied and pasted it from my file.

I fixed the command, please try again: I am sorry for the extra space.
Nice catch!!!

---

### Post by kf7kiu on 2012-07-02
I tried it, but still get the same error.

---

### Post by free1proxy on 2012-07-02
Hi, just copy and paste the commands one at a time, you have a typo I believe.
Thanks

---

### Post by kf7kiu on 2012-07-04
I tried it again, but still get the same error.

---

### Post by wildmanne39 on 2012-07-04
Hi, post the output of:
```
modinfo rt2800pci
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by kf7kiu on 2012-07-07
Okay. I tried it and then got this message. 
```
joshua@ubuntu:~$ modinfo rt2800pci
filename:       /lib/modules/3.0.0-15-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     5E384CCFE20512B386CCE30
alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*
alias:          pci:v00001814d00005390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003593sv*sd*bc*sc*i*
alias:          pci:v00001814d00003592sv*sd*bc*sc*i*
alias:          pci:v00001814d00003562sv*sd*bc*sc*i*
alias:          pci:v00001814d00003062sv*sd*bc*sc*i*
alias:          pci:v00001814d00003060sv*sd*bc*sc*i*
alias:          pci:v00001432d00007722sv*sd*bc*sc*i*
alias:          pci:v00001432d00007711sv*sd*bc*sc*i*
alias:          pci:v00001814d00003390sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001462d0000891Asv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2800lib,rt2x00pci,eeprom_93cx6
vermagic:       3.0.0-15-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)


```

It also said that I do not have output installed.

---

### Post by wildmanne39 on 2012-07-07
Hi, the way the option is activated changed with this kernel and I did not know it, try this please:
```
sudo rmmod -f rt2800pci
sudo modprobe rt2800pci nohwcrypt=Y
```
do not reboot, if this works we will need to make it permanent.
Thanks

---

### Post by kf7kiu on 2012-07-09
Okay. I tried putting in the code but got a message saying that there was no 
[FONT=monospace]rt2800pci directory.[/FONT]

---

### Post by kf7kiu on 2012-07-09
Just curious. Would installing the new version of Ubuntu help?

---

### Post by wildmanne39 on 2012-07-09
Hi, it could but the settings might still have to be tweaked.
Thanks

---

### Post by kf7kiu on 2012-07-13
Okay. The other code did not work either. It said that there was no directory.

---

### Post by hovrashko on 2012-07-13
i did manual install for my other card using this way and it worked.

---

### Post by kf7kiu on 2012-07-14
Okay. How do I do that?

---

