---
title: "Help! upgraded to v8.10 - now no Internet"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by bobmac on 2009-05-08
Folks,

Using the upgrade option from the menu, I upgraded from v8.04 to v8.10. After the upgrade everything appeared to work OK except the fact that I now have no Internet connection.

I'm pretty well a novice so I followed all the prompts as best I could and believe that I got them all correct for my system.

I wonder if anyone can give me a clue (in a step by step way) as to how to fix this.

I've done a previous upgrade from v7.x to 8.04 with no problem and belive that I followed the same steps from 8.04 to v8.10.

Along the way I have installed all of the updates that have been sent.

Regards,

Bob

---

### Post by t0mppa on 2009-05-08
Networking driver issues have been known to happen between version upgrades, at least of late (-> 8.10 and -> 9.04). So, going to need a bit more info to be able to help out. Is it wireless or wired connection or both that broke?

Also, please open up a terminal, run the following commands there and post the output:```
lspci
lshw -C network
ifconfig
```

P.S. Just out of curiosity, why are you upgrading to 8.10 now? Just a step on the way to 9.04?

---

### Post by bobmac on 2009-05-08
t0mppa,

I've run the commands

lspci
lshw -C network
ifconfig

the results are in the attachment. I've also run the route command which is in the other attachment. I can also ping my router which is home.gateway successfully.

As I'm pretty well a novice with anything to do with the command stuff of ubuntu I don't really know what I'm doing so any help will be gratefully appreciated.

Bob

---

### Post by superprash2003 on 2009-05-09
post output of ping 74.125.45.100 .. are other machines on your network able to access?

---

### Post by bobmac on 2009-05-09
superprash2003,
I can communicate with the other machine in my small network successfully. However, when I ping 74.125.45.100, or any other ip on the other side of the router I don't get a reply.

With my other machine (windows xp) I have no problem accessing the internet through the same router.

Bob

---

### Post by Peter09 on 2009-05-09
Can you post the output of the terminal command

```
route
```

---

### Post by Peter09 on 2009-05-09
It looks to me as if you have no DNS server set up.

---

### Post by Peter09 on 2009-05-09
Right Click on your network icon and select Connection Information, what does it tell you about the DNS server?

---

### Post by superprash2003 on 2009-05-09
well he isnt able to ping that ip either.. post output of** sudo iptables -L** .. bring down any other interfaces you have which you arent using

---

### Post by Peter09 on 2009-05-09
See if this command resolves the problem - this is a known problem

```
sudo avahi-daemon
```

---

### Post by bobmac on 2009-05-09
> **Peter09 said:**
> See if this command resolves the problem - this is a known problem

```
sudo avahi-daemon
```
Folks,

The command:  sudo avahi-daemon responds with:
Daemon already running PID 5335.

The command: sudo iptables -L responds with:
Chain INPUT (policy ACCEPT)
target     prot opt source     destination

Chain INPUT (policy ACCEPT)
target     prot opt source     destination

Chain INPUT (policy ACCEPT)
target     prot opt source     destination

I'm afraid that I don't know how to bring down other interfaces you have which I'm not using.

When I open the Connection Information dialog from the icon, the message is 'No valid active connections found!'

Bob

---

### Post by superprash2003 on 2009-05-10
could you post output of **ifconfig** again

---

### Post by bobmac on 2009-05-10
superpras3002,

The output of the ifconfig command is:

calban@ubuntu-desktop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:11:95:d5:ef:92  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fed5:ef92/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13486 (13.4 KB)  TX bytes:4487 (4.4 KB)

eth0      Link encap:Ethernet  HWaddr 00:1a:4d:9b:04:46  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe9b:446/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17926 (17.9 KB)  TX bytes:16816 (16.8 KB)
          Interrupt:222 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-11-95-D5-EF-92-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4001 errors:0 dropped:0 overruns:0 frame:33
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:320589 (320.5 KB)  TX bytes:8140 (8.1 KB)
          Interrupt:21 

Bob

---

### Post by Peter09 on 2009-05-10
Can you try going to System->Admin->Network Tools and selecting the trace route tab.

In the box put something like [www.google.com](www.google.com), or an IP number of an external machine. Hit the Trace button.

Can you post the output.

---

### Post by bobmac on 2009-05-10
Peter09,

Trace route returns:

1 ubuntu-desktop.local     192.168.1.2
1 home.gateway             192.168.1 254
1 home.gateway             192.168.1 254

which I assume means that everything's ok up to the router but nothing can get past it. Which seems strange as I've also got an xp pro box which has no problems in accessing the Internet. (That's what I'm using to talk to you great folks that are trying to help me)

Bob

---

### Post by Peter09 on 2009-05-10
an you do this experiment. I'm not sure of the syntax of the deletes you may have to expriment. These are temporary changes as they will be lost when you restart.

In a terminal

```
sudo route del home.gateway etho
```and
```
sudo route del  home.gateway ath0
```and 
```
 sudo route add default gw 192.168.1.254 eth0
```The difference is that you are specifying the gateway through its IP address. Every route output I have seen has specified an IP address, not the dns name.

I am wondering if there is some sort of fatal catch22 where its trying to look externally to resolve the gateway IP so that it can find the gateway to look externally......

---

### Post by t0mppa on 2009-05-10
Woah, 14 new posts in a day, looks like OP found some well motivated helpers. :)

Anyway, do as Peter09 says. The whole point of a DNS (Domain Name Server) is to give out information of which address (in human readable format, ie. [www.google.com](www.google.com)) has been mapped to which IP. Thus if your gateway is not an IP address and you don't have a DNS server in your local network, it will try to connect through your gateway to the external DNS in order to ask which IP your gateway is on in order to be able to connect to it. Naturally that is a bit of a dilemma and the packets will just end up never getting anywhere.

---

### Post by Peter09 on 2009-05-10
t0mppa,
what tangled webs we weave .... :)

---

### Post by superprash2003 on 2009-05-11
out of ath0,eth0 and wifi0 which one connects to the internet?

---

### Post by Peter09 on 2009-05-11
Hi,
you need to edit /etc/network/interfaces and insert in the eth0 section so that it looks like this.

> 

auto eth0
        up route add default gw <gateway IP>


then restart with

 	Code:
 	/etc/init.d/networking restart 


---

### Post by bobmac on 2009-05-11
Peter09,

Again thanks for your info but, looking at the file, I'm not sure where to enter the data.

Bob

---

### Post by Peter09 on 2009-05-11
OK.
my file looks like this

> 
auto lo
iface lo inet loopback



So I would edit my file to look like this

> 
auto lo
iface lo inet loopback

auto eth0
        up route add default gw <gateway IP>



---

### Post by bobmac on 2009-05-11
Peter09,

Tried what you suggested. This is what my Interfaces file looked like after the change:

root@ubuntu-desktop:/etc/network# cat interfaces
auto lo
iface lo inet loopback



iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.254

auto eth0
up route add default gw 192.168.1.254

iface ath0 inet dhcp
wireless-key s:bobmacpherson
wireless-essid wlan-ap

auto ath0

I tried to access the internet after closing the file and that was no good. I then rebooted and tried again and the browser reported an address not found message.

I've removed the change and saved the file again, rebooted again and entered the temporary data that you suggested (sudo route add default gw (ip address) eth0 and everything is back working.

Perhaps at this point I should let you know that I've been trying to become familiar with ubuntu and, Linux, however, I find it a bit of a challenge, I'm an old foggy (68 yoa very soon) and am extremely gratefull for all the assistance you and others on the ubuntu forums give. For each problem that I manage to get a result for I note in a doc so that I don't forget the next time that I get it. So I hope you don't get too fed up of my stupid questions.

Bob

Bob

---

### Post by Peter09 on 2009-05-11
Hi,
theres no problem  here Bob, us Ubuntuites stick together :)

Can I suggest that you (as an experiment) do this:
This saves your current interfaces file by moving it to a different file name
```
sudo mv /etc/network/interfaces /etc/network/interfaces-saved
```Then make a new one exactly like mine would be (see above)

```
sudo gedit /etc/network/interfaces
```
(This will remove your static IP address, but Hell - we can put that back later)

restart networking

```
sudo /etc/init.d/networking restart
```In the event of no network connection do this to copy back the old one and restart networking again

```
sudo cp /etc/network/interfaces-saved /etc/network/interfaces
```

---

### Post by Peter09 on 2009-05-11
Note small ommission - I mean that the file will be exactly like mine + plus the added gateway.

---

### Post by bobmac on 2009-05-11
Peter09,

That seemed to work OK as soon as I saved the file. However, I stupidly rebooted. When I selected the browser I got a message telling me to enter the key for my wirless net. This I did, the browser came up OK but it's now as slow as a dog. When I check the Connection Information I now get a wired connection and a wireless connection. The wired has:

Interface:    Ethernet (eth0)
Hardware address 00:1A:4D:9B:04:46
Driver           forcedeth
Speed            100Mb/s
Security         None

Ip Address        192.168.1.4
Broadcast Address 192.168.1.255
Subnet Mask       255.255.255.0
Primary DNS       192. 231.203.132

When I open the Edit Connections there are 3 entries, each named Wired connection1 with never located at the rhs of each. One of them has the Ip4 settings tab Addresses box set to:

Address         Netmask         Gateway
192.168.1.4     255.255.255.0   0.0.0.0

I don't know if this helps.

Bob

---

### Post by Peter09 on 2009-05-11
This is OK.

can you post the output of 

```
ifconfig
```

---

### Post by bobmac on 2009-05-11
Peter09,

The ifconfig reads:

calban@ubuntu-desktop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:11:95:d5:ef:92  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fed5:ef92/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2050 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1814 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2114735 (2.1 MB)  TX bytes:303655 (303.6 KB)

eth0      Link encap:Ethernet  HWaddr 00:1a:4d:9b:04:46  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe9b:446/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:522 errors:0 dropped:0 overruns:0 frame:0
          TX packets:287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:94314 (94.3 KB)  TX bytes:30712 (30.7 KB)
          Interrupt:222 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2500 (2.5 KB)  TX bytes:2500 (2.5 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-11-95-D5-EF-92-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28444 errors:0 dropped:0 overruns:0 frame:2265
          TX packets:2707 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:4221860 (4.2 MB)  TX bytes:400915 (400.9 KB)
          Interrupt:21 

Bob

---

### Post by bobmac on 2009-05-11
Peter09,

The ifconfig reads:

calban@ubuntu-desktop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:11:95:d5:ef:92  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fed5:ef92/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2050 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1814 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2114735 (2.1 MB)  TX bytes:303655 (303.6 KB)

eth0      Link encap:Ethernet  HWaddr 00:1a:4d:9b:04:46  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe9b:446/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:522 errors:0 dropped:0 overruns:0 frame:0
          TX packets:287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:94314 (94.3 KB)  TX bytes:30712 (30.7 KB)
          Interrupt:222 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2500 (2.5 KB)  TX bytes:2500 (2.5 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-11-95-D5-EF-92-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28444 errors:0 dropped:0 overruns:0 frame:2265
          TX packets:2707 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:4221860 (4.2 MB)  TX bytes:400915 (400.9 KB)
          Interrupt:21 

Bob

---

### Post by Peter09 on 2009-05-11
OK, you have a hard wired connection and a wireless connection running at the same time, best to disable one of them, either pull the wire or switch of the wireless on the laptop, or right click on the network icon and disable the wireless connection.

The repost ifconfig and see if it still is running badly.

---

### Post by bobmac on 2009-05-11
Peter09,

Disconnected the wireless connection 1st - that seemed to drop the Internet connection. Then took out the wired connection. This seems to work.

The ifconfig file is:

calban@ubuntu-desktop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:11:95:d5:ef:92  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fed5:ef92/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2947 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3449411 (3.4 MB)  TX bytes:476772 (476.7 KB)

eth0      Link encap:Ethernet  HWaddr 00:1a:4d:9b:04:46  
          inet6 addr: fe80::21a:4dff:fe9b:446/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:747 errors:0 dropped:0 overruns:0 frame:0
          TX packets:383 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:148262 (148.2 KB)  TX bytes:40653 (40.6 KB)
          Interrupt:222 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3372 (3.3 KB)  TX bytes:3372 (3.3 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-11-95-D5-EF-92-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41853 errors:0 dropped:0 overruns:0 frame:2600
          TX packets:4176 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:6601153 (6.6 MB)  TX bytes:624034 (624.0 KB)
          Interrupt:21

---

### Post by Peter09 on 2009-05-11
Good,
do you need a static IP, you are running with an internal ip of 192.168.1.4 which has been allocated by your router, this may change between connections. Its best to leave it as is unless you have a specific requirement for a static IP.

---

### Post by bobmac on 2009-05-11
Folks,

To all that replied to my query - my thanks. Your dedication to assist we who are not very technical minded is very much appreciated.

Bob

---

### Post by t0mppa on 2009-05-11
> **bobmac said:**
> Perhaps at this point I should let you know that I've been trying to become familiar with ubuntu and, Linux, however, I find it a bit of a challenge, I'm an old foggy (68 yoa very soon) and am extremely gratefull for all the assistance you and others on the ubuntu forums give. For each problem that I manage to get a result for I note in a doc so that I don't forget the next time that I get it. So I hope you don't get too fed up of my stupid questions.

Documenting solutions is a pretty good idea, I know it's fairly frustrating to try fixing something you know you've fixed before and just can't remember how. And don't worry, these aren't stupid questions. I could well see the average Ubuntu user running into similar trouble as described here. The younger folk might learn quicker, but are often impatient and give up on the first sign of trouble.

---

### Post by mntokman on 2009-05-11
Hello to all, 

I have been reading the threads to find a solution to my problem. I am a beginner linux user. I have had Xubuntu in my Sony VAIO laptop which I set up without partitioning my disk. Now I wanted to switch to Kubuntu and I format my disk. I am having connection problems with it. It is 8.10 version, not sure how to resolve this problem. 

Any suggestions?

---

### Post by Peter09 on 2009-05-11
mntokman, start a new thread, I'll keep an eye out for you. Post the output of

 ```
ifconfig
```

and

```
lshw -C network
```

---

### Post by mntokman on 2009-05-11
> **mntokman said:**
> Hello to all, 

I have been reading the threads to find a solution to my problem. I am a beginner linux user. I have had Xubuntu in my Sony VAIO laptop which I set up without partitioning my disk. Now I wanted to switch to Kubuntu and I format my disk. I am having connection problems with it. It is 8.10 version, not sure how to resolve this problem. 

Any suggestions?

I have a modem and router together that came from my ISP, the connection is ADSL. I can post iwconfig and ifconfig is it helps.

---

### Post by Peter09 on 2009-05-11
Yes do that, but start a new thread, this one is too long.

---

### Post by mntokman on 2009-05-11
new thread subject is "[B]having wireless connection problems after switching from Xubuntu to Kubuntu"

I attached the outputs as well. 

Thanks
[/B]

---

