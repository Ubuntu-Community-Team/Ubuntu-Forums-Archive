---
title: "Ubuntu 11.04 + Cisco VPN - can't access remote network IPs"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by pgagnon on 2011-07-08
Hi,

I have just installed Ubuntu 11.04 and the Cisco VPN client with : 

apt-get install network-manager-vpnc 
I have imported the PCF provided by my employer into the GUI. The group password also seems ok, when I login to the VPN server, I am provided with the "VPN Login message". (On Windoze, I get an Ok/Cancel popup with the same message). In Ubuntu, I don't get to click "Ok" but it looks like I'm connected properly.

The /var/log/syslog file contains numerous static routes added, 30 or so. After the Login Message, I see the couple of line: 

Jul  8 12:40:51 ubuntu02 vpnc[1613]: can't open pidfile /var/run/vpnc/pid for writing
Jul  8 12:40:52 ubuntu02 NetworkManager[630]: <info> VPN connection 'VPN to my network' (IP Config Get) complete.

I get an IP from the external network correctly as well:

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:172.16.10.170  P-t-P:172.16.10.170  Mask:255.255.255.0


However, I cannot ping any of the machine on the remote network. None of the network services seems to be accessible. For what I read, it could be a routing problem but I don't know how to resolve it.

Could someone have an answer on why the machines on the VPN are not accessible?

I'm a newbie to Linux, apologies in advance if any other useful information could have been provided.

Cheers.

---

### Post by pgagnon on 2011-07-08
To add to say, my kernel version is: 2.6.38-8-generic, if helps

---

### Post by Nic Botha on 2011-07-21
Have you figured out what the problem was?

Thanks
Nic

---

### Post by d4m1r on 2011-11-22
Had this same issue....I tried everything but I was not able to connect to my work PC for 4-5 days.

Trying googling "resolv.conf" or lookup how to use vpnc by command line. I am not sure what fixed the issue (IT guy did send out an email out to the office saying he would restart the firewall because it was acting up) but 1 day it started working via the command line so I used it that way to avoid breaking anything and now I am back to using VPNC under Network Manager...

---

