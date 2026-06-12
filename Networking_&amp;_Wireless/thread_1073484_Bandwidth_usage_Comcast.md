---
title: "Bandwidth usage Comcast"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by ear9mrn on 2009-02-18
Dear all,

For my sins I am a Comcast customer :( 

AS you may know they recently introduced a "fair usage" policy (don't get me started). Anyway, I am a "power" user but would probably never reach the 250gb limit they have set but I have know way of knowing as far as I can tell Comcast do not make their tracking information avaliable to their customers (am I right ?). 

So my question is. How can I track my monthly usage ? My ideal vision is to have a small screenlet on my desktop that is just a running total of my bandwidth usage for the month !

Here is the challenge. My system consists of a motorola surfboard connected to a netgear WGT624v5 wireless router. Connected to that I have:

Skype phone
Roku Netflix box
Mythbuntu Media center
Webserver (mysql, apache, etc)

What is the simplest way to keep track of all that internet traffic ? I have looked into using the modem or router but neither appear to offer that functionality. Can anyone recomend another router or modem. I see netgear now sell cable modem and routers combined, could that have the functionality I am looking for or is there a software solution I could use?

Thanks,

Pete.

---

### Post by superprash2003 on 2009-02-18
you could use one machine as a gateway and connect all your other machines,skype phone etc behind the gateway machine.. and then install a software like [https://help.ubuntu.com/community/HowToMonitorInternetTrafficTotals](https://help.ubuntu.com/community/HowToMonitorInternetTrafficTotals)

---

### Post by dannyboy79 on 2009-02-18
> **ear9mrn said:**
> Dear all,

For my sins I am a Comcast customer :( 

AS you may know they recently introduced a "fair usage" policy (don't get me started). Anyway, I am a "power" user but would probably never reach the 250gb limit they have set but I have know way of knowing as far as I can tell Comcast do not make their tracking information avaliable to their customers (am I right ?). 

So my question is. How can I track my monthly usage ? My ideal vision is to have a small screenlet on my desktop that is just a running total of my bandwidth usage for the month !

Here is the challenge. My system consists of a motorola surfboard connected to a netgear WGT624v5 wireless router. Connected to that I have:

Skype phone
Roku Netflix box
Mythbuntu Media center
Webserver (mysql, apache, etc)

What is the simplest way to keep track of all that internet traffic ? I have looked into using the modem or router but neither appear to offer that functionality. Can anyone recomend another router or modem. I see netgear now sell cable modem and routers combined, could that have the functionality I am looking for or is there a software solution I could use?

Thanks,

Pete.
I have the WGT624 but with Firmware version 4.2.11_1.0.1 so I am not sure if this is applicable but under the Router Status Section within Maintenance, you scroll to the bottom and see the Statistics Button, click on that and it brings up your statistics of Packet Usage, transmitted and received. That would be the easiest but setting up linux gateway would be most accurate etc etc. I took a screenshot of mine.
[[IMG]http://img153.imageshack.us/img153/1175/wgt624me8.th.jpg[/IMG]](http://img153.imageshack.us/my.php?image=wgt624me8.jpg)

---

### Post by darco on 2009-02-18
Comcast is coming out with a Bandwidth monitor any day now...

darco

---

### Post by ear9mrn on 2009-02-25
Thanks dannyboy79 I did not know about this. Unfortunately it does not have any way to remember the data. Power off and its gone. I cannot work out a way of "logging" the data and saving it to my server.

There must be an easy solution to this. I had a look at Untangle but its a bit of overkill and it does not appear to give a monthly amount, just the last 30 days. I need a monthly, how much used in January, how much used so far in February etc.

Pete.

---

### Post by punx45 on 2009-02-26
see if the tomato firmware is compatible with your router.  it has nice bandwidth monitoring.

---

### Post by ear9mrn on 2009-02-27
So i bought a new netgear router WRG614L and installed tomato. Very nice. Word of warning. There is a batch of router WGR614 V9 with a big sticker on the front saying that it is the open sourced 'L' version but its not. It as apparently miss labeled by Netgear. If anyone is planning to buy one of these make sure you check the side of the box and that the version is WRG614L (and the unit itself is called WGR614 v8).

So much more functionality that the standard version. I can even ssh into my router !!!

Pete.

---

### Post by punx45 on 2009-02-27
yeah i used to use the DDWRT firmware, and actually bought the buffalo router i have specifically for the compatibility.   it didnt have built in bandwidth monitoring, and the add on solutions looked like a PITA, so i switched to tomato right after the 250GB cap was announced.

---

