---
title: "WL110 Not Working"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by johndoe32102002 on 2010-02-04
I have a Compaq WL110, and it is being detected as a Texas Instruments PCI1410 PC Card Bus Controller.

It does not detect any wireless networks in Ubuntu 9.10.

Here is the lsmod | grep orinoco
orinoco_cs             13312  1 
orinoco                63600  1 orinoco_cs
pcmcia                 36808  1 orinoco_cs
pcmcia_core            36528  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic

Any help in getting this card working in Ubuntu 9.10 would be great.

---

### Post by johndoe32102002 on 2010-02-07
More Details: (ignore 2200bg, that works fine)

lspci | grep -i network

01:07.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

lspci

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
01:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
01:07.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by johndoe32102002 on 2010-02-07
More information from dmesg (10 seconds after plugging in the card):

[ 4495.384074] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
[ 4495.384094] pcmcia_socket pcmcia_socket0: cs: memory probe 0xffb00000-0xffbfffff: excluding 0xffb00000-0xffb0ffff 0xffbf0000-0xffbfffff
[ 4495.393715] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
[ 4495.462186] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[ 4495.478652] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[ 4495.559630] eth2: Hardware identity 0001:0001:0004:0002
[ 4495.559731] eth2: Station identity  001f:0001:0006:0010
[ 4495.559735] eth2: Firmware determined as Lucent/Agere 6.16
[ 4495.560733] orinoco_cs 0.0: firmware: requesting agere_sta_fw.bin
[ 4495.563963] eth2: Attempting to download firmware agere_sta_fw.bin
[ 4495.563985] hermes_dld: AUX enable returned 0
[ 4495.564869] hermes_dld: AUX disable returned 0
[ 4495.564872] hermes_dld: Actual PDA length 998, Max allowed 1000
[ 4495.564875] eth2: Read PDA returned 0
[ 4495.564879] orinoco_cs 0.0: firmware: requesting agere_sta_fw.bin
[ 4495.570841] eth2: Cannot find firmware agere_sta_fw.bin
[ 4495.570903] eth2: Hardware identity 0001:0001:0004:0002
[ 4495.571003] eth2: Station identity  001f:0001:0006:0010
[ 4495.571007] eth2: Firmware determined as Lucent/Agere 6.16
[ 4495.571010] eth2: Ad-hoc demo mode supported
[ 4495.571013] eth2: IEEE standard IBSS ad-hoc mode supported
[ 4495.571016] eth2: WEP supported, 104-bit key
[ 4495.571097] eth2: MAC address XX:XX:XX:XX:XX:XX
[ 4495.571188] eth2: Station name "HERMES I"
[ 4495.571722] eth2: ready
[ 4495.572795] eth2: orinoco_cs at 0.0, irq 4, io 0xc100-0xc13f
[ 4495.604861] ADDRCONF(NETDEV_UP): eth2: link is not ready
[ 4495.614079] eth2: New link status: Disconnected (0002)
[ 4495.640005] hermes @ 0001c100: Timeout waiting for command 0x0002 completion.
[ 4495.640005] eth2: Unable to disable port while reconfiguring card
[ 4495.640005] eth2: Resetting instead...
[ 4496.144524] eth2: Attempting to download firmware agere_sta_fw.bin
[ 4496.144542] hermes_dld: AUX enable returned 0
[ 4496.145246] hermes_dld: AUX disable returned 0
[ 4496.145249] hermes_dld: Actual PDA length 998, Max allowed 1000
[ 4496.145252] eth2: Read PDA returned 0
[ 4496.145258] orinoco_cs 0.0: firmware: requesting agere_sta_fw.bin
[ 4496.150362] eth2: Cannot find firmware agere_sta_fw.bin
[ 4496.150369] eth2: orinoco_reset: Error -2 re-initializing firmware
[ 4496.150374] eth2: Device has been disabled!
[ 5391.957997] ipw2200: Firmware error detected.  Restarting.
[ 5480.872611] pcmcia_socket pcmcia_socket0: pccard: card ejected from slot 0
[ 5515.536061] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
[ 5515.536364] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
[ 5515.622153] eth2: Hardware identity 0001:0001:0004:0002
[ 5515.622261] eth2: Station identity  001f:0001:0006:0010
[ 5515.622271] eth2: Firmware determined as Lucent/Agere 6.16
[ 5515.623364] orinoco_cs 0.0: firmware: requesting agere_sta_fw.bin
[ 5515.626258] eth2: Attempting to download firmware agere_sta_fw.bin
[ 5515.626280] hermes_dld: AUX enable returned 0
[ 5515.627140] hermes_dld: AUX disable returned 0
[ 5515.627143] hermes_dld: Actual PDA length 998, Max allowed 1000
[ 5515.627146] eth2: Read PDA returned 0
[ 5515.627150] orinoco_cs 0.0: firmware: requesting agere_sta_fw.bin
[ 5515.638485] eth2: Cannot find firmware agere_sta_fw.bin
[ 5515.638547] eth2: Hardware identity 0001:0001:0004:0002
[ 5515.638647] eth2: Station identity  001f:0001:0006:0010
[ 5515.638651] eth2: Firmware determined as Lucent/Agere 6.16
[ 5515.638654] eth2: Ad-hoc demo mode supported
[ 5515.638657] eth2: IEEE standard IBSS ad-hoc mode supported
[ 5515.638659] eth2: WEP supported, 104-bit key
[ 5515.638740] eth2: MAC address XX:XX:XX:XX:XX:XX
[ 5515.638832] eth2: Station name "HERMES I"
[ 5515.639365] eth2: ready
[ 5515.640415] eth2: orinoco_cs at 0.0, irq 4, io 0xc100-0xc13f
[ 5515.659388] ADDRCONF(NETDEV_UP): eth2: link is not ready
[ 5515.671712] eth2: New link status: Disconnected (0002)

---

### Post by johndoe32102002 on 2010-02-07
More Details:

Input: cd /lib/firmware && ls agere*
Output: ls: cannot access agere*: No such file or directory

Input: System -> Administration -> Hardware Drivers
Output: No proprietary drivers are in use on this system (none listed either)

---

### Post by johndoe32102002 on 2010-02-07
Advice from ZykoticK9:

Take from [http://www.linuxforums.org/forum/peripherals-hardware/131767-help-elderly-newbie-wifi.html](http://www.linuxforums.org/forum/peripherals-hardware/131767-help-elderly-newbie-wifi.html)

You needed the Agere firmware, so download it from here:

[http://marc.info/?l=orinoco-devel&m=121078835610877&q=p3](http://marc.info/?l=orinoco-devel&m=121078835610877&q=p3)

Unpack it and rename the orinoco.fw file to "agere_sta_fw.bin". Then copy it into the /lib/firmware folder.

---

### Post by johndoe32102002 on 2010-02-07
Results:

The second light on the Compaq WL110 works, and it can now detect wireless networks.  It first crashed the Ubuntu network-manager, but after unplugging, logging off, re-logging in, and plugging back in, the card worked fine for detecting ad-hoc networks (not regular for some reason).

Attached is the orinoco driver in use:
orinoco.fw.tar.bz2

---

