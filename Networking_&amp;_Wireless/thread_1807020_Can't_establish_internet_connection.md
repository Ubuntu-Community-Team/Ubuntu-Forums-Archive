---
title: "Can't establish internet connection"
date: 2011-07-18
forum: Networking &amp; Wireless
---

### Post by mp300 on 2011-07-18
First I need to say: Hi I'm new to this forum and I'm from Slovenia. ):P  So please forgive me for my bad english, I will give my best! 


I'm using Ubuntu for almost two years and everything has worked well till now. One day I have reinstall ubuntu in my computer, but then something went wrong. I couldn't anymore establish my internet connection. I have tried everything but nothing helped. I even reinstall my ubuntu multiple times but there was no efekt. Even when I installed Kubuntu or an older Ubuntu 10.10, there was no internet.  I'm also using Windows 7 but there is always a internet connection. I didn't change any hardware on my computer, only a new AMD graphic card. 
I'm using wired optical Internet 10/10 MB. 

I hope this will help you solve my problem:

On terminal I have typed ifconfig and got this:

```
eth0    Link encap:Ethernet  HWaddr 00:1d:7d:90:45:25  
          inet6 addr: fe80::21d:7dff:fe90:4525/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:540 (540.0 B)  TX bytes:8094 (8.0 KB)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11376 (11.3 KB)  TX bytes:11376 (11.3 KB)
```

And also typed dmesg | grep eth:
```

[    0.961788] i2c-core: driver [adp5520] using legacy suspend method
[    0.961790] i2c-core: driver [adp5520] using legacy resume method
[    1.220318] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.220489] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[    1.220493] forcedeth 0000:00:07.0: setting latency timer to 64
[    1.750925] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1d:7d:90:45:25
[    1.750929] forcedeth 0000:00:07.0: highdma pwrctl mgmt gbit lnktim msi desc-v3
[   11.195977] forcedeth 0000:00:07.0: irq 41 for MSI/MSI-X
[   21.620017] eth0: no IPv6 routers present  
```

Those things I have found on some other posts here in this forum.


I'm sorry to say this but Ubuntu is not cool without internet, so please help me. :(

Edit: I using now Ubuntu 11.04 64bit.

---

### Post by jmoorse on 2011-07-18
Hello and welcome!

Yes, you do not have a IPv4 address on your adapter.

Can you please run:

```

sudo dhclient eth0

```

And then see if ifconfig shows an IP address?  (listed as: inet addr)

---

### Post by mp300 on 2011-07-18
> **jmoorse said:**
> Hello and welcome!

Yes, you do not have a IPv4 address on your adapter.

Can you please run:

```

sudo dhclient eth0

```And then see if ifconfig shows an IP address?  (listed as: inet addr)


Ok I have done like you said. This is what terminal showed me:

```
mp2@mp2-M52S-S3P:~$ sudo dhclient eth0

[sudo] password for mp2: 



mp2@mp2-M52S-S3P:~$ 

mp2@mp2-M52S-S3P:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1d:7d:90:45:25  

          inet6 addr: fe80::21d:7dff:fe90:4525/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:6 errors:0 dropped:0 overruns:0 frame:0

          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:360 (360.0 B)  TX bytes:18435 (18.4 KB)

          Interrupt:41 Base address:0xc000 



eth0:avahi Link encap:Ethernet  HWaddr 00:1d:7d:90:45:25  

          inet addr:169.254.5.149  Bcast:169.254.255.255  Mask:255.255.0.0

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          Interrupt:41 Base address:0xc000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:124 errors:0 dropped:0 overruns:0 frame:0

          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:9416 (9.4 KB)  TX bytes:9416 (9.4 KB)
```

---

### Post by jmoorse on 2011-07-18
Doesn't appear you grabbed a DHCP lease (IP address)

When you are running Windows 7 can you please post the output of:

```

ipconfig /all

```

Thanks!

---

### Post by mp300 on 2011-07-18
didn't work:

```
mp2@mp2-M52S-S3P:~$ ipconfig /all

No command 'ipconfig' found, did you mean:

 Command 'tpconfig' from package 'tpconfig' (universe)

 Command 'iwconfig' from package 'wireless-tools' (main)

 Command 'ifconfig' from package 'net-tools' (main)

ipconfig: command not found

```

Also tried ifconfig /all  and still nothing

---

### Post by jmoorse on 2011-07-18
From your Windows 7 box please

> **jmoorse said:**
> Doesn't appear you grabbed a DHCP lease (IP address)

When you are running Windows 7 can you please post the output of:

```

ipconfig /all

```

Thanks!

---

### Post by mp300 on 2011-07-18
> **jmoorse said:**
> From your Windows 7 box please

Could you please tell me how do I do that? I don't know much about windows.

---

### Post by jmoorse on 2011-07-18
Here is a good tutorial:

[http://www.myaccount.charter.com/customers/support.aspx?supportarticleid=2265#cmd](http://www.myaccount.charter.com/customers/support.aspx?supportarticleid=2265#cmd)

Follow just up to the first command "ipconfig /all"

You don't need to do the renew / release stuff.

Please post the output.

Edit:  Here is a youtube video showing the same: [http://www.youtube.com/watch?v=ztXB9EjGh70](http://www.youtube.com/watch?v=ztXB9EjGh70)

---

### Post by mp300 on 2011-07-18
O I get it now. You mean use ubuntu on  Virtual Box. Ok then I will need to install it. I have installed ubuntu on a partition.

---

### Post by mp300 on 2011-07-18
Ok I will follow the tutorial

---

### Post by jmoorse on 2011-07-18
> **mp300 said:**
> O I get it now. You mean use ubuntu on  Virtual Box. Ok then I will need to install it. I have installed ubuntu on a partition.

No.  Nothing with virtualbox.

You said you also run windows 7 at home:

> 
I'm also using Windows 7 but there is always a internet connection


Please run those commands from one of the internet connected Windows 7 boxes.  I assume that is where you are updating this forum from?

---

### Post by mp300 on 2011-07-18
Thank you!

Ok this is it:
```


C:\Users\mp>ipconfig /all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : mp-PC
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : t-2.net

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : t-2.net
   Description . . . . . . . . . . . : NVIDIA nForce Networking Controller
   Physical Address. . . . . . . . . : xx-xx-xx-xx-xx-xx
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : xxxx::xxxx:xxxx:xxxx:xxxxxxx(Preferred)
   IPv4 Address. . . . . . . . . . . : xxx.xxx.xxx.xxx(Preferred)
   Subnet Mask . . . . . . . . . . . : xxx.xxx.xxx.x
   Lease Obtained. . . . . . . . . . : 18. julij 2011 23:01:51
   Lease Expires . . . . . . . . . . : 19. julij 2011 23:01:51
   Default Gateway . . . . . . . . . : xxx.xxx.xxx.x
   DHCP Server . . . . . . . . . . . : xxx.xxx.xxx.x
   DHCPv6 IAID . . . . . . . . . . . : xxxxxxxxx
   DHCPv6 Client DUID. . . . . . . . : xx-xx-xx-xx-xx-xx-xx-xx-xx-xx-xx-xx-xx-xx

   DNS Servers . . . . . . . . . . . : xx.xxx.xxx.xx
                                       xx.xxx.xxx.xx
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter VirtualBox Host-Only Network:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : VirtualBox Host-Only Ethernet Adapter
   Physical Address. . . . . . . . . : xx-xx-xx-xx-xx-xx
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : xxxx::xxxx:xxxx:xxxx:xxxxxxx(Preferred)
   IPv4 Address. . . . . . . . . . . : xxx.xxx.xx.x(Preferred)
   Subnet Mask . . . . . . . . . . . : xxx.xxx.xxx.x
   Default Gateway . . . . . . . . . :
   DHCPv6 IAID . . . . . . . . . . . : xxxxxxxxx
   DHCPv6 Client DUID. . . . . . . . : xx-xx-xx-xx-xx-xx-xx-xx-xx-xx-xx-xx-xx-xx

   DNS Servers . . . . . . . . . . . : xx.xxx.xxx.xxx
                                       xx.xxx.xxx.xxx
                                       xx.xxx.xxx.xxx
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter isatap.t-2.net:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : t-2.net
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : xx-xx-xx-xx-xx-xx-xx-xx
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter 6TO4 Adapter:

   Connection-specific DNS Suffix  . : t-2.net
   Description . . . . . . . . . . . : Microsoft 6to4 Adapter
   Physical Address. . . . . . . . . : xx-xx-xx-xx-xx-xx-xx-xx
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : xxxx:xxxx:xxxx::xxxx:xxxx(Preferred)
   Default Gateway . . . . . . . . . : xxxx:xxxx:xxxx::xxxx::xxxx
   DNS Servers . . . . . . . . . . . : xx.xxx.xxx.xx
                                       xx.xxx.xxx.xx
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : xx-xx-xx-xx-xx-xx-xx-xx
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : xxxx:x:xxx:xxxx:xxx:xxx:xxxx:xxxx(Prefer
red)
   Link-local IPv6 Address . . . . . : xxxx::xxx:xxx:xxxx:xxxxxxxPreferred)
   Default Gateway . . . . . . . . . :
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter isatap.{xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #2
   Physical Address. . . . . . . . . : xx-xx-xx-xx-xx-xx-xx-xx
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes


```

---

### Post by jmoorse on 2011-07-18
Ok, are both your Windows and Ubuntu machines plugged into the same router?  If so, please try turning off / unplugging the ethernet cable to the Windows 7 machine and running the following command on the ubuntu box:

```

sudo service networking restart

```

Also you may want to edit your previous post and pull out the IP addresses, just to be on the safe side.

---

### Post by mp300 on 2011-07-18
Yes I using the same router and computer for oboth systems.

Ok I will do this now.

---

### Post by mp300 on 2011-07-18
Only this shows me: 

```
mp2@mp2-M52S-S3P:~$ sudo service networking restart

restart: Unknown instance: 

```

---

### Post by jmoorse on 2011-07-18
> **mp300 said:**
> Only this shows me: 

```
mp2@mp2-M52S-S3P:~$ sudo service networking restart

restart: Unknown instance: 

```

I'm sorry, the service command doesn't work for that.  My fault.

Unplugging / re-plugging the ethernet cable will accomplish the same goal.  So to recap:

1. Unplug ethernet cable on Windows
2. Unplug ethernet cable on Ubuntu
3. Re-plug ethernet cable on Ubuntu
4. On Ubuntu run ifconfig, hope for an IP address :)
5. Test internet browsing in Ubuntu

---

### Post by mp300 on 2011-07-18
Tried your advice and still no connection: 

```
mp2@mp2-M52S-S3P:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1d:7d:90:45:25  

          inet6 addr: fe80::21d:7dff:fe90:4525/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:1 errors:0 dropped:0 overruns:0 frame:0

          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:60 (60.0 B)  TX bytes:5944 (5.9 KB)

          Interrupt:41 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:116 errors:0 dropped:0 overruns:0 frame:0

          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:8784 (8.7 KB)  TX bytes:8784 (8.7 KB)

```

Oh man I'm geting sick of this. I can't believe everything was working fine and on linux before I had internet and now nothing. How is this even possible?

---

### Post by jmoorse on 2011-07-18
So there are a few possibilities, here is the most likely:

Your ISP filters DHCP by mac addresses or only provides you 1 IP address.

You have a few options, in order of least effort.

1. Speak to your ISP, ask if they will allocate you more IPs for free.  Give them the mac address of your ubuntu machine: 00:1d:7d:90:45:25  
2. Speak to your ISP, ask them to put your modem/fiber bridge into NAT mode
3. Buy a router and set that up behind your ISP device.

---

### Post by mp300 on 2011-07-18
It seems the problem is from ISP.
Then I will go to our ISP forum and ask them about this problem.

Thank you sooo much for your time and help!  :smile:

---

### Post by jmoorse on 2011-07-18
Sure thing, respond back with any further questions.  This is just a hypothesis, but it looks like it is the ISP :)

It's good to see users from all over the world.

---

