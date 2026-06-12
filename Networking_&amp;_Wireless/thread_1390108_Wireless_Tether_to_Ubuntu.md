---
title: "Wireless Tether to Ubuntu"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by FoxRacR17 on 2010-01-25
Hey everyone, just finished installing Ubuntu to my dell mini 10v netbook.  I really like it so far but I have hit a problem that may be a potential deal breaker.  I have a CDMA HTC Hero phone that I have rooted.  I installed the "wireless tether for root users" app on my phone and use it ALL the time to go online on my netbook through my phone on windows.  However Ubuntu 9.10 does not seem to connect to my phone running this app.  It sees the SSID, and i tell it to connect, and then I just get that circle thing for a couple of minutes then it gives up and connects to my main router if its in range.  

Anyone have any ideas?  I'm not sure if its Ubuntu or the app, it worked perfect with XP :confused:

---

### Post by Blue_Alien on 2010-01-25
I am having the same issues with wireless tethering in xubuntu to my g1. Xubuntu can see the network but when I try to connect, it will be unable to get an ip address.

---

### Post by dotdot on 2010-01-26
Hey a tethering thread - another one - i've read so many of these of late...

anyway i have a g2 am in the uk (read htc hero) - and have finally got it working - I'm tethered no wifi yet.

followed instructions from hak5 web site - following the cross refed site as well. (nice to see the script got blasted) - read the site if you're interested. ([here]("http://www.hak5.org/hack/droid-tethering-in-linux-without-root-access"))

anyway ok so now I've got that working - I can't get instant messaging working. I'm on 9.04 using pidgin.

anyone got any ideas. ?

oh and before someone asks why "don't i use the one on the driod?" - well i'm tethered and working... not using both.... ! yi know !

cheers in adv.

..

---

### Post by FoxRacR17 on 2010-02-01
well guys I may be no help to you but i did manage to solve this by myself.  I took off the desktop version of ubuntu 9.10 and instead installed the netbook remix version of 9.10.  Then I hooked up my mini 10v via ethernet and did "sudo apt-get update" and it went thru and downloaded or updated a bunch of stuff (i'm not sure, i'm still very new to ubuntu) and then it said restricted drivers available.  However this time there were to options for my wireless and I choose the other one (that would not show up in the normal desktop version) and BAM! now i can tether perfectly to my rooted hero running wireless tether for root users.

---

