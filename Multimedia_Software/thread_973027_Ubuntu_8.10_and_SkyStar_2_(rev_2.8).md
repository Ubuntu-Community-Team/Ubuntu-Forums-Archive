---
title: "Ubuntu 8.10 and SkyStar 2 (rev 2.8)"
date: 2008-11-06
forum: Multimedia Software
---

### Post by MonGol on 2008-11-06
Hey folks,

today i tried to get the skystar 2 rev 2.8 working on ubuntu 8.10. but unfortunatly it doesn't really work. it seems the firmware for the skystar 2 is loaded successfully (after i compiled an recent snapshot of video4linux using the driver from the technisat homepage):
```
[   17.044232] b2c2-flexcop: B2C2 FlexcopII/II(b)/III digital TV receiver chip loaded successfully
[   17.254211] b2c2_flexcop_pci 0000:02:03.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   17.270221] b2c2-flexcop: MAC address = 00:08:c9:a1:2d:ca
[   17.270537] b2c2-flexcop: i2c master_xfer failed
[   17.272325] b2c2-flexcop: CX24113 successfully attached
[   17.344986] b2c2-flexcop: ISL6421 successfully attached
[   17.344998] b2c2-flexcop: found 'Conexant CX24123/CX24109' .
[   17.345247] b2c2-flexcop: initialization of 'Sky2PC/SkyStar 2 DVB-S rev 2.8' at the 'PCI' bus controlled by a 'FlexCopIIb' complete
```

but when i try to scan all transponders on astra using the program scan nothing is happening:
```
scanning Astra-19.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
```
this is the only output (btw: the program doesn't exit)
and when i start kaffeine nothing happens as well. no window opens, only a process is started in the background)

any ideas how to get this card working on ubuntu 8.10?

greez,
marcel

---

