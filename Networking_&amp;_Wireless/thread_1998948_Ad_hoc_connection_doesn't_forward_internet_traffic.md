---
title: "Ad hoc connection doesn't forward internet traffic"
date: 2012-06-07
forum: Networking &amp; Wireless
---

### Post by SOIMiMozO on 2012-06-07
Hi there. 
Another newbie here, with another stupid question.
I have a laptop with 3945 ABG Golan WiFi card on board, running Ubuntu 12.04, which is connected to Internet with DSL wired connection.
So right now I'm trying to share this wired connection with some other devices through Ad-hoc wireless connection.  I have created a New Wireless Network with Connection Manager, set it to ad-hoc and IP address sharing mode. My iPhone, (as well as my roommate's MacBook) has no problem connecting to this network (yet it always has some strange IP, like 10.42.0.59 with 255.255.255.0 Subnet Mask), and I can actually ping these devicesm and can ping my own laptop from Mac. But it won't let me go any further. Any attempt to ping something outside from Mac fails. 

If somebody have any idea, please, shed some light on it for me guys. Thanks in advance.

---

### Post by sanderj on 2012-06-07
Did you follow in the instructions on [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) ?

---

### Post by SOIMiMozO on 2012-06-08
Yeah, tried that too. I have *dnsmasq-base* installed by default, and *dnsmasq* removed by default. 
Manual iptables configuration doesn't do the trick either. Well, considering I'm doing it in the right way of course, because I'm not sure what those commands actually do. I've just copy-pasted all of them replacing *eth1* device with *wlan0* one, and skipped iptables saving\restoring part.  And yeah, I can't fulfill that client set up part, because I'm trying it on iPhone, so I've just set static IP, routing and DNS on it. I still can ping it, be it a manual, or shared to other computers mode, but I can't access Internet with it.

---

### Post by sanderj on 2012-06-08
Testing with an iPhone sounds difficult to me: better to have a pc for it.

Setup:

pc1 ---- pc2 ---- Internet

On PC1 can you:
- "ifconfig"
- "mtr -n 8.8.8.8"
- "ip route show"

---

### Post by SOIMiMozO on 2012-06-09
And here I am.
And... I've fixed it just 10 min ago. Sorry **sanderj, **you were completely right about that guide you pointed at for me.
Looks like when I tried it first time I, actually, somehow managed to NOT uncomment this 
[I]
net.ipv4.ip_forward=1

[/I]string. Yet I was sure I did it. The most idiotic mistake I've ever made.
Sorry for that. Right now have my Internet connection on Mac up and running.
Thank you pal.

So I guess this topic can be closed. The problem is solved, thanks to **sanderj**.

P.S. And yeah, **sanderj **if you read it before they close it. Maybe you could stick my nose into documentation once more.
Just want to understand how exactly those commands work.

---

### Post by sanderj on 2012-06-09
Cool.

---

### Post by rajespande on 2012-07-01
Cool, this post solved my problem. Sharing internet between ubuntu and Android over Ad-hoc
The following topic also helped me about how to create an ad-hoc.
[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc) 

Note that I had already worked a lot earlier. I worked hard enough to get ad-hoc working under windows+android. So my android is already rooted, patched with the ad-hoc supporting wpa_supplicant and works fine in windows + ad-hoc +android. However now I felt easier in Ubuntu to use ad-hoc + android. 

So, 
1) I just had to know how to setup ad-hoc in ubuntu 
2) I needed to know about setting up  *net.ipv4.ip_forward=1*
3) I was trying this post [http://www.reality-life.com/wireless-connection-ubuntu-for-android-without-adhoc/](http://www.reality-life.com/wireless-connection-ubuntu-for-android-without-adhoc/) , and so I knew about ipv4 thing through this while setting up a dhcpd server, later I removed dhcpd because I just wanted ad-hoc and now it works like a charm.


============
Story
November 2011: bought an Android phone, googled four hours daily for enabling ad-hoc.
In December I succeeded but it was just for one hour because I rebooted my phone and laptop and after that I kept scratching my head what I did. 

I had used a custom wpa_supplicant. 
Automatic update 
-----------------------
So I was pretty sure that this can be done, I kept on screwing things until an android update of the phone restored the phone in original format. The update also unrooted it and now I could start afresh. 

The next day:
-----------------------
 I succeeded in using ad-hoc in windows. 
The thing I had forgotten was : I had to manually set the computer's and mobile's ip addresses. The same thing applies in ubuntu about setting manual ips. 
[Or we can use a dhcp server to broadcast ips, I don't want to do that because everyone around might be able to use my internet. ]

Computer :
--------------
Wireless ip(Dell wifi adaptor under windows 7) was : 192.168.137.1 [manual ips]

Android
-------------
 ip : 192.168.137.2 [manual ips, gateway for android : 192.168.137.1]

[The computer would connect via a wired internet , sometimes I used an external huawei modem for internet.]

================================================
Today I succeeded in Ubuntu. 
================================================
Here are the steps : 
================================================
My android was already configured. 
Android : 
1) wpa_supplicant with ad-hoc support
2) rooted. [might not be necessary, but my android is rooted, so I can do whatever I like in my android]
3)settings->wireless and network->wifi settings->
click on menu (hardware button ) to get "Advanced" menu
4) use static ip
4) Go to Ip addresses : 192.168.137.2
5) gateway : 192.168.137.2
6) Netmask: 255.255.255.0
7) DNS1 : 4.2.2.2 (you'll get dns from your internet provider, I am using google's dns here )
8) DNS2: 8.4.4.4(you'll get dns  from your internet provider, I am using google's dns here )

Now ubuntu part: 
right click on connections , 
Edit connections, wireless, 
Add
Mode: Adhoc
ssid: Helloworld
GOTO : ipv4 tab
method: manual
click add: ip = 192.168.137.1
netmask: 255.255.255.0

That's it .
=====================================================================
Both your phone and ubuntu should connect as expected. It worked for me. I have written the steps hoping that this would be helpful for others. Because I know Its been several months, I had been searching for it. Finally I got it. I had been searching from 2011 November to July 1 2012 :D

@njoy :)
Thank you everyone for such a nice post !! 
Ubuntu community rocks. !!

---

