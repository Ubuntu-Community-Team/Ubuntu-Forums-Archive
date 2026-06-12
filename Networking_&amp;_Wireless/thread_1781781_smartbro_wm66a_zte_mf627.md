---
title: "smartbro wm66a zte mf627"
date: 2011-06-14
forum: Networking &amp; Wireless
---

### Post by caloy230 on 2011-06-14
need a little help here...i cant get my smartbro to work on ubuntu 11.04. model wm66a... hindi madetect ung device pag gumagawa aq ng new mobile broadband connection.meron nman n siyang usb modeswitch at usb modeswitch data..ano po kaya marapat...maraming salamat po

---

### Post by itagomo on 2011-07-20
dati pag ka plug ko lang ng smartbro, automatic connect agad ng Ubuntu. Gamit ko nun 10.04. nag upgrade aku sa 10.10, di sya makita. hanap tayo tol ng soluxon.

---

### Post by itagomo on 2011-07-20
gumana na sakin with usb_modeswitch.

How to Connect Steps:

- turn on your PC pero dapat naka plug na smartbro
- pag ka boot, go to Terminal then type lsusb
- lalabas mga available plugged devices
- piliin ang naiiba, ganito lumabas sakin:

Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[COLOR="red"]Bus 001 Device 004: ID 1c9e:9605 [/COLOR]
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

- walang label/title yun pang fourth line, sigurado yun na si smartbro

- yun nasa left ay ang vendor ID (1c9e), right naman product ID (9605)

- tapos run this command:

sudo usb_modeswitch -v 0x1c9e -p 0x9605 -V 0x1c9e -P 0x9605 -H

- nilagyan ko lang ng '0x' yun vendor & product id (-v means vendor ID, -p product ID, -V is target ven ID, -P is target prod ID, basta ganun, try mu issue this command: usb_modeswitch for more info ng mga options)

why '-H' sa dulo? (hula ko Huawei gamit ko, parehas lang tayo wm66a), try mo dud, kaya lang ang bagal. ininsert ko nalang sim sa Nokia for tethering, mas mabilis pa.

Goodluck bro!

---

### Post by neen2k on 2011-07-20
[http://ubuntuforums.org/showthread.php?t=1807718](http://ubuntuforums.org/showthread.php?t=1807718)

same here mga bossing. taga mga taga sb ba kau?

usb modem nga lang gamit ko. huawei 1552.

paano ba gumawa ng batch file sa linux?

para gawan natin yan para hindi na type2x paulit2x.

newbie din ako sa linux pro at least napagana nman ang vpn client. manual nga lang wla pang program.

---

### Post by itagomo on 2011-08-09
nilalagay ko yun command sa StartUp Applications

System > Preferences > StartUp Applications

Click 'Add'

Name: SmartBro
Command: sudo usb_modeswitch -v 0x1c9e -p 0x9605 -V 0x1c9e -P 0x9605 -H
Comment: SmartBro AutoConnect

everytime nag-startup Ubuntu, hintay lang ako, auto-connect na.. pero sakin, mga less than 3mins bago sya auto-connect, tagal din..

---

### Post by itagomo on 2011-08-09
nilalagay ko yun command sa StartUp Applications

System > Preferences > StartUp Applications

Click 'Add'

Name: SmartBro
Command: sudo usb_modeswitch -v 0x1c9e -p 0x9605 -V 0x1c9e -P 0x9605 -H
Comment: SmartBro AutoConnect

everytime nag-startup Ubuntu, hintay lang ako, auto-connect na.. pero sakin, mga less than 3mins bago sya auto-connect, tagal din..

---

