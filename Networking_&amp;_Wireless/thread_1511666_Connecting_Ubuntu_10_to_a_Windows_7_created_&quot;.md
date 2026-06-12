---
title: "Connecting Ubuntu 10 to a Windows 7 created &quot;Wireless Adhoc Network&quot;"
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by shankar556288 on 2010-06-17
Hi,
   am trying to share my internet connection between 2 laptops one with **Windows 7** and the other with **Ubuntu 10.04(LTS)** installed in it. I created a "**Wireless Adhoc Network**" in Windows and allowed Internet sharing through it. I set a password and set Authentication mode as "**WEP & WPA2 Personal**".

  Now, I am able to connect other Windows machines to this network but I cant make it work in Ubuntu. The network's name is displayed but once I click it and enter the password using the same Authentication settings, it keeps trying to connect but does not ever connect! What am I missing here? Need urgent help!!!

---

### Post by creek23 on 2010-06-17
I was just going to create a new thread and ask for help too.

Same case here. My friend have Windows 7 with open Ad-hoc connection. I couldn't connect my Ubuntu 10.04 installation either.

Would be grateful if someone could help us. Please. :(

---

### Post by AdmiralNotorious on 2010-07-06
this is pissing me the hell off too. i abandoned xp for 7 just to get this to work, and i'll be damned if i fail again

---

### Post by Vegemite on 2010-07-08
> **shankar556288 said:**
> .... The network's name is displayed but once I click it and enter the password ....

I'm new to Linux and have the same problem connecting my Eee PC 701SD to a Win 7 laptop. I only get the Network name though with no option to connect when I click on it. Various encrypted WiFi networks in the area show and allow a connect option.
My netbook also freezes if I turn wireless off (Fn + F2) and sometimes hangs when logging off but doubt that is related.

---

### Post by 9170 on 2010-07-11
I have got the same problem but there was something strange. While looking at the ad-hoc network (installed in Ubuntu), win7 recognized the protocol as "WEP" but it was "WAP/WAP2". 

](*,)

---

### Post by 9170 on 2010-07-13
I found one main problem why it hasn't worked out for me! The reason was that the WEP code wasn't correct. After that I had generated one on a web page my two computers "saw" each other in the ad-hoc network but unfortunate only with limited access in Win7. 

](*,)

---

### Post by Alan502 on 2010-07-20
I have the exactly same problem. Somebody please help!!

---

### Post by chiyam on 2010-09-11
I too have the same issue. I think the encryption is the problem. It worked when i made the windows ad-hoc connection security as none, I was able to connect and use internet.

Also if I do the reverse i.e create an ad-hoc wireless in ubuntu and connect using windows7 after providing the password it does not work. When i make the encryption none, i am able to connect but not having internet access. This is due to the fact that the eth0 and wlan0 are not bridged. I have tried to ask in many forums but every one gives some link or other.

---

### Post by ninh2d on 2010-10-27
I had the same problem! there's anyone can help me???? I can see the wireless name, but when i click on it, nothing happen

---

### Post by ngx on 2010-10-27
me too! I have difficulty to access ubuntu 10 tru wireless connection. I have no choice  better to use physical cable connection, and it works! But if you have solution for wireless network pls. share to us...thanks!:smile:

---

### Post by Woooza on 2010-12-16
Hi,
I had the same problem but finally found a solution. 
Download the software "[Connectify]("http://www.connectify.me/")" which allows you to turn your computer to a wireless Access point, and install it on the Win7 computer.
Now just set up a new Hotspot with the software and you can connect Ubuntu to it.
Its really easy to use and workes without any problems.
I hope this will help some of you too.

---

### Post by nikhilmallela on 2011-01-21
Thanks a lot..!! It works for me...!

---

### Post by Turin Turambar on 2011-03-22
Finally!! Thank you!

I had ad-hoc working on Win7 without this program but it was SO unstable and frustrating... this program just works!!

---

### Post by enobayram on 2011-06-13
Hi,

Connectify sounds really nice, but I've ruined my laptop with a 64 bit windows 7 while trying to install it... :(

---

### Post by macflav on 2011-07-02
> **enobayram said:**
> Hi,

Connectify sounds really nice, but I've ruined my laptop with a 64 bit windows 7 while trying to install it... :(
Me too. Fixed it thanks to System Restore.

---

