---
title: "TechnoTrend TT-budget S-1500 scans bud doesn't zap"
date: 2008-09-05
forum: Multimedia Software
---

### Post by luxscs on 2008-09-05
I've just installed a TT-budget S-1500 on a machine with the intention to turn it into a MythTV server. 

Obviously, I first just tried to test my DVB card. 
Whilst I was perfectly able to scan and create a channels.conf file, tzap returns a parsing error.

More specifically, e.g. ```
tzap -r "ZDF"
``` provides the following output:
> using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
ERROR: error while parsing inversion (syntax error)


As a matter of intrest, azap provides a different parsing error. 
```
azap -r -c /root/.tzap/channels.conf "ZDF"

``` provides the following output:
> using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
ERROR: error while parsing modulation (syntax error)


Anyway, I've trying to find out what the problem, but with no success. Being a ubuntu newbie, I would greatly appreciate some help.

I'm using kernel version 2.6.24-21-generic.

The relevant pieces in dmesg are:
> [   44.663624] saa7146: found saa7146 @ mem ffffc20001040000 (revision 1, irq 18 ) (0x13c2,0x1017).
[   44.663628] saa7146 (0): dma buffer size 192512
[   44.663630] DVB: registering new adapter (TT-Budget/S-1500 PCI)
[   44.700599] adapter has MAC addr = 00:d0:5c:64:91:34
[   44.700798] input: Budget-CI dvb ir receiver saa7146 (0) as /devices/pci0000:00/0000:00:1e.0/0000:05:02.0/input/input6
[   44.766997] budget_ci: CI interface initialised
[   45.155422] DVB: registering frontend 0 (ST STV0299 DVB-S)...

 
lspci -v return:
> 05:02.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
	Subsystem: Technotrend Systemtechnik GmbH Unknown device 1017
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at f8102000 (32-bit, non-prefetchable) [size=512]


and ```
lsmod | grep -e budget -e dvb
``` returns:
> budget_ci              22788  0 
budget_core            14468  1 budget_ci
dvb_core               94380  3 stv0299,budget_ci,budget_core
saa7146                22152  2 budget_ci,budget_core
ttpci_eeprom            3968  1 budget_core
ir_common              39812  1 budget_ci
i2c_core               28544  5 lnbp21,stv0299,budget_ci,budget_core,ttpci_eeprom


Anybody have some good advise?

---

### Post by luxscs on 2008-09-14
If anybody ever stumbles on this post with the same issue:
The answer is simple: You're using an DVB-S card, so you need to use szap.:oops:

---

