---
title: "Reconnect automatically on connection loss"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by brad_pitt on 2009-07-08
Hi All,

My internet connection goes down very frequently and it requires me to connect it to network manually by clicking so i searched for another network manager and i found wicd network manager has this feature but it does not support wired network connection with authentication.

Here is the link to the post about wicd [IMG]http://wicd.net/punbb/viewtopic.php?id=624[/IMG][http://wicd.net/punbb/viewtopic.php?id=624](http://wicd.net/punbb/viewtopic.php?id=624)

If there is any solution for my problem can any body please help me.

Thanks in Advance
Brad

---

### Post by brad_pitt on 2009-07-09
Any suggestions guys

Regards
Brad

---

### Post by Philo1 on 2009-07-09
It forces you to click to reconnect. What exactly do you mean by this? Are you on wifi when it drops. Is it affecting any other devices such as those on cat5?

---

### Post by brad_pitt on 2009-07-10
[quote=Philo1]It forces you to click to reconnect. What exactly do you mean by this? Are you on wifi when it drops. Is it affecting any other devices such as those on cat5?[/quote]

I will try to explain my issue in detail..We have a option in Network Manager Applet i.e. 'Connect Automatically'

Whenever i boot my machine i don't have to manually connect to my network it only connects to the network automatically(may be ''Connect Automatically'' option means this)

Scenario is :Suppose if my network goes down for 15 or 20 minutes network manager is trying for only 2 or 3 minutes attempting to connect to the network after that it **displays a splash message that your network connection is disconnected and now you are offline**, that's it does not attempt to connect to the network after that.if my network connection is up after 10 minutes i have to sit at my machine to manually clicking on the network manager icon to connect to the network.

I am really looking for a feature like we have in windows(If network connection goes down for even one hour it tries to connect for every 90 seconds)

Suppose if i keep downloading in the night by the morning i woke up and check it the network connection light glows on my modem but network connection is disconnected but if i click on network manager again it connects to the network.


I am not using Wireless network.I use Wired network connection(DNS) which requires quthentication.I used to connect to the this network using PPPOE in windows.

Can somebody resolve my problem..

I am having hard time to download movies because of this problem :(

---

### Post by superprash2003 on 2009-07-10
so you mean it connects to the network but doesnt do the authentication part?

---

### Post by brad_pitt on 2009-07-10
[QUOTE=superprash2003]so you mean it connects to the network but doesnt do the authentication part? [/QUOTE]

No.It does not even attempt to connect to the network.

Regards
Brad

---

### Post by superprash2003 on 2009-07-10
hmm..thats weird , since its a wired connection it should detect it automatically and connect although yes for a wifi connection after a while it does stop attempting to connect.. is this a static ip setup or DHCP?

---

### Post by brad_pitt on 2009-07-10
[QUOTE=superprash2003]hmm..thats weird , since its a wired connection it should detect it automatically and connect although yes for a wifi connection after a while it does stop attempting to connect.. is this a static ip setup or DHCP?[/QUOTE]

It is DHCP.I think a script or something like that should resolve this problem but i am looking for a network manager which has this option built in.

Regards
Brad

---

### Post by superprash2003 on 2009-07-11
well are you running 9.04 ?cause it seems to connect automatically for me

---

### Post by brad_pitt on 2009-07-12
[QUOTE=superprash2003]well are you running 9.04 ?cause it seems to connect automatically for me[/QUOTE]


I am running Ubuntu 9.04 but even i faced the same problem in Ubuntu 8.10...
Can i depend on knetworkmanager to resolve this issue?

Regards
Brad

---

