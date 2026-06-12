---
title: "Personal file sharing Preferences"
date: 2010-08-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by coolcaseley67 on 2010-08-07
Hi 


-when i go Personal file sharing Preferences .

- it says i can not enable it because the file its needs are not installed ...


- what are the files ???



any thoughts ???

thanks & 10:10 is looking good

---

### Post by qamelian on 2010-08-07
Go to the folder you want to share in the file manager. Right-click on the folder and click on Sharing Options. Put a check mark in "Share this folder". Ubuntu will tell you that the sharing service is not installed and will offer to install it for you at that point. Click the "install service" button and all should be well.

---

### Post by Morbius1 on 2010-08-07
"Personal File Sharing" has got to be the most misunderstood feature in all of Linuxdom.

Personal File Sharing is not Samba. It's a baby apache file server that uses avahi to announce to the network that it has one folder ( and only one folder ) to share at /home/user_name/Public. It requires the following packages be installed:
```
Apache2.2.bin
libapache2-mod-dnssd
```> Go to the folder you want to share in the file manager. Right-click on the folder and click on Sharing Options. This is samba - specifically it's a method of samba called Nautilus-share or Usershares. 

Personal File Sharing in use has been rather flaky on my network but it may work for you. On the whole I would suggest using the samba method qamelian suggested but that's just my opinion.

---

### Post by coolcaseley67 on 2010-08-07
hi  
 
yeah i've all ready got  samba  up and runing . 
 
 
I'll give it a go , file sharing  [SIZE=1]neededs MUST [/SIZE] to be improved ! 
 
on UI front that is ....:o

---

### Post by coolcaseley67 on 2010-08-07
hi 

it works ! 


thanks

---

