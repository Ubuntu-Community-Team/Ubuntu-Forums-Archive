---
title: "Fake AP, Please Help"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by GuiltySpark on 2009-08-18
[I][B][SIZE=4][FONT=Palatino Linotype]I'v had this problem and its driving me insane I have Even googled Everything... Can't seem to get this working, Im trying to
make a Fake AP that when I connect to it on my Windows XP box It I can
access the Internet. Thats it...Thats All I want. I can't seem to get
my DHCP server working it seems. I can make the fake AP but when I
connect to to it "Limited Or No connectivity" Iv tried Disabling
adapters...Changing Configs...Everything even from google. Nothing Seems to work. If someone could post thier DHCP .conf
and settings Maybe this can help. No Clue Im running outa ideas and
this is really Irritating. :confused: Im using airbase-ng by the way. And Just to be clear I do
Sudo apt-get install dhcp3-server For the DHCP server Right? Make sure I have the correct one...

Using Ubuntu 9.04

Thanks
[/FONT][/SIZE][/B][/I]

---

### Post by GuiltySpark on 2009-08-18
***I Can now Connect to my network. But I still have no internet on my XP box.***



[IMG]http://i69.photobucket.com/albums/i44/trickster_03/DHCPtes.png[/IMG]

---

### Post by lex0429 on 2010-02-07
Been a while, not sure if you figured this out but if so maybe it will help someone else.

check out this walk through.

[http://adaywithtape.blogspot.com/2009/10/fake-ap-using-airbase-ng.html](http://adaywithtape.blogspot.com/2009/10/fake-ap-using-airbase-ng.html)

specifically i think this part will fix your issue,

Needed to give further privilages to the dhcpd.
[COLOR=lime]mkdir -p /var/run/dhcpd && chown dhcpd:dhcpd /var/run/dhcpd
[/COLOR]

Then to point the command to the alternative dhcpd.conf file and the alternative .pid file
dhcpd3 -cf /etc/dhcp3/dhcpd.conf -pf /var/run/dhcpd/dhcpd.pid at0

---

