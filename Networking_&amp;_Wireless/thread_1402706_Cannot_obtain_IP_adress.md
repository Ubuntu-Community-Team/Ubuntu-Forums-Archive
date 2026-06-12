---
title: "Cannot obtain IP adress"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by lamaschine on 2010-02-09
hey 
I have been trying to connect to the wireless network at work, and at the minute am running on ubuntu 9.10, I have installed drivers, and updated system, the identification works but I cannot obtained IP. I have tried using a static IP and using global DNS, I can then connect but when I go on firefox it is not working. I think the wireless is on etho2. 
My knowledge of command and linux in general is minimal and am new to ubuntu can somebody possibly help me, I am aware that there is tones of topic on the subject but loads require complicated manip I dont understand.

thanks

---

### Post by lamaschine on 2010-02-09
yeah also forgot to precise that I have been using wcid till now if that helps.

---

### Post by lamaschine on 2010-02-10
ok also checked the wired connection on the router at work which works; tried to connect to another wireless not protected by WEP and it worked just fined.... however I still cannot log on to the wireless here. 
Help please !! :)

---

### Post by superprash2003 on 2010-02-10
is ubuntu able to recognize the wifi network? does it make an attempt to connect? could you post output of **iwconfig **from the terminal

---

### Post by lamaschine on 2010-02-10
ok this is the result of the iwconfig

lamaschine@lamaschine-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:203  Noise level:166
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

but after I turned off the wep protection of the router I have been able to connect , therefore meaning that I cannot obtain IP while the WEP is on which is a problem ..

thanks for answering btw ;)

---

