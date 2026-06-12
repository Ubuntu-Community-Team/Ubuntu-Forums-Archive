---
title: "WIFI off but Wifi LED stays on??"
date: 2011-05-17
forum: Networking &amp; Wireless
---

### Post by nexul on 2011-05-17
Hi,
 
I've got a clean install of ubuntu 10.10 (Maverick) on toshiba nb500 and the problem is that when I disable WIFI (via Jupiter or Ubuntu) my wifi led stays on!!
 
So Im wondering if my WIFI radio is REALLY on (and sucking my battery dry!!) and scanning for WIFI's:
 
**When I DISABLE WIFI and run sudo iwconfig I get this:**
 
```
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11bgn  ESSID:off/any
         Mode:Managed  Access Point: Not-Associated   Tx-Power=off
         Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
         Encryption key:off
         Power Management:off
``` 
 
**When I ENABLE WIFI** 
 
```
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11bgn  ESSID:off/any
         Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm
         Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
         Encryption key:off
         Power Management:off
``` 
 
 
Does "Tx-Power=off" mean that my WIFI radio is turned off and not scanning for WIFI's ?
 
Is there any other sure-fire way to tell whether my WIFI radio is really on or not ?
 
Thank's guys.

---

### Post by chili555 on 2011-05-17
> Does "Tx-Power=off" mean that my WIFI radio is turned off and not scanning for WIFI's ?Yes, exactly. You might also check:```
rfkill list all
```Here is an example from my machine:> 0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no
As you can see, my wireless is working and my bluetooth is switched off.

---

### Post by nexul on 2011-05-17
Chilli555,

Thank's for your reply.  Heres my rfkill all:

```
rfkill list all
0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

```I guess I got a bug with my WIFI Led on 10.10.

Cheers.
N.

---

### Post by fuduntu on 2011-05-18
Try setting acpi_osi="Linux" as a boot option in GRUB.

It is a common problem, if you turn off your WIFI with Jupiter and you don't see the LED turn off it normally means that Windows was returned when the kernel queried the BIOS for ACPI information.

---

### Post by nexul on 2011-05-19
fuduntu,
 
Thank you for your post.
 
When I search for the string "acpi_osi" in grub.cfg it does not exist.
 
If I need to insert acpi_osi="Linux" could you please tell me where I need to put it.
 
I was thinking first line:?
 
### BEGIN /etc/grub.d/00_header ###
**acpi_osi="Linux"**
if [ -s $prefix/grubenv ]; then 
....
....
*.....*

---

### Post by fuduntu on 2011-05-19
> **nexul said:**
> fuduntu,
 
Thank you for your post.
 
When I search for the string "acpi_osi" in grub.cfg it does not exist.
 
If I need to insert acpi_osi="Linux" could you please tell me where I need to put it.
 
I was thinking first line:?
 
### BEGIN /etc/grub.d/00_header ###
**acpi_osi="Linux"**
if [ -s $prefix/grubenv ]; then 
....
....
*.....*


It would go on the kernel options line.  I'm not sure where it would be in Ubuntu's GRUB2.

---

