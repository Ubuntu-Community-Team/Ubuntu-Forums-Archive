---
title: "Cant Connect to Network When login is required using browser."
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by zieklecknerizer on 2010-02-03
On the college campus that i go to it requires you to log in to the internet connection through the internet browser like firefox. so while on campus the internet connection will not connect while im on my ubuntu 9.10 installation. how can i set up the network connection to tell it to allow me to connect and then log in to get network connection?

---

### Post by Fire_Chief on 2010-02-03
If it requires you to login to the network before allowing Internet access, then you are getting an IP address on the network. It sounds like you are on wireless. So you get on campus, boot your laptop and login to Ubuntu. NetworkManager should detect the wireless network and connect to it giving you an IP address, DNS, gateway, etc. Then if you open Firefox, does it take you to a login page to enter your credentials?

Any additional details you can give on the process, the specific software, the login page, etc would be very helpful.

---

### Post by zieklecknerizer on 2010-02-03
like it wont even connect to the network. no ip or anything. the connection just will try to connect for a while then say network disconnected.

---

