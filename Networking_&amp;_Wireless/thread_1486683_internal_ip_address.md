---
title: "internal ip address"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by katj12480 on 2010-05-18
I'm trying to make my wireless router always give me the same ip address every boot (192.168.1.100).  I do not have a static ip address from my isp.

Everything I've tried from online help has made my internet break and I'm not even sure what exactly I should be searching for on google.

Ultimately, I'm trying to get my wireless router to forward ftp requests to my computer which shares the network with an xp machine.  I think this is the way to go about it.

Clues for the clueless?

---

### Post by CharlesA on 2010-05-18
Are you setting a static IP on the box or trying to set it so that DHCP (from the router) assigns you the same IP address regardless?

If the router supports a DHCP reservation, set it by using the MAC address of the NIC you are using. It will be listed as this on ifconfig:

```
HWaddr 22:D6:69:EE:57:A6
```

Otherwise set the machine to to a static IP by editing /etc/network/interfaces:
```
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

```

Also add the DNS servers to /etc/resolv.conf:

```
nameserver 192.168.1.1
```

---

### Post by fix_ on 2010-05-18
> **katj12480 said:**
> I'm trying to make my wireless router always give me the same ip address every boot (192.168.1.100).  I do not have a static ip address from my isp.

Everything I've tried from online help has made my internet break and I'm not even sure what exactly I should be searching for on google.

Ultimately, I'm trying to get my wireless router to forward ftp requests to my computer which shares the network with an xp machine.  I think this is the way to go about it.

Clues for the clueless?

You can try to use web interface of your router to configure DHCP. There is possibility to make static mapping of IP to MAC address of your network adapter. To get your adapter MAC address, run ifconfig|grep HWaddr. Use it to configure static DHCP mapping to IP 192.168.1.100. 

If you want to forward ftp requests coming from internet, you need to configure NAT/PAT on your router. The configuration dialog is varying on different routers, but the idea is to create a inbound NAT rule specifying target host - 192.168.1.100 and port - TCP 21.

---

### Post by brayden551 on 2010-05-18
I would take fix_'s advice. Your router might be setup to retrieve a different IP address. Are you sure you don't have a static IP address?

---

### Post by katj12480 on 2010-05-18
> Are you setting a static IP on the box or trying to set it so that  DHCP (from the router) 
> assigns you the same IP address regardless?

I do not have a static IP address from my ISP. I am using dynamic DNS. I'm trying to set it so that router assigns the same IP address every time.  I modified /etc/network/interfaces as you suggested and rebooted.  The router still assigned me a different address (192.168.1.101 instead of 192.168.1.100).  I checked the windows computer and it is not using *.101 so there is no conflict there.

Again, I'm not entirely sure if I'm even doing the right thing to set up my ftp server.  I am using afraid.org and lastip2 for for dynamic dns.  I need the router to know which computer I am to forward port 21 to me.

Here is my /etc/network/interfaces:

auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet static
    address 192.168.1.100
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.1

Here is the output from ifconfig:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3320 (3.3 KB)  TX bytes:3320 (3.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:63:a5:af:15  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:63ff:fea5:af15/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1485 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1807 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1113592 (1.1 MB)  TX bytes:299237 (299.2 KB)

I am using an AirLink 101 Wireless router.

Thanks for your assistance!

---

### Post by lisati on 2010-05-18
Whether or not you have a static IP address from your ISP should make no difference whatsoever to the IP addresses on your internal network. My preference is to go to do what someone else has already suggested: go to your router's browser-based control panel and associate a fixed IP address with the MAC address of the machine on which you wish to use a static IP address. If you give us a hint as to what make and model router you are using, someone might be able to guide you through this process.

---

### Post by katj12480 on 2010-05-18
I added a static DHCP address to my router using my computer's MAC address.
It still won't give me the ip I want.

Things I tried:
changed the lease time on the router to one minute in case it just needed to relinquish my lease.
changed /etc/network/interfaces to auto eth0
restarted both the computer and the router.

As I mentioned in my previous post, I am using an AirLink 101 Wireless N router.

---

### Post by fix_ on 2010-05-19
As far as I can see you have already tried to configure your PC for static ip:

```

#auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

```

If you want to receive settings from router, change it back to dhcp:

```

auto eth0
iface eth0 inet dhcp

```

Also, setting the ip lease to 1 minute is bad idea because your PC will start to ask for new lease every minute. Set it to one day at least. You can always retrieve DHCP setting at any time by launchin command
```

sudo dhclient eth0

```

---

### Post by chili555 on 2010-05-19
Is Network Manager running on your machine? Check with:```
ps aux | grep Network
```If it is, it is unlikely that you will get a static address to work with *interfaces*. I have tried...err, failed many times.

I suggest you remove NM entirely.```
sudo apt-get remove network-manager*
```Then I'd change *interfaces*:```
auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
```And then restart networking:```
sudo /etc/init.d/networking restart
```You will have a persistent address on every boot. Be sure you pick an address outside the range of the DHCP server in the router.> Whether or not you have a static IP address from your ISP should make no difference whatsoever to the IP addresses on your ***internal*** network. Exactly correct. Emphasis added.

---

