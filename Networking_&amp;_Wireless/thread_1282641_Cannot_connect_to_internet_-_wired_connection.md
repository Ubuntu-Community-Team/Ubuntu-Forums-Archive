---
title: "Cannot connect to internet - wired connection"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by rvdb86 on 2009-10-04
Hi, I am a newbie and was hoping someone can help.
I have a HP pavilion dv800 laptop and i recently installed ubuntu server on it. Everything is going well except for the internet.

I have a static IP with 2 DNS servers.
I setup my IP address and the default gateway in /etc/network/interfaces 
and the name servers in /etc/resolv.conf

the resolv.conf file has the following entries:
nameserver 212.117..
nameserver 212.117...

still I can't seem to be able to connect to the LAN/internet.

I would really appreciate any suggestions!

---

### Post by ermeyers on 2009-10-04
What did you put in /etc/network/interfaces?

---

### Post by jward3010 on 2009-10-04
Have you the cable plugged in both ends. I know it's hilarious but you're not even able to talk to your LAN!

---

### Post by Iowan on 2009-10-04
Does **ifconfig -a** show an IP address for the interface?

---

### Post by ermeyers on 2009-10-04
Just "ifconfig" will show all interfaces, and "ifconfig eth0" will show just eth0, etc.  Give me a "cat /etc/network/interfaces".

---

### Post by rvdb86 on 2009-10-05
Here is what i put into /etc/network/interfaces:

address 192.168.11.31
netmask 255.255.255.0
network 192.168.11.0
broadcast 192.168.11.255
gateway 192.168.11.1

I did check that the cable was connect.. twice.. before i posted :)
And yes ifconfig eth0 shows the ip that i set in the interfaces.

Thanks for taking the time and i hope i have provided enough information!

---

### Post by kevdog on 2009-10-05
I dont think you need the network line personally.  can you ping the router?

---

### Post by ermeyers on 2009-10-05
> **rvdb86 said:**
> Here is what i put into /etc/network/interfaces:

address 192.168.11.31
netmask 255.255.255.0
network 192.168.11.0
broadcast 192.168.11.255
gateway 192.168.11.1

Does your /etc/network/interfaces look like this:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
   address 192.168.11.31
   netmask 255.255.255.0
   network 192.168.11.0
   broadcast 192.168.11.255
   gateway 192.168.11.1


```

---

### Post by ermeyers on 2009-10-05
Please describe how your router is connected to the WAN/internet.  Is 192.168.11.1 your router/gateway, and can you ping it and anything else connected to your LAN?  Depending on the type of router you have, you may be able to set those DNS server numbers in it, and use "nameserver 192.168.11.1".

---

### Post by jward3010 on 2009-10-05
The only thing I'm thinking now is that the networking service is not set to use those settings, but I assume you've restarted since you've talked to us. If not run:
```
sudo /etc/init.d/networking restart
```

---

### Post by rvdb86 on 2009-10-05
The problem is the server i am trying to set up is in an organization and I do not have direct access to the router.

The whole idea is just to have a local webserver for development purposes, however i cannot get and install apache2, mysql or php5 without access to the internet. Maybe there is another way to install these packages without an internet connect, like saving them to a disk or usb stick?

thanks for your time!

---

### Post by urugTON on 2009-10-05
Would you show us the results of 

```
ping 127.0.0.1
```

Then please do as jward3010 asked you to do.  Give us the results of:

```

ping 192.168.11.1

```

After you do that, please let us know the results of:

```
arp -n -v 
```

---

### Post by jward3010 on 2009-10-05
> **rvdb86 said:**
> The problem is the server i am trying to set up is in an organization and I do not have direct access to the router.

The whole idea is just to have a local webserver for development purposes, however i cannot get and install apache2, mysql or php5 without access to the internet. Maybe there is another way to install these packages without an internet connect, like saving them to a disk or usb stick?

thanks for your time!
Dude, you may need to set up a proxy info.

Are there any other Windows / working machines in there, that you can check proxy configuration on. Do that by going into Internet Explorer > Tools > Internet Options > Connections and proxy stuff should be somewhere around there.

---

### Post by rvdb86 on 2009-10-05
> **urugTON said:**
> Would you show us the results of 

```
ping 127.0.0.1
```


The result was extremely long like this:
```
64 bytes from 127.0.0.1: icmp_seq=780 ttl=64 time=0.044 ms
64 bytes from 127.0.0.1: icmp_seq=781 ttl=64 time=0.044 ms
64 bytes from 127.0.0.1: icmp_seq=782 ttl=64 time=0.044 ms
...
64 bytes from 127.0.0.1: icmp_seq=1081 ttl=64 time=0.044 ms

```
After icmp_seq=1090 i got impatient and stopped the ping

> **urugTON said:**
> 
Then please do as jward3010 asked you to do.  Give us the results of:

```

ping 192.168.11.1

```


Same sequence of results for ping 192.168.11.1 however the host was unreachable:

```
From 192.168.11.241: icmp_seq=121 ttl=64 Destination Host Unreachable
From 192.168.11.241: icmp_seq=780 ttl=122 Destination Host Unreachable
From 192.168.11.241: icmp_seq=780 ttl=123 Destination Host Unreachable
...
From 192.168.11.241: icmp_seq=780 ttl=1193 Destination Host Unreachable

```

> **urugTON said:**
> 
After you do that, please let us know the results of:

```
arp -n -v 
```
[/QUOTE]

here are the results:
```

Address         HWtype  HWaddress         Flags Mask   Iface
192.168.11.1            (incomplete)                   eth0
192.168.11.159  ether   00:19:d1:aa:3e:b3  C           eth0
Entries:2   Skipped: 0  Found: 2

```
[/CODE]

---

### Post by jward3010 on 2009-10-05
Thanks for that info.

Sorry we all should have recommended you do ping with a count number like so:
```
ping -c 3 192.168.11.1
```
That would have just pinged the particlular client 3 times max. I think I mentioned it but far back in previous posts.

Couple of things here.
1. Your IP seems in fact seems to be 192.168.11.241, not .31. Please post the output of ```
ifconfig -a
``` 
This is way more important than "cat /etc/network/interfaces" as it proves the IP is actually set correctly which it doesn't seem to be.

2. Your arp table is showing something interesting, it's not able to get the hardware address of the router "(incomplete)". Maybe try a restart of your server and the router.
3. Can you run ipconfig /all (Windows) / ifconfig -a (Linux) from a functioning machine and post it here. We'll see the exact network details from that.

---

### Post by rvdb86 on 2009-10-05
> **jward3010 said:**
> 
1. Your IP seems in fact seems to be 192.168.11.241, not .31. Please post the output of ```
ifconfig -a
``` 
This is way more important than "cat /etc/network/interfaces" as it proves the IP is actually set correctly which it doesn't seem to be.
[/QOUTE]

ok here it is:

```
th0      Link encap:Ethernet  HWaddr 00:16:d4:07:b5:0f
          inet addr:192.168.11.241  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe07:b50f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1631 errors:0 dropped:0 overruns:0 frame:0
          TX packets:233 errors:0 dropped:0 overruns:0 carrier:0
          collisions:10 txqueuelen:1000
          RX bytes:117585 (117.5 KB)  TX bytes:31375 (31.3 KB)
          Interrupt:22 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1308 (1.3 KB)  TX bytes:1308 (1.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:a2:a5:f6
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-A2-A5-F6-00-00-00-00-00-00-00-00-00-00
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


[QUOTE=jward3010;8057308]
2. Your arp table is showing something interesting, it's not able to get the hardware address of the router "(incomplete)". Maybe try a restart of your server and the router.


like i said before i dont have access to the router and defiantly cant do a reset

> **jward3010 said:**
> 
3. Can you run ipconfig /all (Windows) / ifconfig -a (Linux) from a functioning machine and post it here. We'll see the exact network details from that.

here we go:
```
Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Realtek RTL8168/8111 Family PCI-E Gigabit
 Ethernet NIC (NDIS 6.0)
   Physical Address. . . . . . . . . : 00-19-D1-AA-3E-B3
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::428:5aeb:4a64:30f3%8(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.11.159(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.11.1
   DNS Servers . . . . . . . . . . . : 212.117.129.3
                                       212.117.129.6
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter Local Area Connection* 6:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : isatap.{BFFD586D-3DDF-49C0-B70F-D63CE24C2
892}
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::5efe:192.168.11.159%9(Preferred)
   Default Gateway . . . . . . . . . :
   DNS Servers . . . . . . . . . . . : 212.117.129.3
                                       212.117.129.6
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter Local Area Connection* 7:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 02-00-54-55-4E-01
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:4137:9e50:2c57:37ad:c17f:cf7d(Pref
erred)
   Link-local IPv6 Address . . . . . : fe80::2c57:37ad:c17f:cf7d%10(Preferred)
   Default Gateway . . . . . . . . . : ::
   NetBIOS over Tcpip. . . . . . . . : Disabled
```

hope this helps

---

### Post by jward3010 on 2009-10-05
An obvious question to ask - can that Vista machine get out on the internet without any problems?

OK, your server definitely has an IP of ".241" and not ".31" as set in "interfaces". Try pinging 192.168.11.31 to see if it's already used:
```
ping -c 3 192.168.11.31
```
If you get successful replies there's already a machine on the network with that address and you can't use it. Maybe even put something different in /etc/network/interfaces now and see if you can get to the internet.

So:
```
sudo nano /etc/network/interfaces
```
Change the IP section to something different. Use Ctrl+X to save and exit from nano.

```
sudo /etc/init.d/networking restart
```
Restarts networking services and use the new IP settings. Mandatory step.

```
ping -c 3 208.67.222.222
```
This will test internet connectivity, this is the IP address of a well known DNS server.

```
ping -c 3 resolver1.opendns.com
```
```
ping -c 3 www.irishtimes.com
```
This is the ultimate test, if these reply then your resolv.conf file is set correctly and DNS is working. Thats pretty much all you need for a fully functioning internet connection.

---

### Post by urugTON on 2009-10-06
Actually, I think the problem is the ipconfig /all line that says: "Autoconfiguration enabled: yes".

Details are at [http://support.microsoft.com/kb/220874](http://support.microsoft.com/kb/220874)

The long and short of it is that Microsoft can assign IP addresses dynamically without DHCP.  Note the "DHCP enabled: no"

I don't see a way that Ubuntu can play nice with MS's IP address assignment scheme.  My searches have been fruitless.  OTOH, I've never even heard of the fool thing until a few minutes ago.

I don't know where to go with this.  Maybe rvdb86 can beg and grovel to the network admin for a static IP address.

---

### Post by rvdb86 on 2009-10-06
Hey thanks for the replies!

First urugTON, I do have a static ip.

jward3010, I changed my ip in the interfaces file and tried to ping 
208.67.222.222 and it said that the host cannot be found.

The vista computer does connect to the internet (it's the one im using to post these messages).

---

### Post by jward3010 on 2009-10-06
> **urugTON said:**
> Actually, I think the problem is the ipconfig /all line that says: "Autoconfiguration enabled: yes".

Details are at [http://support.microsoft.com/kb/220874](http://support.microsoft.com/kb/220874)

The long and short of it is that Microsoft can assign IP addresses dynamically without DHCP.  Note the "DHCP enabled: no"

I don't see a way that Ubuntu can play nice with MS's IP address assignment scheme.  My searches have been fruitless.  OTOH, I've never even heard of the fool thing until a few minutes ago.

I don't know where to go with this.  Maybe rvdb86 can beg and grovel to the network admin for a static IP address.

What this talks about is APIPA, a fallback addressing system if a DHCP server goes down, this is unrelated to to Vista machine as it has a correct address (a 192.168... address). Say 400 machines in an organisation switch themselves on at 8:45 to 9:00AM in the morning but the DHCP server crashed earlier in the morning and is not around to give out addresses. After a number of attempts the machines will realise that there is no DHCP server and set themselves up with a random 169.254.XXX.XXX/16 IP address. After a couple of minutes they'll all be on the same network even if theres no DHCP server about. They won't necessarily have internet access as the internet routers will be on the correct subnet (different from the APIPA one, as they havwe static addresses) but they'll be able to talk to each other.

---

### Post by jward3010 on 2009-10-06
The only last things I can recommend are:
```
sudo ifconfig eth0 up
``` and then try a ping of the router.

Have you restarted the server yet, I'm hoping this fills the arp tables correctly. 

If you have restarted post again the output of:
```
arp -v -n
```

Then:
```
route -n
```

Most importantly try a ping of...
```
ping -c 3 192.168.11.159
```
This will confirm your able to send packets and the network driver is definitely working.

Sorry for all the command requests but as much info as I can get will help us figure what the fudge is going on.

If worst comes to worst we'll get the MAC address of the router from the Vista PC and set up a manual entry in your arp table, but first those above things. It's really weird that the Ubuntu box can't get the MAC address of the router.

---

### Post by jward3010 on 2009-10-06
Here's a weird one to bring up, if you're ping replies to 192.168.11.159 (the Vista machine) don't bring up anything then ask yourself the question: Am I plugged into the same switch as the rest of the network?

---

### Post by rvdb86 on 2009-10-06
Ok so heres some strange information.

First of all, I am accessing the server from the vista computer using PuTTY and the ip address 192.168.11.239, so it must be connected to the network and the network device is working.

However when I ping the vista computer I get the following result:
```
PING 192.168.11.159 (192.168.11.159) 56(84) bytes of data.

--- 192.168.11.159 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2002ms
```

here is the result of arp -v -n:
```
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.11.1             ether   00:0e:7f:7d:b2:c8   C                     eth0
192.168.11.159           ether   00:19:d1:aa:3e:b3   C                     eth0
Entries: 2      Skipped: 0      Found: 2
```

---

### Post by jward3010 on 2009-10-06
You have the WEIRDEST network problem I have ever seen.

I seriously doubt a firewall is switched on:
```
sudo iptables -L
```
and give us output.

Although to be fair the Vista machine could have a firewall setup not to reply to ping requests, thats not unusual with modern AV and firewall combined apps like Norton Internet Security and other cr@pology like that. I'll think on it.

Something useful for troubleshooting network problems is a program called nmap. See if you have it installed by typing:
```
sudo apt-get install nmap
```
If it's there it will tell you "Current version already installed".

---

### Post by rvdb86 on 2009-10-07
results for sudo iptables -L
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```


Results for sudo apt-get install nmap
```
ronny@c4w:~$ sudo apt-get install nmap
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package nmap
```

I think i am going to abandon ubuntu and install CentOS, maybe i will have more luck with that :(

---

### Post by jward3010 on 2009-10-08
OK, nmap is not installed.

Maybe before you rid yourself of Ubuntu, do you have a standard live CD around, one with Ubuntu desktop on it. It might be worth running a live one to see if it has the same problems - if yes, you're network is acting the dick somewhere, if not, something was wrong with server or configuration somewhere or possibly even a bug.

Live CD's have great network support especially on wired and it's easy to configure network-manager for DHCP or manual. You'll know instantly whether theres a problem or not.

---

