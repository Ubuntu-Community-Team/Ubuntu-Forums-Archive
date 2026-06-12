---
title: "Wired network card never works without full powerdown on every shutdown."
date: 2011-11-17
forum: Networking &amp; Wireless
---

### Post by davebz on 2011-11-17
I have a dual boot XP/Ubuntu 11.10 machine, and regardless of which OS I used last, I must power off the computer at the switch, and the modem prior to bootup or the nic won't be recognized in Ubuntu (wired system). Then it works perfectly until the machine is shut down, and I must power down everything before starting up again. 

I've found somewhat similar problems and solutions searching the forums, but since I'm a raw Linux noob and everything works well so as long as I remember to power off, I'm scared to try something I'm not sure of and turning this small hassle  into a major problem.  Already tried one little command I saw here and all it did was make the nic disappear.:confused: 

I downloaded all the updates available and it didn't help.

*-network 
             description: Ethernet interface 
             product: VT6102 [Rhine-II] 
             vendor: VIA Technologies, Inc. 
             physical id: 12 
             bus info: pci@0000:00:12.0 
             logical name: eth0 
             version: 78 
             serial: 00:19:21:3b:95:4a 
             size: 100Mbit/s 
             capacity: 100Mbit/s 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full ip=10.0.0.3 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s 
             resources: irq:23 ioport:ee00(size=256) memory:f6fff800-f6fff8ff 

Any help would be appreciated, Thanks

---

### Post by praseodym on 2011-11-18
Hi,

try to shut off the auto-negotiation. Install the package "ethtool" and:

```
sudo apt-get install ethtool
sudo ethtool -s eth0 speed 100 autoneg off
sudo /etc/init.d/networking restart
```

---

### Post by davebz on 2011-11-18
Thank you for your tip. But it didn't work for me. 

I executed those commands; confirmed autoneg was off, rebooted, but "sudo lshw -C network" showed nothing. So I shutdown, powered off everything as has been my ritual, and network is back up, but now autoneg turned back on by itself.

---

### Post by praseodym on 2011-11-18
Try it via
```
sudo ifdown eth0
sudo ifup eth0
```
Please show the output of
```
cat /etc/network/interfaces
```

---

### Post by davebz on 2011-11-18
Thanks again! Here it is:

dave@dave-P4M800PRO-M:~$ sudo ifdown eth0
[sudo] password for dave: 
ifdown: interface eth0 not configured

dave@dave-P4M800PRO-M:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
dave@dave-P4M800PRO-M:~$ 

dave@dave-P4M800PRO-M:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

Well I'm really stupified. eth0 not configured? Maybe I should be thankful it works at all??? :confused:

---

### Post by praseodym on 2011-11-19
Is it a single modem without router?

[LIST]
[*]If No:
[/LIST]

If you are using the network-manager, try the following:

```
echo "auto eth0" | sudo tee -a /etc/network/interfaces
echo "iface eth0 inet dhcp" | sudo tee -a /etc/network/interfaces
```

[LIST]
[*]If yes:
[/LIST]

Add yourself to the group "dip"

```
sudo adduser $USER dip
```
and _login again_. After that configure with

```
sudo pppoeconf
```
type in your Login and PW from your ISP, and answer anything else with YES or OK.

[LIST]
[*]In both cases:
[/LIST]

Replace "false" with "true" in the file:
```
gksu gedit /etc/NetworkManager/NetworkManager.conf
```
save, close and restart the network:
```
sudo /etc/init.d/networking restart
sudo service network-manager restart
```
Check:
```
ifconfig -a
cat /etc/resolv.conf
dmesg | grep via
sudo ethtool eth0
```

---

### Post by davebz on 2011-11-19
Thank you again!

It's a single modem, no router.

But the second command gave me this, so I stopped after it:

"Sorry, I scanned 1 interface, but the Access   
Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for    
the scan failure may also be another running pppoe        process which controls the modem."
If you're not burned out with this newbie, what can I do about that?

(The connection was up and running fine at this time.) 



BTW, I don't know if it's relevant, but If I do not power off the modem and nic prior to booting, all four of the leds just stay on at the modem - no blinking, and then I have no eth0.

Maybe you already know this, but for what it's worth, I played around a bit and found that I don't have to cycle the modem at all. Just turning off the power to computer and waiting until the led goes out at the nic will do the trick. Since I know so little, I hesitate to even ask, but is there some way I can have linux turn the power to the modem off at shutdown? (I can disconnect/shut down the network, but that doesn't do anything.) 

Just a wild noob guess on my part, but I tried to turn off WOL thinking that might power off the nic when I shutdown the computer, but linux said something like "can't get wol status" "wol not permitted". And I didn't see any wol options in bios to goof around with either(AMI bios dated 2006)  

thanks so much!
Dave

---

### Post by praseodym on 2011-11-20
Try:
```
sudo ifdown eth0
sudo ifup eth0
sudo pppoeconf eth0
```

---

### Post by davebz on 2011-11-20
Hi, thanks again. 

Unfortunately that didn't work at all. The first 2 commands returned something like "eth0 not configured"

The third did something...

And now I can't connect at all no matter what I do :confused: Even after powering everything down. (I'm using a different machine now)

How can I undo whatever that did?

Thanks,
Dave

---

### Post by praseodym on 2011-11-20
Please show now:
```
cat /etc/network/interfaces
ifconfig -a
cat /etc/resolv.conf
```

---

### Post by davebz on 2011-11-20
OK,

Thank you. 

While you were responding, I was commenting out some lines in a few files, and it looks like I got lucky and stumbled and bumbled my way back to where I was :D  - I can now get back online!

Let me run those commands and I'll get back here shortly. I've probably got you wishing you had never seen this thread! Sorry. And Thanks!

---

### Post by davebz on 2011-11-20
Internet is working fine here:

auto lo
iface lo inet loopback


# auto dsl-provider
# iface dsl-provider inet ppp
# pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
# provider dsl-provider

# auto eth0
# iface eth0 inet manual

[ You got it! - As you can see, the above is one of the files I commented lines. I suspect if you were here you'd have this thing right in 10 minutes.]

============================================================

eth0      Link encap:Ethernet  HWaddr 00:19:21:3b:95:4a  
          inet addr:10.0.0.3  Bcast:10.0.0.31  Mask:255.255.255.224
          inet6 addr: fe80::219:21ff:fe3b:954a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:522 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:366773 (366.7 KB)  TX bytes:60630 (60.6 KB)
          Interrupt:23 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

eth0      Link encap:Ethernet  HWaddr 00:19:21:3b:95:4a  
          inet addr:10.0.0.3  Bcast:10.0.0.31  Mask:255.255.255.224
          inet6 addr: fe80::219:21ff:fe3b:954a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:522 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:366773 (366.7 KB)  TX bytes:60630 (60.6 KB)
          Interrupt:23 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


If you're weary of messing with this, and want to bow out, I certainly understand. I know I would be if I were you. It's not  a big deal flipping the switch on the power cord when I shut down.  

Thanks!

---

