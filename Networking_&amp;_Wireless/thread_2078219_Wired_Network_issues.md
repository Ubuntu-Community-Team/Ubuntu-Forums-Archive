---
title: "Wired Network issues"
date: 2012-10-30
forum: Networking &amp; Wireless
---

### Post by PAKeenan on 2012-10-30
Hello All! 

I recently upgraded my desktop and netbook from Ubuntu 12.04 to 12.10. Both duel boot Windows and Ubuntu. 

After upgrading, my desktop no longer connects to the internet, but shows that it is connected to the network. My netbook however can see our wireless network, and connects to the internet fine. The Windows side of my desktop shows no issues, and loads web pages.

I noticed that some other users also seem to have a similar situation as I. I tried a few suggestions but to no avail. 

:confused:

Any help would be appreciated! Thanks!

---

### Post by aromo on 2012-10-30
First thing you should try is:
 ifconfig eth0

That will show the IP address assigned to your NIC.  Please post the output for further troubleshooting.

---

### Post by ORF1000 on 2012-10-30
This sounds exactly like my problem.  I will be waiting eagerly to see how it's resolved.  I have restored my install to 12.04 with an image I made before the upgrade to 12.10.  I will see what happens with this thread, then do the upgrade over.  Thanks, aromo, for your attention to this.

For clarification, I can ping my router and other computers on the network.  Other computers on the network can ping the upgraded computer, too.  The router interface shows the computer present, but the upgraded computer can't ping outside the network.  I can't ping Google, even with their IP address.

/etc/resolv.conf shows the loopback address as 127.0.0.1.  I thought it was supposed to change to 127.0.1.1?  Could that be a clue?

Thanks.  I'll wait to see what transpires.

---

### Post by PAKeenan on 2012-10-31
Here's what it came up with

eth0      Link encap:Ethernet  HWaddr 1c:6f:65:2c:42:f5  
          inet addr:192.168.2.8  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::1e6f:65ff:fe2c:42f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8847 (8.8 KB)  TX bytes:9343 (9.3 KB)


Like ORF, My computers can ping each other as well.

---

### Post by chili555 on 2012-11-04
> **ORF1000 said:**
> This sounds exactly like my problem.  I will be waiting eagerly to see how it's resolved.  I have restored my install to 12.04 with an image I made before the upgrade to 12.10.  I will see what happens with this thread, then do the upgrade over.  Thanks, aromo, for your attention to this.

For clarification, I can ping my router and other computers on the network.  Other computers on the network can ping the upgraded computer, too.  The router interface shows the computer present, but the upgraded computer can't ping outside the network.  I can't ping Google, even with their IP address.

/etc/resolv.conf shows the loopback address as 127.0.0.1.  I thought it was supposed to change to 127.0.1.1?  Could that be a clue?

Thanks.  I'll wait to see what transpires.Please post:```
nm-tool
ping -c3 www.google.com
ping -c3 8.8.8.8
ifconfig
route -n
```Thanks.

---

### Post by Alfred14 on 2012-11-04
I have had similar problems to this. I was able to ping computers on my local network with an i.p address only and also external ip address would ping but hostname didnt work at all.

I seem to have resolved the issue but the built in ubuntu network manager doesnt show a connection exists yet my internet now works fine.

This is the output from nm-tool and i think the problem is the state of the device is unmanaged and i dont know how to change that.


NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unmanaged
  Default:           no
  HW Address:        1C:6F:65:CD:C9:62

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

---

### Post by chili555 on 2012-11-04
> Type: Wired
Driver: r8169
State: *unmanaged*Let's have a look at:```
cat /etc/network/interfaces
```

---

### Post by Alfred14 on 2012-11-04
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto eth0
iface eth0 inet dhcp

iface lo inet loopback
```

---

### Post by chili555 on 2012-11-05
Network Manager is not managing your wired ethernet because the manual method, /etc/network/interfaces, is managing it. If it's working perfectly fine for you, you need do nothing. If you insist that NM have exclusive control, then amend /etc/network/interfaces:```
sudo gedit /etc/network/interfaces
```Change it to:```
# interfaces(5) file used by ifup(8) and ifdown(8)
[COLOR="Red"]#[/COLOR]auto eth0
[COLOR="Red"]#[/COLOR]iface eth0 inet dhcp

[COLOR="Red"]auto lo[/COLOR]
iface lo inet loopback
```Proofread, save and close gedit. Restart NM:```
sudo service network-manager restart
```Frankly, if it isn't broken, I wouldn't fix it.

---

### Post by ORF1000 on 2012-11-05
So, Alrfred, what did you do to correct the problem?

---

### Post by Alfred14 on 2012-11-10
> **ORF1000 said:**
> So, Alfred, what did you do to correct the problem?

I ran the command 
```
sudo gedit /etc/network/interfaces 
```
and made the file look like this
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto eth0
iface eth0 inet dhcp

iface lo inet loopback
```
That seemed to fix the problem for me after a reboot but if you want the inbuilt network manager to control your connection follow the guide posted by Chili555 above and let me know whether that fixes your problem.

---

### Post by emanuelv on 2012-11-14
Hi,

I had the same issue, after upgrading from Xubuntu 12.04 to 12.10, I could not resolve domain names anymore.

I simply followed this procedure found at [http://askubuntu.com/questions/212013/name-resolver-doesnt-work](http://askubuntu.com/questions/212013/name-resolver-doesnt-work)

```
sudo dpkg-reconfigure resolvconf
```And I answered Yes to the prompts

It fixed my issue 8)

---

