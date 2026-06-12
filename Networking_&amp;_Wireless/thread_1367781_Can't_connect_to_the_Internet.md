---
title: "Can't connect to the Internet"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by Urhungry on 2009-12-29
Ok, so I have finally managed to install xubuntu, and it's fabulous. Only one problem. I can't connect to the internet. I'm using xubuntu 8.04 on a Dell latitude c600. I try to plug it in through both ethernet and USB plug, and it appears to connect properly, through both autodetect, and IP, but webpages don't load. My wireless card broke, so no using it that way. Any help? Thanks!

---

### Post by shredder12 on 2009-12-30
How are you trying to access internet (dhcp or ppp modem etc)?

---

### Post by Urhungry on 2009-12-30
Well I'm trying to plug in through Ethernet, If that's what you mean.

---

### Post by shredder12 on 2009-12-30
I mean do you get an IP automatically when you plug in the ethernet cable or do you use modem to access internet..

---

### Post by Urhungry on 2009-12-30
Oh sorry. On my other computer, a mac, I just connect wirelessly, or over eathernet, and it picks it up fine. This computer used to run an ancient version of mandravia, from back when it was mandrake, and then it conneced fine too. But now, and when it breifly ran windows xp, when I plug in the eathernet cable, nothing happens. And when I try and manually configure the connection it still dosent work.

---

### Post by Urhungry on 2009-12-30
Any help? I can't install anything without Internet.

---

### Post by shredder12 on 2009-12-30
So, if  you were able to connect to Internet just by plugging the cable earlier in XP then you should be able to access internet in xubuntu too unless there is some other problem.

Do you see a connection named "auto eth0" when you click on the network-manager icon on the right side of the top panel. This one is responsible for getting you an automatic address. Try connecting using this connection(even though it is set as default) by clicking on it, if it still doesn't work then please post the output of
```
ifconfig -a
```

and please do clarify that after plugging the cable and selecting "auto eth0" does it connect or not and whether you are able to access internet or not.

P.S. I am considering that you get an automatic address using dhcp i.e. you don't have to manually enter your IP address, netmask etc to get connected.

---

### Post by Urhungry on 2009-12-30
No I couldn't get Internet in xp, only in mandrake. There is no eth0 connection.

---

### Post by shredder12 on 2009-12-30
Alright then lets try nd configure xubuntu to get connected.

Go to System->preferences->network connections ( it could be system->administration->network connections for hardy) nd add a new connection under wired section. Set the IP address to be automatic. And then try to connect..

---

### Post by Urhungry on 2009-12-30
What exactly do you mean add a new connection? I tried the auto dchp and it didn't work at all.

---

### Post by shredder12 on 2009-12-30
> **Urhungry said:**
> What exactly do you mean add a new connection? I tried the auto dchp and it didn't work at all.

yeah, i was talking about auto dhcp. Does it show disconnected after attempting for a while or it gets connected but Internet doesn't seem to work?

---

### Post by Urhungry on 2009-12-30
It connects and then dosent seen to work.

---

### Post by shredder12 on 2009-12-30
alright.. once it connects.. please post the ouptput of 
```
ifconfig -a
```
or if you are sure which interface it is (its mostly eth0) then use 
```
ifconfig eth0
```

I am actually checking if you are getting an IP address or not.

btw.. do you use any network proxy for internet connection?
and also what's the output of 
```
ping google.com
```

---

### Post by Urhungry on 2009-12-30
Ok just booting back up.

---

### Post by shredder12 on 2009-12-30
> **Urhungry said:**
> It connects and then dosent seen to work.

I know but I will need you to post the output of the commands (see my last post).

If you don't know how to run these commands then go to Applications->accessories->terminal and then run these commands.

copy the output and post them here.

**P.S.** If you are unsure of anything, please don't hesitate to ask. Nobody knows everything.

---

### Post by Urhungry on 2009-12-31
Ok so here are the results:
eth0             Link endcap:Eathernet HWaddr 00:00:86:49:c3:9f
                     UP BROADCAST MULTICAST  MTU:1500  Metric:1
                      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
                    Collisions:0 txqueuelen:1000
                     RX bytes:0 (0.0 B)   TX bytes:0 (0.0 B)
                     Interrupt:11 Base address:0x6c00
And thank you for being so helpfull.

---

### Post by Urhungry on 2009-12-31
And for ping google.com it just returns ping: unknown host google.com

---

### Post by alexfish on 2009-12-31
> **Urhungry said:**
> Ok, so I have finally managed to install xubuntu, and it's fabulous. Only one problem. I can't connect to the internet. I'm using xubuntu 8.04 on a Dell latitude c600. I try to plug it in through both ethernet and USB plug, and it appears to connect properly, through both autodetect, and IP, but webpages don't load. My wireless card broke, so no using it that way. Any help? Thanks!

Hi 

Can You Tell Us About This USB PLUG

Thanks in advance 
 alexfish

---

### Post by shredder12 on 2009-12-31
> **Urhungry said:**
> Ok so here are the results:
eth0             Link endcap:Eathernet HWaddr 00:00:86:49:c3:9f
                     UP BROADCAST MULTICAST  MTU:1500  Metric:1
                      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
                    Collisions:0 txqueuelen:1000
                     RX bytes:0 (0.0 B)   TX bytes:0 (0.0 B)
                     Interrupt:11 Base address:0x6c00


So, if the concerned wired network's interface is eth0 then i don't think you are even getting an IP..
i.e. you are not connected so obviously other softwares won't work. 

Are you trying to connect to a router using the cable. Do other computers(if there are) get connected directly when ethernet cable is plugged in? And I am still assuming that they use auto dhcp rather than manually configuring IP (static IP). Am i correct? 

Since, you are unable to access internet even on XP it could be a hardware issue too.

---

### Post by Urhungry on 2009-12-31
Yes other computers are directly pluged in. I don't think that it's a hardware issue, because mandrake connected just fine. I didn't configure mandrake, though. And axelfish, the USB is just a cable that plugs into  a USB port on the computer, and a printer plug port on the modem/router.

---

### Post by Urhungry on 2009-12-31
Just upgraded to 9.10, still no Internet though.

---

### Post by Urhungry on 2009-12-31
Problem solved. I just had it in the wrong plug in the router this whole time. Sorry for all the trouble.

---

### Post by shredder12 on 2010-01-01
> **Urhungry said:**
> Problem solved. I just had it in the wrong plug in the router this whole time. Sorry for all the trouble.
:lolflag: that's for me the whole time. ;-)

---

