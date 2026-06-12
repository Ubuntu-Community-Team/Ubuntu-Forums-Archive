---
title: "Set NIC speed to full duplex permanent in 12.04 LTS"
date: 2013-08-25
forum: Networking &amp; Wireless
---

### Post by QKC on 2013-08-25
Dear Ubuntu Member
I am running 12.04 LTS on a pentium system. My network speed is at the moment Auto Negotiation. I have use the ethtool to turn off auto negotiation on my NIC and using the command [COLOR=#0000ff]_**sudo ethtool -s eth0 speed 100 duplex full **_[/COLOR]to set my NIC to 100mps full duplex. But each time after rebooting the system, my NIC will revert back to Auto Negotiation. Is there any way to have the setting permanent in 12.04 LTS? 

Appreciate all helpers
Thanks
JQ

---

### Post by chili555 on 2013-08-25
Please open a terminal and do:```
gksudo gedit /etc/rc.local
```Add a new line above exit 0:```
ethtool -s eth0 speed 100 duplex full
```Proofread carefully, save and close gedit. You should be all set.

---

### Post by QKC on 2013-08-26
Hi chili555,
Thank you very much for your help. My 12.04 LTS now is a little faster. :). Do you mind to help me out on another system that is install with Linux Mint 14 64 bit edition as I cannot get the NIC to set 100mps full duplex on permanent

JQ

---

### Post by chili555 on 2013-08-26
> **QKC said:**
> Hi chili555,
Thank you very much for your help. My 12.04 LTS now is a little faster. :). Do you mind to help me out on another system that is install with Linux Mint 14 64 bit edition as I cannot get the NIC to set 100mps full duplex on permanent

JQI believe Mint is Ubuntu based and the same technique should work. Did you try it?

---

### Post by QKC on 2013-08-27
Hi
I have tried it but it doesn't seem to work. Below is the outputs of my try

asus@ASUS ~ $ sudo ethtool eth0
[sudo] password for asus: 
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  100baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: Symmetric
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes
asus@ASUS ~ $ gksudo gedit /etc/rc.local

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
ethtool -s eth0 speed 100 duplex full
exit 0

I have also attach my NIC details. Can you please help to see which part I make a mistake

Thanks

---

### Post by chili555 on 2013-08-27
> asus@ASUS ~ $ sudo ethtool eth0
[sudo] password for asus:
Settings for eth0:
Supported ports: [ TP MII ]
Supported link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Half 1000baseT/Full
Supported pause frame use: No
Supports auto-negotiation: Yes
Advertised link modes: 100baseT/Full
Advertised pause frame use: Symmetric Receive-only
Advertised auto-negotiation: Yes
Link partner advertised link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
Link partner advertised pause frame use: Symmetric
Link partner advertised auto-negotiation: Yes
[COLOR="#FF0000"]Speed: 100Mb/s
Duplex: Full[/COLOR]
Port: MII
PHYAD: 0
Transceiver: internal
Auto-negotiation: on
Supports Wake-on: pumbg
Wake-on: g
Current message level: 0x00000033 (51)
drv probe ifdown ifup
Link detected: yesAnd in /etc/rc.local, you asked for:> ethtool -s eth0 [COLOR="#FF0000"]speed 100 duplex full[/COLOR]What part seems not to have worked?

---

### Post by QKC on 2013-08-27
Hi 
See the red part


asus@ASUS ~ $     sudo ethtool -s eth0 autoneg off
[sudo] password for asus: 
asus@ASUS ~ $     sudo ethtool -s eth0 speed 100 duplex full
asus@ASUS ~ $ sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  Not reported
    Advertised pause frame use: No
    Advertised auto-negotiation: No
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
 - This    PHYAD: 0
    Transceiver: internal
    **[COLOR=#0000FF]Auto-negotiation: off   <---------------is the part that is having problem.[/COLOR]**
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes
asus@ASUS ~ $ 

After adding [COLOR=#000000]ethtool -s eth0 speed 100 duplex full 			 		[/COLOR]to /etc/rc.local, after a restart the Auto Negotiation should be Off and should be permanent but each time after restart I will have to do this ethtool -s eth0 [COLOR=#000000]speed 100 duplex full[/COLOR] again to turn off 

Thanks

---

### Post by chili555 on 2013-08-27
Your original inquiry didn't mention autonegotiation. However, I suggest that you amend the /etc/rc.local setting to:```
ethtool -s eth0 speed 100 duplex full autoneg off
```Turning off autonegotiation is a bit dangerous because you may be demanding that the router and NIC card perform at levels for which they are incapable. If it doesn't always work as expected or you get errors or dropped packets, you know how to undo it.

---

### Post by QKC on 2013-09-08
Hi chili555
Update on the problem.
After inserting ethtool -s eth0 speed 100 duplex full autoneg off in the /etc/rc.local settings, I experience as what you inform, my internet connection speed drop. Then I insert back ethtool -s eth0 speed 100 duplex full and my internet connection speed went back to normal.

Thank you for help.

---

### Post by chili555 on 2013-09-08
So you are all set? Glad it's working.

---

### Post by QKC on 2013-09-08
Hi chili555
Yeah. All back to normal. Thanks:lolflag:

---

