---
title: "Using laptop as 3G ICS hotspot 12.04"
date: 2012-07-11
forum: Networking &amp; Wireless
---

### Post by TimoCpt on 2012-07-11
Hi all,

I have a laptop running Ubuntu 12.04 64 bit which has a built in 3G modem which i currently use to connect to the internet.
I would like to share that internet connection using a WIFI hotspot so my mobile phone and other devices can use it.

I get as far as setting up an Adhoc Wireless Hotspot (WEP) in
System Settings -> Network -> Wireless and connecting an iphone to it (Samsung Galaxy S2 never seems to pick up the network...)

However when i try do anything internet related on the iphone, it just doesn't seem to work.

I've had a read through [https://help.ubuntu.com/community/Internet/ConnectionSharing/](https://help.ubuntu.com/community/Internet/ConnectionSharing/) and tried the suggestions there but with no luck.

Anyone out there with a similar setup that has got this to work.

Ciao

Timo
:confused:

---

### Post by Kirk Schnable on 2012-07-11
First thing's first, can I assume the 3G connection is working on the Ubuntu laptop?  If so, please get the name of that interface for us (or do ifconfig and that will show all interfaces, then we can try and pick it out for you).

What you probably want to do is some quick iptables commands.  I can give you some syntax to try out if you can get me your two interface names. (the one for your 3G card, and the one for your WiFi card).  Otherwise I've given you a tutorial below.

Also, unless you plan on giving clients static IP addresses, you should plan on running a DHCP server on your laptop. (See: [https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server))

1. Set a static IP for your WiFi card.  192.168.1.1 will work in a pinch.

2. Connect someone to the WiFi.  Can you ping the IP above? If not, you need a DHCP server or you need a static IP on the client.

3. Beyond that, the next step is to push the Internet traffic from the WiFi to the 3G interface.  This is not too complicated once you get used to it.
I don't recall the tutorial I used to learn how to do this on day one, but this one looks like it should do the trick or at least push you in the right direction: [http://users.telenet.be/mydotcom/howto/lanconnect/router/linux.htm](http://users.telenet.be/mydotcom/howto/lanconnect/router/linux.htm)  
Since I assume your network cards already work, skip down to "Make it route" on that tutorial.


If you have any questions don't hesitate to ask. Sometimes, I tend to assume a higher level of knowledge than I should...

Kirk

---

### Post by TimoCpt on 2012-07-29
Hi Kirk,

Thanks for the reply and apologies for my uber late reply, thought this forum would email me if an update was sent (probably my settings tho :$)

That dhcp-server link you sent me did the trick, i can now connect my work laptop to my personal laptop (hotspot) and browse the internet. 

Still no luck with the mobiles tho, iphone can connect to the network but doesn't seem to use the internet and my Galaxy S2 doesn't work at all...

Details below:

root@timo-dell-1110:~/temp/Bumblebee# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:26:b9:d2:3f:8e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 

eth2      Link encap:Ethernet  HWaddr 70:f1:a1:81:1b:6b  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::72f1:a1ff:fe81:1b6b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:66920
          TX packets:305 errors:83 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:59211 (59.2 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4332 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:745624 (745.6 KB)  TX bytes:745624 (745.6 KB)

wwan0     Link encap:Ethernet  HWaddr 02:80:37:ec:02:00  
          inet addr:41.5.173.89  Bcast:41.5.173.95  Mask:255.255.255.248
          inet6 addr: fe80::80:37ff:feec:200/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48341 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42197 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:52017591 (52.0 MB)  TX bytes:5536263 (5.5 MB)

And output of dhcp-server running:

root@timo-dell-1110:~/temp/Bumblebee# ps -ef | grep dhcp
root     11515   976  0 Jul29 ?        00:00:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/sendsigs.omit.d/network-manager.dhclient-wwan0.pid -lf /var/lib/dhcp/dhclient-2cafcef7-b1c3-4e61-b389-fe250410badc-wwan0.lease -cf /var/run/nm-dhclient-wwan0.conf wwan0
nobody   11600   976  0 00:00 ?        00:00:00 /usr/sbin/dnsmasq --conf-file --no-hosts --keep-in-foreground --bind-interfaces --except-interface=lo --clear-on-reload --strict-order --listen-address=10.42.0.1 --dhcp-range=10.42.0.10,10.42.0.100,60m --dhcp-option=option:router,10.42.0.1 --dhcp-lease-max=50 --pid-file=/var/run/nm-dnsmasq-eth2.pid

I also can't see any connections when checking with jnettop -i eth2 for the mobile phones...

So not quite sure why it works for pc's and not mobile phones, will do some more digging.

Thanks again for your help.

Ciao

Timo

---

### Post by Kirk Schnable on 2012-07-29
Not a problem.  Hmm, I wonder if those devices don't support Ad-Hoc mode.   I've heard some things in the past about mobile devices not being able to connect to Ubuntu hotspots for this reason.

Kirk

---

