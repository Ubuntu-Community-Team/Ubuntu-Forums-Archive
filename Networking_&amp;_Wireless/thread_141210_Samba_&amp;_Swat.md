---
title: "Samba &amp; Swat"
date: 2006-03-07
forum: Networking &amp; Wireless
---

### Post by ivoencarnacao on 2006-03-07
Hi All!

Just installed Samba and Swat with sudo apt-get install samba swat but when trying to configure Samba with Swat by going to localhost:901 i get the connection refused  when atempting to contact localhost:901 alert.

Could anyone tell me what am i doing wrong?
I just want to share some folders on an Ubuntu box with a Windows LAN.

Thanks in advance,
Ivo Encarnacao.

---

### Post by bohmto on 2006-03-08
I think that you must do sudo gedit /etc/services and then uncomment port 901 if its 
have a # sign in the front off the phrase if its already uncomment then perhaps you have a firewall installed in that case you have to open the port for swat otherwise try reinstall the swat pkg

---

### Post by ivoencarnacao on 2006-03-08
I have checked everything you said in your post, and everything seems to be ok, but i keep having that connection refused when atempting to contact localhost:901.

Any other ideas?

Thanks for your answer!
Ivo Encarnacao.

---

### Post by WelterPelter on 2006-03-08
This probably isn't what you're looking for, but I configure Samba using Webmin. It works quite well.

---

### Post by ivoencarnacao on 2006-03-08
[QUOTE=WelterPelter]This probably isn't what you're looking for, but I configure Samba using Webmin. It works quite well.[/QUOTE]

Well, i was trying to configure Samba in a GUI way, Swat was my first choice!
I will now try Webmin, and see what i can do with it.

Ivo.

ps. WelterPelter's post leads me to another question, in your , UbuntuUsers opinion, what is the best GUI for Samba? NOTE: I am really trying to avoid configuring Samba by hand aka text-mode!

---

### Post by ivoencarnacao on 2006-03-08
In the meanwhile i have managed to configure Swat or, i think so... at least now i can access localhost:901 but... wheres my Shares, Printers and others stuff buttons? I only have Home, Status, View and Password!!!

What have i done wrong?



Please advise!
Ivo. :-?

---

### Post by ivoencarnacao on 2006-03-09
Any ideas?

---

### Post by ivoencarnacao on 2006-03-09
No one is using Swat? I dont believe it!
Guys, i really need your help here!

---

### Post by dgermann on 2006-03-20
ivoencarnacao--

I am at the same place right now. I think it is looking for you to login as root. But on Ubuntu there is no root user.

Anybody got a workaround for this?

---

### Post by dgermann on 2006-03-20
OK, here was the answer for me: 
[http://ubuntuforums.org/archive/index.php/t-1795.html]("http://ubuntuforums.org/archive/index.php/t-1795.html")

This got me in and let me work on SWAT.

---

### Post by chrism7 on 2006-03-22
[QUOTE=ivoencarnacao]In the meanwhile i have managed to configure Swat or, i think so... at least now i can access localhost:901 [/QUOTE]

I'm having the same problem connecting to localhost:901, I've checked my /etc/services file and OK, and even tried turning off the firewall and still no luck.  Can you tell me what you did to get to connect to localhost:901?

Thanks,
Chris

---

### Post by dgermann on 2006-03-22
Chris--

Don't know what ivoencarnacao did, but for me it was a matter of gediting inetd.conf--there are **two** #s on the line by it--I took them both out and the text in between (something like "<off>"). That got me connected.

But did not have the ability as an ordinary user to do any real work here, so I then did sudo passwd root to give myself a root user for swat.

hth.

---

### Post by chrism7 on 2006-03-23
Doug, I'll give that a try over the next few days.  I managed to manually configure samba though so the network is working so I don't *need* swat, but want to get it working so I can learn
Chris

---

