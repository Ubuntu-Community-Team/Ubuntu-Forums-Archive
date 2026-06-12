---
title: "Network manager says cable is unplugged...?"
date: 2012-06-03
forum: Networking &amp; Wireless
---

### Post by Reboot.Revival on 2012-06-03
Hey I have been using Ubuntu since 10.04 came out and have visited the forums but never posted.  I cannot figure this out so here I am posting the question.  I havent used Ubuntu much since I upgraded to 11.10 and I had problems with 11.10 dropping internet connection after 2 or 3 minutes and was able to figure that out.  The r8169 driver problem.  Managed to fix that, and then upgrade to 12.04 last night.  From the first time it booted it showed no connection.  My cable is plugged in and works(so does wireless), but the network manager says it isn't plugged in.  I tried this, 

"sudo service network-manager restart"

but no dice.   I can't figure it out despite having searched aroud for hours.  I see similar problems but nothing that fixes mine.  Most of them are just cable problems which doesn't help me. I also have a dual boot to Win7 on the drive which connects just fine.

EDIT:  How Do I change it to [SOLVED]

---

### Post by chili555 on 2012-06-03
I hope this will be helpful:  [http://en.opensuse.org/SDB:Realtek_8169_driver_problem](http://en.opensuse.org/SDB:Realtek_8169_driver_problem)> The Realtek Windows driver disables the NIC at Windows shutdown time. The current linux r8169 driver does not know how to turn on the NIC from this disabled state, therefor the device will not respond, even if the driver loads and reports that the device is up.

---

### Post by Reboot.Revival on 2012-06-04
That didnt really help. It made the assumption I could download something to my src folder and gave steps to do that.  I had to work around it.  When 12.04 started it loaded up r8169, despite having it blacklisted.  My old r8168 driver wouldnt reinstall so I had to download the new one on my win7 and then pull it over from Ubuntu. From there I unpacked it and went through the terminal to get it. 

"# cd /home/username/Desktop/r8168-8.031.00"
then
"# ./autorun.sh"


Now its working, and I am writing this post on it.

---

