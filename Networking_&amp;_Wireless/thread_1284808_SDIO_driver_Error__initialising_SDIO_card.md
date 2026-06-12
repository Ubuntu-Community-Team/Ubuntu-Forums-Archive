---
title: "SDIO driver Error  initialising SDIO card"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by mahesh_val on 2009-10-07
I am trying to build the card driver for my SDIO network card, on top of the SDIO stack that comes with linux 2.6.24 . 
The host controller does not get proper a response for CMD5 sent to the device, in order to determine that it is an SDIO card. The response fails and finnaly driver is not registered .
It would be kind if anyone has similar experiences and ways out to share.here is debug log message from dmesg.
 
 
 
mmc0: clock 400000Hz busmode 1 powermode 2 cs 1 Vdd 21 width 0 timing 0
mmc0: starting CMD0 arg 00000000 flags 000000c0
mmc0: req done (CMD0): 0: 00000000 00000000 00000000 00000000
mmc0: clock 400000Hz busmode 1 powermode 2 cs 0 Vdd 21 width 0 timing 0
mmc0: starting CMD8 arg 000001aa flags 000002f5
mmc0: req done (CMD8): 0: 0df80d0d 00000000 00000000 00000000
mmc0: starting CMD5 arg 00000000 flags 000002e1
mmc0: req done (CMD5): 0: 0df80d0d 00000000 00000000 00000000
mmc0: card claims to support voltages below the defined range. These will be ignored.
mmc0: clock 400000Hz busmode 1 powermode 2 cs 0 Vdd 20 width 0 timing 0
mmc0: starting CMD5 arg 00300000 flags 000002e1
mmc0: req done (CMD5): 0: 0df80d0d 00000000 00000000 00000000
mmc0: starting CMD5 arg 00000000 flags 000002e1
mmc0: req done (CMD5): 0: 0df80d0d 00000000 00000000 00000000
mmc0: starting CMD5 arg 00000000 flags 000002e1
mmc0: req done (CMD5): 0: 0df80d0d 00000000 00000000 00000000
mmc0: starting CMD5 arg 00000000 flags 000002e1
mmc0: req done (CMD5): 0: 0df80d0d 00000000 00000000 00000000
mmc0: starting CMD5 arg 00000000 flags 000002e1
mmc0: req done (CMD5): 0: 0df80d0d 00000000 00000000 00000000
mmc0: starting CMD5 arg 00000000 flags 000002e1
mmc0: req done (CMD5): 0: 0df80d0d 00000000 00000000 00000000
mmc0: starting CMD5 arg 00000000 flags 000002e1
mmc0: req done (CMD5): 0: 0df80d0d 00000000 00000000 00000000
mmc0: starting CMD5 arg 00000000 flags 000002e1
mmc0: req done (CMD5): 0: 0df80d0d 00000000 00000000 00000000
mmc0: starting CMD5 arg 00000000 flags 000002e1
mmc0: req done (CMD5): 0: 0df80d0d 00000000 00000000 00000000
mmc0: starting CMD5 arg 00000000 flags 000002e1
mmc0: req done (CMD5): 0: 0df80d0d 00000000 00000000 00000000
mmc0: starting CMD5 arg 00000000 flags 000002e1
mmc0: req done (CMD5): 0: 0df80d0d 00000000 00000000 00000000
mmc0: starting CMD5 arg 00000000 flags 000002e1
mmc0: req done (CMD5): 0: 0df80d0d 00000000 00000000 00000000
mmc0: starting CMD5 arg 00000000 flags 000002e1
mmc0: req done (CMD5): 0: 0df80d0d 00000000 00000000 00000000
mmc0: starting CMD5 arg 00000000 flags 000002e1
mmc0: req done (CMD5): 0: 0df80d0d 00000000 00000000 00000000
mmc0: starting CMD5 arg 00000000 flags 000002e1
mmc0: req done (CMD5): 0: 0df80d0d 00000000 00000000 00000000
mmc0: starting CMD5 arg 00000000 flags 000002e1
mmc0: req done (CMD5): 0: 0df80d0d 00000000 00000000 00000000
mmc0: starting CMD5 arg 00000000 flags 000002e1
mmc0: req done (CMD5): 0: 0df80d0d 00000000 00000000 00000000
mmc0: starting CMD5 arg 00000000 flags 000002e1
mmc0: req done (CMD5): 0: 0df80d0d 00000000 00000000 00000000
mmc0: clock 0Hz busmode 1 powermode 0 cs 0 Vdd 0 width 0 timing 0
mmc0: error -145 whilst initialising SDIO card
mmc0: clock 0Hz busmode 1 powermode 0 cs 0 Vdd 0 width 0 timing 0

---

