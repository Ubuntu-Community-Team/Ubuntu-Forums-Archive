---
title: "Troubles with BT DUN"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by bryceowen on 2009-06-16
I'm trying to use my T-Moblie MDA (HTC Wizard) to connect to the internet using DUN through bluetooth and I'm running into a couple problems.

First, if anyone can show me a page that explains how to do it through Gnome-PPP, that might solve my problems.

Now, I am able to communicate with my phone (after following the instructions [here]("http://dyenibib.wordpress.com/opensource-linux/ubuntu-wvdial-bluetooth-and-my-gsm-phone-as-gprs-modem/") and [here]("http://ubuntuforums.org/showthread.php?t=166617")) and when I issue the wvdial command (which only works as sudo), it goes through the connecting process, connects, gives me an IP address (ifconfig shows the PPP adapter) and I'm even able to ping remote addresses. However, Firefox doesn't work. Nor tsclient. I'm assuming nothing in gnome recognizes the PPP connection. Can anyone tell me what my problem might be? I'm so close to having this work I can taste it. And once this works, I can finally remove the XP partition from my drive.

Here's what I currently have in my wvdial.conf:
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = at+cgdcont=1,"IP","wap.cingular"
Baud = 115200
Modem = /dev/rfcomm0
Phone = *99#
Username = WAP@CINGULARGPRS.COM
Password = CINGULAR1
New PPPD = yes
ISDN = no
Stupid Mode = yes
Carrier Check = no

```
And this is what rfcomm returns:
```

rfcomm0: 00:12:37:93:D6:BA channel 3 clean

```
And this is the contents of /etc/bluetooth/rfcomm.conf:
```

rfcomm0 {
	bind yes;
	device 00:12:37:93:D6:BA;
	channel 3;
	comment "MDA";

```

---

### Post by GeorgeVita on 2009-06-16
Hi **bryceowen**,
connect as you describe, run Firefox and check if File (ALT-F) > Offline (W) mode is set.
Untick it and try browsing.

Regards,
George

---

### Post by bryceowen on 2009-06-16
> **GeorgeVita said:**
> Hi **bryceowen**,
connect as you describe, run Firefox and check if File (ALT-F) > Offline (W) mode is set.
Untick it and try browsing.


Congratulations, sir! You've put the final nail in XP's coffin for my laptop!

Oop! And with this post, I now have 5 Cups of Ubuntu and my beans are now green!

---

