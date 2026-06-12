---
title: "Trying to setup a firewall-router-PC with two ethernet cards"
date: 2013-05-06
forum: Networking &amp; Wireless
---

### Post by held7over on 2013-05-06
I am a complete novice at this, and I could use some help to get the connectivity up and working between these three IP addresses I am listing in these two PCs.

PC#1 - Ubuntu Server 12.04 with two ethernet cards is to be my Firewall-Router
            External IP on my LAN - eth0:  192.168.2.210   Realtek Ethernet Card
            Internal IP - eth1: 192.168.2.211   D-Link Ethernet Card
            PC#1 is connected via Ethernet and CrossOver Plug to PC#2

PC#2 - Ubuntu Server 12.04 - eth0:  192.168.2.212  (This computer only has one Ethernet socket which the crossover-ed ethernet cable is plugged into.)

At the moment, PC#1 can, externally, using eth0 (192.168.2.210) ping anything on my home network LAN or out on the internet, and anything setting on my home LAN can ping this system. Also, from eth0 I can ping eth1. However, if I do a '/etc/init.d/networking restart' odds are I won't be able to ping anything other than eth1...and I will have to reboot. I've looked at a lot of things on the internet, none of which seem to work for me, and I have ended up with the below merger of things I found...I am kind of confused.

Here is my /etc/network/interfaces file on PC#1 presently looks like:

 ```
# The loopback network interface
auto lo eth0 eth1
iface lo inet loopback

# The primary network interface
#auto eth0
iface eth0 inet static
        address 192.168.2.210
        netmask 255.255.255.0
        network 192.168.2.1
        broadcast 192.168.2.255
        gateway 192.168.2.1
# dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 8.8.8.8 8.8.4.4
        dns-search 2.168.192.in-addr.arpa

# Set up the internal wired network
#auto eth1
iface eth1 inet static
        address 192.168.2.211
        netmask 255.255.255.0
        network 192.168.2.210
        broadcast 192.168.2.255
        gateway 192.168.2.210
# dns-* options are implemented by the resolvconf package automatically, if installed
        dns-nameservers 8.8.8.8 8.8.4.4
        dns-search 2.168.192.in-addr.arpa
```


Thanks for your suggestions!

---

### Post by held7over on 2013-05-06
Sorry. I should add that eth1 is failing in the bootup.

# ip addr
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 00:40:f4:72:89:f1 brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.210/24 brd 192.168.2.255 scope global eth0
    inet6 fe80::240:f4ff:fe72:89f1/64 scope link 
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 00:05:5d:36:da:89 brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.211/24 brd 192.168.2.255 scope global eth1
    inet6 fe80::205:5dff:fe36:da89/64 scope link 
       valid_lft forever preferred_lft forever
```

# ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:40:f4:72:89:f1  
          inet addr:192.168.2.210  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe72:89f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:513 errors:0 dropped:0 overruns:0 frame:0
          TX packets:453 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45504 (45.5 KB)  TX bytes:109993 (109.9 KB)

eth1      Link encap:Ethernet  HWaddr 00:05:5d:36:da:89  
          inet addr:192.168.2.211  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::205:5dff:fe36:da89/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9642 (9.6 KB)  TX bytes:468 (468.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1344 (1.3 KB)  TX bytes:1344 (1.3 KB)
```

---

### Post by ahallubuntu on 2013-05-06
~

---

### Post by held7over on 2013-05-10
I'm sorry this took so long to get back to you. For some reason my Number Two computer from which I was going to test my connection through the first computer, stopped seeing the two SATA drives that are in it...that is....BIOS stopped seeing them and I haven't been able to get it to see them since. However, I booted it up on a liveCD this morning and was able to verify that I do in fact have connection to the internet through Computer Number One....so, your help in pointing me at exactly what I needed to read and understand was perfect! So, this thread is solved....if I can now find where to mark it solved at. 

Thanks for your help!!!

---

### Post by agillator on 2013-05-10
Are you intending to continue to use your firewall computer for normal day to day operations also? If not, I would suggest you not try to reinvent the wheel and simply use IPCOP. The problem, of course, is that computer will be ONLY a firewall then. If that is not what you want, then consider getting another inexpensive computer - you should be able to find a used one for very little - and putting IPCOP on that. I think either of those suggestions will suit your purpose.

---

### Post by held7over on 2013-05-10
Thanks for the suggestion about IPCOP. I've never heard of it. But will try to check it out. Perhaps I should mention what I am trying to do:

I am actually trying to create a simulated live commercial setup for purposes of teachig myself how all this works so that I can work toward setting up my own multiple servers and eventually build a business upon it. I want to know how to build every aspect of what I need that cuts a path to what I want to accomplish. Which is why I am not looking for a hosting company at this point. The only part of this project that I already know how to do is setting up LXC containers which took me quite a while to get going, and getting them to be able to be pinged from my network and being able to ping outward to things on the internet. I have no clue about firewalls or apache....yet. But, firewalls are the next step.

More specifically:  I have purchased several domain names, all of which I plan to have pointed at my single IP address (I'm unemployed and that's all I can afford). Since I will only have one actual IP address, I need a way to discriminate which incoming port 80 comminications should be routed to which LXC container that represents that domain name on my system.  I have been told, that if I make that dedicated firewall computer use Shorewall and if I put an Apache server within a container to act as a routing server, I can use the combo to determine which container the communication should go to, and route it to that specific container.

They said it works like this:  Shorewall directs Domain Name based http/s traffic to the container with Apache in it, which is in the firewall's DMZ, Apache, which is running in Virtual Host Mode, reads the incoming domain names and is set up to change the headers of the incoming communications, which then maps the URL domain names to their assigned port numbers which are high unique numbers, like port numbers such as 8800, by swapping the new port number for port 80, AND then Apache is set to send the communication back to the shorewall firewall, which understands port numbers and not domain names, and now sees the new port number and knows the correct internal IP of the proper container to send it to.

Sounds simple. Huh? It probably is for someone who knows what they are doing.  I've heard that apache is kind of hard on system resources and I am using older computers for this, and I have heard that NginX can do this also and is very light weight and fast, so since I have no understanding of either application, I have been thinking I might try the NginX route first, that is of course, after I figure out how to set the firewall up in the dedicated computer I just got networking working in thanks to the answers given in this thread....

I asked the same source which told me the verbal map of how to do this if there were simpler firewalls I could use, but he pretty well insisted that for my purposes and the things I wanted to do in the future I should stick with Shorewall. Unfortunately, he isn't available to walk me through my first implementation of this...

---

### Post by agillator on 2013-05-10
How basic do you want to get? IPCOP is, I believe, based on Shorewall but I don't remember for certain. It may be less than you really are looking for, check out their page on the web. Both, however, are basically frontends for the system that comes with Linux controlled by and commonly called iptables. If you really want to learn what is going on and how everything is happening, learn to do it all through iptables. That would be a monumental task and reinventing the wheel, but in you case and with your goals the education might be worthwhile. What I am suggesting, of course, is 'learn about word processors by writing one' which may be more than you want to do.

---

### Post by held7over on 2013-05-10
I just want to be capable of rebuilding my basic operation from the ground up using my own customized set of HOWto's so that I am not dependent upon another party. I have nothing at all against using high level applications to accomplish this and in fact would rather do so, so that I can get on with life. 

Getting on with life constitutes setting things up inside my containers and utilizing a programming language such as Python (which matches the applications I will be using inside the containers) to stitch thing together. (A long time ago, I was a programmer. So, where I really want to get into the nitty gritty is in the language I pick to accomplish my goals inside the containers.) Then, I want to run my business initially from my home and if it flies, acquire faster internet and equipment as it grows. 

So really, I am really looking to only have to learn the exact path I need to take to get all this set up so I can play with it. If I had a set of Howtos that simply constructed the setup I described above between the dedicated computer for the firewall and the apache or NginX portion in one of the containers, which I need to impliment in order to have my hosting portion set up, you could color me happy! As that would let me go ahead and start the customization process and learn things as they come up.

---

