---
title: "Network manager not saving settings"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by owoaux on 2009-03-25
Hello, ubuntu guys. So, I'm trying to make my internet work on my PC after changing ISP. What I'm doing in Windows is:
1) Change the MAC address of my PC to the one my laptop has.
2) Enter IP address.
3) Enter subnet mask.
4) Enter gateway.
5) Enter DNS.
And it works then but when I try to do that in Ubuntu, first it is not saving the subnet mask i enter and then I can't even chose it from the menu in the tray, cause there's just some connection named "Automatic connection" or similar name, i forgot.

Can you help me?

---

### Post by Cheesehead on 2009-03-25
What kind of network connection are you trying to connect to?
What kind of errors do you get when you let Ubuntu try to connect automatically?
Er, why do you wish to spoof another machine's mac address?

---

### Post by owoaux on 2009-03-25
I don't know, it's normal lan connection.
There's no errors, no internet either. I don't want automatic connection with default settings.
There's no problem with the mac, it's just I haven't call them yet to enter my new mac.

---

### Post by owoaux on 2009-03-25
**UP^**
Please, I really need the help.

---

### Post by Iowan on 2009-03-26
Check settings in */etc/NetworkManager/nm-system-settings.conf.*.

---

