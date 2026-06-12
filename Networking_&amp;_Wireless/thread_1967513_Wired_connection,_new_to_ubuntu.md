---
title: "Wired connection, new to ubuntu"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by Das Wanderer on 2012-04-28
Hello,

I am trying to connect to the internet with my new pc however I have never used ubuntu before so I am a bit clueless.

When I click eth0 it looks like its trying to connect but I haven't put in my routers information and don't know where to start.

Any advice would be appriciated.

---

### Post by nkv1 on 2012-04-28
I have been using Ubuntu for a year now. Ubuntu usually recognizes the wired router without a problem.

Ubuntu is mapping accesses i have a network card port is on eht1.
eht0 is LAN port on my motherboard.

If you still have problems tell me which Ubuntu version you are using and which router model you have?

You can also see whats happening in network tools

this link could help you
[link]("http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html")
Hope this helped.

---

### Post by Das Wanderer on 2012-04-28
Thanks for the reply.

I went into the laptop i'm using and fond the ip etc of here and put that in the wired section, it now accepts that its connected but doesn't let me access the internet.

I'm using Ubuntu version 10.04 and its a sagem router (Sky)

---

### Post by nizamibilal1064 on 2012-04-28
Delete any wired connection shown in "network connection " panel and add new  with correct setting and router information......i hope it might work for you.

---

### Post by Das Wanderer on 2012-04-28
Not really sure what exactly is the correct settings and information if I am honest with you.

---

### Post by nizamibilal1064 on 2012-04-28
> **Das Wanderer said:**
> Not really sure what exactly is the correct settings and information if I am honest with you.
Try with Device mac id only ..you can find it on your router. rest keep as default;)

---

### Post by Das Wanderer on 2012-04-28
I tried this it flashed the icon in the right hand corner for a minute or two then said:

Wireless Network disconnected

---

### Post by Das Wanderer on 2012-04-28
icon has changed now to an up and down arrows, i opened firefox but its being very slow to load the page, and is yet to load a page

It also says when I hover over it Wired network connect 'Auto eth0' active

---

### Post by nizamibilal1064 on 2012-04-28
> **Das Wanderer said:**
> icon has changed now to an up and down arrows, i opened firefox but its being very slow to load the page, and is yet to load a page

It also says when I hover over it Wired network connect 'Auto eth0' active
Well ...it seems that your wireless is not enabled... try this click on network icon and click on enable networking and enable wireless...when icon show that up and down movement it means it is trying to connect ..after connection is successful it will flash message  about success of connection.

---

### Post by Monotoko on 2012-04-28
The up/down arrows are right, that means it's connected via a wired connection (you are plugged into the Sky box via wired aren't you?), not sure what you are trying to configure? The Sky box (I have one too!) should give you an IP and configure the rest automatically... can I have the output of:

sudo ifconfig

---

### Post by Das Wanderer on 2012-04-28
> **Monotoko said:**
> The up/down arrows are right, that means it's connected via a wired connection (you are plugged into the Sky box via wired aren't you?), not sure what you are trying to configure? The Sky box (I have one too!) should give you an IP and configure the rest automatically... can I have the output of:

sudo ifconfig

I'm not sure either.

Its not loading the webpage either its been sitting here for 5-10 mins trying to load a page and getting no where,

---

### Post by Monotoko on 2012-04-28
The output of that command will tell me,

ctrl+alt+T will give you a terminal, type "sudo ifconfig" then give me the output (you may need to take a picture if you're not able to get online with that machine.

Can I just ask your intentions, because you said it told you "Wireless disconnected"... why don't you just connect using wifi?

---

### Post by Das Wanderer on 2012-04-28
I basically want to connect my pc via a wired connection because it doesn't have wifi capability.

Sorry for taking so long had to copy this accross from the pc to my laptop

eth0      Link encap:Ethernet  HWaddr c8:60:00:6e:2f:02   
           inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0  
           inet6 addr: fe80::ca60:ff:fe6e:2f02/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:326 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:307 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:35259 (35.2 KB)  TX bytes:76821 (76.8 KB)  
           Interrupt:35 Base address:0xa000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:76 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:76 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)

---

### Post by Monotoko on 2012-04-28
Hi Das,

Try rebooting and trying again, from what I can see it is up... but the configuration you did beforehand may have killed something. Once you reboot, Eth0 should come up automatically. (Sorry for the "turn it off and turn it back on again" post - just thought I would try this first)

---

### Post by Das Wanderer on 2012-04-28
Any help right now is welcomed.

I've restarted it, however it comes up like before but when it eventually loads the page its blank, white.

---

### Post by Monotoko on 2012-04-28
Hi Das,

Can you open a terminal again and ping "192.168.0.1" or whatever your router IP is.

---

### Post by Das Wanderer on 2012-04-28
Cheers again heres that info, 

christopher@christopher-desktop:~$ ping 192.168.0.5  
 PING 192.168.0.5 (192.168.0.5) 56(84) bytes of data.  
 64 bytes from 192.168.0.5: icmp_seq=1 ttl=64 time=0.020 ms  
 64 bytes from 192.168.0.5: icmp_seq=2 ttl=64 time=0.013 ms  
 64 bytes from 192.168.0.5: icmp_seq=3 ttl=64 time=0.015 ms  
 64 bytes from 192.168.0.5: icmp_seq=4 ttl=64 time=0.015 ms  
 64 bytes from 192.168.0.5: icmp_seq=5 ttl=64 time=0.018 ms  
 64 bytes from 192.168.0.5: icmp_seq=6 ttl=64 time=0.016 ms  
 64 bytes from 192.168.0.5: icmp_seq=7 ttl=64 time=0.016 ms  
 64 bytes from 192.168.0.5: icmp_seq=8 ttl=64 time=0.016 ms  
 ^C  
 --- 192.168.0.5 ping statistics ---  
 8 packets transmitted, 8 received, 0% packet loss, time 6998ms  
 rtt min/avg/max/mdev = 0.013/0.016/0.020/0.002 ms

---

### Post by Monotoko on 2012-04-28
.5 is yourself... I need you to ping the sky router (it's usually 192.168.0.1)

---

### Post by Das Wanderer on 2012-04-28
Sorry misunderstood one moment

---

### Post by Das Wanderer on 2012-04-28
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.  
 64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.875 ms  
 64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.905 ms  
 64 bytes from 192.168.0.1: icmp_seq=6 ttl=64 time=0.921 ms  
 64 bytes from 192.168.0.1: icmp_seq=8 ttl=64 time=0.875 ms  
 64 bytes from 192.168.0.1: icmp_seq=9 ttl=64 time=0.859 ms  
 64 bytes from 192.168.0.1: icmp_seq=10 ttl=64 time=0.845 ms  
 64 bytes from 192.168.0.1: icmp_seq=12 ttl=64 time=1.14 ms  
 64 bytes from 192.168.0.1: icmp_seq=13 ttl=64 time=0.858 ms  
 64 bytes from 192.168.0.1: icmp_seq=14 ttl=64 time=0.849 ms  
 64 bytes from 192.168.0.1: icmp_seq=16 ttl=64 time=0.958 ms  
 64 bytes from 192.168.0.1: icmp_seq=17 ttl=64 time=0.851 ms  
 64 bytes from 192.168.0.1: icmp_seq=18 ttl=64 time=0.846 ms  
 64 bytes from 192.168.0.1: icmp_seq=20 ttl=64 time=0.847 ms  
 64 bytes from 192.168.0.1: icmp_seq=21 ttl=64 time=1.12 ms  
 64 bytes from 192.168.0.1: icmp_seq=23 ttl=64 time=0.848 ms  
 64 bytes from 192.168.0.1: icmp_seq=24 ttl=64 time=0.831 ms  
 64 bytes from 192.168.0.1: icmp_seq=25 ttl=64 time=0.817 ms  
 64 bytes from 192.168.0.1: icmp_seq=28 ttl=64 time=0.814 ms  
 64 bytes from 192.168.0.1: icmp_seq=30 ttl=64 time=0.847 ms  
 64 bytes from 192.168.0.1: icmp_seq=31 ttl=64 time=0.851 ms  
 64 bytes from 192.168.0.1: icmp_seq=32 ttl=64 time=0.835 ms  
 64 bytes from 192.168.0.1: icmp_seq=34 ttl=64 time=1.12 ms  
 64 bytes from 192.168.0.1: icmp_seq=35 ttl=64 time=0.823 ms  
 64 bytes from 192.168.0.1: icmp_seq=39 ttl=64 time=0.854 ms  
 64 bytes from 192.168.0.1: icmp_seq=40 ttl=64 time=0.840 ms  
 64 bytes from 192.168.0.1: icmp_seq=41 ttl=64 time=0.825 ms  
 64 bytes from 192.168.0.1: icmp_seq=42 ttl=64 time=0.817 ms  
 64 bytes from 192.168.0.1: icmp_seq=45 ttl=64 time=0.779 ms  
 64 bytes from 192.168.0.1: icmp_seq=46 ttl=64 time=0.839 ms  
 64 bytes from 192.168.0.1: icmp_seq=47 ttl=64 time=0.851 ms  
 64 bytes from 192.168.0.1: icmp_seq=49 ttl=64 time=0.831 ms  
 64 bytes from 192.168.0.1: icmp_seq=50 ttl=64 time=0.859 ms  
 64 bytes from 192.168.0.1: icmp_seq=52 ttl=64 time=0.824 ms  
 64 bytes from 192.168.0.1: icmp_seq=54 ttl=64 time=0.796 ms  
 64 bytes from 192.168.0.1: icmp_seq=57 ttl=64 time=0.813 ms  
 64 bytes from 192.168.0.1: icmp_seq=64 ttl=64 time=0.892 ms  
 64 bytes from 192.168.0.1: icmp_seq=65 ttl=64 time=0.887 ms  
 64 bytes from 192.168.0.1: icmp_seq=66 ttl=64 time=0.888 ms  
 64 bytes from 192.168.0.1: icmp_seq=68 ttl=64 time=0.866 ms  
 64 bytes from 192.168.0.1: icmp_seq=69 ttl=64 time=0.847 ms  
 64 bytes from 192.168.0.1: icmp_seq=70 ttl=64 time=0.828 ms  
 64 bytes from 192.168.0.1: icmp_seq=71 ttl=64 time=0.822 ms  
 64 bytes from 192.168.0.1: icmp_seq=73 ttl=64 time=0.829 ms  
 64 bytes from 192.168.0.1: icmp_seq=75 ttl=64 time=0.856 ms  
 64 bytes from 192.168.0.1: icmp_seq=77 ttl=64 time=0.841 ms  
 64 bytes from 192.168.0.1: icmp_seq=78 ttl=64 time=0.855 ms  
 64 bytes from 192.168.0.1: icmp_seq=79 ttl=64 time=0.842 ms  
 64 bytes from 192.168.0.1: icmp_seq=80 ttl=64 time=0.834 ms  
 64 bytes from 192.168.0.1: icmp_seq=84 ttl=64 time=0.896 ms  
 64 bytes from 192.168.0.1: icmp_seq=86 ttl=64 time=0.817 ms  
 64 bytes from 192.168.0.1: icmp_seq=87 ttl=64 time=0.857 ms  
 64 bytes from 192.168.0.1: icmp_seq=88 ttl=64 time=0.849 ms  
 64 bytes from 192.168.0.1: icmp_seq=90 ttl=64 time=0.832 ms  
 64 bytes from 192.168.0.1: icmp_seq=93 ttl=64 time=0.826 ms  
 64 bytes from 192.168.0.1: icmp_seq=94 ttl=64 time=0.902 ms  
 64 bytes from 192.168.0.1: icmp_seq=95 ttl=64 time=1.49 ms  
 64 bytes from 192.168.0.1: icmp_seq=96 ttl=64 time=0.823 ms  
 64 bytes from 192.168.0.1: icmp_seq=98 ttl=64 time=0.852 ms  
 64 bytes from 192.168.0.1: icmp_seq=99 ttl=64 time=0.836 ms  
 64 bytes from 192.168.0.1: icmp_seq=102 ttl=64 time=0.903 ms  
 64 bytes from 192.168.0.1: icmp_seq=103 ttl=64 time=0.838 ms  
 64 bytes from 192.168.0.1: icmp_seq=104 ttl=64 time=0.925 ms  
 64 bytes from 192.168.0.1: icmp_seq=105 ttl=64 time=1.42 ms  
 64 bytes from 192.168.0.1: icmp_seq=106 ttl=64 time=0.844 ms  
 64 bytes from 192.168.0.1: icmp_seq=107 ttl=64 time=0.795 ms  
 64 bytes from 192.168.0.1: icmp_seq=111 ttl=64 time=0.815 ms  
 64 bytes from 192.168.0.1: icmp_seq=112 ttl=64 time=1.39 ms  
 64 bytes from 192.168.0.1: icmp_seq=114 ttl=64 time=0.814 ms  
 64 bytes from 192.168.0.1: icmp_seq=117 ttl=64 time=0.791 ms  
 64 bytes from 192.168.0.1: icmp_seq=121 ttl=64 time=0.780 ms  
 64 bytes from 192.168.0.1: icmp_seq=124 ttl=64 time=0.963 ms  
 64 bytes from 192.168.0.1: icmp_seq=126 ttl=64 time=0.838 ms  
 64 bytes from 192.168.0.1: icmp_seq=129 ttl=64 time=0.857 ms  
 64 bytes from 192.168.0.1: icmp_seq=131 ttl=64 time=0.872 ms  
 64 bytes from 192.168.0.1: icmp_seq=133 ttl=64 time=0.808 ms

---

### Post by Monotoko on 2012-04-28
Hahaha okay, so we know you are communicating with the internal network perfectly fine.

Try pinging google.com (72.14.204.103)

---

### Post by Das Wanderer on 2012-04-28
christopher@christopher-desktop:~$ ping 72.14.204.103  
 PING 72.14.204.103 (72.14.204.103) 56(84) bytes of data.  
 64 bytes from 72.14.204.103: icmp_seq=1 ttl=56 time=358 ms  
 64 bytes from 72.14.204.103: icmp_seq=2 ttl=56 time=159 ms  
 64 bytes from 72.14.204.103: icmp_seq=6 ttl=56 time=106 ms  
 64 bytes from 72.14.204.103: icmp_seq=8 ttl=56 time=197 ms  
 64 bytes from 72.14.204.103: icmp_seq=10 ttl=56 time=230 ms  
 64 bytes from 72.14.204.103: icmp_seq=14 ttl=56 time=439 ms  
 64 bytes from 72.14.204.103: icmp_seq=15 ttl=56 time=434 ms

---

### Post by Monotoko on 2012-04-28
Your internet is working, although quite slowly... but try opening the software center and installing chromium: [http://www.chromium.org/Home](http://www.chromium.org/Home)

---

### Post by Das Wanderer on 2012-04-28
Thank you very much for all your help.

Ubuntu will get a bit of getting used to but i guess its a whole new experience.

---

### Post by nkv1 on 2012-05-03
> **Das Wanderer said:**
> Thanks for the reply.

I went into the laptop i'm using and fond the ip etc of here and put that in the wired section, it now accepts that its connected but doesn't let me access the internet.

I'm using Ubuntu version 10.04 and its a sagem router (Sky)
I am glad you managed to make it work.
If its sagem usb router,
I am afraid I had a bad experience with this sagem router image below
[IMG]http://www.themad-house.co.uk/sagem-usb/images/Fast%20800_03.gif[/IMG]
I went to my provider and changed to Ethernet tp-link router with adsl.
I imagine your router looks like the image below
[IMG]http://helpforum.sky.com/t5/image/serverpage/image-id/167iA9B2256511120589/image-size/original?v=mpbl-1&px=-1[/IMG]
Did not have a chance to use that one.
Simply said i become allergic to sagem products from than.

---

