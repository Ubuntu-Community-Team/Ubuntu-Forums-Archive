---
title: "Can't get eth0 to appear in ifconfig—connecting OS X and linux via cat5 cable"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by juliushibert63 on 2010-11-07
I'm trying to get my Ubunutu and OSX systems to connected via a cat5 cable to transfer some large files around very quickly. Now i know normally this would require a crossover cable as it's a direct connection but the macbook/OSX can handle changing the wires round to make it work like a crossover cable as I've done it before. 

However the macbook creates a self-assigned IP or as I've tried I've set it to 

IP:10.10.0.1
Subnet: 255.255.255.0

Then I've setup the Ubuntu system both through the System>Admin>Network panel as 

IP:10.10.0.2
Subnet: 255.255.255.0

and my /etc/network/interfaces file is the same;



#lines added to get static crossover cable working
auto lo
iface eth0 inet static
address 10.10.0.2
netmask 255.255.255.0


Yet when I run ifconfig in the terminal eth0 isn't present 

```
htpc:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:912 errors:0 dropped:0 overruns:0 frame:0
          TX packets:912 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:371613 (371.6 KB)  TX bytes:371613 (371.6 KB)

ra0       Link encap:Ethernet  HWaddr 70:f1:a1:e6:b1:97  
          inet addr:192.168.0.42  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::72f1:a1ff:fee6:b197/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:120744 errors:1 dropped:0 overruns:0 frame:0
          TX packets:87499 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:171716865 (171.7 MB)  TX bytes:7815802 (7.8 MB)
          Interrupt:19 

htpc:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 90:fb:a6:e4:c0:b0  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xe000 


```

Also even when I try and ping 10.10.0.2 either from my OS X or the actually Ubunutu machine all I get is 

```
ping 10.10.0.1
PING 10.10.0.1 (10.10.0.1): 56 data bytes
Request timeout for icmp_seq 0
Request timeout for icmp_seq 1
Request timeout for icmp_seq 2
Request timeout for icmp_seq 3

```

Yet the Ubunutu machine is also connected to Wifi and when I ping it's own address I get the expected response. 

To me it just seems like eth0 isn't being recognised somwhere or it's not turned on yet I can't seem to find any toggles or settings for it anywhere. Further more if I check >System>Admin>Network Tools the IP for eth0 is 0.0.0.0.

Any ideas what could be going wrong and why no IP set correctly?

---

### Post by dineshs on 2010-11-08
Can you try configuring manual IP via Network manager?
For this first make /etc/network/interfaces conatain only 
auto lo
iface lo inet loopback
Restart PC and do
[http://ubuntuforums.org/showpost.php?p=9467538&postcount=5](http://ubuntuforums.org/showpost.php?p=9467538&postcount=5)

---

### Post by Decatf on 2010-11-08
A connection can be brought up by doing **sudo ifconfig eth0 up**.

---

### Post by grahammechanical on 2010-11-08
Your wireless (ra0) is UP and RUNNING. This usually prevents an ethernet connection from becoming active automatically. In Ubuntu if wireless (wlan0, in my case) and eth0 and eth1 are marked as connect automatically, then Ubuntu will give first choice to the wireless connection.

Disconnect the wireless connection. Remove the connect automatically tick mark. Select Auto eth0 from the network manger left click drop down menu, and Ubuntu should try to establish a connection. I say should.

Regards.

---

### Post by juliushibert63 on 2010-11-08
Thanks for yoru help guys. So I changed my /etc/network/interfaces to

auto lo
iface lo inet loopback

 and changed my ip settings as suggested below.

```
Pl follow this step by step.
(Note :The IP addresses are examples.Substitute your values)
Right-click on the NM icon(on top right of the panel) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection you want and click edit
select ipv4 
method-manual 
address 192.168.1.100 
mask 255.255.255.0 
gateway 192.168.1.1 then hit enter 
DNS 4.2.2.1
then click apply
note:You may substitute your values for IP DNS gateway etc
```

Now the two computers work fine after changing some firewall settings as well. 

Not a huge problem but it wont connect the Wifi and Wired Connection at the same time as grahammechanical mentioned. Where as my mac is capable of doing this. Is there anyway of tricking the Linux box to keep both connections alive. The Wifi is the only one that will have Internet access ever as the LAN is always being used a direct PC to PC connection?

---

### Post by uncaspi on 2010-11-08
Disable network-manager sudo service network-manager stop

and bring up the cards manually. You`ve already done it with eth0 and do the following steps to establish wifi connection.

sudo /sbin/iwlist scan      

To view your access points. Note ESSID and CHANNEL

sudo /sbin/iwconfig ra0 essid"xxxxxxxxxx" channel x


sudo /sbin/dhclient ra0

---

### Post by Decatf on 2010-11-08
Is this something specific to certain hardware? I have no problem having two interfaces (wireless and wired) connected at the same time though network manager.

---

### Post by juliushibert63 on 2010-12-08
> **uncaspi said:**
> Disable network-manager sudo service network-manager stop

and bring up the cards manually. You`ve already done it with eth0 and do the following steps to establish wifi connection.

sudo /sbin/iwlist scan      

To view your access points. Note ESSID and CHANNEL

sudo /sbin/iwconfig ra0 essid"xxxxxxxxxx" channel x


sudo /sbin/dhclient ra0




Thanks for the advice on this. I know my ssid (network name) and the wifi channel from my router config but I seem to be hitting a snag with these commands.


```
gil@gil-htpc:/sbin$ sudo /sbin/iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Interface doesn't support scanning : Network is down

gil@gil-htpc:/sbin$ sudo /sbin/iwconfig ra0 essid"lolcatz" channel 8
iwconfig: unknown command "essidlolcatz"
gil@gil-htpc:/sbin$ sudo /sbin/iwconfig ra0 essid "lolcatz" channel 8
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ra0 ; Network is down.

```

Any ideas what's causing this error on setting the ESSID?

---

