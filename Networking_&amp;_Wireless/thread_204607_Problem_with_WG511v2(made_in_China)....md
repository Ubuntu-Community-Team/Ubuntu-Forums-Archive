---
title: "Problem with WG511v2(made in China)..."
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by xaxa1982 on 2006-06-27
I have the card NETGEAR WG511v2 with chipset Marvell "made in China"... I am using the ndiswrapper for it like this:
```

sudo ndiswrapper -i WG511v2.inf
sudo ndiswrapper -l
wg511v2
driver present,hardware present
sudo modprobe ndiswrapper

```
When i press enter(at "sudo modprobe ndiswrapper") freezes my laptop. I found this site [http://www.elet.polimi.it/upload/wspinell/website/index.php?sec=20_howto/20_linux_hw&id=00_Netgear%20WG511_on_Ubuntu_6__dot_06](http://www.elet.polimi.it/upload/wspinell/website/index.php?sec=20_howto/20_linux_hw&id=00_Netgear%20WG511_on_Ubuntu_6__dot_06)

but this is for WG511v3 card. I am trying to enable my card with the instructions of this site, but the results are the same. I take this when i am writing "lspci -v":
```

0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 1faa (rev 03)
        Subsystem: Netgear: Unknown device 4e00
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 10
        Memory at 1f800000 (32-bit, non-prefetchable) [size=64K]
        Memory at 1f810000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>

```
How can i solved this problem?

Thanks!

Y.G.: Sorry for my English! :(

---

### Post by xaxa1982 on 2006-06-28
Someone help please....

---

### Post by jacksonz123z on 2006-07-18
I have the same netgear wg511v2 card with Marvell drivers running under Dapper.  Now it works well.  I did have the freeze at the modprobe line, however after the latest Dapper Updates this behavior stopped.
I see you have installed the driver,  after this I did "sudo ndiswrapper -m" I also found that I had to edit /etc/modules by adding ndiswrapper to the end of the file otherwise the wireless would not start at boot.
Having an ethernet cable plugged into the laptop at the same time caused a  hang at "network interfaces"during booting.
Well good luck atleast it does work (today!) on an Acer Aspire3000.

---

### Post by Volcomsnowboard on 2007-03-29
ok i just bought this card on ebay without knowing the trouble i was getting into
im running xubuntu 6.10 on a compaq presario 1200
its a netgear wireless card wg511v2 made in china
the lights on the card will not come on
ive ran ndiswrapper and have the mrv8000c.inf installed
and it recognizes the card when i run ndiswrapper -l
when i run lspci it says its a marvell chipset
when i run iwconfig i only get lo and sit0 with no wireless for each
can someone help me, i read all the other posts and ive tried but im no expert at linux or networking

---

### Post by Volcomsnowboard on 2007-04-10
ok i got my card working finally last week,
i decided to get a clean start and installed i think the beta of xubuntu feisty b/c i didnt have much installed on my laptop
after that i installed ndiswrapper
installed the xp driver from the netgear cd
put the card in, ran modprobe ndiswrapper and to my surprise the light came on and i had wireless
good luck to anyone else with this problem

---

