---
title: "/etc/network/interfaces problem ?"
date: 2013-05-31
forum: Networking &amp; Wireless
---

### Post by MikiBroki on 2013-05-31
[COLOR=#1A1A1A][FONT=Lucida Sans Unicode]Hello everybody, 

I'm using Ubuntu 13 on a virtual machine with VMWare (network configured as 'bridge').[/FONT][/COLOR]

[COLOR=#1A1A1A][FONT=Lucida Sans Unicode]Code in /etc/network/interfaces:[/FONT][/COLOR]

```

[COLOR=#1A1A1A][FONT=Lucida Sans Unicode]auto lo[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Lucida Sans Unicode]iface lo inet loopback[/FONT][/COLOR]

[COLOR=#1A1A1A][FONT=Lucida Sans Unicode]auto eth0[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Lucida Sans Unicode]iface eth0 inet static[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Lucida Sans Unicode]address 192.168.1.11[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Lucida Sans Unicode]gateway 192.168.1.1[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Lucida Sans Unicode]netmask 255.255.255.0[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Lucida Sans Unicode]dns-nameservers 8.8.8.8
[/FONT][/COLOR]
```

The problem is I have access to the network and internet connection too... but the icon at the upper right shows nothing (doesn't appear the two arrows and no "wired connection 1").

I spent many hours until I checked  I really have the connection.

[COLOR=#1A1A1A][FONT=Lucida Sans Unicode]Is that normal?, is possible to fix?, can I specify a connection name manually ?[/FONT][/COLOR]

[COLOR=#1A1A1A][FONT=Lucida Sans Unicode]Thanks !

PD: sorry, my english language is not good [/FONT][/COLOR]

---

### Post by prodigy_ on 2013-05-31
Yes, this is normal. NetworkManager uses its own configs. If you configure an interface in /etc/network/interfaces, NM won't touch it at all.

---

### Post by MikiBroki on 2013-05-31
OK, understood, thanks :)

---

### Post by Hadaka on 2013-05-31
Hi MikiBroki, if you want to set your static ip address with network manager
you can do it with the wired settings for IPv4 with network manager. This
will return your wireless and wired icon like it was before.
first...you need to change /etc/network/interfaces..
```
sudo gedit /etc/network/interfaces
```
delete all the current settings
then add just these 2 lines of code.
```
auto lo
iface lo inet loopback

```
SAVE and close gedit
then boot..
next click the wireless/wired icon and edit your wired connection 1
choose MANUAL and make IPv4 and IPv6 look like the screen shots below.
[ATTACH=CONFIG]243349[/ATTACH][ATTACH=CONFIG]243350[/ATTACH]
click SAVE then boot... then to verify the change do..
```
ifconfig
```
you should see that the IP address for your wired connection is now 192.168.1.11

---

### Post by MikiBroki on 2013-05-31
Thank you so much Hadaka, I knew that, but I was learning how to do this by editing the file :)

---

### Post by Hadaka on 2013-05-31
Good deal, well maybe it will help someone else that doesnt know.
If you are satisfied with the thread conclusion, please mark it SOLVED
How to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks.

---

