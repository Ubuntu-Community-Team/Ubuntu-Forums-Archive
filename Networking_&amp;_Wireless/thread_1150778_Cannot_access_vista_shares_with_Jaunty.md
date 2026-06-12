---
title: "Cannot access vista shares with Jaunty"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by linuxus95 on 2009-05-06
Hello and preliminary thanks to everyone who can help. I am relatively new to ubuntu and i am running Jaunty. I have problems accessing shares on my local network. I am trying to access vista shares. Strangely enough, i can ping the computer i want to access both with an ip and with a its NetBios name. When I try to access the share Nautilus or using the connect server option, i get the error message could not list the files in the share or something like that. I can also see my workgroup name in the network place in file browser, but when i try to access it i get the same message. I have already set up the correct name for my workgroup in the smb.conf file.

Thanks for any help and sorry if this has been covered somewhere.

---

### Post by linuxus95 on 2009-05-07
Bump :confused:

---

### Post by mattgyver83 on 2009-05-07
This is what worked for me, 

1.  sudo gedit /etc/samba/smb.conf
	verify domain is correct 'workgroup = your_workgroup'
2.  sudo apt-get install winbind
3.  sudo gedit /etc/nsswitch.conf
4.  edit 'files' line to include 'wins' before dns and m4dns
	hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

Just verify #1 and see if thats all the problem is, if not follow the rest of the procedures. 

Hope that helps.

---

### Post by linuxus95 on 2009-05-07
Thank you so much! This actually worked! A great and short tutorial on how to get this nightmare working.

---

### Post by mattgyver83 on 2009-05-07
While it works, im not the mastermind!  Thats was in response to a few posts that helped me, just put in order.

Glad to help however!

---

