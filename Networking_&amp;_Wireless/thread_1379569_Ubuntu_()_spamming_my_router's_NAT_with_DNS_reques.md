---
title: "Ubuntu (?) spamming my router's NAT with DNS requests"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by greebothecat on 2010-01-12
Hey,
First of all, I'm kind of a newbie and don't know much about ubuntu or networks, so it might not be an ubuntu problem at all (though I don't remember anything like this happening on windows xp).

So here's the deal:
I have my pc plugged into local network made of two routers with each own separate DHCP, I plug in the one that's directly connected to a cable DSL modem. Thing is, my Ubuntu is the only one in this 7-piece network that's flooding the router with stuff like this:

```

192.168.1.142:37315	UDP	208.67.222.222:53	61015	23
192.168.1.142:60459	UDP	208.67.222.222:53	61017	23
192.168.1.142:45929	UDP	208.67.222.222:53	61019	23
192.168.1.142:40874	UDP	208.67.222.222:53	61021	23
192.168.1.142:33244	UDP	208.67.222.222:53	61023	23
192.168.1.142:37607	UDP	208.67.222.222:53	61025	23
192.168.1.142:43193	UDP	208.67.222.222:53	61027	23
192.168.1.142:34913	UDP	208.67.222.222:53	61029	23
192.168.1.142:40216	UDP	208.67.222.222:53	61031	23
192.168.1.142:43936	UDP	208.67.222.222:53	61035	23
192.168.1.142:60477	UDP	208.67.222.222:53	61037	23
192.168.1.142:41228	UDP	208.67.222.222:53	61039	23
192.168.1.142:32966	UDP	208.67.222.222:53	61067	54
192.168.1.142:37200	UDP	208.67.222.222:53	61069	54
192.168.1.142:36864	UDP	208.67.222.222:53	61071	54
192.168.1.142:56022	UDP	208.67.222.222:53	61083	75
192.168.1.142:48957	UDP	208.67.222.222:53	61085	75
192.168.1.142:47075	UDP	208.67.222.222:53	61087	76
192.168.1.142:50211	UDP	208.67.222.222:53	61125	160
192.168.1.142:59604	UDP	208.67.222.222:53	61127	160
```

192.168.. is my LAN adress, 208.67.. is the OpenDNS server I'm using instead of my ISP's (I changed it when the bug first occured but it seems it's not DNS's fault). The value after that is NAT and last figure is Time-out value. I've no idea what it could be, tried searching it on google a dozen or so times, nothing.. It's not Ipv6, it's disabled (on Ignore position) in my network settings.

OS: Ubuntu 9.10
Router: D-Link DI-524
I've honestly no idea what other data I should post here..

I'd be grateful for any kind of tip or lead that could help deal with it.

---

### Post by changingstate on 2010-01-13
Have you tried :

```
sudo lsof | grep UDP
```This should tell you which programs are accessing the net from the ubuntu machine and on which ports, using the UDP protocol.

---

### Post by greebothecat on 2010-01-13
did that, showed up:
```
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/greebo/.gvfs
      Output information may be incomplete.
avahi-dae   814      avahi   13u     IPv4       4722      0t0        UDP *:mdns 
avahi-dae   814      avahi   14u     IPv4       4723      0t0        UDP *:51038 
dropbox    1875     greebo   19u     IPv4      14802      0t0        UDP *:17500 
dhclient   6305       root    5u     IPv4      38275      0t0        UDP *:bootpc 

```
I used sudo stop avahi-daemon and turned DropBox off, ended up with
```
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/greebo/.gvfs
      Output information may be incomplete.
dhclient   6305       root    5u     IPv4      38275      0t0        UDP *:bootpc 

```
but the problem persists..
it might be a router thing (though i have no idea why it's only present on linux), since netstat -pant shows only one router connection (unless I'm getting something wrong)

---

