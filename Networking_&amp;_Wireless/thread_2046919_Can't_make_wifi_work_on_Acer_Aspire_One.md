---
title: "Can't make wifi work on Acer Aspire One"
date: 2012-08-23
forum: Networking &amp; Wireless
---

### Post by TheBrexas on 2012-08-23
Hey, sorry guys I've been searching on the forums for a couple of hours and trying to fix my problem and It didn't work out so I will just bother you a little bit.

The wireless conection is not working in my netbook Aspire One, I've got Ubuntu 12.04. I've installed rfkill and it will say:


```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

But " rfkill unblock all " will not make it work. Reading and reading around here I think that my main problem has to do with this:

```
quim@quim-AOA150:~$ modinfo ath5k
filename:       /lib/modules/3.2.0-23-generic-pae/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     FA2500C2D3C1A3B6094E37C
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000014sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000011sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000207sv*sd*bc*sc*i*
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       3.2.0-23-generic-pae SMP mod_unload modversions 686 
**parm:           nohwcrypt:Disable hardware encryption. (bool)**
parm:           all_channels:Expose all channels the device can use. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
quim@quim-AOA150:~$ 
```

Any hints on how can I fix this? I would like to try to just press the Wifi on/off key in my netbook but it has no key like that...

Thanks a lot in advance fellas

---

### Post by TheBrexas on 2012-08-23
I reply myself cause I don't have rights to edit:

I wanted to add that It's also remarkable that this is not the first time that my wireless goes wrong randomly. It happened a couple of months ago but I don't remember how I fixed it. The thing is that my netbook/ubuntu seems to disconnect the wifi somewhere and totally in a random way...

Thanks again and please forgive my English

---

### Post by Kirk Schnable on 2012-08-23
I manage a batch of Lenovo netbooks at my work, and we had so many problems with the wireless switches on them.  They had a similar issue, but whenever someone flipped the wireless switch, it would turn off but never back on.  We ended up taking each apart and blocking the hardware switch so it physically couldn't be flipped.

The useful tidbit I gained during my experience with this, is that taking the CMOS battery out of the Lenovo netbooks helped resolve the hard block.

Not that this is a "fix", but until you can figure out what's turning your wireless off, it might be a step you can take to try to get it working again for the time being.

Kirk

---

### Post by TheBrexas on 2012-08-24
Thanks. You mean that I could open the netbook and remove the battery from the hardware?

Well thanks but I don't think I'm brave enough to do that, I wouldn't like to screw the whole computer, but I'll take that as a last option.

Any other tips?

---

