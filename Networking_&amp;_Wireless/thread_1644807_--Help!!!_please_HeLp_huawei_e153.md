---
title: "-**-*Help!!! please HeLp huawei e153"
date: 2010-12-13
forum: Networking &amp; Wireless
---

### Post by pourjour on 2010-12-13
please help me to install huawei e153 on ubuntu  8.04
Please how i can do it:confused:
files needed or somthing else:(

---

### Post by cgroza on 2010-12-13
Take a look here: [http://******************/?How-to-Install-a-Huawei-E220-Modem-in-Ubuntu-Linux&id=1603708](http://******************/?How-to-Install-a-Huawei-E220-Modem-in-Ubuntu-Linux&id=1603708)
EDIT: The forum replaces my link with nonsens. Google this: "huawei install ubuntu"

---

### Post by pourjour on 2010-12-14
thankss but i need the rules file
and how to install usb-modeswitch without internet connexion
and thank u very much again

---

### Post by gradinaruvasile on 2010-12-14
Go here:

sakis3g.org

download the sakis3g script and launch it - preferebly in a terminal with the --interactive --console switches + root access (sudo).
Theoretically a simple "connect" should do it.

Some info on the Huawei-specific commands (if needed):

[http://www.linuxquestions.org/questions/debian-26/usb-mobile-broadband-huawei-e1750-on-debian-5-lxde-32-bits-848195/](http://www.linuxquestions.org/questions/debian-26/usb-mobile-broadband-huawei-e1750-on-debian-5-lxde-32-bits-848195/)

---

### Post by pourjour on 2010-12-14
> **gradinaruvasile said:**
> Go here:

sakis3g.org

download the sakis3g script and launch it - preferebly in a terminal with the --interactive --console switches + root access (sudo).
Theoretically a simple "connect" should do it.

Some info on the Huawei-specific commands (if needed):

[http://www.linuxquestions.org/questions/debian-26/usb-mobile-broadband-huawei-e1750-on-debian-5-lxde-32-bits-848195/](http://www.linuxquestions.org/questions/debian-26/usb-mobile-broadband-huawei-e1750-on-debian-5-lxde-32-bits-848195/)
thank you i'm going to try this

---

### Post by Ashan052 on 2011-04-26
Hi,
My computer have ubuntu 10.04. I bought new Huwaei E153 hsdpa usb modem. But it indicates only as usb storage. I can not install it to use as hsdpa modem. please instruct me.... how to install this modem
 
:(

---

### Post by Rewarp on 2011-08-09
I have a dual boot between Kubuntu 11.04 and Ubuntu 10.04.

In Kubuntu 11.04, simply plugging in the device allows it to be recognised and connected through my Huawei E153 HSPDA without any hassle at all. :KS

In Ubuntu 10.04, thanks to the hints above I downloaded Sakis3G [http://www.sakis3g.org/](http://www.sakis3g.org/)

And after installing it by downloading [sakis3g.gz]("http://www.sakis3g.org/versions/latest/sakis3g.gz"), and extracting it to /usr/bin, I ran

```
sakis3G --zenity
```

And out popped a clean GUI to help install and run your modem with your mobile broadband provider (in my case, DiGi in Malaysia.)

After everything has been configured, you may connect and disconnect via sakis3G, although annoyingly enough, I am unable to get it shown as connected in the network manager applet.

Oh well, at least I know the next LTS will automagically support HSPDA USB Modems. :)

---

