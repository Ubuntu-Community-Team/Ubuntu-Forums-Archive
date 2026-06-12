---
title: "WLAN working randomly"
date: 2012-05-09
forum: Networking &amp; Wireless
---

### Post by seamusd on 2012-05-09
Hey guys,
I am not sure, if my problem is related to the one discussed here: [http://ubuntuforums.org/showthread.php?t=1974852](http://ubuntuforums.org/showthread.php?t=1974852)

Anyway, I'll just explain what hapened: I got a new Lenovo ThinkPad X220 and installed Ubuntu 12.04. Everything worked and still works fine with WLAN networks that are WPA2 encrypted. The problem just occurs on WPA2 Enterprise encryptions that require a certificate and username/password combination.

It seems to work randomly, but the connection aborts after a few minutes/hours and then i cannot login anymore. I really don't have a clue what's going on. I tried several fixes, but nothing succeded. I attached the output of

dmesg > hossub.txt
ifconfig >> hossub.txt
iwconfig >> hossub.txt
cat /etc/resolv.conf >> hossub.txt
ping -c3 192.168.1.1 >> hossub.txt

as it was suggested in a similar thread. Please let me know if I can provide any more information.

Thank you very much!
Regards
Tim

 EDIT: Finally found the launchpad bug corresponding to my problem: [https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/969343](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/969343) I'll not close the thread, probably one of you guys still has a workaround!

---

