---
title: "System failure when connecting to a WPA/PEAP network"
date: 2011-09-17
forum: Networking &amp; Wireless
---

### Post by Willem1 on 2011-09-17
I am experiencing a severe problem when connecting to the network at my university. They use WPA/WPA2 Enterprise, PEAP with MSCHAPv2 authentication. If I connect to this network, I actually get a connection and I can access the internet. But after about 15 seconds very strange, seemingly unrelated things start to happen:
[LIST]
[*]The KDE panel below suddenly hangs and restarts after 2 minutes. Then it works for about 15 seconds again, and it crashes again, and so on.
[*]The icons on the desktop get unresponsive.
[*]Adobe Flash Player randomly crashes in Mozilla Firefox. If I refresh the page, it works for a few seconds and then it crashes again.
[*]If I do not manage to disconnect in five minutes or so, usually the whole system hangs and the only way to shut it down is using the Magic SysRq keys. (Even Ctrl+Alt+F1 to go to tty1 doesn't work anymore.)
[/LIST]
If I am connected at my home network (WEP security) there is no problem at all.
There are other reports on a probably related issue, like [this]("http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2286"), [this]("https://bugs.launchpad.net/ubuntu/+source/plasma-widget-networkmanagement/+bug/577560") and other threads on this forum, but it seems that nobody has such extreme crashes like me.
As I am now connected to my home network to be able to post this, I am now unable to execute commands to get information about the network, but here is information about my system:
[LIST]
[*]Machine: HP EliteBook 8540w
[*]OS version: Kubuntu 11.04, 32 bit
[*]From the *lspci* command:
```
44:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
```
[*]From the *lsmod* command (I think these are the wireless modules):
```
iwlagn                284745  0
iwlcore               148964  1 iwlagn
```
[/LIST]
If you need more information, or information that I have to collect when I am connected to the university network again (on Monday), please ask.
Thanks in advance for any help! :)

---

### Post by Willem1 on 2011-10-22
For your information, this was solved when I upgraded to Oneiric. I have no idea what caused it, but I'm glad it is solved :)

---

