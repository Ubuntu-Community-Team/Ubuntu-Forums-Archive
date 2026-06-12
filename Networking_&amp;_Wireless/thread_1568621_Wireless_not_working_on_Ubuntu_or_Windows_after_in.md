---
title: "Wireless not working on Ubuntu or Windows after install"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by devb16a2vtec on 2010-09-05
Prior to install, Wireless worked perfectly on Windows.  

I installed Ubuntu along side Windows 7 x64, and it works fine wired to the LAN.  
It updated fine on the LAN.  
Reset after the update.  
I tried getting the wireless to work, it finds the wireless networks,  asks me for the password to my encrypted network, which I enter, and it  does nothing-does not connect.  It will ask me after a couple minutes  for the password again.  I'm 100% sure the password is correct.  I've  verified that all of the settings appear to be correct.  

I decided to go back to windows.  Now my wireless connection on windows  will not even find wireless networks, it just says Wireless Networks  unavailable.  I've confirmed on another computer that Wireless networks  are infact available, and working properly.  

The computer is a Dell Inspiron 1545 Laptop.  
Wireless card is a Dell Wireless 1397 WLAN Mini Card.  
It's showing as a BCM43xx.  

I'm currently running on the wired LAN, which is working just fine.  I also tried re-installing the driver from Windows and restarted, and that didn't work.

---

### Post by devb16a2vtec on 2010-09-05
Ok, I just went back to Ubuntu, wireless worked for about 5 minutes and then disconnected, and has yet to reconnect.

---

### Post by devb16a2vtec on 2010-09-05
And now it's been working on Windows just fine.  

Back to Ubuntu to check.  This is very weird that it's resolving itself over the course of a couple restarts.

---

### Post by devb16a2vtec on 2010-09-06
Well, after re-checking to see if it was working in Ubuntu, I found it was not.  

I've got no idea what to do next :(

---

### Post by devb16a2vtec on 2010-09-08
Nothing?

---

### Post by 0N3 on 2010-09-08
is wireless enabled on your machine you may have to enable it right click your wireless icon see if the enable wireless is checked

---

### Post by devb16a2vtec on 2010-09-08
> **0N3 said:**
> is wireless enabled on your machine you may have to enable it right click your wireless icon see if the enable wireless is checked

Yes, it was enabled.  It connects for about 5 minutes, and then drops the connection, and or asks me for my network password over and over again.

---

### Post by 0N3 on 2010-09-08
What wireless card have you?

---

### Post by devb16a2vtec on 2010-09-08
> **0N3 said:**
> What wireless card have you?

It's a Dell 1397 WLAN internal card.  
Has the BCM43xx chipset.

---

### Post by 0N3 on 2010-09-08
[http://blogs.computerworld.com/new_linux_broadcom_wi_fi_drivers_arrive](http://blogs.computerworld.com/new_linux_broadcom_wi_fi_drivers_arrive) 
Try that link sorry i cant help :(

---

### Post by Iowan on 2010-09-08
[Here]("http://ubuntuforums.org/showthread.php?t=1416162") is a similar (but solved) thread.

---

### Post by fortu on 2011-03-06
I had the same problem and it was quiet frustrating. Now everything is working. 
What I did was unistall ubuntu through wubi and reinstall it.
Then the "missing firmware" (or something of sorts) message appeared again.
I got the b43 update and it did not help, I uninstalled it and *then* installed the sat one. That did the trick. After restarting the machine and logging into ubuntu once more to check it was working I restarted it and logged into windows and the problem was solved. Now the card is detecting everything again and both ubuntu and windows have wireless.

---

