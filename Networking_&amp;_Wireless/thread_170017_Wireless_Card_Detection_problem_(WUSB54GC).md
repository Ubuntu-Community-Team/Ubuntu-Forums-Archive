---
title: "Wireless Card Detection problem (WUSB54GC)"
date: 2006-05-03
forum: Networking &amp; Wireless
---

### Post by Steel3 on 2006-05-03
I recently purchased a WUSB54GC wireless USB card so I can connect to a couple already existing networks at my home and in my apartment.  I am able to set up and connect in windows (I'm posting from it right now), so the wireless network is set up correctly.

I'm running Breezy, and I tried to follow a few of the sets of directions, particularly from this page:  [https://wiki.ubuntu.com/WiFiWithSomeoneElsesRouterHowTo](https://wiki.ubuntu.com/WiFiWithSomeoneElsesRouterHowTo)

Unfortunately, the device doesn't show up when I run iwconfig, or in the GNOME network tools.  What should I do to get it to recognize the device?

Thanks

---

### Post by Steel3 on 2006-05-04
Sorry to bump this up and for the newb question, but is there some way I can look up what chipset the device uses, and then proceed from there?

---

### Post by PokeMAME on 2006-05-08
I've been trying to get the same to work, too.

I posted 2 weeks ago and nobody answered.

I've tried the various things that have been posted here to no avail.  My LINUX skills are weak and I have little or no idea what I was trying and whether or not it was correct.

The most I could find was that the Linksys WUSB54GC is related to "RaLink" RT73 drivers?!?!?!?  But I have no idea if this is true or not.

---

### Post by damianubuntu on 2006-05-11
I managed to get a LInksys wusb54g wireless usb adaptor running in Breezy with this howto:

[http://doc.gwos.org/index.php/Rt2x00drivers](http://doc.gwos.org/index.php/Rt2x00drivers)

Another useful site for me was:

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

and I think I got the device driver connection from:

[http://linux-wless.passys.nl](http://linux-wless.passys.nl)

I don't know if the 54gc is the same as teh 54g, but it might be worth a go.

In the UK you can call Linksys on 0800 0261418 or try [www.linksys.com](www.linksys.com) for a more local number.  They should be able to confirm whether the 54g and 54gc are the same.

having said all that I'm now struggling to get it to work in Dapper!
You were warned!!

---

### Post by Steel3 on 2006-06-09
Sorry to bump this up, but now that I'm running Dapper I'm still trying to get this to work.  One of the reasons why I bought this particular wireless card was because I thought the chipset was more linux friendly or something... I guess I was confused.

Has anyone been able to get this to work in Dapper?

---

### Post by burgermann on 2006-06-20
For dapper I followed this guide - [funcation.blogspot.com]("http://funcation.blogspot.com")

First step is you'll have to apply a couple of packages.

most important is build-essential, linux-headers-2.6.15-23-386 and linux-kernel-headers

Apply those and you should be ready to follow the guide.

---

### Post by insyzygy on 2006-07-03
Burgerman.

 I'm curious. I have tried the funcation steps and everthing worked however the new device rausb0 won't let me change its essid. Did you have any problems like this.

Update: Actually it does work but it has a feature (which seems like a bug to me). It seems that if you try to set the essid and it can't associate that moment it immediately defaults to " ".  Today I tried in a different location with a stronger signal and it worked fine. Every other card I have lets you set the essid even if there is no wifi around, but perhaps this isn't uncommon. Anyone having problems setting this up let me know as it was kind of a pain and I would be glad to help anyone avoid the pitfalls. I'm running dapper (though my kernel is a custom 2.6.17.3)

                                                                                                       Josh

---

### Post by aqau on 2006-07-23
After following that guide, the only way to change your essid is to edit the do_wep file.  

Do this by:  sudo vi /etc/network/do_wep

and change eeeeee in this file to your essid and xxxxxxxx to your wep key (if you have one. if you don't have security jsut delete "key restricted xxxxxxx")  you can delete nick nnnnnnn (unless you know what it is...:-) i don't.

---

### Post by bikeboy on 2006-07-23
To identify what type of chip your wireless card uses you need to type the following into a terminal.```
lspci | grep Network
```That's the quickest way at least. It should list what type chipset it is because even the same model of wireless card can vary its chipset. That way it's easier to find the instructions for getting it going.

---

### Post by wieman01 on 2006-07-23
I would use ndiswrapper and the native Windows driver. That's the easiest solution in my opinion. There is enough documentation & howtos available in this forum.

I am using WUSB54G V4 with ndiswrapper and have WPA2/RSN enabled. Works like a charm.

---

### Post by Albaraha on 2007-07-31
Any one successfull with this wireless card?

---

### Post by kevdog on 2007-07-31
Is this an rt73 or rt2500 driver -- Would help for other to clarify the installation

---

### Post by Albaraha on 2007-08-01
I've get it resolved.
I followed diepruis steps on [this thread]("http://ubuntuforums.org/showthread.php?p=3110762").
This WUSB54GC card has rt73 driver.

---

