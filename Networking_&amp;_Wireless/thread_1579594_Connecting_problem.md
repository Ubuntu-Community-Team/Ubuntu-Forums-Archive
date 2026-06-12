---
title: "Connecting problem"
date: 2010-09-22
forum: Networking &amp; Wireless
---

### Post by crytek80 on 2010-09-22
Hello everybody...I am a newbie in linux
Recently I had installed Ubuntu 10.04 in which I had connected to the  internet by way of terminal (pppoeconf) and I could access any site with  ease.But one fine day suddenly I could not access the net, I try to  locate the notification icon (network manager),but could not find it.I  did this and that,googled it trying to find the solution but alas to my  disappointment I had to format it.
 
After reinstallation of Ubuntu I connect the internet by way of editing connection on panel and i could access the net.
 
The problem is that I could not access some site especially org site e.g [Home - Desiring God]("http://www.desiringgod.org/") so can anybody guide me in how to connect in most better way.
 
Thanks a lot in advance....                     __________________

---

### Post by dineshs on 2010-09-22
> Recently I had installed Ubuntu 10.04 in which I had connected to the internet by way of terminal (pppoeconf) and I could access any site with ease.But one fine day suddenly I could not access the net, I try to locate the notification icon (network manager),but could not find it.I did this and that,googled it trying to find the solution but alas to my disappointment I had to format it.

[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)> The problem is that I could not access some site especially org site e.g Home - Desiring God so can anybody guide me in how to connect in most better way.
try disabling ipv6 following [this]("http://support.mozilla.com/en-US/kb/Firefox+cannot+load+websites+but+other+programs+can")

---

### Post by crytek80 on 2010-09-22
> **dineshs said:**
> [http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)
try disabling ipv6 following [this]("http://support.mozilla.com/en-US/kb/Firefox+cannot+load+websites+but+other+programs+can")

Thanks Bro...
But it didnt work...i tried disabling IPV6 and did the sudo
command, alas no help.any solution pl suggest.

pls help

---

### Post by dineshs on 2010-09-23
Hope you are using Network manager(NM) and your router/modem is DHCP enabled
1)First try setting DNS to 4.2.2.1
Right click NM -edit connections-under wired tab select the connection-edit-ipv4-select method as Automatic (DHCP)addresses only -enter DNS as [COLOR="Blue"]4.2.2.1[/COLOR] and apply
Now run
```
sudo service network-manager stop
```then
```
sudo service network-manager start

```
If there is no progress try setting MTU to 1492(default is 1500)
Right click NM -edit connections-under wired tab select the connection-edit-set MTU as 1492 and apply

---

### Post by crytek80 on 2010-09-23
> **dineshs said:**
> Hope you are using Network manager(NM) and your router/modem is DHCP enabled
1)First try setting DNS to 4.2.2.1
Right click NM -edit connections-under wired tab select the connection-edit-ipv4-select method as Automatic (DHCP)addresses only -enter DNS as [COLOR="Blue"]4.2.2.1[/COLOR] and apply
Now run
```
sudo service network-manager stop
```then
```
sudo service network-manager start

```
If there is no progress try setting MTU to 1492(default is 1500)
Right click NM -edit connections-under wired tab select the connection-edit-set MTU as 1492 and apply

Still no progress .... even yahoomail,facebook,hotmail is not opening..
Please help me ...

---

### Post by dineshs on 2010-09-24
Are you using DSL connection in NM to connect?If yes you should do the configurations(DNS and MTU) via the [COLOR="Blue"]DSL tab[/COLOR] under NM and not[COLOR="Blue"] wired[/COLOR]
Also you can try 1480 or 1460 as MTU.[Here]("http://ubuntuforums.org/showthread.php?t=872346") is a tutorial

---

