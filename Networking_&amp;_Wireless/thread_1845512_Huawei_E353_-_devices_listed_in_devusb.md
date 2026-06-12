---
title: "Huawei E353 - devices listed in /dev/usb/"
date: 2011-09-17
forum: Networking &amp; Wireless
---

### Post by expert_vision on 2011-09-17
I plan to migrate E353, and I have read that some people here did use E353. What I wnat to ask them is what devices were listed in /dev/usb/. Was it like with other Huawei modems, 3 serial port devices named /dev/usb/tts/* .. or similar ?

---

### Post by pdc on 2011-09-17
> I plan to migrate E353

so you plan to use it?

from here

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=707&sid=0cd159e66ce5d626a483bb9c2f849f60](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=707&sid=0cd159e66ce5d626a483bb9c2f849f60)

it seems to work fine

(as you may well know, these devices are first seen as virtual CD-ROM devices; they need switching to being seen as a modem: and usb_modeswitch *par excellence* does this...............)

.......so ..... you don't need to worry about /dev/usb etc .......surely you can just plug it in !!  :p

---

### Post by expert_vision on 2011-09-18
I found out that there are 5 serial port devices created, ttyUSB* (after is switched):
```
Sep 17 23:07:04 tvbox mtp-probe: checking bus 2, device 10: "/sys/devices/pci0000:00/0000:00:06.1/usb2/2-2"
Sep 17 23:07:04 tvbox kernel: [ 9419.438401] option 2-2:1.0: GSM modem (1-port) converter detected
Sep 17 23:07:04 tvbox kernel: [ 9419.438522] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
Sep 17 23:07:04 tvbox kernel: [ 9419.438626] option 2-2:1.1: GSM modem (1-port) converter detected
Sep 17 23:07:04 tvbox kernel: [ 9419.438694] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
Sep 17 23:07:04 tvbox kernel: [ 9419.438769] option 2-2:1.2: GSM modem (1-port) converter detected
Sep 17 23:07:04 tvbox kernel: [ 9419.438827] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
Sep 17 23:07:04 tvbox kernel: [ 9419.438915] option 2-2:1.3: GSM modem (1-port) converter detected
Sep 17 23:07:04 tvbox kernel: [ 9419.438979] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB3
Sep 17 23:07:04 tvbox kernel: [ 9419.439065] option 2-2:1.4: GSM modem (1-port) converter detected
Sep 17 23:07:04 tvbox kernel: [ 9419.439121] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB4
```thx to **tvboxspy**
The reason I was interested in this was because I run a bunch of scripts through Minicom to monitor the modem, send SMSs and in the future, phonecalls (I can't switch serial connection in Minicom in data mode after ATD<number>; .. ATD<number> (without ";") gives NO CARRIER).

**pdc**, the problem is that I'm not using this on ubuntu and rather on a linux based router (more precisely, [Oleg's firmware]("http://code.google.com/p/wl500g/")) which uses a modemswitch version that doesn't list this modem. Anyway it might work though, and even if it won't, I have the right information (MessageContent) in the link you provided. Also I found on google USB_ModeSwitch versions that already list E353. Thanks

How is stability, did you experience drop outs (spontaneous disconnection)?

---

### Post by kliq on 2011-10-13
>  I run a bunch of scripts through Minicom to monitor the modem, send SMSs and in the future, phonecalls@ [expert_vision]("http://ubuntuforums.org/member.php?u=1442549"),   - [ Or Anyone ]
Do you mean that the Mbb dongle can be used to directly send text messages to a mobile phone as well as just connect to the internet?

Or Anyone?

---

### Post by expert_vision on 2011-10-14
Exactly .. in windows you can do that easily through Mobile Partner app, in linux you have to improvise. Basically this is done through AT commands (Hayes) sent over a serial link to the modem. What this Broadband dongles do, is that they create 3 or more serial port over USB that can be used simultaneously .. i.e one is used for internet connection and another for monitoring signal strength, SMS, calls .. whatever you can do with AT commands.

[Here]("http://www.atcommander.com/download/AT_Command_Specification/") are 2 documents with Huawei command set & specification. They're not recent, but they'll do.

---

