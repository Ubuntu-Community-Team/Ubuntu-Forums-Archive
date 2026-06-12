---
title: "Network Manager Reinstall"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by Sukotto on 2009-09-08
So the other dau I installed Wicd which uninstalled the defult network manager. I really did not like Wicd after all, it kept dropping the wireless connection so I removed it. Stupid me not I have no way to connect the wireless.

I tried sudo apt-cdrom add

and then 

sudo apt-get install network-manager-gnome
but it trys to connect to us.archive.ubuntu.com which it cant because I have no wireless manager. I thought the above command would pull it off the install cd. Now I am stuck with no wireless connection and I need to get it back.

Thanks!

---

### Post by t0mppa on 2009-09-08
You have to comment out (add a # in front of the lines) the online repositories from the sources file (/etc/apt/sources.list), so it doesn't try connecting to them for that to work.

The other option is to manually connect to your wireless network and then run the install normally, you can find out how that's done from [here]("http://ubuntuforums.org/showthread.php?t=571188").

---

