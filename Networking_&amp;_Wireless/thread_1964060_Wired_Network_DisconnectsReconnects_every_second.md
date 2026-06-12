---
title: "Wired Network Disconnects/Reconnects every second"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by legoEngineer on 2012-04-23
I am using Ubuntu 11 on a laptop which is connected via ethernet to a Windows 7 pc. The ubuntu laptop has internet via its wireless card which I am trying to access with the windows PC.

I tried this link:
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

However, I didn't know exactly which part I should follow. I ended up using the automatic ethernet tool (which created a new wired network) and set the ip4 setting to "Shared with other computers."

Now my windows PC is able to connect to the laptop and get through to the internet!

However, in Ubuntu I see the "Wired Network Disconnected" appear followed by "Wired Network Connected" These repeat continuously. Indeed the internet connection on the PC does not say it disconnects but it appears that the internet connection is dropping.

My only though is that maybe I have to change the router settings to have a fixed IP address? I already set windows to fixed IP and  I am under the  impression that setting my Ubuntu wired network to "Share with other computers" fixed that IP as well.

Any input is greatly appreciated.

---

### Post by jonobr on 2012-04-23
Setting the wired connetion to a fixed IP address in the same subnet is probably a good test,

could you post the result of 

```
ifconfig 
```
and 
```
sudo dmesg |grep eth0
```
that may show something.

Could also be a suspect cable between the machines.
(I assume that cable is a crossover)

---

### Post by legoEngineer on 2012-04-24
[FONT=monospace]ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:b3:bf:6a:9a  
          inet6 addr: fe80::225:b3ff:febf:6a9a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:424 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3062 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:77422 (77.4 KB)  TX bytes:777110 (777.1 KB)
          Interrupt:22 Memory:db300000-db320000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:516 (516.0 B)  TX bytes:516 (516.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:6a:55:31:ce  
          inet addr:192.168.123.100  Bcast:192.168.123.255  Mask:255.255.255.0
          inet6 addr: fe80::221:6aff:fe55:31ce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7366 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6836 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7445655 (7.4 MB)  TX bytes:1412726 (1.4 MB)


sudo dmesg |grep eth0
[sudo] password for chase: 
[    1.433552] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:25:b3:bf:6a:9a
[    1.433555] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.433582] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: 1052FF-0FF
[   17.088317] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  493.308927] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[  493.309501] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  503.848187] eth0: no IPv6 routers present
chase@ubuntu:~$ 


I have no idea what that means, but thank you for helping me. Also of note: I can ping the Ubuntu laptop from my windows desktop but not the other way around. Also, I tried to set the windows desktop's IP address to 127.0.0.2 but it wouldn't let me. it said 127 was reserved for something else. Maybe if I changed the Ubuntu IP to something else?
[/FONT]

---

### Post by jonobr on 2012-04-24
Your eth0 has no ip address save an IPV6 address

What address is your laptop getting?

I would reckon you should set your IP to an address in the same subnet as your Laptop

Cheers

---

### Post by legoEngineer on 2012-04-24
I modified the wired network to give it an ip address and it fixed my connection issues. However, it disabled my wireless internet access. I am guessing there is an IP conflict. Disabling the wired network fixes the problem.

So under IPv4 setting I click on Manual. There is a place for adress netmask and gateway. Do you have suggestions as to what they should be?

---

### Post by jonobr on 2012-04-25
Hello


On your windows box connected to the same segment open a command prompt and type ipconfig,

that should give you the info needed

---

