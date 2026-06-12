---
title: "Wire(eth0) and wireless(wlan0) cannot work at the same time"
date: 2010-07-18
forum: Networking &amp; Wireless
---

### Post by wacky_sung on 2010-07-18
I have also tried to load my iptables and ip6tables rules togather with the wireless but can only connect to the wire(eth0).When i unplug the network cable and the wireless cannot seem to be working.Can somebody shed some light.

```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

auto eth0
iface eth0 inet dhcp
  pre-up iptables-restore < /etc/iptables.rules
  pre-up ip6tables-restore < /etc/ip6tables.rules
  post-down iptables-restore < /etc/iptables.downrules
  post-down ip6tables-restore < /etc/ip6tables.downrules

wpa-driver wext
wpa-ssid Hackproof
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk 100a41ac35e246476e330f4b17457cbad9df354fbb7cca7d3f76f31fd1e6791b

```

---

### Post by Iowan on 2010-07-18
Moved to new thread.

... then merged with this thread.

---

### Post by wacky_sung on 2010-07-20
I have tried to get both my wire(eth0) and wireless(wlan0) to work at the same time but it cannot work either wire or wireless at one time.Below is what i have edit my /etc/network/interfaces.

_**[COLOR="Red"]Can only work in Wire(eth0) but have to disable wireless otherwise cannot get connect[/COLOR]**_
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

auto eth0
iface eth0 inet dhcp
  pre-up iptables-restore < /etc/iptables.rules
  pre-up ip6tables-restore < /etc/ip6tables.rules
  post-down iptables-restore < /etc/iptables.downrules
  post-down ip6tables-restore < /etc/ip6tables.downrules

//Wireless Setup
//wpa-driver wext
//wpa-ssid Hackproof
//wpa-ap-scan 2
//wpa-proto RSN
//wpa-pairwise CCMP
//wpa-group CCMP
//wpa-key-mgmt WPA-PSK
//wpa-psk 100a41ac35e246476e330f4b17457cbad9df354fbb7cca7d3f76f31fd1e6791b

```

**_[COLOR="red"]Can only work in wireless(wlan0) but cannot get connected once get cable connected.[/COLOR]_**
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

auto eth0
iface eth0 inet dhcp
  pre-up iptables-restore < /etc/iptables.rules
  pre-up ip6tables-restore < /etc/ip6tables.rules
  post-down iptables-restore < /etc/iptables.downrules
  post-down ip6tables-restore < /etc/ip6tables.downrules


Wireless Setup
wpa-driver wext
wpa-ssid Hackproof
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk 100a41ac35e246476e330f4b17457cbad9df354fbb7cca7d3f76f31fd1e6791b

```

Is there a way to work both way without disable the wireless for the wire to work?

Apart from what i have also the bridge utils software as well.
[[IMG]http://img188.imageshack.us/img188/2330/screenshotubuntusoftwar.th.png[/IMG]](http://img188.imageshack.us/i/screenshotubuntusoftwar.png/)

Get to learn the tutorial from below.
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)
[https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint](https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint)

---

### Post by wacky_sung on 2010-07-20
Bump

---

### Post by wacky_sung on 2010-07-20
Bump.Seem like nobody actually know it.

---

### Post by valbaca on 2010-07-20
AFAIK, one computer cannot have more than one IP address on a network at a time. So you cannot connect to both wired and wireless at the same time.
 
Someone else is free to correct me if they can show otherwise.

---

### Post by wacky_sung on 2010-07-20
Which mean it does not work as convenience as compare to Window OS.What i am trying to do is when cease using wire and by unplug it cable,switch to wireless without any configuration.

---

### Post by sgosnell on 2010-07-20
You can't use both wired and wireless at the same time.  But if you unplug your ethernet, the wireless card should take over and connect.  The wireless connection must be set to connect automatically, though, for an automatic connection.  If the automatic connection box isn't ticked, you'll have to connect manually when you disconnect the ethernet.

---

### Post by theozzlives on 2010-07-20
Why you would want wired and wireless at the same time is beyond me. I've never tried it, but logically it seems that if you use your DHCP in your router to assign an IP address to each MAC address... it may be a feasible solution to try.

---

### Post by wacky_sung on 2010-07-20
> **sgosnell said:**
> You can't use both wired and wireless at the same time.  But if you unplug your ethernet, the wireless card should take over and connect.  The wireless connection must be set to connect automatically, though, for an automatic connection.  If the automatic connection box isn't ticked, you'll have to connect manually when you disconnect the ethernet.
That's why i find Ubuntu lack of this feature in which you have to manually disable it from wireless to wire or wire to wireless ,plus through a reboot.

I am trying to find a way in which it work like a charm as Window OS by unplug a cable and get connected to wireless without any configuration.

> **theozzlives said:**
> Why you would want wired and wireless at the same time is beyond me. I've never tried it, but logically it seems that if you use your DHCP in your router to assign an IP address to each MAC address... it may be a feasible solution to try.

I going use it at home when i have guest coming to my house when i am wire and get wireless with my laptop mobile within an instant unplug the ethernet cable.

---

### Post by valbaca on 2010-07-20
> **wacky_sung said:**
> That's why i find Ubuntu lack of this feature in which you have to manually disable it from wireless to wire or wire to wireless ,plus through a reboot.

I am trying to find a way in which it work like a charm as Window OS by unplug a cable and get connected to wireless without any configuration.



I going use it at home when i have guest coming to my house when i am wire and get wireless with my laptop mobile within an instant unplug the ethernet cable.

Ubuntu does not lack the feature to switch between wireless and wired. I used wired and wireless to connect to my router and Ubuntu automatically uses wired if plugged in (which is preferable) and wireless if not plugged in.

---

### Post by sgosnell on 2010-07-20
Right-click on the network manager icon in the panel, select Edit Connections, and edit the wireless connection you want to use.  Make sure the box at the top left, which says "Connect Automatically" is checked, and that the box at the bottom, "Available to all users", is checked.  You should then get an automatic wireless connection when you remove the ethernet.

@theozzlives:  He doesn't want them to work at the same time, he wants to connect wirelessly, automatically, when the ethernet connection is removed.  I suspect the OP is not a native English speaker, as is most of the world, and he just put a title on the thread that isn't quite correct.

---

### Post by wacky_sung on 2010-07-20
> **sgosnell said:**
> Right-click on the network manager icon in the panel, select Edit Connections, and edit the wireless connection you want to use.  Make sure the box at the top left, which says "Connect Automatically" is checked, and that the box at the bottom, "Available to all users", is checked.  You should then get an automatic wireless connection when you remove the ethernet.

@theozzlives:  He doesn't want them to work at the same time, he wants to connect wirelessly, automatically, when the ethernet connection is removed.  I suspect the OP is not a native English speaker, as is most of the world, and he just put a title on the thread that isn't quite correct.

Why this is not correct?Well,look into my /etc/network/interfaces file which i loaded iptables and get connected.

I have no doubt this can be done through network manager without much effort.

If you can find solution to it will be much appreciated rather than make a cynical remark.

---

### Post by sgosnell on 2010-07-20
I didn't mean to make a cynical remark.  My understanding is that you don't actually want to use both wired and wireless connections at the same time, as indicated in the thread title, but just want to connect automatically by wireless when the wired connection is disabled.  Is this not correct?  The solution is what I posted in the first paragraph.

Your problem may be in the use of iptables.  Why are you using this on a desktop machine?

---

### Post by wacky_sung on 2010-07-21
> **sgosnell said:**
> I didn't mean to make a cynical remark.  My understanding is that you don't actually want to use both wired and wireless connections at the same time, as indicated in the thread title, but just want to connect automatically by wireless when the wired connection is disabled.  Is this not correct?  The solution is what I posted in the first paragraph.

Your problem may be in the use of iptables.  Why are you using this on a desktop machine?

Yes what you have posted in the first paragraph is using network manager in which i already know the solution.What i requested is auto load iptables during the reboot while running wired / wireless.Which mean that i am not using network manager at all.

If you think my iptables has a problem and i am very doubtful about it.

**_[COLOR="Red"]Iptables for IPv4[/COLOR]_**
```
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           recent: UPDATE seconds: 86400 name: lastmeasure side: source 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW recent: UPDATE seconds: 60 name: DEFAULT side: source 
    4   200 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
 1155  964K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x3F 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x00 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x11/0x01 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x18/0x08 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x30/0x20 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x05/0x05 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x03/0x03 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x06/0x06 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x3F 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x00 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x29 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x2B 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x37 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x04/0x04 limit: avg 2/sec burst 2 
   10  2253 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 2 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 17 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 13 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 0 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 11 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  -f  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       udp  --  eth0   *       0.0.0.0/0            0.0.0.0/0           udp dpt:53 recent: UPDATE seconds: 660 hit_count: 7 name: DEFAULT side: source 
    8  2276 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/24        
    0     0 DROP       all  --  *      *       0.0.0.0/0            127.0.0.0/8         
    0     0 DROP       all  --  *      *       0.0.0.0/0            10.0.0.0/8          
    0     0 DROP       all  --  *      *       0.0.0.0/0            172.16.0.0/12       
    0     0 DROP       all  --  *      *       0.0.0.0/0            192.168.0.0/16      
    0     0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/3         

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    4   200 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
 1130  172K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW,RELATED,ESTABLISHED 
    0     0 DROP       all  -f  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:631 
    0     0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:631 
    0     0 DROP       2    --  *      *       0.0.0.0/0            0.0.0.0/0           

```

**_[COLOR="Red"]Iptables for IPv6[/COLOR]_**
```
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all      *      *       ::/0                 ::/0                recent: UPDATE seconds: 86400 name: lastmeasure side: source 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                state NEW recent: UPDATE seconds: 60 name: DEFAULT side: source 
    4   280 ACCEPT     all      lo     *       ::/0                 ::/0                
    0     0 DROP       all      *      *       ::/0                 ::/0                state INVALID 
    0     0 ACCEPT     all      *      *       ::/0                 ::/0                state RELATED,ESTABLISHED 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x17/0x02 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x3F/0x3F 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x3F/0x00 
    0     0 ACCEPT     tcp      *      *       ::/0                 ::/0                tcp flags:0x17/0x02 limit: avg 1/sec burst 5 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x11/0x01 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x18/0x08 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x30/0x20 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x05/0x05 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x03/0x03 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x06/0x06 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x3F/0x3F 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x3F/0x00 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x3F/0x29 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x3F/0x2B 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x3F/0x37 
    0     0 ACCEPT     tcp      *      *       ::/0                 ::/0                tcp flags:0x04/0x04 limit: avg 2/sec burst 2 
    0     0 DROP       udp      *      *       ::/0                 ::/0                limit: avg 1/sec burst 2 
    0     0 DROP       all      *      *       ::/0                 ::/0                frag ids:100:200 first 
    0     0 DROP       udp      eth0   *       ::/0                 ::/0                udp dpt:53 recent: UPDATE seconds: 660 hit_count: 7 name: DEFAULT side: source 
    0     0 ACCEPT     icmpv6    *      *       ::/0                 ::/0                ipv6-icmp type 128 limit: avg 30/min burst 5 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all      *      *       ::/0                 ::/0                state INVALID 

Chain OUTPUT (policy DROP 6 packets, 384 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    4   280 ACCEPT     all      *      lo      ::/0                 ::/0                
    0     0 DROP       all      *      *       ::/0                 ::/0                state INVALID 
    0     0 ACCEPT     all      *      *       ::/0                 ::/0                state NEW,RELATED,ESTABLISHED 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp dpt:631 
    0     0 DROP       udp      *      *       ::/0                 ::/0                udp dpt:631 
    0     0 DROP       all      *      *       ::/0                 ::/0                frag ids:100:200 first 

```

---

### Post by sgosnell on 2010-07-21
Using network manager, the wireless connection is automatic.  I have no suggestions for using iptables.

---

### Post by cariboo on 2010-07-22
I'm using the UNE, When I plug in the wired cable, the system uses the wired connection, when I disconnect the cable the system automagically connects using wireless. 

If you want to do this without using Network-Manager, have a look at arno-iptables-firewall script, I used to use the script for connection sharing as well as a firewall. The script is in the repositories.

---

### Post by grahammechanical on 2010-07-22
I have just read your post. I was connected to the router by wire. I pulled the cable out of the router and left clicked the network connection manager icon. I selected my wireless network from the list (networks of neighbours are also detected). And now I am writing this comment using wireless connection to the router. I do not think that this is so difficult to do. I suspect that a better way would be to disable networking before pulling out the cable. Enabling networking would then instruct the wireless part of network manager to use wireless to connect to the router, especially if set up to connect automatically.

regards

---

### Post by wacky_sung on 2010-07-22
Thank you all for all the responses and appreciated your time and effort to guide to find an alternative solution to it.I do understand all the methods which you guys suggested worked but what i requested is auto load my customize iptables firewall and work as connection i have requested.I do understand network manager and iptables work on the opposite direction which mean that network manager will keep trying to connect to any available connection while iptables resisted it.

```
Configuration on startup
WARNING: Iptables and NetworkManager seem to have a conflict. However NetworkManager is still in Beta. If you are concerned enough about security to install a firewall you might not want to trust NetworkManager to manage it yet. Also note NetworkManager and iptables have opposite aims. Iptables aims to keep any questionable network traffic out. NetworkManager aims to keep you connected at all times. Therefore if you want security all the time, run iptables at boot time. If you want security some of the time then NetworkManager might be the right choice.

WARNING: If you use NetworkManager (installed by default on Feisty and later) these steps will leave you unable to use NetworkManager for the interfaces you modify. Please follow the steps in the next section instead.

NOTE: It appears on Hardy, NetworkManager has an issue with properly on saving and restoring the iptable rules when using the method in the next section. Using this first method appears to work. If you find otherwise, please update this note.
```

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by sgosnell on 2010-07-24
Just out of curiousity, why are you using iptables?

---

