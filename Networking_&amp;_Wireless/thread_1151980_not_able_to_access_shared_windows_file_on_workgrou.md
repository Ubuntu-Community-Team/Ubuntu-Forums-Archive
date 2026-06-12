---
title: "not able to access shared windows file on workgroup"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by anshul_nit on 2009-05-07
I am using ultimate version 1.8 of ubuntu..but i am not able to access windows drive or shared folders from my machine.The windows machines are showing at the network places but whenever i double click on it, happens nothing. I have installed samba and able to share folders from my ubuntu machine and shared folders can also be accessed from any machine of microsoft eg xp or vista on LAN.
I am not able to figure it out..
plz give the suggestions what can be the problem
thanks..

---

### Post by anshul_nit on 2009-05-07
to access an ip address..
eg
smb://172.16.20.89  also doesnt works and my lan connection setting is fine

---

### Post by mattgyver83 on 2009-05-07
I had this problem as well originally.  Here is what i had to do to get it working.

1.  sudo gedit /etc/samba/smb.conf
	verify domain is correct 'workgroup = your_workgroup'
2.  sudo apt-get install winbind
3.  sudo gedit /etc/nsswitch.conf
4.  edit 'files' line to include 'wins' before dns and m4dns
	hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4


Just verify #1 first as it could be all that is wrong.If not follow through with the rest of the procedure.

That should get you up and running, and it will then prompt for your username and password.

---

