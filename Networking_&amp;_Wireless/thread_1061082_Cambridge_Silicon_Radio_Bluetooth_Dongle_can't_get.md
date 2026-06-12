---
title: "Cambridge Silicon Radio Bluetooth Dongle can't get it working"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by Martyn12 on 2009-02-05
Hello team,

I have a Mini bluetooth dongle (Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)) which initially I thought wasn't being seen at all by Ubuntu Hardy (8.04) LTS. 
After a bit of messing around and reading lots of threads on here I now know that it is being seen by the system and I can even get it to make my phone 'buzz' by typing:
```
sudo hciconfig hci0 reset 
```
followed quickly by
```
sudo hidd --connect AA:BB:CC:DD:EE:FF
``` where this is the address (? BD)

Unfortunately when I put the shared passcode into my phone they both time out without connecting. 

Should my dongle have a name? If so, where do I put it? Also, I have added every reference possible in the repos with Bluetooth in and I have two icons in the info bar - one is Bluetooth Manager and the other is from gnome-bluetooth. BT manager has no devices listed and no services listed. 

I have also searched for two modules, btusb and hci_usb. Neither are on my system and searching the packages, neither are listed on their either. Any clues? 

If you need any more detail please let me know. BTW, I have also tried unsuccessfully with Bluesoleil which looks good (or would if it worked!). 

Thanks in advance, 


Martyn.

---

### Post by xoorox on 2009-04-11
I've had success using Blueman instead, having followed this guide. - [Installing Blueman]("http://www.ubuntugeek.com/blueman-bluetooth-manager-for-ubuntu.html")

or just look here [http://blueman-project.org/downloads.html](http://blueman-project.org/downloads.html)

---

### Post by robhem on 2009-12-24
Hi, 

I too was finding that I could not get bluetooth to work on Jaunty using a Cambridge Silicon Radio Bluetooth Dongle. I followed the link above given by xoorox and installed Blueman. I can confirm this has my bluetooth working. Thanks to xoorox for posting the link. 

Rab

---

### Post by aletum on 2010-01-27
Hi I'm running Karmic with (Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode). Couldn't get it to work, got hci_cmd_task: hci0 command tx timeout in kernel logs.
After downgrading to Jaunty's bluez and blueman (via PPA) I noticed some improvements, viz.
In certain combinations of the following the dongle gets recognized and even though I still get hci_cmd_task: hci0 command tx timeout in logs, blueman sees it.
This certain combination is rather unpredictable:
I need to unplug the dongle and put it back in, having issued /etc/init.d/bluetooth stop plus making sure that rfkill doesnt block bluetooth
rfkill list
if it shows it is blocking type:
rfkill unblock bluetooth
And while detection is still rather random, it's better than nothing.

---

