---
title: "no sound on my pc"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by nickoli on 2007-06-11
I bought this pc brand new from [www.pcinfinity.net](www.pcinfinity.net) for a couple hundred bucks. It came with ubuntu installed. I love it so far however it won't produce any sound. It has an integrated soundchip. The motherboard stats are as fellows.
oxconn K8M890M2MA-RS2H Socket AM2/ VIA K8M890/ RAID/ A&V&L/ MATX Motherboard




Product Description:
Foxconn K8M890M2MA-RS2H Socket AM2/ VIA K8M890/ RAID/ A&V&L/ MATX Motherboard
Specificationss
Mfr Part Number: K8M890M2MA-RS2H
CPU: Socket AM2 support AMD Athlon 64/ Athlon 64 x2/ Sempron/ Athlon 64 FX processors; FSB 2000 MT/s
Chipset: VIA K8M890 & VT8237R plus
Memory: 2x 240pin DIMMs support Dual Channel DDR2-800/667 Memory; Max capacity 2GB
Slots: 1x PCI Express x16 slot; 1x PCI Express x1 slot; 2x PCI slots
IDE/SATA: 2x ATA-133 channels; 2x SATA ports support RAID 0, 1 and JBOD
Audio: Realtek 5.1 channel AC'97 Audio CODEC
Video: Integrated VIA Chrome 9 Graphics Controller
LAN: Realtek 10/100 Fast Ethernet
Ports: 8x USB 2.0 ports (4 rear, 4 by headers); 2x PS/2 ports; 1x Parallel port; 1x Serial port; 1x VGA port; 1x RJ45 LAN port; Audio I/O jack
Form Factor: Micro ATX, 9.6 x 8.8 inch
Package: Retail
RoHS Compliant

after typying lspsi it gives me this information about my audio
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
after typing aplay -l it gives me this
card 0: NVidia [HDA NVidia], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 


Please help me.
 Any help you can give to me will be greatly appreciated. Thanks

---

### Post by veerakumar on 2007-06-11
go to alsa site [http://www.alsa-project.org/](http://www.alsa-project.org/)
and check whether your audio is supported.
Then build alsa and your audio would be up.
Or configure if already have alsa installed.

---

### Post by Erlander on 2007-06-12
If you don't have the front panel audio connected then make sure the jumpers are on the motherboard to enable the rear jacks.

I spent months trying to track down no audio only to find I had left the jumpers off.

Rob

---

