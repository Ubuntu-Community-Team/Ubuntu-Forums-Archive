---
title: "Can't connect to router via wired connection"
date: 2011-06-24
forum: Networking &amp; Wireless
---

### Post by M_Krikke on 2011-06-24
Hello,

I have installed Ubuntu for the first time (version 11.04), finally making the step to open source software. Everything seems to be working fine, however I can't connect to my router via a wired connection.

I can use the wireless network, which was detected and I could connect by giving the code. But when I try to connect to this network by wired network, it tries to connect and it says "connection offline" after a while. It never establishes a connection. I used the standard automatic DHCP settings of eth0. I never got this problem with another OS and it's not the cable that's not working.

Does anyone know how to solve this problem?
I'm using a Fujitsu Amilo-something laptop and a Siemens Gigaset wireless router.

Thanks,
Kristof

---

### Post by M_Krikke on 2011-06-25
No ideas?

---

### Post by d3v1150m471c on 2011-06-25
```

# post the output of the following, please
lspci | grep -i ethernet

```

---

### Post by M_Krikke on 2011-06-26
05:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

---

### Post by MaindotC on 2011-06-26
Ok so your card is detected.  Check if the driver is installed:
```
lshw -c Network | driver
```

If you do see a driver indicated then the next step is:
```
ifconfig
```

---

### Post by M_Krikke on 2011-06-27
It says command driver not found.

---

### Post by pjd99 on 2011-06-27
> **M_Krikke said:**
> It says command driver not found.

Try:
lshw -c Network | grep driver

---

### Post by M_Krikke on 2011-06-27
Ok, I did that and a driver was found:
```
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.38-8-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s

```
Then i did ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:03:0d:63:1e:79  
          inet6 addr: fe80::203:dff:fe63:1e79/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:720 (720.0 B)  TX bytes:8002 (8.0 KB)
          Interrupt:19 Base address:0x800 

```

---

### Post by pjd99 on 2011-06-27
If you're certain DHCP is working properly (i.e. tested another computer using the same cable, or it's a dual boot and is working fine in another OS), try restarting the network service after the cable is plugged in:

sudo /etc/init.d/networking restart

or maybe one of these two (can't test right now, and i'm not sure if they've been implemented yet):
sudo service network restart
sudo service networking restart

If its still not working, try assigning a manual address. If you don't know the settings, let the wireless connect, check the connection information and use that as a guide. You'll need an IP address, subnet mask, gateway and DNS address at a minimum.

Still not working, maybe try and unload the driver kernel module and re-inserting it (sudo rmmod r8169; sudo modprobe -i r8169)
Only try this if nothing works and you're 100% certain the DHCP server is working.

---

### Post by M_Krikke on 2011-06-27
I'm positively sure that this cable works on another OS. I tried everything above and nothing worked.

I tried the manual connection with the connection information of the wireless connection and with this a connection was established (arrow up and down which didn't appear when DHCP was automatic). However, internet does not work and I can't even reach the page of the router.

I'm not sure though if my information is entirely correct. For example, what should I add as MAC-address and should I add some routes in the settings tab of the IPv4 connection or not?

---

### Post by pjd99 on 2011-06-27
What's the output of:
```

dmesg | grep eth0
```It should look something like this:
```

[    1.537567] r8169 0000:07:00.0: eth0: RTL8168c/8111c at 0xffffc9000066a000, 00:21:70:b4:6a:1c, XID 1c4000c0 IRQ 45
[   20.583085] r8169 0000:07:00.0: eth0: link down
[   20.583091] r8169 0000:07:00.0: eth0: link down
[   20.583637] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.186349] r8169 0000:07:00.0: eth0: link up
[   22.816615] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   32.870037] eth0: no IPv6 routers present

```There are a few posts about this particular driver and 11.04. Check out these to see if they apply to you:

[http://ubuntuforums.org/showthread.php?t=1766962](http://ubuntuforums.org/showthread.php?t=1766962)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/770708](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/770708)
[http://askubuntu.com/questions/39487/possible-missing-firmware-lib-firmware-rtl-nic-rtl8105e-1-fw-for-module-r8169-wi](http://askubuntu.com/questions/39487/possible-missing-firmware-lib-firmware-rtl-nic-rtl8105e-1-fw-for-module-r8169-wi)
[http://blog.grumblesmurf.org/2011/05/fixing-realtek-networking-on-ubuntu.html](http://blog.grumblesmurf.org/2011/05/fixing-realtek-networking-on-ubuntu.html)

---

### Post by pjd99 on 2011-06-27
> **M_Krikke said:**
> I'm positively sure that this cable works on another OS. I tried everything above and nothing worked.

I tried the manual connection with the connection information of the wireless connection and with this a connection was established (arrow up and down which didn't appear when DHCP was automatic). However, internet does not work and I can't even reach the page of the router.

I'm not sure though if my information is entirely correct. For example, what should I add as MAC-address and should I add some routes in the settings tab of the IPv4 connection or not?

Don't worry about filling in the "Wired" or "802.1x Security" tabs.
IPv4 Settings:
Method: Manual
Then add:
Address, Netmask, Gateway, DNS

IPv6 Settings: Ignore

That's usually all you need to get an Internet connection.

---

### Post by MaindotC on 2011-06-28
> **M_Krikke said:**
> 
```

eth0      Link encap:Ethernet  HWaddr 00:03:0d:63:1e:79  
          inet6 addr: fe80::203:dff:fe63:1e79/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:720 (720.0 B)  TX bytes:8002 (8.0 KB)
          Interrupt:19 Base address:0x800 

```

Agreed with pjd.  DHCP from your access point is supposed to send this information to your machine.  Either dhclient is not being executed (on the Ubuntu machine) or the access point is not sending it (which doesn't seem to be the case if you're story about connecting another node is true).

You can always try```
sudo dhclient
``` to try and kickstart the DHCP request.  However, you should not have to do this every time you plug in the machine.

---

### Post by M_Krikke on 2011-07-02
On
```
dmesg | grep eth0
```,
I get this:
```

[   19.067328] r8169 0000:05:05.0: eth0: RTL8169sb/8110sb at 0xf8024800, 00:03:0d:63:1e:79, XID 10000000 IRQ 19
[   35.139600] r8169 0000:05:05.0: eth0: link down
[   35.139840] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 7690.808200] r8169 0000:05:05.0: eth0: link up
[ 7690.808552] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 7701.520027] eth0: no IPv6 routers present

```.

I tried the links above, to install the drivers, but this didn't help. I got to this blog ([http://vanvalkinburgh.org/blog/3537]("http://vanvalkinburgh.org/blog/3537")) and tried to install the realtek driver of r8169, but this error appears:
```

install -m 744 -c r8169.ko /lib/modules/2.6.38-8-generic/kernel/drivers/net/
install: kan &#8216;/lib/modules/2.6.38-8-generic/kernel/drivers/net/r8169.ko&#8217; niet verwijderen: Toegang geweigerd (cannot delete this file, acces refused)

```

In the meantime, I've installed another pc with the same edition of Ubuntu and this connects directly to the same cabled network, so it should be a problem of the network card and its drivers.

---

### Post by MaindotC on 2011-07-03
Well - you can continue trying to re-install this driver which will eventually solve the problem and you'll be much wiser.  The error message you displayed could be a permissions issue although I'm sure you're installing using root permissions.  If so, then the installer is looking for that file and it's not there, and refuses to continue if it doesn't remove that file.  This could be that the build is not happening correctly (aka - that file should be there as a result of the configure, make, make install) or it could be that you could just comment out that section of the installation file.

In the meantime, you could go get a NIC for $10 and just move on with your life.

---

### Post by M_Krikke on 2011-07-03
I managed to do the installation of this driver.

But even then, it doesn't connect to the network, automatically nor manually ...
No other ideas by chance?

---

### Post by wannagotopopeyes on 2011-07-03
Hi, I'm having a similar issue of not being able to connect with ethernet...

I ran the "lspci | grep -i enthernet" command but got no output... Does that mean it doesnt detect my ethernet controller?

Does anyone know where to go from here??

---

### Post by MaindotC on 2011-07-04
> **M_Krikke said:**
> I managed to do the installation of this driver.

But even then, it doesn't connect to the network, automatically nor manually ...
No other ideas by chance?

This is not specific enough of a question.  At what part of the network connectivity process are you having difficulty?  What is not present that you should be expecting?

---

### Post by M_Krikke on 2011-07-05
When I try to connect to eth0, the connection is not established, when DHCP is set on automatic. It tries to connect for maybe 30 seconds, but it fails. 

When I fill in the information manually for the connection (address, gateway, etc.), the connection is immediately established, but I cannot reach any webpage nor the page of the router itself.

This problem remained the same from the beginning, although I tried the possible solutions given above.

---

### Post by MaindotC on 2011-07-06
> **M_Krikke said:**
> When I try to connect to eth0, the connection is not established, when DHCP is set on automatic. It tries to connect for maybe 30 seconds, but it fails. 

When I fill in the information manually for the connection (address, gateway, etc.), the connection is immediately established, but I cannot reach any webpage nor the page of the router itself.

This problem remained the same from the beginning, although I tried the possible solutions given above.

Please paste your configuration file. Can you ping your access point?  If so, can you describe your access points DHCP configuration and it's connection information?

---

### Post by M_Krikke on 2011-07-18
Sorry for this late response but I was on vacation.

What do you mean by configuration file? The information for the manual connection? I just filled in the address, gateway and subnet I retrieved by the wireless connection. With this I can still not ping the router.

---

### Post by drmtri on 2013-03-27
I have had the same problem with linksys vonage router. 
I was able to fix it with ethtool command and setting the speed to 10, duplex full and autoneg on. 
Even for xp I had to just similar hoops.
My memory may have been playing tricks on me on this one, but if I remember correctly the problem started when vonage updated the firmware for this router.
But for some reason ethtool does not work under wubi. 
Any guesses?

---

### Post by wildmanne39 on 2013-03-27
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

