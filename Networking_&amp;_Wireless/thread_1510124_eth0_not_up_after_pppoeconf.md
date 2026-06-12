---
title: "eth0 not up after pppoeconf"
date: 2010-06-15
forum: Networking &amp; Wireless
---

### Post by neeraj-vaidya on 2010-06-15
I recently installed Lucid 10.04 on a P-IV desktop. The install went extremely smooth and Ubuntu was up and running. Hats off to the Ubuntu folks for the excellent user-friendly experience in the installation process. However , I have run into a networking issue.
 
I connected my PC to the router issued by my ISP. This is a plug-n-play type of connection where the username/password settings are stored in the router and there is no configuration required in Ubuntu for accessing the internet. All I need to do is connect the router and my PC using the LAN cable. I was able to surf the net without any issues.
 
A few days later , this ISP service was down and hence I switched to another wired ISP. This ISP required me to dial a connection using another supplied router. I setup the connection using pppoeconf where I was asked to enter username/password. Again I was able to surf the internet without any issues. 
 
Next , I shutdown the system and before booting it , I switch back to my original ISP connection (the plug-n-play one). 
But now I am not able to connect to the internet. The router lights show that my PC is connected to it , but when I issue ping 192.168.1.1 to check connectivity with the router configuration, I get 
```
 
$ ping 192.168.1.1
connect : Network is unreachable.

```Also , issuing ifconfig does not show eth0.
NM-applet also does not appear in my notification panel at the top.
 
Can someone shed some light on how I can go back to using my original plug-n-play ISP connection ? I have read some posts about networking issues , but none quite like this one. Please note that all my Internet connections are Wired connections.
 
Here is my interfaces file 
```
 
$ cat /etc/network/interfaces
 
auto lo
iface lo inet loopback
 
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider
 
auto eth0
iface eth0 inet manual

```

---

### Post by dineshs on 2010-06-15
Please try this
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```
and set
```
managed=true
```
Restart the machine and configure NM in DHCP mode
> This ISP required me to dial a connection using another supplied router. I setup the connection using pppoeconf where I was asked to enter username/password
Configure NM via the DSL tab (avoid pppoeconf)

---

### Post by neeraj-vaidya on 2010-06-15
Should I also change this line in /etc/network/interfaces 
 
from
```
 
iface eth0 inet manual

```
 
to
```
iface eth0 inet dhcp
```
 
This is something I read in another post by a member called Detonate.
 
Can you possibly list the steps for configuring NM in DHCP mode ?
 
Also , will these cnfigurations steps you mentioned in your post ,  allow me to connect any of the ISPs ?
 
Thanks!

---

### Post by dineshs on 2010-06-15
Let us first edit* /etc/NetworkManager/nm-system-settings.conf* alone then restart
> Can you possibly list the steps for configuring NM in DHCP mode ?
Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection you want and click edit(you can add the ethernet connection if not listed) 
select ipv4 
method-automatic DHCP
then click apply 
Now try to ping your router

---

### Post by hamid2c on 2010-08-29
Hi,

I think, pppoeconf adds your eth to  /etc/network/interfaces so it no longer gets managed by Network Manager. 
IMHO and from [https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient) you can see that is safe to reduce your /etc/network/interfaces file to the first 2 lines so the Network Manager gets control over it again.

"
 [NetworkManager]("https://help.ubuntu.com/community/NetworkManager")  only allows VPN connections if it is currently managing a connection.   If your network interface is manually configured (in the Network  Administration Tool under System/Administration) or in **/etc/network/interfaces**), it is not managed by [NetworkManager]("https://help.ubuntu.com/community/NetworkManager").   If the option for VPN connections is greyed out, [NetworkManager]("https://help.ubuntu.com/community/NetworkManager") is not managing a connection.  Remove the connections from the Network Administration Tool, or manually edit **/etc/network/interfaces**.  For a general case, it is safe to backup the interfaces file, and reduce its to only contain 
```

auto lo
iface lo inet loopback

```"

> **neeraj-vaidya said:**
> I recently installed Lucid 10.04 on a P-IV desktop. The install went extremely smooth and Ubuntu was up and running. Hats off to the Ubuntu folks for the excellent user-friendly experience in the installation process. However , I have run into a networking issue.
 
I connected my PC to the router issued by my ISP. This is a plug-n-play type of connection where the username/password settings are stored in the router and there is no configuration required in Ubuntu for accessing the internet. All I need to do is connect the router and my PC using the LAN cable. I was able to surf the net without any issues.
 
A few days later , this ISP service was down and hence I switched to another wired ISP. This ISP required me to dial a connection using another supplied router. I setup the connection using pppoeconf where I was asked to enter username/password. Again I was able to surf the internet without any issues. 
 
Next , I shutdown the system and before booting it , I switch back to my original ISP connection (the plug-n-play one). 
But now I am not able to connect to the internet. The router lights show that my PC is connected to it , but when I issue ping 192.168.1.1 to check connectivity with the router configuration, I get 
```
 
$ ping 192.168.1.1
connect : Network is unreachable.

```Also , issuing ifconfig does not show eth0.
NM-applet also does not appear in my notification panel at the top.
 
Can someone shed some light on how I can go back to using my original plug-n-play ISP connection ? I have read some posts about networking issues , but none quite like this one. Please note that all my Internet connections are Wired connections.
 
Here is my interfaces file 
```
 
$ cat /etc/network/interfaces
 
auto lo
iface lo inet loopback
 
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider
 
auto eth0
iface eth0 inet manual

```

---

