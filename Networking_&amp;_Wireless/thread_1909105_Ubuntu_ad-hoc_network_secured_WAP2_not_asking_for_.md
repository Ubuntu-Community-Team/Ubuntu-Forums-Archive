---
title: "Ubuntu ad-hoc network secured WAP2 not asking for password..!"
date: 2012-01-14
forum: Networking &amp; Wireless
---

### Post by deasher on 2012-01-14
Hi guys,
Ubuntu 11.10, Gnome 3.2.1
Create New Wireless Network > (inputting name, choosing WAP2 sec, inputting password).

My friend with win7 tries to connect to my network... no password is asked of them to connect to my network.

Anyone know what's going on? :|
THX, you guys rule!


P.S.
please assume i'm a dumb n00b when you reply

---

### Post by Selmi on 2012-05-15
did you learn something new?

i have same problem. it doesn't matter what security option i choose when i create/edit connection, when i try to connect from another device they find network open and no key/password is requested

when i check connection in network manager dialog (through connection information) it says "Security: WPA/WPA2" but it seems to net be the truth

from what i tried:
when i set WPA/WPA2 my network is in fact open. why it happens is written here [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/905748](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/905748) but it doesn't solve the problem for me
when i use WPE (any of them) then everything seems to be fine, but when i try toconnect from some other device it fails and in dmesg is message "wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)"

so i am stuck
i can have open network or none

i found thread which describes how to do it using config files: [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)
however when i triedit i found i can't boot into ubuntu anymore - on boot screen it 'waits for network interfaces' and fails. i better reverted everything back to how it was before

i don't know what else to try. maybe update oneiric to 12.04 and see if it will help somehow
i live in pretty crowded area so open network is out of question, even while experimenting i noticed few connections

---

