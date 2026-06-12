---
title: "Stop anoying blinking wifi led"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by Ventiman on 2010-10-13
Anyone any idea how to stop the anoying continuous blinking of the wifi led?
here's my hardware
```
sudo lshw -C Network
  *-network
       description: Wireless interface
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 35
       serial: 00:24:d7:37:ec:24
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-22-generic firmware=9.221.4.1 build 25532 ip=192.168.178.226 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:46 memory:f4100000-f4101fff

``` I am using 10.10 Maverick 64-bit ```
uname -a
Linux Tijns-E6410 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux
```
Tried various solutions. On Lucid [http://ubuntuforums.org/showthread.php?t=966511&page=9]("http://ubuntuforums.org/showthread.php?t=966511&page=9") and [http://alexcabal.com/stop-blinking-intel-wifi-led-on-ubuntu-karmic/]("http://alexcabal.com/stop-blinking-intel-wifi-led-on-ubuntu-karmic/") helped me fixing it ultimately using [http://ubuntuforums.org/showpost.php?p=9963917&postcount=13]("http://ubuntuforums.org/showpost.php?p=9963917&postcount=13")

---

### Post by ravi84m on 2010-10-14
```
sudo gedit /etc/modprobe.d/wlan.conf
```copy paste the following line:```
options iwlcore led_mode=1
```save and restart.
it worked for me at least... good luck

---

### Post by wjoyce on 2010-10-23
I can confirm that the above worked for me too.  Thanks.

---

### Post by warpslide on 2010-10-30
This worked for me as well, thank you so much!

---

### Post by garoth2 on 2011-06-15
options iwlagn led_mode=1

for my Intel Ultimate N 6300 on Ubuntu 11.04

---

### Post by vinodkhare on 2011-10-09
> **garoth2 said:**
> options iwlagn led_mode=1

for my Intel Ultimate N 6300 on Ubuntu 11.04

Thanks, this works on my HP dm4 2165dx.

---

### Post by h2oskr on 2011-10-19
options iwllcore_mode=1
Worked for me in 11.04

It did NOT wok when I moved to 11.10.
I tried:
options iwlagn led_mode=1
Did not work.

For now I'm stuck with a blinking LED. I hope there is a solution.

My HW:
HP nc2400
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 02
       serial: 00:19:d2:37:1f:69
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless

---

### Post by dustyjm on 2011-10-25
I found a solution for 11.10. 
```
sudo gedit /etc/modprobe.d/wlan.conf
```

```
options iwlagn led_mode=1
```
note to use iwlagn rather than iwlcore

then you need to do one more thing

```
sudo modprobe -r iwlagn
sudo modprobe iwlagn
```
wait a minute for it to reconnect and you're in business no restart required
Thanks to [http://thegreyhats.blogspot.com/2011/10/ubuntu-1110-upgrade-black-screen-cant.html](http://thegreyhats.blogspot.com/2011/10/ubuntu-1110-upgrade-black-screen-cant.html)

---

### Post by h2oskr on 2011-10-25
Unfortunately it doesn't work for me. I tried it again to see if I messed it up some how, but... no. Perhaps it's something about my HW.

---

### Post by dzejdy on 2011-10-28
> **dustyjm said:**
> I found a solution for 11.10. 
```
sudo gedit /etc/modprobe.d/wlan.conf
```

```
options iwlagn led_mode=1
```
note to use iwlagn rather than iwlcore

then you need to do one more thing

```
sudo modprobe -r iwlagn
sudo modprobe iwlagn
```
wait a minute for it to reconnect and you're in business no restart required
Thanks to [http://thegreyhats.blogspot.com/2011/10/ubuntu-1110-upgrade-black-screen-cant.html](http://thegreyhats.blogspot.com/2011/10/ubuntu-1110-upgrade-black-screen-cant.html)

Thanks!!!

It worked for me (HP Pavillion dv5-1199ec + Ubuntu 11.10) perfectly!

---

### Post by mkjmkj on 2012-01-25
dustyjm, thanks a lot for that hint, worked perfectly on Thinkpad X61t with 11.10 64bit!

update: uh, didn't work after all. Started blinking again the next moment :(
Honestly, who came up with the useless idea of an indicator that constantly flashes? That's somewhat like a smoke detector that constantly beeps to confirm it's still working.

---

### Post by TedTedTed on 2012-02-15
> **dustyjm said:**
> I found a solution for 11.10. 
```
sudo gedit /etc/modprobe.d/wlan.conf
``````
options iwlagn led_mode=1
```note to use iwlagn rather than iwlcore

then you need to do one more thing

```
sudo modprobe -r iwlagn
sudo modprobe iwlagn
```wait a minute for it to reconnect and you're in business no restart required
Thanks to [http://thegreyhats.blogspot.com/2011/10/ubuntu-1110-upgrade-black-screen-cant.html](http://thegreyhats.blogspot.com/2011/10/ubuntu-1110-upgrade-black-screen-cant.html)


Works for me, on Debian Sid / Unstable (15/02/2012 version). Thank you very much, this blinking light was horrible. I wonder who has had this stupid idea to make the Wifi LED Blink whenever there's traffic.

My wifi card by the way : Intel Corporation Centrino Ultimate-N 6300 on a Lenovo Thinkpad W520 (to make future Google Search easy).

---

### Post by mavirroco on 2012-02-22
> **dustyjm said:**
> I found a solution for 11.10. 
```
sudo gedit /etc/modprobe.d/wlan.conf
```

```
options iwlagn led_mode=1
```
note to use iwlagn rather than iwlcore

then you need to do one more thing

```
sudo modprobe -r iwlagn
sudo modprobe iwlagn
```
wait a minute for it to reconnect and you're in business no restart required
Thanks to [http://thegreyhats.blogspot.com/2011/10/ubuntu-1110-upgrade-black-screen-cant.html](http://thegreyhats.blogspot.com/2011/10/ubuntu-1110-upgrade-black-screen-cant.html)



thanks works for me
hp pavillion dv7

---

### Post by Faulkinbizzle on 2012-05-07
Originally Posted by dustyjm  
I found a solution for 11.10. 
Code:
sudo gedit /etc/modprobe.d/wlan.conf
Code:
options iwlagn led_mode=1
note to use iwlagn rather than iwlcore

then you need to do one more thing

Code:
sudo modprobe -r iwlagn
sudo modprobe iwlagn
wait a minute for it to reconnect and you're in business no restart required
Thanks to [http://thegreyhats.blogspot.com/2011...reen-cant.html](http://thegreyhats.blogspot.com/2011...reen-cant.html)


Worked for me on HP.  For 12.04 had to change the iwlagn to iwlwifi on all the command lines.  Thanks!

---

### Post by kkarakk on 2012-06-21
First two methods ie without "sudo modprobe -r iwlagn
sudo modprobe iwlagn" don't work on my pc.
last method mentioned confirmed working in hp dv5 1155ee with ubuntu 12.04
Thanks a lot, was driving me crazy! registered on forums just to post this comment :lolflag:

---

### Post by Gmasterhyde on 2012-07-29
Worked for me on my HP running 12.04! This was driving me nuts, so thanks a lot for the fix! =D

---

### Post by dtrainer on 2012-08-10
This works for me initially, but after a restart the LED initiates crazy blinking again. HP DM4 running 12.04

---

### Post by chili555 on 2012-08-10
> **dtrainer said:**
> This works for me initially, but after a restart the LED initiates crazy blinking again. HP DM4 running 12.04The module is called iwlwifi rather than iwlagn in 12.04. Is that how your conf file reads?> Code:
sudo gedit /etc/modprobe.d/wlan.conf
Code:
options [COLOR="Red"]iwlagn[/COLOR] led_mode=1

---

### Post by Michael Longval on 2013-03-07
This is a solution I found to stop the "das-blinkin-led" .... 

OS: Ubuntu 12.10
System: ThinkPad T61p
Wifi (as reported by : "sudo lshw -c network"):

*-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 61
       serial: 00:1f:3b:51:0e:f3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wir
eless
       configuration: broadcast=yes ***_driver=iwl4965_*** driverversion=3.5.0-25-generi
c firmware=228.61.2.24 ip=192.168.0.30 latency=0 link=yes multicast=yes wireless
=IEEE 802.11abgn
       resources: irq:48 memory:df2fe000-df2fffff

The iwl4965 driver (my bold and underline) is handled by iwlegacy (don't ask where I got this I don't remember).

However when I checked my /etc/modprobe.d/wlan.conf, I found:

> options iwl_legacy led_mode=1

But iwl_legacy is not a module as far as I know.

So I changed it to:

> options iwlegacy led_mode=1

And rebooted the system.

And now "das-blinkin-lights" is not blinkin.... thank God! it was driving me nuts.

Hope this helps,

Mike

---

