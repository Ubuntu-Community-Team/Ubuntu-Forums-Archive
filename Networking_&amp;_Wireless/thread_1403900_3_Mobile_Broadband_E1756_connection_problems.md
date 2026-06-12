---
title: "3 Mobile Broadband E1756 connection problems"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by planesinspace on 2010-02-10
Hi, I have just installed the new Ubuntu 9.10, and when I try and connect to my 3 Mobile Broadband via modem E1756, even after clicking "Network Connections" and "Add", it says "GSM Network Disconnected".
Does anyone know whether this modem is compatible or if I am just wasting my time?
I have searched for similar posts but no one seems to have this model modem.
Any help much appreciated!

---

### Post by crlang13 on 2010-02-10
Hey,

I'm using an E160 with 3 and it works fine.

All I had to do was plug it in and it was automatically found and worked.  Occasionally it is a little unresponsive but I think it's more to do with the network than anything (we're in a weak service area).  I get the same errors when signal strength goes down.  Has the modem worked on other machines in the same area?

I'm not terribly sure about the E1756, but it's obvious on the E160 that it was not built with Linux in mind...

What are your network settings for the connection?

---

### Post by crlang13 on 2010-02-10
Hey, I just did a little searching: [http://www.otubo.net/2009/12/vivo-3g-using-huawei-e1756-on-ubuntu.html](http://www.otubo.net/2009/12/vivo-3g-using-huawei-e1756-on-ubuntu.html)

read the comments at the bottom of the page as their is a revision.

Most of it revolves around usb_modeswitch.  This a thread here: [http://ubuntuforums.org/showthread.php?t=1395965&highlight=usb+modeswitch](http://ubuntuforums.org/showthread.php?t=1395965&highlight=usb+modeswitch) on modeswitch for a different Huwai modem but it may help.

---

### Post by alexfish on 2010-02-10
hi

You could try the latest "USB MODESWITCH "integrated package from

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

read the instructions very carefully / if you are a novice , seek help

or the latest debian package 


[LIST]
[*][SIZE=2][http://packages.debian.org/sid/usb-modeswitch](http://packages.debian.org/sid/usb-modeswitch)[Package  ]("http://packages.debian.org/sid/usb-modeswitch")[/SIZE]
[/LIST]


the device listing is the same as # Huawie 1692

Use wvdial to make the connection

There is also A post here . it is in Portuguese so use the Translate on the browser

[http://www.otubo.net/2009/12/vivo-3g-using-huawei-e1756-on-ubuntu.html](http://www.otubo.net/2009/12/vivo-3g-using-huawei-e1756-on-ubuntu.html)

Regards

alexfish

---

