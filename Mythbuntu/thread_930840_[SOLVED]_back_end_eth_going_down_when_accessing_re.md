---
title: "[SOLVED] back end eth going down when accessing recordings from remote front end"
date: 2008-09-26
forum: Mythbuntu
---

### Post by mark467 on 2008-09-26
when i go into my recordings menu to pick something to watch from my remote front end the nic on my backend goes down and gets some errors. it only happens on the recordings menu i can watch recordings once i get one picked finally, also dvd rips work fine. the backend/frontend works fine by itself. if i access the recorded programs list from mythweb from any pc the same happens. i had a ping from the remote go for 2 days no drops or network resets. any ideas or sugestions? the following is what i see in dmsg after a lock up

[46900.656709] eth0: txs packet size do not coinsist with txd txd_:0x0000ee93, txs_:0x000105ea!
[46900.656718] txd read ptr: 0x86c
[46900.656720] txs-behind:0x800105ea
[46900.656722] txs-before:0x000105ea
[46900.656725] eth0: txs packet size do not coinsist with txd txd_:0x5b64042a, txs_:0x000105ea!
[46900.656728] txd read ptr: 0xf04
[46900.656730] txs-behind:0x8001024d
[46900.656732] txs-before:0x000105ea
[46900.656735] eth0: txs packet size do not coinsist with txd txd_:0x2e2e4440, txs_:0x0001024d!
[46900.656738] txd read ptr: 0x1334
[46900.656740] txs-behind:0x000105ea
[46900.656742] txs-before:0x000105ea
[46900.657114] eth0: txs packet size do not coinsist with txd txd_:0x0e2223e1, txs_:0x000105ea!
[46900.657119] txd read ptr: 0x1778
[46900.657121] txs-behind:0x800105ea
[46900.657124] txs-before:0x0001024d
[46900.657127] eth0: txs packet size do not coinsist with txd txd_:0xb053a574, txs_:0x000105ea!
[46900.657131] txd read ptr: 0x1b60
[46900.657133] txs-behind:0x800105ea
[46900.657136] txs-before:0x000105ea
[46900.657139] eth0: txs packet size do not coinsist with txd txd_:0x674acb29, txs_:0x000105ea!
[46900.657143] txd read ptr: 0xd8
[46900.657146] txs-behind:0x000105ea
[46900.657148] txs-before:0x000105ea
[46900.657930] eth0: txs packet size do not coinsist with txd txd_:0x91088a28, txs_:0x000105ea!
[46900.657934] txd read ptr: 0x408
[46900.657936] txs-behind:0x800105ea
[46900.657938] txs-before:0x000105ea
[46900.657941] eth0: txs packet size do not coinsist with txd txd_:0xc5fdfef2, txs_:0x000105ea!
[46900.657944] txd read ptr: 0x634
[46900.657946] txs-behind:0x800105ea
[46900.657948] txs-before:0x000105ea
[46900.657951] eth0: txs packet size do not coinsist with txd txd_:0x8fe3a3eb, txs_:0x000105ea!
[46900.657954] txd read ptr: 0xd2c
[46900.657956] txs-behind:0x000105ea
[46900.657958] txs-before:0x000105ea
[46900.658337] eth0: txs packet size do not coinsist with txd txd_:0x18105ec0, txs_:0x000105ea!
[46900.658342] txd read ptr: 0x111c
[46900.658344] txs-behind:0x0001015b
[46900.658347] txs-before:0x000105ea
[46900.658746] eth0: txs packet size do not coinsist with txd txd_:0xdbb5badd, txs_:0x000105ea!
[46900.658750] txd read ptr: 0x17e0
[46900.658752] txs-behind:0x80010106
[46900.658754] txs-before:0x000105ea
[46900.658756] eth0: txs packet size do not coinsist with txd txd_:0x75756561, txs_:0x00010106!
[46900.658759] txd read ptr: 0x1ac4
[46900.658761] txs-behind:0x000105ea
[46900.658763] txs-before:0x000105ea
[46900.704145] eth0: txs packet size do not coinsist with txd txd_:0x1688d6e4, txs_:0x000105ea!
[46900.704152] txd read ptr: 0x2c
[46900.704154] txs-behind:0x000105ea
[46900.704156] txs-before:0x00010106
[46900.704547] eth0: txs packet size do not coinsist with txd txd_:0xd422017f, txs_:0x000105ea!
[46900.704551] txd read ptr: 0x714
[46900.704553] txs-behind:0x800105ea
[46900.704555] txs-before:0x000105ea
[46900.704558] eth0: txs packet size do not coinsist with txd txd_:0x6f430a0d, txs_:0x000105ea!
[46900.704561] txd read ptr: 0x898
[46900.704563] txs-behind:0x800105ea
[46900.704565] txs-before:0x000105ea
[46900.704567] eth0: txs packet size do not coinsist with txd txd_:0xa2135902, txs_:0x000105ea!
[46900.704570] txd read ptr: 0xaac
[46900.704572] txs-behind:0x000105ea
[46900.704574] txs-before:0x000105ea
[46900.704954] eth0: txs packet size do not coinsist with txd txd_:0xd5a7669d, txs_:0x000105ea!
[46900.704958] txd read ptr: 0xbb4
[46900.704960] txs-behind:0x800105ea
[46900.704962] txs-before:0x000105ea
[46900.704965] eth0: txs packet size do not coinsist with txd txd_:0xfd0e7e18, txs_:0x000105ea!
[46900.704968] txd read ptr: 0x1258
[46900.704970] txs-behind:0x000105ea
[46900.704972] txs-before:0x000105ea
[46900.705365] eth0: txs packet size do not coinsist with txd txd_:0x09edee98, txs_:0x000105ea!
[46900.705369] txd read ptr: 0x1874
[46900.705371] txs-behind:0x800105ea
[46900.705373] txs-before:0x000105ea
[46900.705376] eth0: txs packet size do not coinsist with txd txd_:0x5000b401, txs_:0x000105ea!
[46900.705379] txd read ptr: 0x1f10
[46900.705380] txs-behind:0x000105ea
[46900.705382] txs-before:0x000105ea
[46900.705772] eth0: txs packet size do not coinsist with txd txd_:0xdefb7fa0, txs_:0x000105ea!
[46900.705776] txd read ptr: 0x318
[46900.705778] txs-behind:0x800105ea
[46900.705780] txs-before:0x000105ea
[46900.705783] eth0: txs packet size do not coinsist with txd txd_:0x4e563f32, txs_:0x000105ea!
[46900.705786] txd read ptr: 0xabc
[46900.705787] txs-behind:0x000105ea
[46900.705789] txs-before:0x000105ea
[46900.706182] eth0: txs packet size do not coinsist with txd txd_:0xde61eb76, txs_:0x000105ea!
[46900.706186] txd read ptr: 0x11f4
[46900.706188] txs-behind:0x800104d3
[46900.706190] txs-before:0x000105ea
[46900.706192] eth0: txs packet size do not coinsist with txd txd_:0xd5a0c481, txs_:0x000104d3!
[46900.706195] txd read ptr: 0x1570
[46900.706197] txs-behind:0x000105ea
[46900.706199] txs-before:0x000105ea
[46900.759044] eth0: txs packet size do not coinsist with txd txd_:0x7a7b22b9, txs_:0x000105ea!
[46900.759051] txd read ptr: 0x19f8
[46900.759053] txs-behind:0x000105ea
[46900.759055] txs-before:0x000104d3
[46900.759446] eth0: txs packet size do not coinsist with txd txd_:0xa8c0bc2f, txs_:0x000105ea!
[46900.759450] txd read ptr: 0x1cb8
[46900.759452] txs-behind:0x000105ea
[46900.759454] txs-before:0x000105ea
[46900.759855] eth0: txs packet size do not coinsist with txd txd_:0xd8eb6a67, txs_:0x000105ea!
[46900.759858] txd read ptr: 0xec
[46900.759860] txs-behind:0x000105ea
[46900.759862] txs-before:0x000105ea
[46909.662361] NETDEV WATCHDOG: eth0: transmit timed out
[46911.187010] ATL2: eth0 NIC Link is Up<100 Mbps Full Duplex>

---

### Post by mark467 on 2008-09-27
anybody have any ideas as to what is causing this?

---

### Post by mark467 on 2008-10-01
how about some suggestions on where to look. It only happens on the recorded tv menu screen or in mythweb on same. it seems to have something to do with the preview images maybe. can i turn them off. any pc i access the backend from via mythweb (in windows or linux running firefox) or from the remote front end causes this. videos no problem, once i get a recording started no problem.

---

### Post by mark467 on 2008-10-03
Anyone????

---

### Post by mark467 on 2008-10-10
Ok Iswitched from onboard lan to a wireless and the problem stopped. the motherboard is an asus p5gc  Intel® 945GC / ICH7 chipset.
I want to use the wired port is this a driver issue? (autodetected)

---

### Post by mark467 on 2008-10-10
ok i did a fresh install same problem. disabled onbaord nic and put in a card works fine. any suggestions. i dont have the room to keep the xtra nic in the pc

---

### Post by mark467 on 2008-10-11
Well in case anyone else has this issue:
It turns out it is a problem with the Atheros onboard chipset for lan on the ASUS P5GC MX motherboard (the onboard audio also did not work right with Linux). I bought an Intel DG31PR to replace it and all onboard features work great.

---

