---
title: "How to enable wireless card"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by Burnasty on 2008-12-05
I am running ubuntu 8.10 with an acer aspire 3680.  I have a broadcom bcm4311 wireless adapter.  When walking through the trouble shoot with wireless networking I have found my card is disabled and the cure from the trouble shoot is to turn it on via a button or through windows.  I can't find any button (unless i don't know what i am looking for) and I completely removed windows.  Any help is much appreciated.

Brian

---

### Post by Kevbert on 2008-12-05
Welcome to Ubuntu.
Have you tried the following in terminal ?
```
iwconfig
```
This will give you the wireless name. Assuming it is 'eth0' use
```
ifconfig eth0 up
```
to power it up.

---

### Post by razy60 on 2008-12-05
On your keyboard do you have a FN key(normaly situated near the alt+ctrl keys) if you do then one of your F keys will have a icon on it which will be for wireless or you have a slide switch on the side.

Raz

---

### Post by superprash2003 on 2008-12-05
have you enabled the driver in system->admin->hardware drivers [http://prash-babu.blogspot.com/2008/11/how-to-configure-broadcom-wireless-in.html](http://prash-babu.blogspot.com/2008/11/how-to-configure-broadcom-wireless-in.html)

---

### Post by Burnasty on 2008-12-05
Thank you all for the replys.  I found a slider on the side and enabled that, with the same results.  I ran the code in terminal and it said permission denied. Do i need to be in root?  I also have the drivers enabled.  Thank you again for all the help.

---

### Post by razy60 on 2008-12-05
have you looked in system-preferences-networkcontrol-wireless then add.
or in synaptics load sysinfo at least that will tell you if your card is being seen by your pc.

Raz

---

### Post by Burnasty on 2008-12-06
Alright, I got the sysinfo package from the add/remove and it listed my broadcom under network controller.  I am assuming that means it is being seen.  When i run in terminal iwconfig it is listed in eth1 with no nickname and the access point is not assigned.  When i ran the power up code it said permission denied.  Thank you again for your help.
Brian

---

### Post by Burnasty on 2008-12-06
I also downloaded wifi rader and it found a network around my area but couldn't connect.  Is this something that is common?  I appologise if I am asking the same question everyone else is.

---

### Post by Kevbert on 2008-12-06
> **Burnasty said:**
> Alright, I got the sysinfo package from the add/remove and it listed my broadcom under network controller.  I am assuming that means it is being seen.  When i run in terminal iwconfig it is listed in eth1 with no nickname and the access point is not assigned.  When i ran the power up code it said permission denied.  Thank you again for your help.
Brian

It possible that you need to use sudo at the beginning of the command, so it should be
```
sudo ifconfig eth0 up
```
Sorry, for any inconvenience.

---

### Post by razy60 on 2008-12-06
Questions that should have been asked how far and or where is the wifi router?. in other is it at home or elsewhere?, i ask as i am not convinced that if you are not within a reasonable range and strength of signal if you can even attempt to connect/switch on wifi, i had a few problems recently in a wifi hotspot when i was out i actually had to move a table over before i could activate my wifi, (it asked me to switch on etc). I have to admit when i tried in that other os that i didnt have the same problem, signal was the same but the wifi was quite happy. move a couple of feet and i could use Ubuntu, weired!:confused:

Raz

---

