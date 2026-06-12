---
title: "setting up a repeater"
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by izar on 2010-11-25
i have a siemens sl2-141 [(manual)]("http://www.iad.cz/prez/ADSL_SL2-141_User_Manual.pdf")router which i want to use as a repeater to increase the wireless range of an existing wireless network.
in the configuration page of the router i dont see wds option yet it has "repeater" option. in order to use this option i need to set the same ssid as the existing network and put it on the same channel. then it lets me link it with the mac adress of the existing router.
(edit: later i found out that this option actually uses the wds protocol.)
yet when i connect my pc to the repeater i cant access the internet.
what have i done wrong? :confused:

---

### Post by izar on 2010-11-26
success!

if anyone is interested, here is what i did:
i set the ssid on the repeater to be the same as the existing network and set it to the same channel.
then in the configuration page under wireless>repeater i set it to repeat the other router.
i also set the old router to contact the repeater through wds, although i dont know if this was heeded.
at first i thought that i need to disable the dhcp service on the repeater, but i was wrong.

all i need to do now is to connect my pc to the wireless network of the repeater, and i can surf the net.

&#1488;&#1504;&#1497; &#1497;&#1493;&#1491;&#1506; &#1513;&#1500;&#1488; &#1492;&#1512;&#1489;&#1492; &#1497;&#1513;&#1512;&#1488;&#1500;&#1497;&#1501; &#1502;&#1495;&#1508;&#1513;&#1497;&#1501; &#1499;&#1488;&#1503;, &#1488;&#1489;&#1500; &#1488;&#1501; &#1497;&#1513; &#1500;&#1499;&#1501; &#1489;&#1506;&#1497;&#1492; &#1491;&#1493;&#1502;&#1492; &#1506;&#1501; &#1491;&#1490;&#1501; &#1491;&#1493;&#1502;&#1492; &#1488;&#1504;&#1497; &#1497;&#1499;&#1493;&#1500; &#1500;&#1506;&#1494;&#1493;&#1512;.

---

### Post by izar on 2010-11-26
only problem now is that when i set wep protection to the repeater, it stops providing internet and provides only local network
any idea?

---

### Post by izar on 2010-11-27
no solution yet but i managed a workaround:
i set two different ssid's to the repeater (as it has the ability to do so)-
the first one is the same ssid as the one of the primary router. it has no protection (wep OR wap) and it is also disabled.
the second ssid is the one i use to connect to the repeater. this one has wap protection.

now everything works the way i want it.
i will conclude this thread as solved, and claim that the problem reported in the previous post is simply a bug in the router's firmware.

---

### Post by dtzortzis on 2011-12-05
I can confirm this worked for me as well! :P
Thank you!
So, I have to SL2-141's.
I set up the router A normally. Then, on router B I did the following: 

[LIST=1]
[*]Firstly set up a different IP address than router A. They both had 192.168.1.1 so when you put them on the same network they can't play.
[*]On router B, configure the DHCP server to relay everything to router A. So, put router A's IP address there.
[*]On router B, enter as a DNS server the address of router A, that is, 192.168.1.1
[*]On router B, make the exact same ocnfiguration for the wireless network. Same SSID, same password and authentication method etc.
[*]Go to the settings for the repeater (WDS) and select the SSID of the common wireless network. Do that on both routers.
[*]That's it!
[/LIST]

My friend, this immediately came to my mind, I dedicate it to you: [https://www.xkcd.com/979/](https://www.xkcd.com/979/)

---

