---
title: "BSNL EVDO on ubuntu 8.10"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by shibabroto on 2009-03-17
Pl. help me in installing BSNL EVDO USB data card on ubuntu 8.10 which I've installed on my HP pavilion laptop. I've downloaded zte driver from [www.ztemt.com](www.ztemt.com). But, unfortunately the ztemt software doesn't detect the modem though it is attached. During installation of the software it gives an error "insmod: error inserting 'ztemt.ko': -1 invalid module format". I've tried the to install the software using "dpkg -i ztemt..... .deb".

---

### Post by vish on 2009-04-08
I am getting the same error
A dmesg gives:

ztemt: Uknown symbol usb_control_msg

any idea what this means??
I compiled the module on my machine

---

### Post by shibabroto on 2009-04-08
I've left my idea of configuring using the software and used wvdial. That's the best way I've found to connect using any USB wireless modem. 'wvdial' and 'wvdialconf' both of these are needed. I can help all regarding this. It's very nice and also I'm getting a good speed in BSNl EVDO data card.

---

### Post by farhanaaz3 on 2009-04-29
So pls go ahead and give the details how to connect............
either by inserting driver or by using wvdail and wvdailconf.............

Thanks in advance

---

### Post by raj47i on 2009-05-10
Hi,

Using Ubuntu 9.04, all i have to do was plug in the device.
Go to the Networking menu in the system tray.
Edit the connections and enter the username / passwords. There was no further issues. I dnt think i installed any additional packages for this. 
The EvDo is added to the Networks list as 
"Auto Mobile Broadband (CDMA) Connection".

But however i am not able to use the connection in my home; there are no EvDo networks. only ordinary data network is available. I am able to use the ordinary connection using windows, but not able to connect using Ubuntu.

---

### Post by a2banjo on 2009-09-18
You can get this working in network manager. The modem is not detected by NM, its a known bug .In oreder to fix,
edit [COLOR="Blue"]/lib/udev/rules.d/77-nm-probe-modem-capabilities.rules[/COLOR]
change the line that looks like
[COLOR="Blue"]DRIVERS=="option|sierra|hso|cdc_acm|qcserial", GOTO="probe"[/COLOR]
to
[COLOR="DarkOrchid"]DRIVERS=="option|sierra|hso|cdc_acm|qcserial|moto-modem", GOTO="probe"[/COLOR]
save and replug your device. It should get detected by network manager,
you can then edit connections, enter the username and password and start
using the device.

---

### Post by G M T Junaidi on 2009-12-14
> **raj47i said:**
> Hi,
 
Using Ubuntu 9.04, all i have to do was plug in the device.
Go to the Networking menu in the system tray.
Edit the connections and enter the username / passwords. There was no further issues. I dnt think i installed any additional packages for this. 
The EvDo is added to the Networks list as 
"Auto Mobile Broadband (CDMA) Connection".
 
But however i am not able to use the connection in my home; there are no EvDo networks. only ordinary data network is available. I am able to use the ordinary connection using windows, but not able to connect using Ubuntu.
 
 
Hi, i have done each & every trick what i got it from the site, u r absolutely right , it will show the connection but never connect. I got totally pisse off. Please help me if ur connection is working. Thanks for all the details.

---

### Post by arvindmohansk on 2010-06-27
Guys, did any one try this: [http://ubuntuforums.org/showthread.php?t=343989](http://ubuntuforums.org/showthread.php?t=343989)

---

