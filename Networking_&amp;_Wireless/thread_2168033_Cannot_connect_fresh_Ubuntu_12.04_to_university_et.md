---
title: "Cannot connect fresh Ubuntu 12.04 to university ethernet"
date: 2013-08-16
forum: Networking &amp; Wireless
---

### Post by Floel on 2013-08-16
Hi all, 

I'm quite new to ubuntu, but so far I've liked it when I had to work with it. 
Right now I'm installing a new PC as a research tool, and I will run my data acquisition in Ubuntu. However, this computer has been giving me quite some problems in getting online. As far as I can tell the university has allowed me to connect to the outside world from this computer, but I have not been able to open webpages through my browser or to update my system using apt-get update. During installation the computer first thinks it's connected (in the window saying that for an optimal installation at least 4.4 GB drive space and an internet connection are needed). however, after ~15 seconds the green checkmark becomes a grey cross, meaning that the computer is not connected. In other posts with comparable problems I have seen people ask for the ethernet controller and output of ifconfig, which are:

Ethernet controller is an Intel 82579V

sudo ifconfig gives:
eth0      Link encap:Ethernet  HWaddr 74:d0:2b:28:5e:eb  
          inet addr:145.108.182.213  Bcast:145.108.183.255  Mask:255.255.252.0
          inet6 addr: fe80::76d0:2bff:fe28:5eeb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9518 (9.5 KB)  TX bytes:12442 (12.4 KB)
          Interrupt:20 Memory:f7f00000-f7f20000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:342 errors:0 dropped:0 overruns:0 frame:0
          TX packets:342 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:29162 (29.1 KB)  TX bytes:29162 (29.1 KB)

I really hope you guys can help, I would be grateful for any suggestions.

Floel

---

### Post by zero2xiii on 2013-08-16
Hay,

I assume one of the following might be the problem:

1. You are not requesting and or getting a DHCP supplied address.
2. There is no DHCP server and all IPs are manually given to each computer on the network.

In case 1:
run in terminal:
```
sudo dhclient
```
or
```
sudo dhclient eth0
```

In case 2:
Get an IP from the network admin or who ever gives those and then:
[https://help.ubuntu.com/lts/serverguide/network-configuration.html](https://help.ubuntu.com/lts/serverguide/network-configuration.html)
[http://ubuntuforums.org/showthread.php?t=1985170](http://ubuntuforums.org/showthread.php?t=1985170)

That should resolve your issue.

If you connect locally (aka get an IP) but can not access the internet, you need to set a DNS server (I use 8.8.8.8 and 8.8.4.4 which is google's):
[https://help.ubuntu.com/lts/serverguide/network-configuration.html](https://help.ubuntu.com/lts/serverguide/network-configuration.html)
And see the section on "Name Resolution"
Please note this step is a MUST for manually supplied (aka static) IP addresses. 

Also might be useful to test and see if you can access the internet via IP.
Try going to:
[http://74.125.233.80](http://74.125.233.80)
That is one IP of google, you should see the google home page when you load that. If you do see the home page but not when you go straight to [www.google.com](www.google.com), then you definitely have internet access, but your name resolution (DNS server) is not working properly. See the link above on how to fix that.

Hope this helps you.

---

### Post by Floel on 2013-08-16
Hi zero2xiii,

Thanks for the quick reply. 
The first option only generated a response saying "file exists", so apparently that wasn't the problem.
As for the second option, I'm going to see if I can get the admin to grant me a static IP and if that will work.

Thanks again!
Floel

---

