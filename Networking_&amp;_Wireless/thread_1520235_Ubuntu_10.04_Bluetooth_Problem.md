---
title: "Ubuntu 10.04 Bluetooth Problem"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by Nightstrike2009 on 2010-06-29
Hiya everyone,

I have a I.Tech BlueCON U2 V2.0 (Std O2 Bluetooth USB Dongle) and a Samsung G600 Mobile Phone.  

I have problems with "Bluetooth Applet" it sees some files but not others, resorting to me having to use VirtualBox and Windows just to get Bluetooth to function properly (It has no problems with Windows)

Any Ideas on how to get this working in Ubuntu 10.04? 
(I don't like having to use Windows) or is Ubuntu Bluetooth still Work In Progress at this point?

PS: I have totally migrated to Ubuntu 10.04 LTS and I am seeking a few Windows equivalents to make life easier this list is down to a couple of utilities now Bluetooth is one of them.

---

### Post by Nightstrike2009 on 2010-06-29
Looks like this problem is common a quick search shows that 9.04 and 9.10 users have problems with various bluetooth setups.

Is my hunch about Ubuntu Bluetooth being work in progress correct or is it just very buggy?

---

### Post by Nightstrike2009 on 2010-06-29
Looks like I am answering myself again huh, I know I am an intermediate but god this is getting silly, I seem to use Google more than I get any answers. :-(

---

### Post by kostkon on 2010-06-29
Mine works just fine. But what's your problem exactly.

My USB BT stick has this ID:
```
Bus 001 Device 009: ID 1131:1004 Integrated System Solution Corp. Bluetooth Device
```

---

### Post by cookie427 on 2010-06-29
Have you tried Blueman Bluetooth Manager (avaliable in Ubuntu Software Centre (Applications > Software Centre))? That works perfectly with my bluetooth usb stick.

---

### Post by Nightstrike2009 on 2010-06-29
I have since upgraded to blueman, problems still persist. It recognises some files on my mobile but doesnt others, works fine in windows but iffy in ubuntu. blueman looks an ace gui but these probs are very annoying, friends of mine report similar problems.

---

### Post by Nightstrike2009 on 2010-07-03
Got it working fine now, just needed to change settings as listed below:

> Click on Bluetooth applet

Select "Set up new device", select device, click "forward", enter pin on device

select "Preferences"

check "Make computer visible", then "receive files"

SHARE FILES OVER BLUETOOTH

Check "Share public files over Bluetooth"
Check "Require remote devices to bond with this computer"

RECIEVE FILES OVER BLUETOOTH

Check "Recieve files in Downloads folder over Bluetooth"
Accept files: "Only for set up devices"

check "Notify about recieved files"

Then click "Close"

Then use Phone to send files to Ubuntu PC over bluetooth

Enjoy :-)

---

