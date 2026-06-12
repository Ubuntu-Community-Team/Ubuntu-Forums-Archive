---
title: "Wifi not working after reboot"
date: 2012-12-26
forum: Networking &amp; Wireless
---

### Post by ohmy28 on 2012-12-26
Hi guys,
I just reinstalled Ubuntu 12.10 and I was able to update my computer with wifi. But since I rebooted I didn't have wifi. I checked additional drivers and everything was good. So under system settings I went on Networking and saw that wireless wasn't even listed. So after searching I was able to get it to work by running:

 sudo apt-get install --reinstall bcmwl-kernel-source

and everything was ok but once again after rebooting, my wifi doesn't work again until i run the above command. Is there anyway to having it stick after running the command? I never had this problem with 12.10

---

### Post by ohmy28 on 2012-12-26
Hi guys,
I just reinstalled Ubuntu 12.10 and I was able to update my computer  with wifi. But since I rebooted I didn't have wifi. I checked additional  drivers and everything was good. So under system settings I went on  Networking and saw that wireless wasn't even listed. So after searching I  was able to get it to work by running:

 sudo apt-get install --reinstall bcmwl-kernel-source

and everything was ok but once again after rebooting, my wifi doesn't  work again until i run the above command. Is there anyway to having it  stick after running the command? I never had this problem with 12.10 before.

---

### Post by ohmy28 on 2012-12-26
Was able to follow this and now everything is fine:p

[http://askubuntu.com/questions/232532/cant-get-wireless-working-on-12-10-and-dell-latitude-d630](http://askubuntu.com/questions/232532/cant-get-wireless-working-on-12-10-and-dell-latitude-d630)

---

### Post by ohmy28 on 2012-12-26
Was able to follow this and now everything is fine :razz:

[http://askubuntu.com/questions/23253...-latitude-d630]("http://askubuntu.com/questions/232532/cant-get-wireless-working-on-12-10-and-dell-latitude-d630")

---

### Post by overdrank on 2012-12-26
Please do not create multiple threads on the same issue. Threads merged.

---

