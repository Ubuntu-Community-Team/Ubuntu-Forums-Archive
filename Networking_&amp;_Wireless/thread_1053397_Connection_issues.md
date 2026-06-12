---
title: "Connection issues"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by slammed87d21 on 2009-01-28
I'm running 8.10 32 bit on an Acer Aspire. I am trying to figure out how to setup my cell phone as a modem. The Sprint guy I talked to told me the number for it to dial was #777, and the network was sprint cdma. Well, I can put the number in, but when I try to enter spreint cdma into network, I can no longer select OK to save it. Oh, I'm using Network Manager. Anyone know? Thanks in advance.

---

### Post by slammed87d21 on 2009-01-28
bump

---

### Post by slammed87d21 on 2009-01-28
Bump

---

### Post by slammed87d21 on 2009-01-29
bump

---

### Post by jms1989 on 2009-01-29
I honestly have no clue but network manager needs a valid ip address to connect. How is the phone connected to the computer?

---

### Post by W2IBC on 2009-01-29
I have never heard of b'in able to connect to the net from your pc using a cell phone.

---

### Post by denden on 2009-01-29
Hi,

The application your looking for is supplied with ubuntu base install. Do a google for 'wvdial'. its a command line app and will connect to the intertubes through your cellphone. 

There are configs for numerous phones floating about so i'm sure it won't be too hard to figure out. I'm currently using wvdial and a nokia 6121 connected via USB for my remote needs. Works great.

---

### Post by spegru on 2009-01-29
Hi, yes you can use a suitable phone to connect to the internet but there's a few bits of info needed here.

How are you connecting to the phone: USB or Bluetooth?
BT may be easier, depending on what you phone is and whether it has internal virtual CDs like some seem to (they can block the modem ports).
If it's a nokia then it may be easy enough.

Ubuntu 8.10 has an excellent network manager designed for just such a task as this - and unless you're a real command line fan, steer away from wvdial configs

Even if you have all the above sorted already, there are a few things in the config that can stop the connection working if they are wrong, such as APN and user name as well as the phone number. I am not familiar with sprint so I suggest you google for those settings and do not take the help desk guys advice as gospel (FYI most UK mobile data networks seem use *99# as the dialup number).

---

### Post by slammed87d21 on 2009-01-29
Well, it's an LG Rumor, and my service is Sprint. I'm connecting it with a USB cable. Ubuntu recognizes it as a modem, but with Network Manager, it won't let me enter the network.I tried using Gnome PPP last night, and it got me further than anything else. The screen on my Rumor shows it's making a data call, but since noone at Sprint can tell me what username and password to use, I don't think that will work.

---

### Post by spegru on 2009-01-29
Nice phone, I don't think I've seen one of those this side of the pond

According to this site [http://www.webmessenger.com/support/APN.jsp](http://www.webmessenger.com/support/APN.jsp)
The APN is Internet.com and username/password is blank

You can change these settings from inside network manager from system>preferences>network configuration> mobile broadband>sprint (I assume) 

That site doesn't give the dialup number though, so I suggest the one you have - #777, or maybe *777# (as that would then be the same format number that UK operators use). If that doesn't work try *99#, like we use over here.


Another issue I've had over here is DNS server problems that prevent websites working even though you have a connection. This is down to the carrier having a poor network.

Do you have skype? If you do I've found that it goes through most reliably even when other things don't work - watch out for that little green tick that shows you are online!

If you do get connected but without web access it is worth trying an alternative DNS, such as OpenDNS. You can select it inside network manager by selecting IPv4 Settings and select 'automatic (ppp) addresses only' and then enter the OpenDNS servers into the DNS servers box
they are 208.67.222.222 and 208.67.220.220 (enter them both separated by a comma)
 
Hope this is a help

---

