---
title: "USB modem not working with modeswitch"
date: 2011-06-02
forum: Networking &amp; Wireless
---

### Post by Ferb on 2011-06-02
I have received a new huawei k3770 usb modem but ubuntu 11.04 (32 bit) picks it up as a cd rom but not as a modem. Modeswitch is installed and I have reinstalled it as well. I have googled it but I found nothing. 
Any help here?

---

### Post by garryzn on 2011-06-03
> **Ferb said:**
> I have received a new huawei k3770 usb modem but ubuntu 11.04 (32 bit) picks it up as a cd rom but not as a modem. Modeswitch is installed and I have reinstalled it as well. I have googled it but I found nothing. 
Any help here?
Try this guy

[http://www.riply.co.za/2011/01/06/how-to-use-cell-c-usb-hsdpa-on-ubuntu/](http://www.riply.co.za/2011/01/06/how-to-use-cell-c-usb-hsdpa-on-ubuntu/) 

I know it's a different modem but he will probably be able to help you.

I'm interested in that 2+2 deal also, let me know if you come right.

Garry

---

### Post by alexfish on 2011-06-03
> **Ferb said:**
> I have received a new huawei k3770 usb modem but ubuntu 11.04 (32 bit) picks it up as a cd rom but not as a modem. Modeswitch is installed and I have reinstalled it as well. I have googled it but I found nothing. 
Any help here?

  	 	 	 	 	 	  **Can have a look here first**
  **[Natty, known bugs, fixes and work arounds]("http://ubuntuforums.org/showthread.php?t=1749312")  post #****[30]("http://ubuntuforums.org/showpost.php?p=10793568&postcount=30")**
 

 **[B]if unresolved can post back here **[/B] 
 

 **[B]regards**[/B]
 

 **[B]alexfish**[/B]

---

### Post by SneakPeak on 2011-08-28
Hi All,

I followed the instructions given here:

[http://forum.sakis3g.org/smf/index.php?topic=1616.0](http://forum.sakis3g.org/smf/index.php?topic=1616.0)

I found the plugging in of the modem a bit of a fiddle.  The first few times I ran the script it didn't work but if I did the following it did:

Let Ubuntu find the modem and recognize it as a CD Rom Drive.  Safely remove the CD Rom Drive and unplug the modem.  Be ready to run your script. Plug the modem back into the same usb port and then run the script.  You get a nice little success message if it has worked.

In my case I wasn't prompted for a PIN and the standard network manager didn't "find" the modem and give me an option to connect.  So I downloaded sakis3g script.  I placed it in the same folder as the little script I had to use to get the modem recognized.  I had to change it to an executable:

chmod + x sakis3g

I then ran it. It asked a few questions.  One I had no idea on.  It wanted to know something about which modem interface it should use and there was an option 1 or an option 0.  I flipped a coin and chose option 1.  It worked.   I am now online and very happy.  It'd be nice if this is "fixed" in future versions of Ubuntu though.

Good luck. Hope this works for you.  It has for me.

(By the way I am running more than one version of Ubuntu (Desktop and Laptop) I did this on my Laptop on version 11.04.  My desktop runs version 10.10 I think)  (What I am trying to say is my signature is wrong.)

Cheers

Adrian

---

### Post by kareempharmacist on 2011-10-14
It works perfectly and out-of-the-box on ubuntu 11.10 .....tried..all u have to do is to upgrade.
it works also on debian and any debian-based distribution.

---

### Post by narcisgarcia on 2011-11-29
These are the simplest ways I found to use this device on Ubuntu Natty.

**Method 1:** Terminal commands with the device already plugged
(this must be done on every session)
```
sudo usb_modeswitch -v 0x12d1 -p 0x14d1 -V 0x12d1 -P 0x14c9 -M 55534243123456780000000000000011062000000100000000000000000000
sudo modprobe usbserial vendor=0x12d1 product=0x14c9

```

**Method 2:** Upgrading packages from 11.10 (Oneiric) to do it automatic
[LIST=1]
[*]Uninstall the package usb-modeswitch-data
[*]Install the next version package from [http://packages.ubuntu.com/oneiric/usb-modeswitch-data](http://packages.ubuntu.com/oneiric/usb-modeswitch-data)
[*]Install the next version package from [http://packages.ubuntu.com/oneiric/usb-modeswitch](http://packages.ubuntu.com/oneiric/usb-modeswitch)
[/LIST]

---

