---
title: "kismet and bcm43xxccept stuff like: and the kismet.conf source line??"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by towsonu2003 on 2006-07-08
I am using bcm43xx as the driver for my broadcom wireless and I cannot find what to write for the source line of kismet.conf... I doesn't accept stuff like
bcm43xx,eth1,kismet
Broadcom,eth1,kismet

and so on... does anyone use bcm43xx + kismet? what do you have in your kismet.conf?

---

### Post by tturrisi on 2006-07-08
from the kismet doc: [http://www.kismetwireless.net/documentation.shtml](http://www.kismetwireless.net/documentation.shtml) (see section 12 & see section "cards that do not work")
```
    bcm43xx         Broadcom            Linux       Berlios-BCM43XX
                    http://bcm43xx.berlios.de
                    Capture interface:  'ethX'
                    *Very experimental* drivers with *experimental* Kismet
                     support.  These reverse-engineered drivers support a
                     range of Broadcom based wireless cards.  At the time
                     of this writing, they support ONLY monitor mode, normal
                     mode is not functional.
                    These drivers are in a state of high development, and 
                     support is only added because of demand.  If it doesn't
                     work, I wouldn't be too surprised.
```

---

### Post by towsonu2003 on 2006-07-08
> **tturrisi said:**
> from the kismet doc: [http://www.kismetwireless.net/documentation.shtml](http://www.kismetwireless.net/documentation.shtml) (see section 12 & see section "cards that do not work")
```
    bcm43xx         Broadcom            Linux       Berlios-BCM43XX
                    http://bcm43xx.berlios.de
                    Capture interface:  'ethX'
                    *Very experimental* drivers with *experimental* Kismet
                     support.  These reverse-engineered drivers support a
                     range of Broadcom based wireless cards.  At the time
                     of this writing, they support ONLY monitor mode, normal
                     mode is not functional.
                    These drivers are in a state of high development, and 
                     support is only added because of demand.  If it doesn't
                     work, I wouldn't be too surprised.
```

I read that part before. But if it wasn't supported, the error message would be more like: 
```
Source 0 (kismet): Enabling monitor mode for bcm43xx source interface eth0 channel 6...
FATAL: mode get ioctl failed 95:Operation not supported

``` or am I wrong (output taken from a PC withouth the bcm43xx card but source line has bcm43xx in that machine... hence kismet says this isn't supported with the card)?...

But with the laptop that has bcm43xx card and the same line in the conf file, the error message is something like
"Illegal source line: bcm43xx". Wouldn't that mean that kismet cannot understand that line, rather than the card not working with kismet?

---

### Post by tturrisi on 2006-07-08
What driver are you using for that card?  There's only one broadcom driver that works with kismet and it ONLY works in monitor mode, which means you cannot do anything else such as use internet, etc.  The driver is the one stated in the kismet readme: ( driver: [http://bcm43xx.berlios.de](http://bcm43xx.berlios.de) )
```
Chipsets known to NOT WORK:
     Broadcom           - No linux drivers, only useable with ndiswrapper or
                          linuxant wrappers around windows drivers.
                          *** UPDATE ***
                          See the bcm43xx source type entry.  There are
                          experimental reverse-engineered drivers which have
                          monitor mode support now under Linux!  If they don't
                          work, however, then too bad.
     Airport Extreme    - Really a Broadcom, with no rfmon in the OSX drivers.
                          *** UPDATE ***
                          See the bcm source for linux on ppc, it MAY work, it
                          may not.  Currently theres no solution for OSX but
                          I'm looking for OSX hackers interested in redoing the
                          Kismet port and looking into adding more support.
     Atmel              - There is a hack for pseudo-monitor in USB.  There is
                          currently no equivalent hack for PCMCIA.
     HermesII           - Proxim successor to the Orinoco/HermesI.  No support
                          yet in the drivers, may be available in the future.
     ndiswrapper        - Anything using ndiswrapper is using WINDOWS drivers
                          AND CAN NOT BE USED WITH KISMET.
```
kismet source try:
source=bcm43xx,$iface,broadcom

---

### Post by towsonu2003 on 2006-07-09
> **tturrisi said:**
> 
kismet source try:
source=bcm43xx,$iface,broadcom

I'll try this line, thanks. 

A stupid question, though: does it matter if my wireless card is associated with a wireless point while I am using kismet, or not? Your suggestion > it ONLY works in monitor mode, which means you cannot do anything else such as use internet seems to mean that I should not be connected to a wireless access point while using kismet, is this right?

thanks a lot for the help, I appreciate it.

---

### Post by tturrisi on 2006-07-09
> **towsonu2003 said:**
> I'll try this line, thanks. 

A stupid question, though: does it matter if my wireless card is associated with a wireless point while I am using kismet, or not? Your suggestion  seems to mean that I should not be connected to a wireless access point while using kismet, is this right?

thanks a lot for the help, I appreciate it.
No, you don't have to not be connected first, kismet will auto disconnect you.  What I was saying though was at the time f writing of that kismet readme doc, the broadcom driver did not work in any mode except monitor.  I'm not certain that the broadcom driver that comes w/ ubuntu is the same driver as the one referred to in the kismet readme.

---

