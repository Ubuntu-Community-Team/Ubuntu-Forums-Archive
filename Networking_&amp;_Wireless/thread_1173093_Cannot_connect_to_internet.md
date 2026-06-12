---
title: "Cannot connect to internet"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by crashus on 2009-05-29
Hello!


You could say I'm new to linux- I have already used it a year ago, with no problems.. but let's say i have forgotten almost everything:)

my problem is that i cannot connect to internet using wired connections- this was also the original reason why i changed my sistem back to windows. The problem is, that I'm rigt now living in china- when i got here I was using Ubuntu 8.04- and i had a problem with ipv6- i could not disable it, and therefore i wasn;t able to use the internet connection. right now i'm using 9.04 and vista.
I'm living in a university campus, so I have no iformation on their ISP, router, basically I dont have any other information except the assigend IP, DNS, gateway...

I am conected, my hardware is working properly, the settings are correct, but it seems that my connection just wont work- it just connecting..... like it cannot even establish a connection with the server...

I would really appreciate any help.. last time i tried everything regarding the ipv6 problem.. i didn't help.. 
if you need any additional information just ask, i'm a bit rusty, so i dont really know enymore what is needed for this.

thanks

---

### Post by Iowan on 2009-05-29
Hope we can get you surfing...
Post results of **ifconfig -a**. If it shows no IP address, also include results of **lshw -C network**.

---

### Post by crashus on 2009-05-30
here is the result of ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:1e:ec:c5:50:c2  
          inet addr:210.30.189.247  Bcast:210.30.189.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:fec5:50c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4953 (4.9 KB)  TX bytes:6704 (6.7 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3158 (3.1 KB)  TX bytes:3158 (3.1 KB)

pan0      Link encap:Ethernet  HWaddr 0e:08:4b:7d:19:a3  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:16:ea:9a:7c:c6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-EA-9A-7C-C6-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


and this one is for the lshw -C network


*-network
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:1e:ec:c5:50:c2
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5764m-v3.35 ip=210.30.189.247 latency=0 link=yes mo


and thanks for helping me!

---

### Post by Rofko on 2009-05-30
As far as I understand you need to disable ipv6.

In 9.04:

in terminal:

sudo su -

[enter password]

su echo 0 > /proc/sys/net/ipv6/conf/all/disable_ipv6

See if that works.

Let us know.

---

### Post by crashus on 2009-05-30
doesnt work- still can't connect..

browser still fails to connect

---

### Post by KING^2 on 2009-05-30
Recently i was also met a problem like u, and maybe it will do some good to u.
first ,make sure u have configured the IP address, MASK, and the DNS is in proper,if these r all right, then check the "wired network connection " option, there is a "edit" tab, click it and u will see a option as "connect automatically ", make sure it was choosen. Good luck!

---

### Post by crashus on 2009-05-30
it's checked, and it's still not working.. any more advice?

---

### Post by superprash2003 on 2009-05-30
post output of **ping google.com**

---

### Post by crashus on 2009-05-30
this is the result of 2 websites

uros@ubuntu:~$ ping [www.youku.com](www.youku.com)
ping: unknown host [www.youku.com](www.youku.com)
uros@ubuntu:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

and the result for the university website- actually everytime you go online you first have to go to this address and enter your username,pass so that you are authenticated and so you can use the internet.. dont really know if this is important or not..

uros@ubuntu:~$ ping 2.2.2.3
PING 2.2.2.3 (2.2.2.3) 56(84) bytes of data.
From 210.30.189.247 icmp_seq=1 Destination Host Unreachable
From 210.30.189.247 icmp_seq=2 Destination Host Unreachable
From 210.30.189.247 icmp_seq=4 Destination Host Unreachable
From 210.30.189.247 icmp_seq=5 Destination Host Unreachable

---

### Post by crashus on 2009-05-30
any ideas?

---

### Post by Mosaab on 2009-05-30
does the lan network (if any) work fine? can you ping any computer or the router?

maybe you have a problem with the names service!

---

### Post by crashus on 2009-06-01
I can see other computers on the network, but cannot connect to them, because of en error-

   -Failed to retrieve share list from server

in vista it's the same- i can see the computers but cannot connect- but the internet works in vista.

---

### Post by crashus on 2009-06-02
OK i just noticed that I can connect to internet if I disable my wifi adapter. I am connected and i can also ping any website sucessfully. However my internet still doesn't work, because the web page just keeps loading indefinitly.. it never opens. Is this a DNS problem? and if so, any idea how to solve it? I'm using the same dns as in vista and it still doesn't work..

---

### Post by crashus on 2009-06-02
uros@ubuntu:~$ ping [www.youku.com](www.youku.com)
PING [www.youku.com](www.youku.com) (61.135.196.100) 56(84) bytes of data.
64 bytes from 61.135.196.100: icmp_seq=1 ttl=243 time=24.9 ms
64 bytes from 61.135.196.100: icmp_seq=2 ttl=243 time=25.3 ms
64 bytes from 61.135.196.100: icmp_seq=3 ttl=243 time=25.0 ms
64 bytes from 61.135.196.100: icmp_seq=4 ttl=243 time=24.9 ms
^C64 bytes from 61.135.196.100: icmp_seq=5 ttl=243 time=25.0 ms

--- [www.youku.com](www.youku.com) ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 20143ms
rtt min/avg/max/mdev = 24.936/25.058/25.365/0.187 ms


uros@ubuntu:~$ ping 2.2.2.3
PING 2.2.2.3 (2.2.2.3) 56(84) bytes of data.
64 bytes from 2.2.2.3: icmp_seq=1 ttl=63 time=0.247 ms
64 bytes from 2.2.2.3: icmp_seq=2 ttl=63 time=0.216 ms
64 bytes from 2.2.2.3: icmp_seq=3 ttl=63 time=0.224 ms
64 bytes from 2.2.2.3: icmp_seq=4 ttl=63 time=0.246 ms
64 bytes from 2.2.2.3: icmp_seq=5 ttl=63 time=0.223 ms
^C
--- 2.2.2.3 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 0.216/0.231/0.247/0.016 ms


uros@ubuntu:~$ host [www.youku.com](www.youku.com)
[www.youku.com](www.youku.com) has address 61.135.196.100

so I am connected , but have a problem with name services?

and the content of resolv.conf-

# Generated by NetworkManager
nameserver 202.96.64.68
nameserver 202.96.75.68

the dns is correct, so where is the problem?

---

### Post by grappler on 2009-06-02
Seems to me that your name server is working - or you wouldn't be able to ping [www.youku.com](www.youku.com).

Do you have a proxy set in your browser? If it's firefox go to Edit > Preferences
The click on Network Tab and then settings.

---

### Post by crashus on 2009-06-02
> **grappler said:**
> Seems to me that your name server is working - or you wouldn't be able to ping [www.youku.com](www.youku.com).

Do you have a proxy set in your browser? If it's firefox go to Edit > Preferences
The click on Network Tab and then settings.


just checked and the proxy is off.
i have also noticed that although i cannot open web sites and use update manager, i can however use gmailtalk in pidgin..

---

### Post by grappler on 2009-06-02
Try disabling ipv6 in firefox:

[http://http://en.opensuse.org/Disable_IPv6_for_Firefox]("http://http://en.opensuse.org/Disable_IPv6_for_Firefox")

---

### Post by grappler on 2009-06-02
sorry - meant 

[http://en.opensuse.org/Disable_IPv6_for_Firefox]("http://en.opensuse.org/Disable_IPv6_for_Firefox")

---

### Post by crashus on 2009-06-02
> **grappler said:**
> Try disabling ipv6 in firefox:


thx grappler for the advice, tried it but still doesnt work. could an ipv6 problem also explain, why update manager cant connect?

---

### Post by crashus on 2009-06-03
any new ideas?

---

### Post by Buffalo Soldier on 2009-06-03
Try changing your DNS to OpenDNS
208.67.222.222
208.67.220.220

---

### Post by crashus on 2009-06-10
> **Buffalo Soldier said:**
> Try changing your DNS to OpenDNS
208.67.222.222
208.67.220.220

Tried changing it, but still no difference.. I'm connected but still can not surf..
but my originally dns works normally on my vista, so how could this be a dns problem?

---

### Post by crashus on 2009-06-16
any new ideas?

---

### Post by jhannah on 2009-06-16
It sounds like your DNS settings are correct if you can reliably resolve names with ping. Original that did not seem to be the case, do you happen to recall what the contents of /etc/resolv.conf were when ping was unable to resolve domain names?

In order to clearly rule if this is a networking issue or browser issue try to telnet to a web server on port 80 using the below line:

```
telnet www.hostmysite.com 80
```If that fails, try connecting directly using the IP:

```
telnet 209.41.173.126 80
```Provided it connected successfully, you should see something like this:

```
[11:50:25 PM] jhannah@octave:~$ telnet www.hostmysite.com 80
Trying 209.41.173.126...
Connected to hostmysite.com.
Escape character is '^]'.


```You can hit Ctrl-5, press return and type quit to disconnect. If you do not see this, egress HTTP traffic may be blocked. I also say this since it seems this issue is limited to HTTP (and possibly HTTPS?). Some locations require that you use their proxy server for making HTTP connections. If you think that might be the case with your internet connection you can have Firefox try to automatically detect proxy settings. Simply click Edit -> Preference -> Advanced Icon -> Network Tab -> Click 'Settings' under 'Connection' -> Select 'Auto-detect proxy settings for this network' and click OK on all of the open dialogs.

Hope that helps.

---

### Post by crashus on 2009-06-18
I can successfuly connect to a web site

uros@ubuntu:~$ telnet [www.hostmysite.com](www.hostmysite.com) 80
Trying 209.41.173.126...
Connected to hostmysite.com.
Escape character is '^]'.


and I've tried enabeling avto detect proxy in firefox, but that didnt solve it.. now the browser wouldnt even connect. firefox just says "stopped" whene thrying to connect to a web site..

I unchecked it and got the good old "waiting for..." sign:)



as for the resolf.conf file goes- i think it was the same as it is now which is :


# Generated by NetworkManager
nameserver 202.96.64.68
nameserver 202.96.75.68

---

### Post by alphacrucis2 on 2009-06-18
> **crashus said:**
> I can successfuly connect to a web site

uros@ubuntu:~$ telnet [www.hostmysite.com](www.hostmysite.com) 80
Trying 209.41.173.126...
Connected to hostmysite.com.
Escape character is '^]'.


and I've tried enabeling avto detect proxy in firefox, but that didnt solve it.. now the browser wouldnt even connect. firefox just says "stopped" whene thrying to connect to a web site..

I unchecked it and got the good old "waiting for..." sign:)



as for the resolf.conf file goes- i think it was the same as it is now which is :


# Generated by NetworkManager
nameserver 202.96.64.68
nameserver 202.96.75.68

Do they require you to connect via a proxy server to get to the internet? If so, you may need to ask the IT support for the details. The AUTO setting may not work.

---

### Post by crashus on 2009-06-18
no proxy is needed.. and i'm using the exact same setting as in vista but it still doesn't work- so i belive it's not a settings problem...

---

### Post by crashus on 2009-06-22
new ideas anyone? i really dont want to  be using vista but up until now i have no other choise...

---

### Post by papangul on 2009-06-22
Have you tried another browser? Like google chrome developer preview:
[http://dev.chromium.org/getting-involved/dev-channel](http://dev.chromium.org/getting-involved/dev-channel)

---

### Post by crashus on 2009-06-27
everything that has something to do with internet connection isn't working.. update manager and browser(s). 
i've tried a different one, but still no luck

---

