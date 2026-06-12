---
title: "Holding down my upload speed!"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by uldo on 2008-12-04
Something is holding down my upload speed. I have wired network and I'm behind router. In LAN i have 2 pc with windows xp and 3'rd is me running Ubuntu Intrepid 8.10 32bit. How can I fix this?

---

### Post by jonobr on 2008-12-04
Hello


You need to supply more information,
specifically how you came to deduce this,
how your gauging the speeds you expect vs what you are getting,

any tests you did and results.

---

### Post by uldo on 2008-12-04
well first thing is that azureus and utorrent upload speed never gets higher than 50kb/s - at windows the same files (from my pc, i have both OS - windows and ubuntu) goes about 5-8 mb/s .... file transfers via skype e.t.c. are very slow and i just know that my speed is much bigger than it is in ubuntu. Also azureus in "Test NAT/firewall" shows:
```
NAT Error - Connection to my ip adres:33848 (your computer) refused.
```

if you need some special testings then just say what i have to do...

---

### Post by uldo on 2008-12-05
anyone?

---

### Post by jmoorse on 2008-12-07
Most likely the windows box is using UPNP to dynamically open up ports required for applications.

You may want to investigate your router's documentation for instructions on how to forward ports, and next find out which ports Azureus and Skype uses.

---

### Post by uldo on 2008-12-08
I already forwarded ports - nothing changes.... Is there any chance that Ubuntu is limiting quanity of outgoing connections??

---

### Post by jonobr on 2008-12-08
post your output to ifconfig -a

Also, you might search around for disabling IPV6 if you are running IPV4,
people have mentioned that that does work sometimes

---

### Post by uldo on 2008-12-08
where can i search for him? i only found ipv4...
ifconfig -a output:
```
eth0      Link encap:Ethernet  HWaddr 00:19:d1:5a:72:9a  
          inet addr:192.168.2.8  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:475425 errors:0 dropped:0 overruns:0 frame:0
          TX packets:713950 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:149833388 (149.8 MB)  TX bytes:236928103 (236.9 MB)
          Memory:93200000-93220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:33129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3439296 (3.4 MB)  TX bytes:3439296 (3.4 MB)

pan0      Link encap:Ethernet  HWaddr 2e:6c:bb:94:b6:37  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by jonobr on 2008-12-08
Im guessing your using eth0 ,
Also it looks as if your MTU size is a 3rd the size it usually is for Ethernet connections.

I would recommend you try changing mtu to 1500 which is default.

There should be info on the forums on changing the MTU size.
Always be prepared to change back in case of any undesired affects.

MTU is the max transmission unit which is the size of the payload on your ethernet packet,

Having it small means smaller packets of data, more fragmentation.
Sometimes its a balance to get it right , however, for most folks default 1500 should be fine for regular Ethernet

---

### Post by uldo on 2008-12-09
ok i will do that and post my results after that, but i have another question - so if my internet speed is high i can chage the MTU even higher to raise usage of it?

---

### Post by jonobr on 2008-12-09
The MTU is max transmission unit, so there is a max,

The MTU is typically defined by standards, and for ethernet (Im guessing your using ethernet as you have eth0) its set to 1500 by default.

The MTU is changeable, so if you were talking to another network interface card that is using say dial up, the MTU will be a lot smaller,

Making the MTU very large or very small will not help you out any and will only clog slower cards oin the case of large packets and do a lot of data fragmentation in the case of small.

I would strongly recommend that you find out that you are definitely using an  ethernet V2 card  as 576 sounds old and I think applies to an older standard.

---

### Post by jonobr on 2008-12-09
mmmmm....
Just found this resource (which has good info on finding the MTU sweet spot.

[http://www.internetweekly.org/llarrow/mtumss.html]("http://www.internetweekly.org/llarrow/mtumss.html")

Looking at this , it notes that dialup (its a long time since I did dial up) uses the MTU of 576,.

Are you using dial up internet service?

---

### Post by jmoorse on 2008-12-09
It would be wise to keep your MTU at 1492-1500.  At times an MTU decrease is useful to troubleshoot lower layer problems, I have only seen this a handful of times in many years.

DSL will also adjust the MTU on the WAN side as needed by the remote carrier, although this change will not propagate past your CPE.

Please issue a:

sudo ifconfig eth0 mtu 1500

and test from there.

Edit- One thing to note: this change will not be persistent following a reboot.  Let us know if it resolves the upload issue.

Good eyes jonobr

---

### Post by uldo on 2008-12-09
No, i have cable connection - i don't know how its called corectly but definetly not dial up.

I have found this [http://ubuntuforums.org/showthread.php?t=996396](http://ubuntuforums.org/showthread.php?t=996396) and as i understud, the size of mtu is so low because of my router.
also i tried ping -s 1500 google.lv and it gave me no reply. so i guess that i didnt get it becouse my router cant handle higher size :confused:

---

### Post by frankleeee on 2008-12-09
You might also besides these suggested adjustments try deluge for torrents.

---

### Post by uldo on 2008-12-09
> **frankleeee said:**
> You might also besides these suggested adjustments try deluge for torrents.

whats the difference between utorrent and deluge (except that utorrent goes under wine)??

---

### Post by jmoorse on 2008-12-09
> **uldo said:**
> No, i have cable connection - i don't know how its called corectly but definetly not dial up.

I have found this [http://ubuntuforums.org/showthread.php?t=996396](http://ubuntuforums.org/showthread.php?t=996396) and as i understud, the size of mtu is so low because of my router.
also i tried ping -s 1500 google.lv and it gave me no reply. so i guess that i didnt get it becouse my router cant handle higher size :confused:

In any case still try adjusting the MTU or, as suggested, another torrent client.

The command posted above will cause the OS to auto-fragment the frame per its MTU as needed to carry a 1500 byte packet.

---

### Post by frankleeee on 2008-12-09
> **uldo said:**
> whats the difference between utorrent and deluge (except that utorrent goes under wine)??

I don't really know the difference but of all the torrent programs I have found this one to provide the fastest downloads, it has multiple types of networks and random port usage and encrypts both ways. This might be done in others but I have never run into throttling. As far as wine goes I have never used Microsoft software or need it so wine is not needed for my basic use.

---

### Post by uldo on 2008-12-09
EDIT: this is wrong, i will make it right as soon i will have a little bit more time
i did: 
```
sudo ifconfig eth0 mtu 1500
ping -s 1400 google.lv
```

and i didnt get answer... then i tried ping -s 500 google.lv recieved answer the time: 5084ms
after that i changed back to 576 and trid ping -s 500 google.lv again - recieved answer, time: 3014ms
can't understand why it is that way....??????

---

### Post by jonobr on 2008-12-09
Hey


If while experimenting you are getting ping response times between 3000msec and 5000msec that looks like a big big problem.

If your posting is right,and  you are getting a 3 second delay in your ping, it sounds like your ISP is greedy.
It looks like your cable connection is oversubscribed.
The more people on the slower your connection.

Im wondering is there any off time (say in the very small hours or during worktime) when things get better.

For a ping across the US it should be under 100msec, probably 150 msec for an international one.

I would be sending your ping times to your providor, again, Im not sure if your missing a decimal point in your post, but those times are huge

---

### Post by uldo on 2008-12-09
dont bother about it - its completly wrong becouse i did it wrong (didnt add "-c 5" for example and posted wrong time shown)

---

### Post by Harry_Iyer on 2008-12-21
> **jonobr said:**
> 

Im guessing your using eth0 ,
Also it looks as if your MTU size is a 3rd the size it usually is for Ethernet connections.

I would recommend you try changing mtu to 1500 which is default.

There should be info on the forums on changing the MTU size.
Always be prepared to change back in case of any undesired affects.

MTU is the max transmission unit which is the size of the payload on your ethernet packet,

Having it small means smaller packets of data, more fragmentation.
Sometimes its a balance to get it right , however, for most folks default 1500 should be fine for regular Ethernet

_


I was having similar problem and changing the MTU saved my day

---

