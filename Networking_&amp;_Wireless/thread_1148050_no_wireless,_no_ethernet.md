---
title: "no wireless, no ethernet"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by va1en0k on 2009-05-04
Hello!

After compressing /usr folder, I can't connect my EEE PC 710 running under last Ubuntu version (I've installed Ubuntu from geteasypeasy.com and then I've upgraded it) to wireless (It doesn't write anything, only that It's trying to connect and It's disconnected).

And I can't connect it to the internet by Ethernet cable (the icon shows that it's trying to connect and it's disconnected again).

Please help me!


(If you need results of some commands, please, tell me. But I think I would have to type this results from EEE here by myself - I can't think up a way to take text from my very no-internetable notebook)

ps: sorry for my english!

---

### Post by ceylonerana on 2009-05-04
Type following command on your Terminal.

[FONT="Courier New"]ifconfig[/FONT]

Then post the result which you get.:)

---

### Post by va1en0k on 2009-05-04
> eth0      Link encap:Ethernet  HWaddr 00:1f:c6:68:8a:aa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:5
          collisions:0 txqueuelen:1000 
          RX bytes:1532 (1.5 KB)  TX bytes:0 (0.0 B)
          Memory:fbfc0000-fc000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:748 (748.0 B)  TX bytes:748 (748.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:a1:3b:ba  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7862 (7.8 KB)  TX bytes:2008 (2.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-A1-3B-BA-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
here it is

---

### Post by va1en0k on 2009-05-04
i tried to follow some instructions in wiki, but i havent succeeded, maybe i'm too stupid for them %)

---

### Post by va1en0k on 2009-05-04
huh one guy have helped me so now everything works fine thank you )

---

### Post by jkarcz on 2009-05-04
Uncompress the /usr directory.  There is a lot of important scripts that ubuntu needs to work properly.

Compressing any directory in / is not a good idea.

---

### Post by va1en0k on 2009-05-04
i compressed it following howto guide in this forum and everything seems ok (except wi-fi)

problem was in apparmor

---

### Post by ceylonerana on 2009-05-05
Ok, thanks for the result you had post :). It seems that you had no network connection. So first of all you need to setup connection. It is pretty easy. Remember this is for wired network:KS.
Try these codings.

[FONT="Courier New"]ifconfig eth0 192.168.1.xxx netmask 255.255.255.0 broadcast 192.168.1.50[/FONT]

Eg:-
[FONT="Courier New"]ifconfig eth0 192.168.1.1 netmask 255.255.255.0 broadcast 192.168.1.50[/FONT]

After that you should restart the networking. It can done by executing these commands.

[FONT="Courier New"]/etc/init.d/networking stop
/etc/init.d/networking start[/FONT]

You need to execute those 2 commands.

After that try to ping to another PC on your network. It will work :)

===========================================================================

For Wireless network....:KS

Try this command to assign ip address.

[FONT="Courier New"]ifconfig ath0 192.168.1.1 netmask 255.255.255.0 broadcast 192.168.1.50[/FONT]

After that the other codings are same as above. Hope you can go through this. :guitar:

---

