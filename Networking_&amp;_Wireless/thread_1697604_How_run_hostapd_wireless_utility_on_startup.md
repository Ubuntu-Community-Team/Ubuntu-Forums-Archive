---
title: "How run hostapd wireless utility on startup?"
date: 2011-03-01
forum: Networking &amp; Wireless
---

### Post by jogi.nayak on 2011-03-01
Hi

I run the following command on my terminal to start hostapd which sets up my router to behave like a wireless access point.

$ ./hostapd -dd hostapd.conf

The service starts successfully. But now i am trying to figure out a way to run this program automatically at start up so that my access point is permanently visible. Could somebody please guide me|?

Thank you!

---

### Post by ankith13 on 2011-03-01
all you need to do now is go to System > Preferences > Startup Applications. Click 'Add' and enter the name and give the path of your .sh file. It should do the work from there!


you can also add the command in the end of rc.local file.

---

### Post by jogi.nayak on 2011-03-03
Thanks a lot Ankith ! But the problem is that i need to run the script as root. Because i cannot restart the dhcp server without being the root.Which is why i think even if i follow the steps you said i dont see my script run at startup :-

script startap.sh ( chmod 777) :-

ifconfig wlan0 10.254.239.10
cd /etc/init.d
./dhcp3-server restart
cd /home/transit/hostap/hostapd
./hostapd -dd hostapd.conf

---

