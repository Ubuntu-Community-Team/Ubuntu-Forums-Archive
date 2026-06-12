---
title: "how can i connect from my work pc to home pc"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by inter-m on 2009-01-21
im using windows xp on my work pc... sometimes i need to connect to my two computers at home... one is a pc running windows xp... the other is a toshiba laptop running ubuntu hardy... at home i connect to the internet using a wireless connection through a router... i would like to know the way i can connect to my computers cuz i had searched the net but not many helpful howtos r out there... thanx in advance...
K.H

---

### Post by docawk on 2009-01-21
First of all your router has to have "Port forwarding" where you can establish rules that allow incoming traffic form outside on a specific port to be forwarded to local machine on a local port.

e.g.: 0.0.0.0:2222 -> 192.168.1.2:22

Would forward incoming traffic on port 2222 from any IP to your local machines local port 22 (SSH).
Be aware of that those piercings are a threat to security of your system since traffic from outside gets forwarded unfiltered to your local machines. Use it wisely;-)

Then you could use e.g. Putty SSH client ([www.putty.org](www.putty.org)) to connect from your work PC to your Linux Notebook via SSH.
Connection to a Windows XP PC, I have no idea, but there could be something, which works similar.

Alternatively, you could work on a VPN (Virtual Privat Network) which is a ability of your internet router. Anyways I have no experience with that. Sorry.

Hope that helps a little

---

### Post by geus on 2009-01-21
You might wanna check [NoMachine NX]("http://www.nomachine.com/select-package.php?os=linux&id=1") 

Free, works great and some good documentation on the site. This requires openssh to be installed and configured properly. But enough guides around on the internet for that or search this forum. For the XP machine you could use remote desktop assuming it's XP pro. Again; enough howto's for that, google it. And obviously to have static IP´s on your machines and the proper ports forwarded on your router if using NAT.




PS: The laptop may be kind of tricky unless it's on 24 hours a day.

---

