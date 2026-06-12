---
title: "My network manager icon says im connected but internet wont work!"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by kmaster228 on 2009-05-19
Hello everybody

recently i plugged in my broadband connection cable (that me and my brother are sharing through a router) into my laptop and and the internet worked.

then when i plugged it back into my computer, auto eth0 did not work, it would not connect. so i made a new connection using ipv4 setting i got from the properties of the connection (im dual booting with windows and on windows it works fine)  it does not say any DNS settings on windows. for routes i put the same ip, netmask and gateway, i do not know what metric is so i just put 1. then clicked apply. then i double clicked the network manager icon again and the only wired connection was auto eth0 even thought there were two connections when i click edit connections, after about two hours of trying to find a solution i gave up and then edited the settings for auto eth0 putting the same ipv4 settings as before. when i click apply it says connectione stablished, yet when i start anything to do with internet it doesnt work, in firefox it says server not found or something. so i go to the terminal and type: ifconfig -a
this is the result
```

eth0      Link encap:Ethernet  HWaddr 00:1c:c0:38:75:e7  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fec0::8:21c:c0ff:fe38:75e7/64 Scope:Site
          inet6 addr: 2002:7be7:5565:8:21c:c0ff:fe38:75e7/64 Scope:Global
          inet6 addr: fe80::21c:c0ff:fe38:75e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1669 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1541 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:224655 (224.6 KB)  TX bytes:257016 (257.0 KB)
          Memory:e3200000-e3220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:167592 (167.5 KB)  TX bytes:167592 (167.5 KB)

pan0      Link encap:Ethernet  HWaddr 56:d9:04:7f:63:07  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```and then i tried pinging my IP 
```
PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.
64 bytes from 192.168.0.2: icmp_seq=1 ttl=64 time=0.015 ms
64 bytes from 192.168.0.2: icmp_seq=2 ttl=64 time=0.013 ms
64 bytes from 192.168.0.2: icmp_seq=3 ttl=64 time=0.017 ms
64 bytes from 192.168.0.2: icmp_seq=4 ttl=64 time=0.015 ms
64 bytes from 192.168.0.2: icmp_seq=5 ttl=64 time=0.016 ms
64 bytes from 192.168.0.2: icmp_seq=6 ttl=64 time=0.019 ms
64 bytes from 192.168.0.2: icmp_seq=7 ttl=64 time=0.018 ms
64 bytes from 192.168.0.2: icmp_seq=8 ttl=64 time=0.015 ms
64 bytes from 192.168.0.2: icmp_seq=9 ttl=64 time=0.018 ms
64 bytes from 192.168.0.2: icmp_seq=10 ttl=64 time=0.016 ms
64 bytes from 192.168.0.2: icmp_seq=11 ttl=64 time=0.018 ms
64 bytes from 192.168.0.2: icmp_seq=12 ttl=64 time=0.012 ms
64 bytes from 192.168.0.2: icmp_seq=13 ttl=64 time=0.013 ms

```Please help!, i am a totale noob at these things!

---

### Post by pricetech on 2009-05-19
Switch you Linux box back to DHCP and see what happens.  Give us the same info afterwards.

---

### Post by kmaster228 on 2009-05-19
i switched to DHCP and deleted the routes entry that i added to turn it back to the default settings. 

```

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:38:75:e7  
          inet6 addr: fec0::8:21c:c0ff:fe38:75e7/64 Scope:Site
          inet6 addr: 2002:7be7:5565:8:21c:c0ff:fe38:75e7/64 Scope:Global
          inet6 addr: fe80::21c:c0ff:fe38:75e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:512 (512.0 B)  TX bytes:7686 (7.6 KB)
          Memory:e3200000-e3220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:384 errors:0 dropped:0 overruns:0 frame:0
          TX packets:384 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28368 (28.3 KB)  TX bytes:28368 (28.3 KB)

pan0      Link encap:Ethernet  HWaddr 22:b0:a3:0e:1d:20  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

``````

ping 192.168.0.2
connect: Network is unreachable

```

---

### Post by Iowan on 2009-05-19
You can see if [this]("http://ubuntuforums.org/showpost.php?p=7280398&postcount=3") helps with DHCP problem.

---

### Post by superprash2003 on 2009-05-20
post output of sudo dhclient eth0

---

### Post by kmaster228 on 2009-05-20
OK ill try those thanks

---

### Post by kmaster228 on 2009-05-20
OK @superprash2003 here is the output of that command before i commented out rfc3442

sudo dhclient eth0
```
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1c:c0:38:75:e7
Sending on   LPF/eth0/00:1c:c0:38:75:e7
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4

No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

and then i entered 

gksudo gedit /etc/dhclient.conf
but was greated with an epty text file. so i manually went to /ect and saw that one of the folders was called dhcp3 and in that there was dhclient.conf, so i entered 
gksudo gedit /etc/dhcp3/dhclient.conf
and came up a text file containing two instances of rfc3442 so i commented them both out, saved the file and restarted, still no connection! and the network manager icons says connection failed.
so i entered sudo dhclient eth0
again and this is the result

```
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

/etc/dhcp3/dhclient.conf line 16: expecting "code" keyword.
send host-name 
     ^
/etc/dhcp3/dhclient.conf line 23: ,: expected option name.
#}
  ^
Listening on LPF/eth0/00:1c:c0:38:75:e7
Sending on   LPF/eth0/00:1c:c0:38:75:e7
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
Please Help! im soo confused!

---

### Post by superprash2003 on 2009-05-20
could you post the contents of your dhclient.conf file

---

### Post by kmaster228 on 2009-05-20
here is the entire contents of dhclient.conf
 ```

# Configuration file for /sbin/dhclient, which is included in Debian's
#    dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#    man page for more information about the syntax of this file
#    and a more comprehensive list of the parameters understood by
#    dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#    not leave anything out (like the domain name, for example), then
#    few changes must be made to this file, if any.
#

#option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    netbios-name-servers, netbios-scope, interface-mtu,
    rfc3442-classless-static-routes, ntp-servers;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}


```

PLEASE hurry! i am almost using windows full time and the experience is making me cringe!, once you go ubuntu you can never go back!;)

---

### Post by Iowan on 2009-05-20
I see the one line you commented out - where was the second instance? I usually make a backup copy of config files before I change them - then I can go back if I messed something up.  

The "request" line has another instance that should be removed. You can copy the line and comment it out for reference... then change the line by *deleting* **rfc3442-classless-static-routes,**. You'll might need the **ntp-servers** part, but will certainly need the semicolon to end the statement.

Dunno if it's the problem, but you might try putting your actual hostname on the send **host-name** line.

---

### Post by kmaster228 on 2009-05-21
sorry i didnt quite understand. first you want me to delete both lines with *rfc3442* and then comment out 
[I]request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    netbios-name-servers, netbios-scope, interface-mtu,[/I]
    rfc3442-classless-static-routes, ntp-servers;

then what exactly do you want me to do with the ntp-servers? line, and arent i supposed to comment that out?
and what shoud i put for *host-name*

I have no idea! please help im a total noob at these things

---

### Post by Iowan on 2009-05-21
Sorry if I caused more confusion.```
#option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;
``` This line looks fine - it's commented out.```
    [COLOR="Red"]rfc3442-classless-static-routes,[/COLOR] ntp-servers;
```Delete the part in red - leaving the line looking like:```
     ntp-servers;
```
For hostname, my machine has the line:```
send host-name "Dell4100";
```You would want to copy the results of **hostname** between the quotes.

---

### Post by kmaster228 on 2009-05-23
Which host name, the one for my windows or the one for my ubuntu, the one on my windows is Panora-PC and on my ubuntu its kmaster-desktop. which one do i use?

---

### Post by Iowan on 2009-05-23
The one on which you're configuring dhclient.conf - so that'd be the Ubuntu box. The line should look something like:```
send host-name "kmaster-desktop";
``` I haven't seen a good explanation of the angle brackets ( < > ). Perhaps they are *supposed* to automatically embed the machine's hostname... but the direct approach works better for me. [This]("http://ubuntuforums.org/showthread.php?t=275733") old thread shows the fun I was having.

---

### Post by kmaster228 on 2009-05-24
ok thanks so i enter that save the file and restart my computer and i should be connected rite? and btw out of interest did the whole hostname messing with work after all?

---

### Post by Iowan on 2009-05-24
It *seemed* to work... but when my dial-up router/firewall got replaced with DSL modem, I have misconfiguration that messed up local DNS, so I can't ping (or connect) by name.  Still on my To-Do list to fix...

---

### Post by kmaster228 on 2009-05-26
It didnt work! i put everything the way you showed me... here is the dhclient again with the changes
```

# Configuration file for /sbin/dhclient, which is included in Debian's
#    dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#    man page for more information about the syntax of this file
#    and a more comprehensive list of the parameters understood by
#    dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#    not leave anything out (like the domain name, for example), then
#    few changes must be made to this file, if any.
#

#option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<kmaster-desktop>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    netbios-name-servers, netbios-scope, interface-mtu,
     ntp-servers;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

```

i had high hopes for ubuntu defending it when people would talk about how complicated it is. now i have to agree, ubuntu isnt that easy

---

### Post by Iowan on 2009-05-26
> **Iowan said:**
> ```
send host-name "kmaster-desktop";
``` > **kmaster228 said:**
> ```
send host-name "<kmaster-desktop>";
```Notice any difference?
What part isn't working - connecting or seeing machines by hostname... or both?

---

### Post by kmaster228 on 2009-05-27
hahahah yes! im on the internet on ubuntu! but the weird thing is when i booted onto ubuntu the connection manager said that auto eth0 was active, i went to firefox and it didnt work, so i changed the option to use dhcp insted of ipv4. so i disabled and ree\-enabled networking and to my suprise without changing the hostname or anything , it said auto eth0 active! this is kinda suspicious, i wonder whehter it will go off agian.
but thanks you soo much. truly aprieciate it! i doubt i can do much, but if u ever need help, pm me n ill try giving u the best advice, or ill just google it! any ways thank you agian!:p

PS; sorry about there being so many typos!

---

### Post by Iowan on 2009-05-27
> **kmaster228 said:**
> i had high hopes for ubuntu defending it when people would talk about how complicated it is. now i have to agree, ubuntu isnt that easyNo, Ubuntu isn't that easy, so there's more than a little satisfaction when you can beat a problem (not quite so much if it comes back ;)  )

---

