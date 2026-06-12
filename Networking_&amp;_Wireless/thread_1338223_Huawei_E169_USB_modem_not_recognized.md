---
title: "Huawei E169 USB modem not recognized"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by pavka14 on 2009-11-26
Hi,

I am trying to get a Vodafone USB modem to work - Huawei K3765 (which is a rebranded E169).
It's supposed to be recognized by the kernel (latest generic kernel installed - 2.6.31-15-generic) - and just added through Network Manager, but - no luck.
I also installed vodafone-mobile connect from here: [https://forge.betavine.net/frs/?group_id=12](https://forge.betavine.net/frs/?group_id=12) (as well as the other packages). What happens when I start it - it doesn't see the modem.
It's seen as a CD drive, and clicking "eject", "unmount" or "remove safely" on it doesn't help - it disappears, then several seconds later appears as a CD drive again.

Any ideas?

---

### Post by pavka14 on 2009-11-27
ps More info here: [http://forums.fedoraforum.org/showthread.php?t=235018](http://forums.fedoraforum.org/showthread.php?t=235018) (same modem, same issue, on a different machine running Fedora).

---

### Post by suyog on 2009-11-27
Try to install gnome-ppp or wvdial and configure connection.

---

### Post by pavka14 on 2009-11-27
The machine doesn't see the modem, what use is that connection? I already have a connection through NM - it has nothing to work with...

---

### Post by pdc on 2009-11-27
sorry to hear of this problem: I have read your fedora posting; I get a vodafone connection with an E220: I find that just works and works: used in NZ and Oz; (with appropriate simcards); 

having access with the 220, and relying on that; I have bought one or two other modems second-hand, to try them; and learn about them; and not having much luck; eg Vodafone now have ZTE modems, and they again need some type of usbmodeswitch;

what about joining the VMC forum: see if they can help;

[http://www.betavine.net/bvportal/forums/index.html?forumId=320](http://www.betavine.net/bvportal/forums/index.html?forumId=320)

like you, I tried fedora 12; (with the ZTE modem); I was clicking "eject" on the VMC software, and getting a changed ID (identified by "lsusb") but I did not get a connection; currently looking at installing VMC on the latest mandriva, as an experiment;

other suggestion is: buy a 220 modem; with firmware, they can be upgraded to double-speed and I have been pleased with that; (used in Brisbane recently; no effort at all to access the network); similarly a Huawei 160G worked fine on 3 in Oz; second-hand 220 modems appear on ebay.com.au and are cheap; (and can be unlocked)

[http://computers.shop.ebay.com.au/items/Wireless__W0QQBrandZHuaweiQQ_catrefZ1QQ_dmptZAUQ5fModemsQQ_flnZ1QQ_sacatZ162340QQ_ssovZ1QQ_trksidZp3286Q2ec0Q2em282](http://computers.shop.ebay.com.au/items/Wireless__W0QQBrandZHuaweiQQ_catrefZ1QQ_dmptZAUQ5fModemsQQ_flnZ1QQ_sacatZ162340QQ_ssovZ1QQ_trksidZp3286Q2ec0Q2em282)

---

### Post by pavka14 on 2009-11-27
Thanks, I already posted there and here:
[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=1342](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=1342)

Yes, I'd buy one of these modems from eBay but I only got this one because I was in a hurry - will travel to Melbourne tomorrow and wanted to have some connection there.

---

### Post by suyog on 2010-01-02
@pavka14, have you got connection working with Network manager?
After 2 months of 9.10 release , I havent got it working.
Seems very strange that I didnt have issues in 9.04.

---

### Post by GeorgeVita on 2010-01-03
> **suyog said:**
> @pavka14, have you got connection working with Network manager?
After 2 months of 9.10 release , I havent got it working.
Seems very strange that I didnt have issues in 9.04.

Have you updated 9.10?
You need kernel version >= 2.6.31-15-generic

Regards,
George

---

### Post by alexfish on 2010-01-03
hi
 
can you provide the following details
 
DefaultVendor=  
 
DefaultProduct=
 
thanks in advance 
 
alexfish

---

### Post by suyog on 2010-01-03
I have updated to 9.10 and currently i have 2.6.31-17-generic

@alexfish How do i find following? I am newbie even after 2 years.

DefaultVendor= 

DefaultProduct=

Thanks in advance. :)

---

### Post by GeorgeVita on 2010-01-03
To define VendorID : ProductID open a terminal window:
```
lsusb
```
attach modem, **wait 20 seconds**, repeat:
```
lsusb
``` compare output. The different (new one) is the modem.

G

---

### Post by alexfish on 2010-01-03
> **suyog said:**
> I have updated to 9.10 and currently i have 2.6.31-17-generic

@alexfish How do i find following? I am newbie even after 2 years.

DefaultVendor= 

DefaultProduct=

Thanks in advance. :)

Hi

from the terminal 

Cod:

lsusb 


then

Code:

dmesg | grep -e "modem" -e "tty"






then post details here

---

### Post by suyog on 2010-01-04
Hey guys finally good news !!!!
My Huawei modem is working with Network Manager !!!
I just decided to give a try today which I hadnt done in past 2-3 days. It worked after asking me to confirm access to keyring.

I hope they have fixed this.

Anyone else can confirm here?

---

### Post by GeorgeVita on 2010-01-04
Good news actually!
> **GeorgeVita said:**
> Have you updated 9.10?
You need kernel version >= 2.6.31-15-generic
> **suyog said:**
> I have updated to 9.10 and currently i have 2.6.31-17-generic
I think that above is the 'confirmation'!

Regards,
George

---

### Post by suyog on 2010-01-05
Yes, very good news, my sleepless nights with this issues gone!!!
:)

---

### Post by Concrete Gannet on 2010-10-31
I had similar problems with NetworkManager 0.8 and my Huawei E160E. The fix was to upgrade ppp to 2.4.5. See the report at [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=592444](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=592444) for details.

---

