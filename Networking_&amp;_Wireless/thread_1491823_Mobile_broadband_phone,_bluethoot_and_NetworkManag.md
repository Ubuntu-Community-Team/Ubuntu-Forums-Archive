---
title: "Mobile broadband phone, bluethoot and NetworkManager setup"
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by fgianardi on 2010-05-24
Hello everyone,
I ask your help to diagnose a problem.
For business reasons I use a broadband internet connection via a mobile phone's connected via bluetooth [rfcomm]. Speed is not the maximum but it is more than sufficient for my work.
For configuration of ppp I followed this [guide]("https://help.ubuntu.com/community/BluetoothDialup")
Pon pulls up dialup, but I can't navigate also if resolv.conf and default route are correct. In addition I would like to use the NetworkManager that by default, does not see the device.
I worked around the problem this way:

I modified the / etc / rc.local so that launch at boot time:

# Rfcomm bind yes

After starting Lucid Lynx, bluetooth connects to the phone but NetworkManager does not see the modem.
When I run the connection manually, by:

# Pon BluetoothDialup

NetworkManager sees the device, but can not use it because obviously it is locked by the ppp daemon.
So I close the connection with:

# poff

Now NetworkManager sees the broadband modem via / dev/rfcomm0, dialup is performed properly. I can finally surf and just enable vpn with NetworkManager.
I wish that all start automatically at boot, without the need to manually connect and disconnects the dialup to use, finally, the NetworkManager.
Can you help me diagnose the problem? dmesg and syslog do not help, and google has no answers ...


Thank you to everyone who help me.

P.S. Forgive my rough English.
fgianardi

---

### Post by fgianardi on 2010-06-06
To  answer my question: Blueman solves the problem! : D

Thank's to all.
fgianardi

---

