---
title: "[SOLVED] no internet?!!"
date: 2006-02-03
forum: Networking &amp; Wireless
---

### Post by arai on 2006-02-03
i have installed ubuntu and i am unable to connect to the net. adsl connection. i tried to ping different sites using the "network tools" and it is pinging. but when i use firefox to browse the site. no page is displaying. 

please help me.

---

### Post by bscbrit on 2006-02-03
Are you pinging by name or by IP address?  If it works by address and then not by name it is a DNS problem.

---

### Post by mips on 2006-02-03
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337)
Option1

---

### Post by arai on 2006-02-03
hi mips,

according to [this link option 01]("http://www.ubuntuforums.org/showpost.php?p=423242&postcount=4") it works. i get internet. but there is trouble ie., i am able to access the internet only via firefox (after ur suggestions from the link) but i am not able to use gaim (for google talk). pls help. and also not other applications are not able to access the internet. when we changed ipv6 to true it worked for firefox. the same way how to allow other applications to access the internet. i hope you have some solution for this.

---

### Post by arai on 2006-02-03
i am able to access internet through firefox only. i want to use google talk (gaim). but it is not connecting. also other applications irc client are not connecting.:confused: pls help me.

---

### Post by towsonu2003 on 2006-02-04
do you have a firewall installed (firestarter, guarddog)? if yes, make sure you have the ports for chatting open in that firewall's setting... if no firewall, i have no idea, sorry.

---

### Post by arai on 2006-02-04
i do not have firewall under linux.

---

### Post by arai on 2006-02-04
pls help me access the internet. i changed according to mips [advice (option01)]("http://www.ubuntuforums.org/showpost.php?p=423242&postcount=4")  and then i could access the internet via firefox. but sadly gaim and other applications are not able to connect to the net.  ](*,)

i think the problem lies with ipv6 which i changed and now i could access net via firefox. but unable to access net via gaim and bittorrent etc., 

note i use realtech. 

i need your help. thanks in advance.

---

### Post by mips on 2006-02-04
What is your ADSL router Brand&Model, weblink please ???
Who is your ISP, weblink please ???

---

### Post by mips on 2006-02-04
```
[B][U]Option1:
[/U][/B]
In the firefox address/URL space type "about:config" , scroll down to **network.dns.disableIPV6 = false** 
,double click this line to change it to **true**.
In the above do NOT type in any quotes.

[COLOR="Red"]The above will most probably help for Firefox but not your other applications. 
Test with Synaptic, GAIM and other stuff using the net and if they dont work try the following:[/COLOR]

Open a terminal and enter:
**sudo gedit /etc/modprobe.d/aliases**

Look for the line that reads:
**alias net-pf-10 ipv6**

Change it to:
**alias net-pf-10 off #ipv6**

Save and reboot your PC.
```


[COLOR="Red"]**Did you edit your /etc/modprobe.d/aliases file ???**[/COLOR]

---

### Post by arai on 2006-02-04
router brand is Utstar
model is UT300r2
weblink is [http://www.utstar.com/](http://www.utstar.com/)

isp is BSNL (NIB govt of india)
weblink [http://www.bsnl.co.in/service/dataone.htm](http://www.bsnl.co.in/service/dataone.htm)

net not accesable. only ff could access net due to your technic of changing something using about:config and ipv6. 

help me in connecting to the internet. thanks .

---

### Post by arai on 2006-02-04
i did as it is written in box ie., option 1 . 

then i restarted. but i could not connect using gaim and others.

> Did you edit your /etc/modprobe.d/aliases file ???

dono whether i did or not. should we also disable ipv6 in other applications too like in firefox?

---

### Post by mips on 2006-02-04
[QUOTE=arai]i did as it is written in box ie., option 1 . 

then i restarted. but i could not connect using gaim and others.



dono whether i did or not. should we also disable ipv6 in other applications too like in firefox?[/QUOTE]

Would it be to much to ask you to check whether you did or not, I cannot tell from where I am sitting ???

---

### Post by mips on 2006-02-04
Is your router setup as per this guide ? [http://blog.taragana.com/wp-content/upload/bb7.swf](http://blog.taragana.com/wp-content/upload/bb7.swf)

---

### Post by batty505 on 2006-02-04
I would check to see if your running some type of port forwarding on your router. 

make sure you enable them on your router. depending on what type of IM client you are using, make sure you enable the ports on your router.

if this is on a work site, check with the LAN folk to see if they are blocking specific ports

hth
Mike

---

### Post by arai on 2006-02-04
a snapshot i got when i pinged ubuntuforums.org. here is the picture so that somebody could solve the issue.

[[img=http://img384.imageshack.us/img384/2750/screenshot8fu.th.png]](http://img384.imageshack.us/my.php?image=screenshot8fu.png)

[[img=http://img384.imageshack.us/img384/3236/screenshot25kv.th.png]](http://img384.imageshack.us/my.php?image=screenshot25kv.png)

it is pinging with success via terminal.

yes, it is setup according to [this link]("http://blog.taragana.com/wp-content/upload/bb7.swf")

i dont think i am using port forwarding. 

i just now came to know that there are two ethernet or cards in my cpu (the one which came with the system and the other fixed by the ISP. the one fixed by the isp is the one which is used for internet in winxp and it works fine. also ff in ubuntu uses this eth0 only. but other applications may not be using it. 

other way is the problem might be due to ipv6.

my question is it due to some conflict that the other applications use the unused ethernet device that i am not able to connect?

[i am able to access the internet only throught firefox. but other applications like gaim and bittorrent etc cannot access the internet. this is my problem]

shall i try to reinstall ubuntu again. will it help me in accesing the internet?

---

### Post by arai on 2006-02-04
```
vaag@huser1:~$ sudo ifconfig
Password:
eth0      Link encap:Ethernet  HWaddr 00:80:48:38:07:4B
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:669 errors:0 dropped:0 overruns:0 frame:0
          TX packets:664 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:531700 (519.2 KiB)  TX bytes:184778 (180.4 KiB)
          Interrupt:21 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:638 errors:0 dropped:0 overruns:0 frame:0
          TX packets:638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:56760 (55.4 KiB)  TX bytes:56760 (55.4 KiB)


```

```
vaag@huser1:~$ sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         mygateway360.my 0.0.0.0         UG    0      0        0 eth0
vaag@huser1:~$

```

```
vaag@huser1:~$ ping -c 4 www.google.com
PING www.l.google.com (72.14.203.99) 56(84) bytes of data.
64 bytes from www.google.com (72.14.203.99): icmp_seq=1 ttl=238 time=321 ms
64 bytes from www.google.com (72.14.203.99): icmp_seq=2 ttl=238 time=321 ms
64 bytes from www.google.com (72.14.203.99): icmp_seq=3 ttl=238 time=320 ms
64 bytes from www.google.com (72.14.203.99): icmp_seq=4 ttl=238 time=321 ms

--- www.l.google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 320.713/321.374/321.790/0.417 ms
vaag@huser1:~$

```

---

### Post by mips on 2006-02-05
Did you edit your /etc/modprobe.d/aliases file ???

---

### Post by arai on 2006-02-05
[QUOTE=mips]Did you edit your /etc/modprobe.d/aliases file ???[/QUOTE]

i dont know. but i can check whether it has been edited or not if you could give the syntax / command. thanx.

---

### Post by mips on 2006-02-05
[QUOTE=arai]i dont know. but i can check whether it has been edited or not if you could give the syntax / command. thanx.[/QUOTE]

:???: 

I repeat, again:

Open a terminal and enter:
**sudo gedit /etc/modprobe.d/aliases**

Look for the line that reads:
**alias net-pf-10 ipv6**

Change it to:
**alias net-pf-10 off #ipv6**

**Save and reboot your PC.**

---

### Post by arai on 2006-02-05
yes it is already like this only.

alias net-pf-10 off #ipv6

i did as u said but it is already changed ( as u asked me to change it before itself)

---

### Post by mips on 2006-02-05
Please post your /etc/network/interfaces file here.
Please post your /etc/resolv.conf file here.

---

### Post by arai on 2006-02-05
gedit /etc/network/interfaces

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface

iface eth0 inet dhcp

auto eth0

```

gedit /etc/resolv.conf

```
nameserver 192.168.1.1
```

---

### Post by mips on 2006-02-05
Ok, try this:

sudo gedit /etc/network/interfaces
```

nameserver 61.1.96.69
nameserver 61.1.96.71
nameserver 192.168.1.1
```

In that order, make sure your router IP Address is LAST.

---

### Post by arai on 2006-02-05
should i copy 
```
nameserver 61.1.96.69
nameserver 61.1.96.71
nameserver 192.168.1.1

```

at the end of 
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface

iface eth0 inet dhcp

auto eth0

```

and save it ?

---

### Post by arai on 2006-02-05
[QUOTE=mips]Ok, try this:

sudo gedit /etc/network/interfaces
```

nameserver 61.1.96.69
nameserver 61.1.96.71
nameserver 192.168.1.1
```

In that order, make sure your router IP Address is LAST.[/QUOTE]

yes, my router's ip address is 192.16.1.1

do i need to copy this anywhere? :cry:

---

### Post by arai on 2006-02-05
shall i re-install ubuntu linux? will that solve the problem? may be this should be the last move. if even then i could not connect then i shall leave my linux adventures. :-|

---

### Post by mips on 2006-02-05
[QUOTE=arai]yes, my router's ip address is 192.16.1.1

do i need to copy this anywhere? :cry:[/QUOTE]

Sorry, I mentioned the wrong file.

Edit your **/etc/resolv.conf** file with that information.

**sudo gedit /etc/resolv.conf** is the command and ensure you have these lines in the file in the exaxt same order.

nameserver 61.1.96.69
nameserver 61.1.96.71
nameserver 192.168.1.1

---

### Post by arai on 2006-02-05
when i do as i u said above it only shows the following

```
nameserver 192.168.1.1
```

shall i add the other two lines to make it as shown above ?

---

### Post by bscbrit on 2006-02-05
Yes, as mips said.  Make you resolv.conf look IDENTICAL to his.

---

### Post by arai on 2006-02-05
[QUOTE=bscbrit]Yes, as mips said.  Make you resolv.conf look IDENTICAL to his.[/QUOTE]

it says resolv.conf is a read only file. i am not able to edit / add something to it. Here is a screenshot i got when i try to **gedit /etc/resolv.conf** 

[[img=http://img147.imageshack.us/img147/9904/screenshot8cb.th.png]](http://img147.imageshack.us/my.php?image=screenshot8cb.png)

resolv.conf is read only and i am not able to edit / add the first two lines to it.

---

### Post by mips on 2006-02-06
No offence but PLEASE read post #28 again.

---

### Post by arai on 2006-02-06
excellent mips. it works. i could login in to my google talk, yahoo and msn messenger using gaim.

but there is also a downfall. i ll explain it as far as i can. i did as u said. i changed to as you said in post 28 . saved it. it worked. i could login to msn, yahoo & google talk. but when i restarted ubuntu. i could not connect. i tried the same command. but to my surprise, the three lines were not there. intead there was only one line (the last line). for me to connect all the three lines should be there. but it changes when i restart the computer. how to solve this.

note: after i changed the values i even saved it . but after i restart it became back to  single line (as in post 29)

---

### Post by arai on 2006-02-06
dear mips, 

i think i starting to understand it. in [this link]("http://blog.taragana.com/wp-content/upload/bb7.swf") under point 2) additional dns is given. i need to put it somewhere in ubuntu. where should i add it. if i could add it then it would work i think. is there a place to fill additional dns under network tools. if yes where could be tell me. sorry for asking again and again.

---

### Post by arai on 2006-02-06
applications-system tools-network tools-ethernet interface eth0-configure-interface properties

even here, "interface properties" there is no provision to add additional dns. where should i add additional dns to make it permanent?

---

### Post by mips on 2006-02-06
You did add the additional DNS servers by editing your /etc/resolv.conf file.

DHCP is over writing your /etc/resolv.conf file.

You can look at post #2 here, [http://www.ubuntuforums.org/showthread.php?t=11544&highlight=d-link+adsl+router](http://www.ubuntuforums.org/showthread.php?t=11544&highlight=d-link+adsl+router)

Or you can configure your network setting to use a static IP address instead of obtaining the tcp/ip details via DHCP.

---

### Post by arai on 2006-02-06
it works perfect. i restarted again and agin and it works. thanks a lot. bittorrent, gaim everything works fine. thanks for the great support(specially to mips and also to bscbrit). this operating system is really goin 2 rock.  linux is going to be the real alternative for windows. a big thank u once again. 

note: it would be much better if somebody could document all thest things so that it would be useful for others.

---

### Post by mips on 2006-02-06
[QUOTE=arai]
note: it would be much better if somebody could document all thest things so that it would be useful for others.[/QUOTE]

It's not possible to document every possible scenario. The trouble shooting thread at the top of this forum contains a lot of this info.

The other option is to use the search feature on this site which is very usefull.

---

### Post by bscbrit on 2006-02-07
Arai, the documentation that you seek is right in front of you, as mips has pointed out.  The value of this forum is that you can search for keywords relating to your problem and see how it has been solved in the past.  In my case, if I think that it is something I need to know, I put a link/reference to it in my notebook.  

The problem with this forum, or more correctly the forum users, is that many do not carry out a search before starting a thread.  Why?  I haven't a clue.  But most seem to think that they will be the only person to have seen such-and-such a problem before, and that everyone will be so fascinated by it as to want to solve it themselves.  Its just not so.

Many of the replies that you see to problems are links to _existing_ threads, wiki pages or even other sites.  They were there before the user posed his/her question but, for some reason, were not found by that user (probably, but not in every case, because the user didn't even look).  True, some newbies need educating in how to search, use a wiki or even interpret the answers in other threads to learn things from them.

This is not a criticism directed at you personally - but, if like me on occasion, you haven't done your homework before asking the question then perhaps we should both take a lesson from it.:cry: 

Personally, I think part of the solution is to make the 'Search' button much bigger than the others, and direct users to a page that not only asks for their input but explains briefly how to carry out an effective search.

---

### Post by mips on 2006-02-07
[QUOTE=bscbrit]
Personally, I think part of the solution is to make the 'Search' button much bigger than the others, and direct users to a page that not only asks for their input but explains briefly how to carry out an effective search.[/QUOTE]

Yeah, make it bigger, put it in the middle of the Menu and make it a flashing red colour :D

---

