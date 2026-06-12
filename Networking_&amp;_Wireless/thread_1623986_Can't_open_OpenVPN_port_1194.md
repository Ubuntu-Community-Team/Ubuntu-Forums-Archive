---
title: "Can't open OpenVPN port 1194"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by majjj on 2010-11-17
Hi!

I was hoping that someone here could help me.
So, I've installed and configured OpenVPN on Ubuntu server 10.04, but I can't connect to it. When i try connecting from another ubuntu machine it's "connection attempt timed out" and i can't seem to fix it. I think the problem is that port 1194 (which i've configured openvpn to use) isn't open. I've created iptables rules, but no luck. 

Here are the rules:
```
sudo iptables -L -nv
Chain INPUT (policy ACCEPT 1033K packets, 58M bytes)
 pkts bytes target     prot opt in     out     source               destination         
    9   384 fail2ban-postfix  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           multiport dports 25,465 
   42  1708 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:1194 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:1194 


```When I run:
```
sudo nmap -sU -p 1194 localhost

Starting Nmap 5.00 ( http://nmap.org ) at 2010-11-17 17:31 EET
Interesting ports on localhost (127.0.0.1):
PORT     STATE  SERVICE
1194/udp closed unknown

Nmap done: 1 IP address (1 host up) scanned in 0.20 seconds


```I also tried to see using```
 sudo netstat -tulnp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
...
udp        0      0 192.168.1.45:1194       0.0.0.0:*                           7837/openvpn    
...

```It should be running:```

$ sudo /etc/init.d/openvpn start
 * Starting virtual private network daemon(s)...                                                                                                                         *   Autostarting VPN 'server' 

```Can you **please** help me. I've tried searching everywhere for the answer but no luck.

---

### Post by uncaspi on 2010-11-17
Have you enabled iptables and rebooted? also check ufw status

---

### Post by majjj on 2010-11-17
> **uncaspi said:**
> Have you enabled iptables and rebooted? also check ufw status

I don't know if ufw was enabled but it is now. I also rebooted but nothing seems to have changed. Port still seems to be closed. (How do I check if iptables is enabled, because there's no /etc/init.d/iptables)

Any thoughts?

---

### Post by SeijiSensei on 2010-11-17
Try setting net.ipv4.ip_forward to 1 in /etc/sysctl.conf.  You're probably being blocked because Ubuntu by default doesn't permit forwarding between interfaces.

You can do a quick test by running 

```
sudo echo '1' > /proc/sys/net/ipv4/ip_forward
```

and see if that fixes the problem.  To make the fix permanent, you need to change the entry in sysctl.conf and reboot.

---

### Post by majjj on 2010-11-17
> **SeijiSensei said:**
> 
```
sudo echo '1' > /proc/sys/net/ipv4/ip_forward
```

Tried to do it, but it said "Permission denied"?! Then I changed it in the configuration file like you suggested, rebooted, but it doesn't seem to have made any difference. 

Syslog shows now though 
```
Nov 17 20:00:00 ubuntuserver ovpn-server[4396]: TLS Error: cannot  locate HMAC in incoming packet from [AF_INET]192.168.1.37:54934
```But when I try to connect outside my lan (android) it doesn't show any logs. I have port forwarding and firewall on my router set up so that should be fine.

---

### Post by majjj on 2010-11-17
YEAH! It finally works. The problem was that for some reason port 1194 didn't work. I changed it to 1193.

And for the > Nov 17 21:14:39 ubuntuserver ovpn-server[2655]: TLS Error: cannot locate HMAC in incoming packet from error i disabled ```
#tls-auth ta.key 0 # This file is secret
``` which caused the error. I will probably will have to just configure it also for my client so that it will work. For now though it's fixed I got connection to VPN

---

