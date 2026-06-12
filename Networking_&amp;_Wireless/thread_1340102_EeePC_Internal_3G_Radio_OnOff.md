---
title: "EeePC Internal 3G Radio On/Off"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by CrunchBuntu on 2009-11-28
Hi guys,

Has anyone got any ideas for this problem I'm having? I've looked everywhere but can't find reference to this particular situation.

I have WinXP as my main system but have been playing around with Ubuntu 9.10 installed on an SDHC card.
I'm using a "Live" setup with a persistence loop file.

I just got a 3G sim card and have been trying it out in Windows and Ubuntu using the built in Huawei EM770 modem of my EeePC 901 Go.
In Windows the Mobile Partner software that comes supplied with the modem drivers has a "disable radio" function that presumably helps to save power especially when running on the battery.
When I boot into Ubuntu after disabling the radio in Windows I am unable to use the modem and have to reboot into Windows to re-enable it.

When I first installed Ubuntu I had a problem with the webcam being switched on by Ubuntu at boot up, and that state being in effect back in Windows, overriding the previous setting.
The webcam was apparently being enabled at the bios level. The Asus EeePC tray utility for hardware specific control in Windows seemed to enable/disable it at the bios level too.
I was eventually able to stop Ubuntu turning the camera on by default at every boot.

Things seem to be different with the 3G modem. The modem remains active at the bios level but the radio power is switched on and off independently.

Network manager in Ubuntu has been able to use the modem but does not appear to have any ability to enable the radio.
If the radio is not enabled in Windows then network manager cannot connect and sometimes does not offer 3G as an option at all.
I have to reboot twice. Once into Windows to re-enable the radio and again to get back into Ubuntu.
So, does anybody know how to turn the radio on and off under Ubuntu?

As a minor side issue if anyone can suggest how to get network manager to remember all the details for the 3G connection it would be appreciated too. For some reason I have to keep re-telling it what password to use though it remembers the APN and username settings. I have ticked the box to make it available to all users which stopped me having to enter a password for the wifi connection every time it connected.

I should warn you that I'm not particularly Linux savvy but can usually get by with moderately detailed instructions.

Thanks in advance for any light you may be able to shed on this.

---

### Post by gunnar123 on 2009-12-29
Usually the discovery of the USB device shall trigger initialisation of the modem. You use scripts under /etc/udev/rules.d and such.

There are many forum threads on this so some googling could get you to the right place.

---

### Post by alawson on 2010-05-02
CrunshBuntu, did you get to the bottom of this?
It looks like I may be having the same problem under 10.04 with an eeePC 1000HG.

Cheers!

---

### Post by el_rico on 2010-09-21
Same here (with an 1005HAG though). Do you know how to do this ?

Thanks!

---

### Post by Herfen on 2011-06-02
Same here with asus eeepc 1005hag/Hog and actual ubuntu release.

---

