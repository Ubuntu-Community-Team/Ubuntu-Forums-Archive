---
title: "Leadtek DTV1000T not Detected Alfter System Update"
date: 2010-04-04
forum: Mythbuntu
---

### Post by Macus on 2010-04-04
Hi, 

I have a mythbox with 2 PCI tuners

terratek cinergey 1400 DVB-T which works great

and a Leadtek Winfast DTV1000T which was working 

both set to:
card type: DVB DTV capture card v3.x

I did the upgrade to 9.10
which breaks the card

the cinergy shows up as /dev/dvb/adapter0/frontend0, 
and the winfast in not there (i assume its ment to be adapter1)

last time i used:
[http://kernellabs.com/hg/~mkrufky/dtv1000s/summary](http://kernellabs.com/hg/~mkrufky/dtv1000s/summary)
which worked 

so I tried the above installer, no change

I ran lspci -v 

...
01:01.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
	Subsystem: LeadTek Research Inc. Device 6655
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at f3001000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: saa7134
	Kernel modules: saa7134

01:02.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Subsystem: TERRATEC Electronic GmbH Device 1166
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at f0000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel driver in use: cx8800
	Kernel modules: cx8800
...

so its detected, but is it ment to be Philips?
and the kernel driver according to [http://www.mythtv.org/wiki/Leadtek_DTV-1000T](http://www.mythtv.org/wiki/Leadtek_DTV-1000T)
its ment to be cx88-dvb

also for some reason mythweb now thinks it has 3 encoders

---

### Post by Macus on 2010-04-05
No Suggestions?

I have all the right modules in /etc/modules

lp
cx88_dvb
cx8802 
cx88-dvb
dvb-core
cx88-alsa

Still it miss detects the card, is there a way to tell the device what driver to use as im sure its not saa7134

the mythbox is very close to working at its potential, just this tuner issue to iron out so any help is appreciated 

thanks

---

