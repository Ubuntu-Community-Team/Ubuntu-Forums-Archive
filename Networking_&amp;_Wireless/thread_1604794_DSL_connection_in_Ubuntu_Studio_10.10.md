---
title: "DSL connection in Ubuntu Studio 10.10"
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by lymphor on 2010-10-24
Hi everyone,
I just installed **Ubuntu Studio 10.10** and having problems connecting to the internet.
In Ubuntu 10.04 I had to go to **VPN Connections** and in the **DSL** tab enter **username**, **password** and **name of the provider**.
In Ubuntu Studio 10.10 I just can't find VPN connections or DSL tab.
Could you please help me?
Thx!

---

### Post by dineshs on 2010-10-25
> In Ubuntu 10.04 I had to go to VPN Connections and in the DSL tab enter username, password and name of the provider.This statement is not clear.If network manager is not installed (I think NM is not installed by default in ubuntu studio)Please try if this works
Configure DSL connection using```
sudo pppoeconf
```
to connect use```
pon dsl-provider
```and to disconnect```
poff dsl-provider
```
more info [here]("https://help.ubuntu.com/community/ADSLPPPoE")

---

### Post by lymphor on 2010-10-26
Thank you,
I used **sudo pppoeconf** command and managed to connect to the internet but I'm having SERIOUS problems connecting to many sites (like yahoo, youtube and many others).
I receive a message like my internet connection is down. In yahoo I can enter the main page but I cannot access the mail page. The only site always working so far is Facebook. The other ones work once in a while.
I tried using another browser (Chromium) but nothing changed.
I thought it's a problem of my provider but in Windows the same connection-provider works fine.
I also installed the network manager in Ubuntu Studio and configured my DSL connection but the network manager says this connection it has never been used :confused:
Is there anything I could do? #-o
Thank you in advance for your support :)

---

### Post by dineshs on 2010-10-27
Can you post the output of ```
sudo gedit /etc/ppp/peers/dsl-provider
```

---

### Post by lymphor on 2010-10-28
Sure
(I just modified the text here on the forum changing my real username with the generic term **username**):
 
 
```
 
# Minimalistic default options file for DSL/PPPoE connections 
 
 
noipdefault 
defaultroute 
replacedefaultroute 
hide-password 
#lcp-echo-interval 30 
#lcp-echo-failure 4 
noauth 
persist 
#mtu 1492 
#persist 
#maxfail 0 
#holdoff 20 
plugin rp-pppoe.so eth0 
usepeerdns 
user "username"

```
 
I also added a zip with the screenshots regarding the procedure of configuring my internet connection :)

---

### Post by dineshs on 2010-10-28
1)I understand that you have 2 ethernet cards and DSL is connected to eth0.Please confirm.Are you using both ethernet ports?
2)Please post the contents of ```
sudo gedit /etc/network/interfaces
```
3)What do you get for ```
ping 4.2.2.1 -c3
```after connecting

---

### Post by lymphor on 2010-10-28
> **dineshs said:**
> 1)I understand that you have 2 ethernet cards and DSL is connected to eth0.Please confirm.Are you using both ethernet ports?
No I'm not using both ethernet but I don't know to which one is DSL connected #-o:)
Here is what you asked, thanks:
 
**sudo gedit /etc/network/interfaces**
```
 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
 
 
# The loopback network interface
auto lo
iface lo inet loopback
 
 
iface ppp0 inet ppp
provider ppp0
 
 
auto ppp0
 
 
 
 
iface eth1 inet dhcp
 
 
auto eth1
 
 
 
 
iface eth0 inet dhcp
 
 
auto eth0
 
 
auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

```
 
**ping 4.2.2.1 -c3**
```

 
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data. 
64 bytes from 4.2.2.1: icmp_req=1 ttl=244 time=39.6 ms 
64 bytes from 4.2.2.1: icmp_req=2 ttl=244 time=39.7 ms 
64 bytes from 4.2.2.1: icmp_req=3 ttl=244 time=39.3 ms 
 
 
--- 4.2.2.1 ping statistics --- 
3 packets transmitted, 3 received, 0% packet loss, time 2003ms 
rtt min/avg/max/mdev = 39.355/39.593/39.774/0.175 ms 

```
 
I'm also adding some screenshots with additional info that might be useful.

---

### Post by utilitytrack on 2010-10-28
**lymphor**

Please tell it's you made changes in **/etc/network/interfaces** file, or you didn't touch it? Simply interesting. Thanks.

---

### Post by lymphor on 2010-10-28
I did not touch **/etc/network/interfaces** file.
Why are you asking? :)

---

### Post by utilitytrack on 2010-10-28
Ok, I realized that you changed it through NetworkManager.

---

### Post by dineshs on 2010-10-28
_Method-I_
Please try this
First backup  /etc/network/interfaces using
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```
Now run
```
 gksudo gedit /etc/network/interfaces
```
Let the file contain only these lines (delete all other lines)```
auto lo
iface lo inet loopback
```
Restart machine
Try to connect using the DSL connection configured via NM (Click NM icon on right top of the panrl and click RDS to connect)
_Method-II_
If you have problems disconnect RDS (the DSL connection configured in NM) and run ```
sudo pon dsl-provider
```to connect
Please let us know the results.
by the way,Do you have use a DSL modem?

---

### Post by lymphor on 2010-10-29
> **dineshs said:**
> _Method-I_
Please try this
First backup  /etc/network/interfaces using
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```Now run
```
 gksudo gedit /etc/network/interfaces
```Let the file contain only these lines (delete all other lines)```
auto lo
iface lo inet loopback
```Restart machine
Try to connect using the DSL connection configured via NM (Click NM icon on right top of the panrl and click RDS to connect)

It worked! \\:D/ 
Thank you VERY VERY VERY MUCH!
Can I ask what was my problem? :-)

> **dineshs said:**
> 
by the way,Do you have use a DSL modem?

No, I'm directly connected trough LAN.

---

### Post by dineshs on 2010-10-29
If you are using Network manager or pppoeconf your /etc/network/interfaces should only contain those 2 lines
Please mark the thread as solved via thread tools

---

### Post by lymphor on 2010-10-29
Ok, thank you again ):P

---

