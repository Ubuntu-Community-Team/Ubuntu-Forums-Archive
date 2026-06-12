---
title: "Connection established, yes IP, yes ping, but won't browse"
date: 2010-05-23
forum: Networking &amp; Wireless
---

### Post by Crowd Control on 2010-05-23
So, here's the problem:

I configured a crappy Belkin wireless router to function as an accesspoint. Pw set, DHCP done by wired router, etc. All this works under Window$, but not under Ubuntu which is frustrating because Ubuntu!! (don't need more reasons)

Now the crappy part from the router is that it sometimes just neglects to establish the connection. This is usually at start up and just takes a couple of minutes to re-establish, but this only happens in Window$ as Ubuntu keeps asking to connect (while it knows the pw and is set to auto-connect). Funny thing is that the router DOES show up as a network all the time.

Now at first it didn't even connect to it, but now sometimes Ubuntu *can* connect to it automatically. Naturally I had to boot up to the other OS to troubleshoot what to do further. The solution offered were, among others:

check IP (it's there when connected), 
check ping (works, when connected), 
change DNS (that actually made a couple of lines from Google's mainpage show up -i.e. I browsed for a moment!!- , but then the router just disconnected :/ )

So now I'm stuck and have no idea how to proceed. That disconnection once I got it slightly working after the DNS change is worrying though. I had the feeling that the connection itself made it to disconnect. Another solution was to edit a line in a config file in /etc/[something] to disable IPv6 alltogether in Ubuntu but that file wasn't even there. So I didn't create it.

So, what to do next?

I'm running that 10.04 64-bit version btw. 

Many thanks in advance.

Grtz CC

---

### Post by linuxonbute on 2010-05-23
when you say ping works when connected are you pinging 

by ip address or by domain?

eg.is it ping 209.85.227.147

or ping google.com

---

### Post by Crowd Control on 2010-05-23
Errrm, I'm not sure what you mean here. 

I get an IP in the 192.blabla etc, which I didn't get before. So that means I got a connection to the wired router. The second suggestion was to try a ping, which I did on [www.ubuntu.com](www.ubuntu.com) . The feedback was that data transmission display with regular intervals. 

Does that answer your question?

Thanks in any case.

---

### Post by linuxonbute on 2010-05-23
> **Crowd Control said:**
> Errrm, I'm not sure what you mean here. 

I get an IP in the 192.blabla etc, which I didn't get before. So that means I got a connection to the wired router. The second suggestion was to try a ping, which I did on [www.ubuntu.com](www.ubuntu.com) . The feedback was that data transmission display with regular intervals. 

Does that answer your question?

Thanks in any case.

Guess I wasn't clear so try 
ping google.com
and 
ping 209.85.227.147
and post the results please.

---

### Post by Crowd Control on 2010-05-23
Point of note: it seems I have had solid connections for the last couple of boots. Sot that means I didn't disconnect. The ping turned out quite differently in the mean time though, so I redid ifconfig and iwconfig again too. Here are the results:


> ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:19:d1:85:de:55  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:93200000-93220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0c:f6:4f:84:24  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f6ff:fe4f:8424/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2339 (2.3 KB)  TX bytes:5428 (5.4 KB)
> iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"BeerWifi"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:57:C4:2D   
          Bit Rate=5.5 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

> ping google.com

ping: unknown host google.com

> ping 209.85.227.147

PING 209.85.227.147 (209.85.227.147) 56(84) bytes of data.
64 bytes from 209.85.227.147: icmp_seq=1 ttl=56 time=118 ms
64 bytes from 209.85.227.147: icmp_seq=2 ttl=56 time=89.5 ms
64 bytes from 209.85.227.147: icmp_seq=3 ttl=56 time=17.8 ms
64 bytes from 209.85.227.147: icmp_seq=4 ttl=56 time=86.2 ms
64 bytes from 209.85.227.147: icmp_seq=5 ttl=56 time=20.1 ms
64 bytes from 209.85.227.147: icmp_seq=6 ttl=56 time=162 ms
64 bytes from 209.85.227.147: icmp_seq=7 ttl=56 time=208 ms
64 bytes from 209.85.227.147: icmp_seq=8 ttl=56 time=19.9 ms
64 bytes from 209.85.227.147: icmp_seq=9 ttl=56 time=20.6 ms
64 bytes from 209.85.227.147: icmp_seq=10 ttl=56 time=19.1 ms
64 bytes from 209.85.227.147: icmp_seq=11 ttl=56 time=17.8 ms
64 bytes from 209.85.227.147: icmp_seq=12 ttl=56 time=18.2 ms
64 bytes from 209.85.227.147: icmp_seq=13 ttl=56 time=22.3 ms
64 bytes from 209.85.227.147: icmp_seq=14 ttl=56 time=20.0 ms
64 bytes from 209.85.227.147: icmp_seq=15 ttl=56 time=23.7 ms
64 bytes from 209.85.227.147: icmp_seq=16 ttl=56 time=19.2 ms
64 bytes from 209.85.227.147: icmp_seq=17 ttl=56 time=20.2 ms
etc (continues endlessly?)

---

### Post by linuxonbute on 2010-05-24
> **Crowd Control said:**
> Point of note: it seems I have had solid connections for the last couple of boots. Sot that means I didn't disconnect. The ping turned out quite differently in the mean time though, so I redid ifconfig and iwconfig again too. Here are the results:

The results show that your system does not know any DNS servers to translate google.com 

Try 
sudo ifdown eth0  
first and see what happens.
 Essentially all you need now is access to DNS lookups and you should be fine.

---

### Post by Crowd Control on 2010-05-24
> **linuxonbute said:**
> The results show that your system does not know any DNS servers to translate google.com 

Try 
sudo ifdown eth0  
first and see what happens.
 Essentially all you need now is access to DNS lookups and you should be fine.


Alright, I tried this and this yielded:

> ifdown: interface eth0 not configured

So that didn't change anything. I tried to do the same by manually removing it from 'system-admin-network connections'. And even after reboot it didn't change anything. 

Point of note: I'm sure I changed the DNS in resolve.conf to google's DNS, but when I just checked it back it was returned to its original value. Maybe that's something?

Also, I barely have a 30% network connection. Maybe Ubuntu handles connections that hang by thread poorly?

Thanks again, for your responses.

---

### Post by linuxonbute on 2010-05-24
> **Crowd Control said:**
> 

Point of note: I'm sure I changed the DNS in resolve.conf to google's DNS, but when I just checked it back it was returned to its original value. Maybe that's something?

Thanks again, for your responses.

What IP address has it put in resolv.conf?
Try pinging it and see if it responds.

also 
whois the-ip-address-in-resolv.conf
will show who it belongs to.

---

### Post by Crowd Control on 2010-05-25
Hmm, not quite what I expected.

> resolv.conf:

# Generated by NetworkManager
domain groni1.gr.home.nl
search groni1.gr.home.nl
nameserver 212.54.35.25
nameserver 212.54.40.25

> ~$ ping 212.54.35.25

PING 212.54.35.25 (212.54.35.25) 56(84) bytes of data.
64 bytes from 212.54.35.25: icmp_seq=1 ttl=251 time=15.2 ms
64 bytes from 212.54.35.25: icmp_seq=2 ttl=251 time=18.6 ms
64 bytes from 212.54.35.25: icmp_seq=3 ttl=251 time=22.1 ms
64 bytes from 212.54.35.25: icmp_seq=4 ttl=251 time=15.4 ms
64 bytes from 212.54.35.25: icmp_seq=5 ttl=251 time=15.4 ms
64 bytes from 212.54.35.25: icmp_seq=6 ttl=251 time=17.5 ms
64 bytes from 212.54.35.25: icmp_seq=7 ttl=251 time=22.6 ms


> 
~$ ping 212.54.40.25

PING 212.54.40.25 (212.54.40.25) 56(84) bytes of data.
64 bytes from 212.54.40.25: icmp_seq=1 ttl=250 time=18.7 ms
64 bytes from 212.54.40.25: icmp_seq=2 ttl=250 time=16.3 ms
64 bytes from 212.54.40.25: icmp_seq=3 ttl=250 time=14.3 ms
64 bytes from 212.54.40.25: icmp_seq=4 ttl=250 time=16.5 ms
64 bytes from 212.54.40.25: icmp_seq=5 ttl=250 time=21.2 ms
64 bytes from 212.54.40.25: icmp_seq=6 ttl=250 time=124 ms
64 bytes from 212.54.40.25: icmp_seq=7 ttl=250 time=15.8 ms
64 bytes from 212.54.40.25: icmp_seq=8 ttl=250 time=17.2 ms
64 bytes from 212.54.40.25: icmp_seq=9 ttl=250 time=20.3 ms


> 
~$ whois 212.54.35.25
getaddrinfo(whois.ripe.net): No address associated with hostname


> 
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=247 time=24.1 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=247 time=20.8 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=247 time=19.0 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=247 time=113 ms
64 bytes from 8.8.8.8: icmp_seq=6 ttl=247 time=126 ms
64 bytes from 8.8.8.8: icmp_seq=7 ttl=247 time=22.4 ms
64 bytes from 8.8.8.8: icmp_seq=8 ttl=247 time=20.9 ms
64 bytes from 8.8.8.8: icmp_seq=9 ttl=247 time=1122 ms
64 bytes from 8.8.8.8: icmp_seq=10 ttl=247 time=121 ms
64 bytes from 8.8.8.8: icmp_seq=11 ttl=247 time=19.3 ms
64 bytes from 8.8.8.8: icmp_seq=12 ttl=247 time=18.8 ms
64 bytes from 8.8.8.8: icmp_seq=13 ttl=247 time=18.8 ms
64 bytes from 8.8.8.8: icmp_seq=14 ttl=247 time=18.5 ms


> 
erik@erik-desktop:~$ ping 8.8.4.4
PING 8.8.4.4 (8.8.4.4) 56(84) bytes of data.
64 bytes from 8.8.4.4: icmp_seq=1 ttl=247 time=67.9 ms
64 bytes from 8.8.4.4: icmp_seq=2 ttl=247 time=18.2 ms
64 bytes from 8.8.4.4: icmp_seq=3 ttl=247 time=18.4 ms
64 bytes from 8.8.4.4: icmp_seq=4 ttl=247 time=31.7 ms
64 bytes from 8.8.4.4: icmp_seq=5 ttl=247 time=53.0 ms
64 bytes from 8.8.4.4: icmp_seq=6 ttl=247 time=19.8 ms
64 bytes from 8.8.4.4: icmp_seq=7 ttl=247 time=18.2 ms
64 bytes from 8.8.4.4: icmp_seq=8 ttl=247 time=27.0 ms
64 bytes from 8.8.4.4: icmp_seq=9 ttl=247 time=116 ms
64 bytes from 8.8.4.4: icmp_seq=10 ttl=247 time=19.6 ms
64 bytes from 8.8.4.4: icmp_seq=11 ttl=247 time=26.1 ms
64 bytes from 8.8.4.4: icmp_seq=12 ttl=247 time=19.4 ms
64 bytes from 8.8.4.4: icmp_seq=13 ttl=247 time=18.6 ms


> 
erik@erik-desktop:~$ whois 8.8.8.8
getaddrinfo(whois.arin.net): No address associated with hostname


Quite the list here. I'll check what DNS I have in the other OS. If it differs I will edit this in below.

edit: darn, I forgot I got Window$ set to Google's DNS. :)

---

### Post by Crowd Control on 2010-05-26
Is there any new input for this problem?

---

### Post by linuxonbute on 2010-05-26
> **Crowd Control said:**
> Is there any new input for this problem?

what happens when you ping google.com now?
With nameservers available browsing should work now.

---

### Post by Crowd Control on 2010-05-31
Pinging google didn't work. Also the connection establishes almost always now, but still kicks out every now and then.

Furthermore I have checked to see if I could update or something (using the internet), but to no avail. 

I am completely puzzled by this. I just downloaded another flavour of Ubuntu to see if that makes any difference.

---

### Post by puppywhacker on 2010-05-31
[http://dnswijziging.casema.nl/](http://dnswijziging.casema.nl/)

Use 83.80.1.236

---

### Post by Crowd Control on 2010-05-31
Zomg! Could it be this simple? I wouldn't possibly think to look in that direction though. Again, it's normal Ubuntu didn't pick this one up? 

Anyway, I will most definitely give this a try. 

Thanks. \\:D/



edit:

Ok, I read up on changing the DNS servers. I haven't actually tried that DNS server but Google's as it slightly worked before. Now I had to look up how to override resolv.conf in dhclient.conf which actually worked, so upon reboot I had 8.8.8.8 set as DNS. The wireless connected to the accesspoint but instantly disconnected as soon as I opened Firefox. So then I messed around (only slightly) more in dhclient, because I have a STRONG feeling we are poking the problem by looking at that. 

This is how it looked:
> 
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

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


So I removed the request domain-name-servers, removed the hash before the 'prepend' line. That didn't work as stated above. But there are several options to try (to remove or not, to change 127.0.0.1 to preset DNS, etc. I could sure use help setting up this file, as I think the solution lies somewhere in here.



edit2: I rechecked with the Window$ partition to compare numbers. It appears the original DNS server in resolv.conf is the same as in Ubuntu's (when not set to Google's). So maybe we there are some other addresses we need to change in dhcp? 
I uploaded a screeny with the available info [here]("http://yfrog.com/emipconfigallp").

---

### Post by Crowd Control on 2010-06-01
Any new ideas on this? I have the feeling we are close! :)

---

