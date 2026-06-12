---
title: "Cannot connect to Wired internet, though DSL connection works"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by bitterfriend99 on 2009-10-05
[SIZE=3]Hello All.[/SIZE]

[SIZE=3]I am using router UTStarcom UT300R2U. It is configured in Bridged mode. *No* Static IP.
In Windows XP, I can connect in Bridged mode via a *New broadband connection that requires an username & password *as well as in PPPoE mode which doesn't require dialing a connection.
However, in Linux, at first it showed a Wired Ethernet connection (Auto eth0). But after [/SIZE][SIZE=3]I created a DSL connection, Auto eth0 was gone (Honestly, I didn't do anything! :-|). But DSL connection works fine (I just provided my username & password to it).

But now I want to connect in PPPoE mode. For that I deleted my DSL connection & tried to open Router Settings page : [http://192.168.1.1](http://192.168.1.1), but it never opens.
After hours of Googling, searching, editing */etc/network/interfaces *and **finally **replacing it back with original, rebooting manytimes, after I clicked on Add Wired connection, an Auto eth0 came by itself (*After* that a window came which could create "Wired Connection 1" and asked *me* for options, but this Auto eth0 came by itself :confused: ). My /etc/network/interface doesn't have any entry of eth0.[/SIZE] 
[SIZE=3] 
 [/SIZE]```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```[SIZE=3]

[/SIZE][SIZE=3]I tried replacing with[/SIZE][SIZE=3] :
[/SIZE]```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
```[SIZE=3]
[/SIZE][SIZE=3]but it didn't work, [/SIZE][SIZE=3]that Auto eth0 didn't turn up untill I replaced it with original.

[/SIZE][SIZE=3]What shall I do to connect Internet in PPPoE mode?
Don't ask me *why *I need it anyway when Bridged mode is working great. In PPPoE mode, AFAIK, if connection temporarily disconnects (which happens often here), as username & password is stored in Router, it reconnects automatically.
But in Bridged mode, I have to trigger that connection manually. That suspends all the downloads when I am away from desk. :-x
[/SIZE][SIZE=3]
PS : I am using Linux Mint 7 Gloria Main Edition. Hope you do not mind it, as (they say) it is fully compatible (and similar) to Ubuntu. And not to mention I am a total novice to Linux Environment. ;) 

Regards,
[/SIZE]

---

### Post by bitterfriend99 on 2009-10-05
[SIZE=3].
[/SIZE]

---

### Post by bitterfriend99 on 2009-10-06
I am very new to this Forum.
Did I break any rules in my post that prevails others from replying?

Kindly guide me if I have made any mistake.

---

### Post by Iowan on 2009-10-06
> **bitterfriend99 said:**
> Did I break any rules in my post that prevails others from replying?None that I'm aware of...
Network Manager won't (usually) manage interfaces defined in */etc/network/interfaces* - that's why Auto Eth0 disappeared.
My DSL modem handles all the PPPOE "stuff" so the clients see it more like a router... so I can't help much with the bridged connection.

---

