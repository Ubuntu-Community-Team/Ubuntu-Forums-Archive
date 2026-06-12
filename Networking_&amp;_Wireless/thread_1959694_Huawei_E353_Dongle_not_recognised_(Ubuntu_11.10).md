---
title: "Huawei E353 Dongle not recognised (Ubuntu 11.10)"
date: 2012-04-16
forum: Networking &amp; Wireless
---

### Post by phildogg on 2012-04-16
NOW RESOLVED. THANKS FOR THE HELP!

Hello,
I'm trying to get my Huawei E353 dongle to work on Ubuntu 11.10 (64 bit). The laptop is a Thinkpad X121e, with an Intel i3-2367M processor.

When I insert the dongle, it is not recognised, so am assuming that I need some drivers.
I've searched online, but have not had any luck. 
After reading a few forums, I have ensured that the latest versions of modemmanager, usb-modeswitch & usb-modeswitch-data are installed.

If I can get the dongle to be recognised, would it then be possible to run the included software (on the dongle) using either wine or Windows XP in parallel to connect to the internet? 

If anyone can help, I would greatly appreciate it.
Thanks,
Phil

---

### Post by westie457 on 2012-04-16
Hello and welcome to UF.

With the dongle plugged in can you open a terminal pressing 'Ctrl+Alt+T' then type in lsusb and hit Enter.

Then in a New Reply paste the output in the window, highlight it then click on the # at the top of the window to place [ code] [ /code] tags.

Thank you.

---

### Post by phildogg on 2012-04-16
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 04f2:b2b9 Chicony Electronics Co., Ltd
```

There you go.
cheers for the quick response

---

### Post by westie457 on 2012-04-16
> Bus 002 Device 003: ID 04f2:b2b9 Chicony Electronics Co., Ltd

Hi, apologies for the slow response. Have spent some time researching this issue and have to admit that I am stumped on this.

If the quote above is your USB dongle I have not found anything on Google or googlubuntu that is of any help.

Could only find the same things that you have already tried and a couple of bug reports concerning the above device which seem to relate to a webcam.

Sorry I cannot help you further.

---

### Post by phildogg on 2012-04-17
It has now decided to start recognising the dongle. I don't know why, as I didn't investigate any further (???).
This comes up now in addition to the other output
```
Bus 002 Device 006: ID 12d1:1506 Huawei Technologies Co., Ltd.
```
When I open XP in parallel, I am able to install the software and connect to the Internet.
Thanks a lot for the help!

---

### Post by alexfish on 2012-04-17
Don't know if this will help

This device may have Ether type interface

this device may need Huawie drivers to be installed for the ether interface to work

Check out here

Post #[**64**]("http://ubuntuforums.org/showpost.php?p=11709821&postcount=64")

---

### Post by coffeecat on 2012-04-17
@phildogg, the Huawei E353 works out of the box with Ubuntu 11.10. You do not need to install any driver. I don't know why yours was not detected at first, but now it is, see if the dongle is flashing a blue light. Click on the network manager applet icon near the top right and you should see the line "New Mobile Broadband (GSM) Connection" in the drop down menu. Click on this and follow the wizard, after which you will be connected so long as the dongle detects a sufficient signal.

Give the system a couple of minutes after you plug the dongle in. It can take this long for the mobile connection choice to appear in the network manager menu.

---

