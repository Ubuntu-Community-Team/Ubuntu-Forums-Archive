---
title: "ethernet network connectivity problem,9.10. (Partialy know the problem)"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by AlexZaim on 2009-11-18
Firstly i have upgraded to 9.10 from 9.04 . The network was working after the upgrade... but while installing it asked me if a newer version of a file can be added. I choose yes, and it was the configuration file from "/etc/default/NetworkManager". 
After the install there where some incompatibilities so it asked me to *replace* the old version with the newer and thus worked.

After that i did a clean install... configured IPv4 but no connection!

I believe the problem could be easy to solve if someone would look into their config file (from within 9.04!) and tell me the difference between mine.

This is my present config file (posting from Win): 
> # This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

no-auto-default=00:19:db:b5:c5:73,

[ifupdown]
managed=false



Btw, it does say that the connection is established(but i don't have any access to the i-net), but after a while it disconnects.

---

### Post by AlexZaim on 2009-11-19
Another problem is that when i enter my configuration setup in win and press OK (instead of cancel) not doing any changes it gives me the following message (look at the atachment).

Plus the i-net connection is very weak/slow. :(

---

### Post by AlexZaim on 2009-11-19
Can someone also tell me what's inside there config file in ~/.gconf/nm-applet/...
The file is called %gconf.xml

This is what i have in mine:
> <?xml version="1.0"?>
<gconf>
	<entry name="stamp" mtime="1258617924" type="int" value="1"/>
</gconf>


Please help me someone with these config files! Those who have their connection up-nd-going, pls help.

---

### Post by Aearenda on 2009-11-19
My system has worked from day 1 on the Internet with 9.10, both wired and wireless - but it was a fresh installation. There is no /etc/default/NetworkManager, but the contents of /etc/NetworkManager/nm-system-settings.conf match what you posted with the exception of the no-auto-default line, which is absent.

Likewise the contents of .gconf/apps/nm-applet/%gconf.xml match except that the timestamp is understandably different.

I don't think these files are particularly relevant to your problem. When you say 'configured IPv4' what do you mean? I think you will have to tell us more about your network to get any help.

Is this wired or wireless?
Are you trying to set a static IP address or use an automatic one from DHCP?
If static, why, and what is your IP address, net mask and gateway address?
Are you connecting to a home network with a router, or direct to an ISP, or something else?
What settings did you have for Windows XP when it gave you that error?

Also please post the contents of /etc/network/interfaces, and the output from running 'ifconfig' in a terminal.

---

### Post by rahilm on 2009-11-19
i have the same problem. but fortunately i didn't upgrade so i have my 9.04 still installed.
here is my nm-system-settings.conf
```

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false


```

and here is the same file from 9.10

```

# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false


```

---

### Post by rahilm on 2009-11-19
here is the output of ifconfig from my 9.04 where internet is working:

```

eth0      Link encap:Ethernet  HWaddr 00:19:d1:83:fe:cb  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe83:fecb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4695 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4652 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4761143 (4.7 MB)  TX bytes:1082856 (1.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


```

and here is from 9.10 where internet is not working:

```

eth0      Link encap:Ethernet  HWaddr 00:19:d1:83:fe:cb  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe83:fecb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1779 (1.7 KB)  TX bytes:5469 (5.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


```

there is a lot of difference, can you tell me how to correct it??

---

### Post by Aearenda on 2009-11-19
Rahilm, I can't say what is right or wrong without a lot more information. Please will you answer the same set of questions that I gave AlexZaim:

Are you trying to set a static IP address or use an automatic one from DHCP?
If static, why, and what is your IP address, net mask and gateway address?
Are you connecting to a home network with a router, or direct to an ISP, or something else? (It looks like a home network, since your address is a 192.168.x.x one.)

Also, please post the contents of /etc/network/interfaces, and one extra item: the ouput from running 'route' in a terminal.

---

### Post by AlexZaim on 2009-11-20
> Is this wired or wireless?
Are you trying to set a static IP address or use an automatic one from DHCP?
If static, why, and what is your IP address, net mask and gateway address?
Are you connecting to a home network with a router, or direct to an ISP, or something else?
What settings did you have for Windows XP when it gave you that error?
1. Wired
2. Static, 'cause other doesn't work.
3. I installed Wicd network manager and it works out of the box, but it changed some numbers (some combinations i did tried on nm-applet later) IP:89.28.91.191; Netmask : 255.255.255.0 (should have been 255.255.254.0); Gateway : 89.28.91.1 (should have been 89.28.60.1); 
4. I don't know what's  an ISP but it's a direct connection with a lan card. I also know its fiber link.
5. The  "should have been" setting are now in win 7. (I'm posting from ubuntu with Wicd)

/etc/network/interfaces
> 
auto lo
iface lo inet loopback


---

### Post by Aearenda on 2009-11-20
'ISP' is 'Internet Service Provider', the organisation that gives you Internet access. Sorry for not being clear. Your /etc/network/interfaces looks good.

It's unusual for you to have to use a static address on a direct connection to the Internet. In Australia you generally have to pay extra to get a static address, and it's only needed if you have a server that you want people 'out there' on the Internet to get to by name.

If you have been asked by your Internet provider to use a static address, then they usually provide the gateway, netmask and DNS server (for name resolution) details to use when you set the service up. You never have to guess them, and if they haven't asked you to do this, and you haven't asked them to do this, you probably shouldn't be using a static address at all.

It is more normal for the Internet provider to use a method called 'DHCP' which allocates your computer all these details automatically. Ubuntu (both WiCD and NM) and Windows expect this to be used by default. The address you get allocated can change automatically from time to time, so you should never set a static address on a computer that is supposed to use DHCP since the address could be reallocated to somebody else, and you would be interfering with their service by hanging on to it - it's like keeping a book out of a public library longer than your loan time.

If I understand your last post correctly, WiCD has used DHCP to get a working address for you - if you had set a static address it wouldn't have changed anything on its own. Now that it is working I think you should let it continue to do its job and not override it unless you have a really good reason.

Edit: The 'no-auto-default=00:19:db:b5:c5:73' setting is probably what is preventing NM from getting a DHCP address in the normal way. But if WiCD is working, just leave it!

---

### Post by AlexZaim on 2009-11-20
No, i wasn't using dhcp since i conected to my new provider StarNet. The technician wrote the ip's in static in the first place... It never changed since then.
Ok, back to wcid...

When i placed my cursor and clicked the gateway form, it automaticly wrote the gateway for me. I was inserting everything in static 'mode'.

So i'm using the same static configuration before (just a little bit diffrent), but with wicd, and it's working :).

---

### Post by rahilm on 2009-11-20
> **Aearenda said:**
> Rahilm, I can't say what is right or wrong without a lot more information. Please will you answer the same set of questions that I gave AlexZaim:

Are you trying to set a static IP address or use an automatic one from DHCP?
If static, why, and what is your IP address, net mask and gateway address?
Are you connecting to a home network with a router, or direct to an ISP, or something else? (It looks like a home network, since your address is a 192.168.x.x one.)


I have no idea. My connection has been working OOTB since 8.04 and in windows. So, I never configured anything. I only went as far as configuring my router username and password.

> **Aearenda said:**
> 
Also, please post the contents of /etc/network/interfaces, and one extra item: the ouput from running 'route' in a terminal.

/etc/network/interfaces
```

auto lo
iface lo inet loopback

```

route output:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         mygateway1.ar7  0.0.0.0         UG    0      0        0 eth0

```

The above outputs are the same for both my distros

---

### Post by Aearenda on 2009-11-20
rahilm, everything looks ok to me. You say you have the same problem as the original post in this thread, but I suspect it's the same only in that something isn't working as you expect it to. 

The output from 'route' names your gateway, which I think it would not do if the local network were not working. 

What happens if you enter this command in a terminal?
```
ping 192.168.1.1
```
Also please post the contents of /etc/resolv.conf.

---

### Post by rahilm on 2009-11-21
ping 192.168.1.1
```

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=255 time=0.614 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=255 time=0.591 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=255 time=0.596 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=255 time=0.598 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=255 time=0.604 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=255 time=0.597 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=255 time=0.594 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=255 time=0.526 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=255 time=0.596 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=255 time=0.594 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=255 time=0.599 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=255 time=0.599 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=255 time=0.596 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=255 time=0.599 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=255 time=0.614 ms
64 bytes from 192.168.1.1: icmp_seq=16 ttl=255 time=0.602 ms
64 bytes from 192.168.1.1: icmp_seq=17 ttl=255 time=0.534 ms
64 bytes from 192.168.1.1: icmp_seq=18 ttl=255 time=0.609 ms
64 bytes from 192.168.1.1: icmp_seq=19 ttl=255 time=0.608 ms
64 bytes from 192.168.1.1: icmp_seq=20 ttl=255 time=0.536 ms
64 bytes from 192.168.1.1: icmp_seq=21 ttl=255 time=0.620 ms
^C
--- 192.168.1.1 ping statistics ---
21 packets transmitted, 21 received, 0% packet loss, time 19998ms
rtt min/avg/max/mdev = 0.526/0.591/0.620/0.038 ms

```sorry had to ctrl-C in between

```

cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1

```I keep getting this screen forever:
(if someone could tell me how to upload an image)

---

### Post by Aearenda on 2009-11-21
Well, there's nothing apparently wrong with your Ubuntu setup, since you can ping your router, your computer knows where to send traffic to addresses beyond its own network, and it knows where to send name resolution requests. 

What happens if you try pointing Firefox to 'http://192.168.1.1', or 'www.google.com', or 'www.ubuntu.com'?

Also, what happens of you enter the following in a terminal? ```
wget www.google.com
```

---

### Post by rahilm on 2009-11-21
192.168.1.1 navigates to the router configuration page

for all others ..nothing happens,..
just the same
stuck at connecting to .....

---

### Post by Aearenda on 2009-11-21
I'm assuming here that the 'wget' command gets stuck too, since you didn't say. This is intended to rule out any problem with Firefox, so if you didn't try it, please do. However, since Firefox brings up the router page, it seems that it is working ok.

I have realised that I have also assumed that 'mygateway1.ar7' is the name of your router - but just to be sure, please tell us what this says:```
route -n
```

Also, please post the output of this command:```
dig www.google.com
```This should test the name resolution service - but I think that is working, otherwise Firefox would give you an error message, not just sit there forever.

In your earlier post, what did you mean when you said "I only went as far as configuring my router username and password"? Was this in Firefox, or something else?

EDIT: By the way, have you added any firewall or proxy settings on 9.10? AND, does your router have any access restrictions set up, which might be triggered by your IP address being 192.168.1.2 instead of 192.168.1.3? Are there any other computers on your network at the same time?

EDIT 2: (sorry, getting late here, not thinking well) If there are other computers on the network, please list their IP addresses (you can get these from 'ipconfig /all' on Windows and 'ifconfig' on Ubuntu).
Also, lets rule out ipv6 issues in Firefox: follow the instructions at [http://kb.mozillazine.org/Error_loading_any_website#IPv6](http://kb.mozillazine.org/Error_loading_any_website#IPv6) and then restart Firefox and see if it works.

---

### Post by rahilm on 2009-11-21
Hey..Aearenda...I just want to thank you for all the trouble you are taking.
All this is becoming very inconvenient since I have to read the instructions, save them to a file, restart my computer, log into 9.10 , execute and save the outputs to a file, then restart my computer, log into 9.04 then post my outputs.
(not mentioning that i usually forget one or two outputs)

Alright,
here is route -n
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```dig [www.google.com]("http://www.google.com")
```

; <<>> DiG 9.6.1-P1 <<>> www.google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 54534
;; flags: qr rd; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;www.google.com.            IN    A

;; ANSWER SECTION:
www.google.com.        10000    IN    A    209.85.231.104

;; Query time: 1 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sat Nov 21 21:01:15 2009
;; MSG SIZE  rcvd: 48

```> 
In your earlier post, what did you mean when you said "I only went as far as configuring my router username and password"? Was this in Firefox, or something else?
Well, i have a broadband connection through a router that connects via LAN cable (ethernet) and the router connects to my ISP via telephone line. So , when i change my password, i have to do that in my router firmware as well, so i input 192.168.1.1 in any browser (both linux and windows) and there i have various options to change.
Router - D-Link DSL 502T


and mine is the only computer at home

I've been having problems even in the Live-Cd so no chance of configuration of firewall..


hey..when i do 
ifconfig eth0 inet 192.168.1.3

Firefox displays page cannot be loaded error...



EDIT:
Problem update::
[http://ubuntuforums.org/showthread.php?p=8361231#post8361231](http://ubuntuforums.org/showthread.php?p=8361231#post8361231)

it is a DNS issue..perhaps you can guide me better now..
regards

---

### Post by rahilm on 2009-11-21
Thanx for all the help guys..i added few DNS servers and net is up and running..
In hindi we say:
Khoda pahaad nikla chuha
which means
Dug the whole mountain only to find a rat..
couldn't thank you much
my regards

---

### Post by Aearenda on 2009-11-21
I'm glad it's working now! Your persistence is rewarded.

It would have been helpful to know you had the other thread going on the same issue - but I think we were converging on the same answer. The 'dig' command in my last post is a DNS test - it tells us whether you can resolve the name ([www.google.com](www.google.com)) to an address.

p.s. I wonder if you have been affected by [this bug]("https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757"), since a workaround for that (configuring DNS servers) is what made your system work.

---

### Post by ajparag on 2010-05-01
> **Aearenda said:**
> I'm glad it's working now! Your persistence is rewarded.

It would have been helpful to know you had the other thread going on the same issue - but I think we were converging on the same answer. The 'dig' command in my last post is a DNS test - it tells us whether you can resolve the name ([www.google.com](www.google.com)) to an address.

p.s. I wonder if you have been affected by [this bug]("https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757"), since a workaround for that (configuring DNS servers) is what made your system work.

can u post the DNS servers you added to start the connection?

---

