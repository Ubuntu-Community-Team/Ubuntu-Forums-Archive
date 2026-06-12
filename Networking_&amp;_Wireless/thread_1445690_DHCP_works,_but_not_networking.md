---
title: "DHCP works, but not networking?"
date: 2010-04-02
forum: Networking &amp; Wireless
---

### Post by hevnsnt on 2010-04-02
Hey all, 

Recently my headless ubuntu NAS "fell off" the network and I can use determining exactly what happened.  I am not sure at this point if it is a hardware or software issue.

Ip address: 192.168.1.100 (Statically assigned)

Plugged in a monitor and keyboard, and pulled up a console and attempted to ping the default gateway, with 100% packet loss.  Then tried to ping another host (.66) on the network (actually on the same switch) same result.  Tried to resolve a host on the internet (nslookup google.com) fail.

First thing first, restarted networking:
```
/etc/init.d/networking restart
```

Attempted same ping tests, same result.

Next I replaced the network cable with a new one.  Attempted same ping tests, same result.

Next I went to .66 and attempted to see if it could see .100.  Using nmap I did a:
```
sudo nmap -A 192.168.1.100
```
and I got a surprising result:

```
macbook:nmap-5.30BETA1 hevnsnt$ sudo nmap -A 192.168.1.100

Starting Nmap 5.21 ( http://nmap.org ) at 2010-04-02 20:23 CDT
Nmap scan report for linuxbox (192.168.1.100)
Host is up (0.0020s latency).
All 1000 scanned ports on linuxbox (192.168.1.100) are filtered
MAC Address: 00:DE:AD:BE:EF:29 (Asiarock Incorporation)
Too many fingerprints match this host to give specific OS details
Network Distance: 1 hop

HOP RTT     ADDRESS
1   1.96 ms linuxbox (192.168.1.100)

OS and Service detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 24.86 seconds

```

hmm.. it is up, but all ports are filtered, and I cant ping it.  Remember this was my NAS, it had multiple Samba shares, VNC port, and a few other hosted services.

Frustrated, I wondered if maybe I was getting some cached results or something, So I changed .100 (the one in question) to dhcp by editing my /etc/network/interfaces.  I then configured my router to give my MAC address a defined dhcp address (.101), and then restarted networking.

Guess what, it pulls a DHCP address just fine (it is now 192.168.1.101) so I repeat 100% of all the tests above, 100% same result.  ARRRGH.  Ok, fine, Lets try the Microsoft solution.  I restarted the whole box.  Repeated 100% all tests, guess what.... Same result.

Maybe my route is jacked?
```
route del *
```

100% same results.  Can anyone think of anything else to try?  I really need to get my NAS back up, my kids are screaming for their movies :)

---

### Post by hevnsnt on 2010-04-03
Anyone have any clue

---

### Post by chili555 on 2010-04-03
> /etc/networking/interfacesI hope it's /etc/network/interfaces. May we have a peek?

---

### Post by hevnsnt on 2010-04-03
Whoops, of course you are correct.. 

--Begin /etc/network/interfaces--
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
#address 192.168.1.100
#netmask 255.255.255.0
#gateway 192.168.1.254

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp
```
--end /etc/network/interfaces--

---

### Post by chili555 on 2010-04-03
If you are sure that x.254 is the router, and not x.1 or some such, I'd suggest cleaning up interfaces to:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.254
```All those other lines are in interfaces as placeholders for a new install. I am not sure they hurt, but they sure do slow down the boot. Then do:```
sudo ifdown eth0 && sudo ifup eth0
ifconfig
ping -c3 www.google.com
```

---

