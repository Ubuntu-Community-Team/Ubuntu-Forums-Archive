---
title: "Network-Manager Connects to DSL but no real internet connection!"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by ario on 2010-11-01
I used to use **pon dsl-provider** to connect to Internet. As a sin I decided to use network-manager to do this. It connects to recently created connection "DSL Connection 1" successfully. I mean it shows me that it's connected. I can see this in output of ifconfig command:
```
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:89.165.81.243  P-t-P:89.165.81.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:54 (54.0 B)  TX bytes:54 (54.0 B)

```
But I cannot connect to any site. I can not ping any site. Output of plog command is empty. It is not really connected. It just feigns it!
I can use the same username and password in pppoeconf to connect and no problem. Problem is only with network-manager.
Any Idea?

---

### Post by dineshs on 2010-11-01
> ppp0      Link encap: Point-to-Point Protocol  
          inet addr:89.165.81.243  P-t-P:89.165.81.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:54 (54.0 B)  TX bytes:54 (54.0 B)This means you are connected.I think it is a DNS issue.Please run
```
ping 4.2.2.1 -c5
```If there is reply,Rightclick NM icon on right top of the panel- click edit connections-click DSL tab-select DSL connection -edit-ipv4-select Automatic PPPoE addresses only-Give DNS as [COLOR="Blue"]4.2.2.1[/COLOR] and apply.Now run
```
sudo service network-manager stop
```and
```
sudo service network-manager start
```
Connect DSL (click NM click DSL connection) and see if pages are loading

---

### Post by ario on 2010-11-02
> **dineshs said:**
> This means you are connected.I think it is a DNS issue.Please run
```
ping 4.2.2.1 -c5
```First connected trough DSL Connection 1 of network-manager applet. Then pinged [www.google.com](www.google.com) but as I guessed before there was no reply. Then tried that. The result was:
```
 ping 4.2.2.1 -c5
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
^C
--- 4.2.2.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2008ms


```> If there is reply,Rightclick NM icon on right top of the panel- click edit connections-click DSL tab-select DSL connection -edit-ipv4-select Automatic PPPoE addresses only-Give DNS as [COLOR="Blue"]4.2.2.1[/COLOR] and apply.Now run
```
sudo service network-manager stop
```and
```
sudo service network-manager start
```
Connect DSL (click NM click DSL connection) and see if pages are loading
Although no reply given by 4.2.2.1 tried above solution but still no success pinging any site like [www.google.com](www.google.com).
Now will turn back all settings and waiting for further response from you.
Thanks.

---

### Post by satish_j on 2010-11-02
Are you using static IP??
What does your /etc/network/interfaces file say for eth0?

---

### Post by dineshs on 2010-11-02
When you are using NM ensure that /etc/network/interfaces contain only```
auto lo
iface lo inet loopback

```So edit the file as above,restart and see if it works[COLOR="Red"](Note:Before editing /etc/network/interfaces save a copy)[/COLOR]
> ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
Do you use firewall?what does 
```
sudo iptables -L
```
say?

---

### Post by ario on 2010-11-03
> **satish_j said:**
> Are you using static IP??
What does your /etc/network/interfaces file say for eth0?

Nop. My IP is dynamic. Each connection attempt a different IP from my ISP.
This is the whole interfaces file:
```
auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

```

---

### Post by ario on 2010-11-03
> **dineshs said:**
> When you are using NM ensure that /etc/network/interfaces contain only```
auto lo
iface lo inet loopback

```So edit the file as above,restart and see if it works[COLOR="Red"](Note:Before editing /etc/network/interfaces save a copy)[/COLOR]Did. No success!> 
Do you use firewall?what does 
```
sudo iptables -L
```
say?
It says:
```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
LOG        all  --  127.0.0.0/8          anywhere            LOG level warning 
DROP       all  --  127.0.0.0/8          anywhere            
ACCEPT     all  --  anywhere             255.255.255.255     
ACCEPT     all  --  anywhere             89.165.81.25        
DROP       all  --  anywhere             ALL-SYSTEMS.MCAST.NET 
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
DROP       all  --  anywhere             ALL-SYSTEMS.MCAST.NET 
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             255.255.255.255     
ACCEPT     all  --  89.165.81.25         anywhere            
DROP       all  --  anywhere             ALL-SYSTEMS.MCAST.NET 
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere            

```

Any idea? Thanks a lot:)

---

### Post by dineshs on 2010-11-03
> policy DROPI think it is a firewall issue.I get```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```Pl see this
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by ario on 2010-11-03
> **dineshs said:**
> I think it is a firewall issue.I get```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```Pl see this
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Thanks a lot. But I cant figure out what exactly I supposed to search the mentioned link for?

---

### Post by dineshs on 2010-11-04
> But I cant figure out what exactly I supposed to search the mentioned link for? Says the iptables -L command output should be *policy ACCEPT* if there is no firewall rules
Do you have firestarter installed?
[This]("https://help.ubuntu.com/community/Firestarter") link says there is a conflict between Firestarter and NetworkManager.

---

### Post by ario on 2010-11-05
> **dineshs said:**
> Says the iptables -L command output should be *policy ACCEPT* if there is no firewall rules
Do you have firestarter installed?
[This]("https://help.ubuntu.com/community/Firestarter") link says there is a conflict between Firestarter and NetworkManager.

Thanks. I will read and read and read that link to find a solution there whenever I have enough time to, but here:
```
:~$ firestarter
The program 'firestarter' is currently not installed.  You can install it by typing:
sudo apt-get install firestarter

```
This shows that firestarter is not installed on my system. I searched ubuntu forums, and find out I'm not the first man who have problem with Network Manager specially the DSL Option!

---

### Post by uncaspi on 2010-11-05
Try to add
ACCEPT all -- anywhere ppp0

in the middle of INPUT section of the iptables file and reboot or restart the network service.

---

### Post by dineshs on 2010-11-06
> I will read and read and read that link to find a solution there whenever I have enough time toEspecially the commands given under the heading _Allowing Established Sessions_ and _Configuration on Startup for NetworkManager_ .
By the way why dont you use pon dsl-provider ?

Thanks

---

### Post by ario on 2010-11-09
> **dineshs said:**
> Especially the commands given under the heading _Allowing Established Sessions_ and _Configuration on Startup for NetworkManager_ .
By the way why dont you use pon dsl-provider ?

Thanks

Got a strange problem here:
[http://ubuntuforums.org/showpost.php?p=10065124&postcount=15](http://ubuntuforums.org/showpost.php?p=10065124&postcount=15)
Some people there told me to use network-manager instead of pon.
Tried network-manager but as mentioned above it has it's own problems!
I appreciate your responses but please for your owns sake try to solve a problem instead of erasing it!
Thanks;)

---

### Post by satish_j on 2010-11-09
> **ario said:**
> 
This is the whole interfaces file:
```
auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet ***manual***

```
Interface eth0 is not up at boot time.Try running foll command first:
```

sudo ifconfig eth0 up

```
and then do "pon dsl-provider"
It should work now.

---

### Post by ario on 2010-11-10
> **satish_j said:**
> Interface eth0 is not up at boot time.Try running foll command first:
```

sudo ifconfig eth0 up

```
and then do "pon dsl-provider"
It should work now.

Sorry dude! ofcource pon works for me even without your mentioned command. My problem is that as I mentioned above to do it in GUI way with network manager.
Thanks.

---

### Post by satish_j on 2010-11-11
> **ario said:**
> Sorry dude! ofcource pon works for me even without your mentioned command. My problem is that as I mentioned above to do it in GUI way with network manager.
Thanks.

whatever the method to access internet,be it command or GUI,did you try running the 'ifconfig' command first ?

---

### Post by ario on 2010-11-16
> **satish_j said:**
> whatever the method to access internet,be it command or GUI,did you try running the 'ifconfig' command first ?

Sorry! Running ifconfig for what?

---

