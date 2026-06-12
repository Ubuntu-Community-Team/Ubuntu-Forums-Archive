---
title: "Modem Upgraded - PPPoE config wont work"
date: 2010-06-23
forum: Networking &amp; Wireless
---

### Post by akh00 on 2010-06-23
I've been using an old modem from 2007, which my ISP calls Type I. It didn't have wireless connectivity and I used pppoeconf to setup my connection - username and password and set it to connect at boot time and everything was fine till today. I bought a Type II modem from my ISP and had to return the type I modem to them. Since the technician had no knowledge of Ubuntu (or Linux in general), he configured the modem in Windows 7, tested that the connection was working, tested the wireless connection in my netbook running XP and then he left.

Now I can't connect through pppoeconf in Ubuntu (running 9.10). The terminal says eth0 is listed but the 'access concentrator' or something like that isn't responding (no other process was running at that time). Could someone please help me? I feel very vulnerable while browsing in Windows so I want to get back to Ubuntu ASAP. Any suggestions please? 
 

Oh, and here's the output when I run "dhclient eth0" - dunno if it'll help in any way:

```

Listening on LPF/eth0/00:16:76:33:d2:70
Sending on LPF/eth0/00:16:76:33:d2:70
Sending on Socket/fallback
DHCPDISCOER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.1.5 from 192.168.1.1
DHCPREQUEST of 192.168.1.5 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.5 from 192.168.1.1
bound to 192.168.1.5 -- renewal in 20259 seconds.

```

---

### Post by varunendra on 2010-06-23
Can you log into your modem's web interface ([http://192.168.1.1)?](http://192.168.1.1)?)
If not manually altered, the ID & password both should be "admin" (all in small letters, without quotes). Or you can ask your ISP for them (ID/Pwd).

Make sure DHCP is enabled in it & that you have been assigned valid IP, gateway & DNS addresses. You should also be able to set it to 'Auto-connect' (if not already set) so that the modem connects automatically as soon as powered on.

Alternatively, you can also use Network Manager's 'DSL' tab to save your pppoe ID & password & connect from there.

If it doesn't help, mentioning in your post your modem's name & model, your ISP's name & country may help us suggesting more specific solutions.


EDIT: With the output you posted above, dhcp seems to be enabled. Then you only have to crosscheck gateway & DNS. You can check them using Network Manager's icon at the right corner of the top panel.> Right-Click the NM icon > Connection Information

---

### Post by akh00 on 2010-06-23
Thank you for the quick reply. I cannot access 192.168.1.1 from Ubuntu but I can access it from Windows7. DHCP is enabled and valid gateway, DNS and IP addresses have been assigned. The connection is working perfectly in Windows. I didnt find an option for auto connect but it connects automatically anyway in windows. It's in Ubuntu that I'm out of options.

The 192.....page doesn't open at all, the pppoeconf command recognizes eth0 but doesn't find any access concentrator, and in network management, if I add a DSL connection mentioning my username, password, MAC address and MTU, it simply shows the connection in the Network Connections window. It doesn't connect even though I checked connect automatically. And as for 'Connection Information' I get the error "No valid active connections found!"

Here are a few more details which I hope will help you figure out a solution.

ISP: BSNL
Country: India
Modem Name: Type 2 ADSL 2+ CPE/IAD
Model Name: AR800V v3.0

---

### Post by dineshs on 2010-06-23
pl post the output of
```
ifconfig -a
```
```
cat /etc/network/interfaces
```
```
ping 192.168.1.1 -c5
```and```
ping 4.2.2.1 -c5
```

---

### Post by akh00 on 2010-06-23
```
 $ ifconfig -a
eth0 Link encap: Ethernet HWaddr 00:16:76:33:d2:70
     inet6 addr- fe80::216:76ff:fe33:d270/64 Scope:Link
     UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
     RX packets:7 errors:0 dropped:0 overruns:0 frame:0
     TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen: 1000
     RX bytes:438 (438.0 B)  TX bytes:1408 (1.4 KB)
     Interrupt: 21 Base address:0xde00

lo   Link encap: Local Loopback
     inet addr:127.0.0.1 Mask:255.0.0.0
     inet6 addr:  ::1/128 Scope:Host
     UP LOOPBACK RUNNING MTU:16436 Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:0
     RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

```

```

$cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider
iface eth0 inet manual

```

```

$ ping 192.168.1.1 -c5
connect: Network is unreachable

$ping 4.2.2.1 -c5
connect: Network is unreachable

```


These are the outputs. Further help, please?

auto eth0

---

### Post by akh00 on 2010-06-24
sorry to bump the thread but I'm getting helpless over here - so could someone please suggest a solution?

---

### Post by varunendra on 2010-06-24
Dinesh seems to be offline & I don't have much knowledge about commandline options.
Can you boot off live CD & see if there is any difference?
If it connects with LiveCD, please post here the results of the same commands as Dinesh told.

---

### Post by grahammechanical on 2010-06-24
I am no expert. So, I may be saying something stupid. I am using 10:04 so I can not talk you through 9:10 as things often change with each upgrade. I recently got broadband so I have had some difficulties myself. From my experience in fault finding vehicle alarm systems may I suggest that you check out the obvious? 

1) I assume you are dual booting into windows7. So, there must be a physical connection to the computer. If you were using two machines, one might not be connected to the modem. It is silly, I know but sometimes silly things get forgotten.
2) Does the network manager have the right password for the new modem. May be it still has the password for the old modem. Could this be why you cannot access the modem through the web browser? How can you get through to the internet if you cannot get through to the modem.

I am just suggesting this in trying to help. Forgive me if you have already thought of this. I recently had problems connecting through wireless and it was due to putting my computer login password and not the modem password into network manager. The wired connection worked fine. How things got mixed up I do not know. You say a technician set the windows7 system up. So, may be the Ubuntu system did not get the password changed. It should be written on the base of the modem. Did you get an instruction leaflet? That might help.

Regards

---

### Post by akh00 on 2010-06-24
@varunendra:  I booted off the 9.10 Live CD and the connection was working! Here is the output to those commands:

```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:76:33:d2:70  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:fe33:d270/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1949 (1.9 KB)  TX bytes:6437 (6.4 KB)
          Interrupt:21 Base address:0xde00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```

```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

```
$ ping 192.168.1.1 -c5
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=128 time=0.470 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=128 time=0.394 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=128 time=0.399 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=128 time=0.396 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=128 time=0.392 ms

--- 192.168.1.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 0.392/0.410/0.470/0.032 ms

$ ping 4.2.2.1 -c5
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
64 bytes from 4.2.2.1: icmp_seq=1 ttl=56 time=344 ms
64 bytes from 4.2.2.1: icmp_seq=2 ttl=56 time=342 ms
64 bytes from 4.2.2.1: icmp_seq=3 ttl=56 time=340 ms
64 bytes from 4.2.2.1: icmp_seq=4 ttl=56 time=342 ms
64 bytes from 4.2.2.1: icmp_seq=5 ttl=56 time=337 ms

--- 4.2.2.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 337.154/341.646/344.667/2.552 ms



```

I'm guessing there's something wrong with my network manager? Is there a solution to this? I'm ready to re-install 9.10 if that will help....

@grahammechanical: I appreciate your kind gesture to help :) However I've taken care of the issues you've mentioned:

1)My PC running Ubuntu 9.10 and Windows 7 is connected with a LAN cable (or ethernet whatever its called)to the modem while my netbook running Ubuntu 10.04 and XP has already been connected wirelessly in both OSes.

2)The modem is brand-new and the only password that has been fed into it is the correct one, which is why its working fine in Windows 7. The technician had memorised his instructions to setup the connection in Windows so he couldn't help in any way. There were no instructions with the modem as well. So my only hope now is to re-install network manager or even the whole OS if required.

---

### Post by varunendra on 2010-06-24
On your regular setup, this is the status of your /etc/network/interfaces file:
> **akh00 said:**
> ```

auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider
iface eth0 inet manual

```


While in Live Session, it is:
> **akh00 said:**
> ```

auto lo
iface lo inet loopback

```

What I could get from all this so far is that perhaps your ISP technician has enabled the PPPoE autoconnect function within the modem so that it gets connected automatically as soon as it is powered on. Then you tried pppoeconf forcing it to use eth0 interface.

Now the current scenario is that eth0 interface is forced by pppoeconf to try to establish a ppp connection while there is a pppoe process already running by the modem itself.

If I'm right so far then all you have to do is to remove eth0 from pppoeconf's interfaces' list.
[COLOR=DarkRed][B]This ([click here]("http://ibnaziz.wordpress.com/2010/02/17/removing-pppoeconf-settings-in-ubuntu-9-10/")) should exactly be your problem & solution.
[/B][/COLOR]
If the method in the above link doesn't work, you may also try to manually edit the **/etc/network/interfaces** file to look it like:> auto lo
iface lo inet loopback
(delete the rest of the lines)and then manually deleting **/etc/ppp/peers/dsl-provider** file (you'll need root privilege to access/delete it).

[Note that I've suggested to leave only first two lines in the /etc/network/interfaces file as against to what the linked page suggests. Because this is exactly how mine one looks like & my conn. works perfectly with dhcp]

And Yes! If nothing of this works, then making a fresh install without trying pppoeconf this time should definitely do the job for you. But you should try the above solution first for sake of experience & saving time!
:popcorn:




@grahammechanical,
5-lines of suggestions and 8-lines of "excuse-me" & apology in advance?
Chill out buddy! ;) Who do you think was born-perfect around here? You're trying to help with whatever experience you've got - is all that matters. Anyone whose concerns or comments matter for you would be appreciating your effort & willingness to help out! :)

---

### Post by dineshs on 2010-06-24
Pl try this
```
gksudo gedit /etc/network/interfaces 
``` 
edit the file so that it contains only this
```
auto lo
iface lo inet loopback

```
[COLOR="Blue"]Now restart your PC[/COLOR] and configure the connection via the DSL tab in NM and [COLOR="DarkRed"]do not attempt to use pppoeconf command[/COLOR].While doing this tick the option [COLOR="Blue"]Available to all users[/COLOR] (Pl see the attachment)
Once this setup is ready you can click on the NM icon and connect/disconnect DSL

---

### Post by varunendra on 2010-06-24
> **dineshs said:**
> Pl try this
```
gksudo gedit /etc/network/interfaces 
```edit the file so that it contains only this
```
auto lo
iface lo inet loopback

```[COLOR=Blue]Now restart your PC[/COLOR] and configure the connection via the DSL tab in NM and [COLOR=DarkRed]do not attempt to use pppoeconf command[/COLOR].While doing this tick the option [COLOR=Blue]Available to all users[/COLOR] (Pl see the attachment)
Once this setup is ready you can click on the NM icon and connect/disconnect DSL

The editing part is correct in my opinion too, but what if PPPoE is already running by the modem itself?
I suspect this because the "doesn't find any access concentrator" thing he mentioned suggests so.

Anyway I tried to simulate this scenario on VMware & everytime I try to connect via DSL, it fails & switches back to regular eth0 connection. So there should be no harm trying your suggestion. But I also think there's no need to try the second part (setting DSL in NM).

---

### Post by dineshs on 2010-06-24
varunendra,
You are right.Let akh00 try the first part alone.

---

### Post by akh00 on 2010-06-24
Thanks a lot varun and dinesh for your help :) I edited the file, did a restart the connection was triggered automatically without me having to do anything. What's more, the connection was under the "Wired" tab and not in the  "DSL" tab in Network Manager. Anyway I'm happy that I've got back my connection at last. 


Thanks a lot again!!!!

---

### Post by varunendra on 2010-06-24
You're welcome! You should mark the thread as [Solved] now.
(Thread Tools>Mark this thread as Solved)

---

### Post by dineshs on 2010-06-25
> **akh00 said:**
>  What's more, the connection was under the "Wired" tab and not in the  "DSL" tab in Network Manager
This means your modem is in PPPoE mode ie `always on' mode with username and password stored in it.Had it been in `bridge mode(connect/disconnect on demand)you would have had to create a DSL connection.
Any way happy to hear your problem is solved

---

### Post by akh00 on 2010-06-25
Well it doesn't really make a difference to me if its always on or in bridge mode - I used to set up the connection to start at boot time anyway :) This one is more convenient because I don't have to type "poff" everytime I want to disconnect - I can simply click on the applet to disconnect!

---

### Post by varunendra on 2010-06-25
> **akh00 said:**
> Well it doesn't really make a difference to me if its always on or in bridge mode - I used to set up the connection to start at boot time anyway :) This one is more convenient because I don't have to type "poff" everytime I want to disconnect - I can simply click on the applet to disconnect!

Sorry but I'm not getting you. Just to make it clear- when your modem is in PPPoE mode, it always remains connected to the broadband unless it is powered off. As soon as it is powered on again, it automatically gets connected to the broadband all by itself. It doesn't matter whether any computer is connected to it or not! In this mode it acts like an Internet Server which itself is **always connected** to the internet, and is just sharing its connection with other computers on the LAN it is connected to.

:DWe are happy if you are happy:D, but you should know that **"It doesn't get connected at the time of booting of your computer. It (modem) is always connected!!"**

So if you want it to get connected or disconnected at the click of an applet, then you MUST log into your modem, change it from PPPoE mode to 'bridged' mode & then configure your DSL tab in the NetworkManager as Dinesh told in the first post at this page.

---

