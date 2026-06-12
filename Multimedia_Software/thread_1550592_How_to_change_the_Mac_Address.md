---
title: "How to change the Mac Address"
date: 2010-08-11
forum: Multimedia Software
---

### Post by bugfinder on 2010-08-11
Hi Everybody,

                   I have setup a machine with Ubuntu 10.04 server and i have installed a KNC card for Streaming the channels. Everything is good so far and here is the real deal .. i wanna change the MAC address of the KNC card to try different things. I know how to change the MAC address of the LAN card but not sure about the KNC card. I tried few things by installing macchanger.. but didn't work out. Can any one tell me whether its possible to change the MAC of the KNC card and other tricks.

Here is a little info:-

[   11.344208] saa7146: register extension 'budget_av'.
[   11.344704] budget_av 0000:04:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.344739] IRQ 22/: IRQF_DISABLED is not guaranteed on shared IRQs
[   11.344754] saa7146: found saa7146 @ mem f887e000 (revision 1, irq 22) (0x1894,0x0016).
[   11.344762] saa7146 (0): dma buffer size 192512
[   11.344765] DVB: registering new adapter (KNC TV STAR DVB-S)
[   11.381523] adapter failed MAC signature check
[   11.381528] encoded MAC from EEPROM was ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff
[   11.421093] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   11.424157] e100: eth1 NIC Link is Up 100 Mbps Full Duplex
[   11.436279] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   11.644394] KNC1-0: MAC addr = 00:12:3a:65:89:1b  -------------------->>>>> This is what i wanna change
[   12.145996] DVB: registering adapter 0 frontend 0 (ST STV0299 DVB-S)...
[   12.146194] budget-av: ci interface initialised.


Thanks in advance for any help and Suggestions..

---

### Post by surfer on 2010-08-11
not sure about this, but the mac addresses are in

[FONT="Courier New"]/etc/udev/rules.d/70-persistent-net.rules[/FONT]

i do not know whether they can be changed in there...

---

### Post by Fludizz on 2010-08-11
*edit* nevermind, read wrong, not a NIC

---

### Post by bugfinder on 2010-08-11
Many Thanks guy's for your fast reply .. i appreciate  it .. I try it and let you guys know...Thanks again and have a nice day

---

### Post by Dracona on 2010-08-11
at the risk of sounding like an extreme dumb noob, what is a KNC card?

---

### Post by Fludizz on 2010-08-11
I also did not know, but if I google it, I end up with Sattelite receiver related hits, so I guess it is a card that can talk to a LNB. Correct me if I'm wrong :)

I first thought it was some kind of network card :P

---

### Post by Dracona on 2010-08-11
> **Fludizz said:**
> I also did not know, but if I google it, I end up with Sattelite receiver related hits, so I guess it is a card that can talk to a LNB. Correct me if I'm wrong :)

I first thought it was some kind of network card :P

Thx Fludizz
 I came up with same thing.  learn something new everyday, just i keep forgetting what i learned

---

### Post by bugfinder on 2010-08-12
That is Right Guy's its a PCI card which can Take Signals from the Satellite Dish....:popcorn:

---

### Post by Nick_Jinn on 2010-08-12
Subscribes.

---

