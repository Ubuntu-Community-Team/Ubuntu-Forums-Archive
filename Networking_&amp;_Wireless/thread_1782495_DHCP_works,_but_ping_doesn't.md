---
title: "DHCP works, but ping doesn't"
date: 2011-06-14
forum: Networking &amp; Wireless
---

### Post by herbielondon on 2011-06-14
I have an Ubuntu 10.04 LTS Server, which has been serving several Windows 7 clients with a Samba fileshare and a local web server fine for several months. We've just bought two extra clients, but decided to go with Ubuntu 10.04 LTS Desktop to save on Windows licensing.

Unfortunately, I cannot get the Ubuntu clients to join the network properly. They seem to pick up an IP address from the Ubuntu server via DHCP, but I cannot ping between the client and the server.

The client ifconfig output is:

```
sysadmin@Whitworth:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 10:78:d2:ef:73:59  
          inet addr:192.168.0.27  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1278:d2ff:feef:7359/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31478 (31.4 KB)  TX bytes:11391 (11.3 KB)
          Interrupt:25 Base address:0x2000 

```

The server has a static IP of 192.168.0.0 and seems to be allocating an IP to the client, but I just can't ping at all. The client also seems to pick up the fileshare by displaying a Windows Network icon in Places, but when I try to open the icon, it returns:
"Unable to mount location".

I've searched for "DHCP works cannot ping" and only get suggestions of turning off the firewall, which I've done (```
sudo ufw disable
```). I've also edited smb.conf (both /usr/share/samba/smb.conf and /etc/samba/smb.conf) to show the correct workgroup name, flushed the IP tables and added wins to the list of /etc/nsswitch.conf ([http://ubuntuforums.org/showthread.php?t=1169149]("http://ubuntuforums.org/showthread.php?t=1169149")), but no joy.

Could somebody please suggest a way forward?

Thanks.

---

### Post by dozycat on 2011-06-14
192.168.0.0 is the address of the subnet. change the server to 192.168.0.1 or another between 1 and 254. 255 is the broadcast address.

---

### Post by capscrew on 2011-06-14
> **herbielondon said:**
> I have an Ubuntu 10.04 LTS Server, which has been serving several Windows 7 clients with a Samba fileshare and a local web server fine for several months. We've just bought two extra clients, but decided to go with Ubuntu 10.04 LTS Desktop to save on Windows licensing.

Unfortunately, I cannot get the Ubuntu clients to join the network properly. They seem to pick up an IP address from the Ubuntu server via DHCP, but I cannot ping between the client and the server.

The client ifconfig output is:

```
sysadmin@Whitworth:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 10:78:d2:ef:73:59  
          inet addr:192.168.0.27  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1278:d2ff:feef:7359/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31478 (31.4 KB)  TX bytes:11391 (11.3 KB)
          Interrupt:25 Base address:0x2000 

```

The server has a static IP of 192.168.0.0 and seems to be allocating an IP to the client, but I just can't ping at all. The client also seems to pick up the fileshare by displaying a Windows Network icon in Places, but when I try to open the icon, it returns:
"Unable to mount location".

I've searched for "DHCP works cannot ping" and only get suggestions of turning off the firewall, which I've done (```
sudo ufw disable
```). I've also edited smb.conf (both /usr/share/samba/smb.conf and /etc/samba/smb.conf) to show the correct workgroup name, flushed the IP tables and added wins to the list of /etc/nsswitch.conf ([http://ubuntuforums.org/showthread.php?t=1169149]("http://ubuntuforums.org/showthread.php?t=1169149")), but no joy.

Could somebody please suggest a way forward?

Thanks.
+1 for what @dozycat said.

The only smb.conf that is use is at /etc/samba/smb.conf.  The othe one is a duplicate for referral only.  I would return it to its virgin state.

Also roll back the modifications to /etc/nsswitch.conf.  There are errors in the howto you are using.

Lets see what you get when you renumber the server or at least find the correct IP address for that host.

---

### Post by herbielondon on 2011-06-15
> **dozycat said:**
> 192.168.0.0 is the address of the subnet. change the server to 192.168.0.1 or another between 1 and 254. 255 is the broadcast address.

Thanks for the rapid response; it worked!

I'm not a networking specialist, as you may have noticed, and did some digging on subnet addressing and came up [with this useful article on subnet zero]("http://www.cisco.com/en/US/tech/tk648/tk361/technologies_tech_note09186a0080093f18.shtml#subnetzero"). I had always wondered why wireless routers always had an address ending in .0.1 or .0.254.

It's safe to say that I've learned my lesson.

Thanks again for your help.

---

### Post by herbielondon on 2011-06-15
> **capscrew said:**
> +1 for what @dozycat said.

The only smb.conf that is use is at /etc/samba/smb.conf.  The othe one is a duplicate for referral only.  I would return it to its virgin state.

Also roll back the modifications to /etc/nsswitch.conf.  There are errors in the howto you are using.

Lets see what you get when you renumber the server or at least find the correct IP address for that host.

Thanks for the admin advice.

---

