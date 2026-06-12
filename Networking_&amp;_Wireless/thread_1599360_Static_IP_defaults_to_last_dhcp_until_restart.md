---
title: "Static IP defaults to last dhcp until restart"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by NertSkull on 2010-10-17
I am so lost.  I set up my interfaces file just fine on one of my computers and everything works.

On my desktop its a no go.  This is what I've done.

I set my interfaces file to look like this

```
# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 10.42.32.112
gateway 10.42.32.1
netmask 255.255.255.0
wpa-ssid BDF_Net
wpa-psk big_long_wpa_passphrase
```

Then I uninstalled network manager (sudo apt-get remove network-manager-gnome).

Now I can restart my computer, but I do NOT get a static IP of 112, instead I get the last working dhcp given address (.104).

It connects and I get internet using .104.

BUT, if I run ```
sudo /etc/init.d/networking restart
``` then it DOES work.  It changes to my address .112 and the internet works.

But when I get that I get an error

SIOCDELRT: No such process found (or something similar to that).

But after it sits, it still finished with [OK] and my internet works.

Clearly something is amiss though.  Because it doesn't go to the static IP imediately.

I even tried setting up a rcS.d link to a file with that networking restart command, but still no go.  It starts with the .101 IP.

Any ideas?  Thanks all.  I really appreciate it.  Networking is becoming the most annoying thing to me on ubuntu.  Everything else I can usually figure out, but networking (esp. wireless) is a beast.

---

### Post by chili555 on 2010-10-17
Please do:```
sudo rm -f /var/lib/dhcp3/*
```Any improvement?

---

### Post by NertSkull on 2010-10-18
Allright, that appears to not have helped.

Its my parents computer in another city, so sometimes it takes a while before I can get someone there to help, since I can only SSH some of the time without internet.

But deleted those files this morning, rebooted twice, and still it loaded to the .104 IP, not the assigned static 114 like I want.

I'm kind of stuck on it now until people there get home from work tonight.  So any other ideas of what I can try tonight would be greatly appreciated.

I just can't figure out why it works fine on my laptop here on my network, but the similar settings won't work there.  I honestly can't find anything different (to my very untrained network eye).

Any other things I can try?? Thanks!

---

### Post by chili555 on 2010-10-18
Can you confirm that Network Manager has been removed from the parent's computer? If /etc/network/interfaces is set up correctly and NM is removed, I can't possibly imagine how it could happen. What does this tell us?```
sudo apt-get remove network-manage*
ps aux | grep -i network
```

---

### Post by NertSkull on 2010-10-18
Allright, apparantly I did not remove all of network manager.  But now I have (like you said above).

So that took care of my problem with the IP not changing.  Now when I restart it tells me that I have the correct IP.

But no internet (which is similar to my other recent thread).  I can't ping google, yahoo.  And more importantly I can not ping my router.  So it must not be connecting.

I've tried using the wpa_passphrase programs hex key as well as my plain password and nothing is working.  No internet.

This is the interfaces file I am using with it

```
# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 10.14.19.114
gateway 10.14.19.1
netmask 255.255.255.0
wpa-ssid familynet
wpa-psk big_long_wpa_key
```

Thats not letting me connect.  Any help would be greatly appreciated.  Thanks!


p.s. thanks for setting me straight with removing network manager.  I had only done remove network-manager-gnome, which wasn't enough.  thanks

p.p.s. also I have checked my resolv.conf file and it has servers in it, so I assume that is ok (but clearly I don't know that for 100% surety)

This is what it says when I ping the router

```
ping 10.14.19.1 56(86) bytes of data
from 10.14.19.114 icmp_seq=1 destination host unreahable
```

---

### Post by chili555 on 2010-10-18
You might look at syslog and dmesg to see why it tries and fails to connect:```
dmesg | grep wlan0
sudo cat /var/log/syslog | grep wlan0
```

---

### Post by NertSkull on 2010-10-18
So if I do the dmesg I get two lines that say the same thing with different numbers in the front

```
ADDRCONF (NETDEV_UP): wlan0: link is not ready
```

when I do the sudo cat command I must get 5000 entries, these are just a couple, there's lots more, but since i'm getting information over the phone from a non-computer friend at home, I can't really type them all in

```
ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
wpa_supplicant[901]: could not get interface 'wlan0' flags

```

Its almost like it feels like there's a driver missing.  But before I uninstalled network-manager and started all this is connected just fine with DHCP and the automatic connecting.

I don't know where to go now.

---

### Post by holiday on 2010-10-18
I found that for my static IPs I have to set the DNS hostnames or IPs as well. Maybe that's the problem? What you're seeing is what I see setting up static IPs.

---

### Post by NertSkull on 2010-10-18
well I put in 

```
dns-namerservers 209.53.4.130
```

but that doesn't seem to have helped, still no internet with the static IP

---

### Post by holiday on 2010-10-18
Well namer-servers is wrong. Should be name-servers, probably.

---

### Post by chili555 on 2010-10-18
Actually, it's like this:```
nameserver 209.53.4.130
```

---

### Post by NertSkull on 2010-10-19
Whoops, I just typed namerservers in wrong here, I had it right in the interfaces file.

But I did have it as dns-nameservers, so I tried it just as nameservers, but that still didn't help.  

But I reinstalled network-manager just for a second so I could SSH into the computer and get more complete dmesg info.  Here is what the dmesg | grep wlan0 outputs

```
   14.837452] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.061821] wlan0: direct probe to AP 68:7f:74:c2:f4:af (try 1)
[   22.061841] wlan0: deauthenticating from 68:7f:74:c2:f4:af by local choice (reason=3)
[   22.061958] wlan0: direct probe to AP 68:7f:74:c2:f4:af (try 1)
[   22.064191] wlan0: direct probe responded
[   22.064195] wlan0: authenticate with AP 68:7f:74:c2:f4:af (try 1)
[   22.067330] wlan0: authenticated
[   22.067343] wlan0: associate with AP 68:7f:74:c2:f4:af (try 1)
[   22.071350] wlan0: RX AssocResp from 68:7f:74:c2:f4:af (capab=0x411 status=0 aid=2)
[   22.071352] wlan0: associated
[   22.071890] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   32.808012] wlan0: no IPv6 routers present

```

Since that also includes after reinstalling network-manager so I could connect, I don't know what exactly is from before when it doesn't work.

This is the output from cat /var...  The entire output is thousands of lines so I just took a chunk of it from the time I was working on it last night.

```
Oct 18 17:08:53 ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Oct 18 17:08:53 ubuntu NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Oct 18 17:08:53 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Oct 18 17:08:53 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Oct 18 17:08:53 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Oct 18 17:08:53 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Oct 18 17:08:53 ubuntu NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit
Oct 18 17:08:53 ubuntu avahi-daemon[878]: Registering new address record for fe80::20d:88ff:fe57:5aa8 on wlan0.*.
Oct 18 17:08:53 ubuntu dhclient: Listening on LPF/wlan0/00:0d:88:57:5a:a8
Oct 18 17:08:53 ubuntu dhclient: Sending on   LPF/wlan0/00:0d:88:57:5a:a8
Oct 18 17:08:55 ubuntu dhclient: DHCPREQUEST of 10.14.19.104 on wlan0 to 255.255.255.255 port 67
Oct 18 17:08:55 ubuntu NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
Oct 18 17:08:55 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Oct 18 17:08:55 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Oct 18 17:08:55 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Oct 18 17:08:55 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Oct 18 17:08:55 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Oct 18 17:08:55 ubuntu avahi-daemon[878]: Withdrawing address record for 10.14.19.114 on wlan0.
Oct 18 17:08:55 ubuntu avahi-daemon[878]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.14.19.114.
Oct 18 17:08:55 ubuntu avahi-daemon[878]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct 18 17:08:55 ubuntu avahi-daemon[878]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.14.19.104.
Oct 18 17:08:55 ubuntu avahi-daemon[878]: New relevant interface wlan0.IPv4 for mDNS.
Oct 18 17:08:55 ubuntu avahi-daemon[878]: Registering new address record for 10.14.19.104 on wlan0.IPv4.
Oct 18 17:08:56 ubuntu NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Oct 18 17:08:56 ubuntu NetworkManager: <info>  Policy set 'Auto home_net' (wlan0) as default for routing and DNS.
Oct 18 17:08:56 ubuntu NetworkManager: <info>  Activation (wlan0) successful, device activated.
Oct 18 17:08:56 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Oct 18 17:09:02 ubuntu kernel: [   34.656025] wlan0: no IPv6 routers present
Oct 18 17:10:18 ubuntu kernel: [  110.336117] wlan0: deauthenticating from 68:7f:74:c2:f4:af by local choice (reason=3)
Oct 18 17:10:18 ubuntu avahi-daemon[878]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct 18 17:10:18 ubuntu avahi-daemon[878]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.14.19.104.
Oct 18 17:10:18 ubuntu avahi-daemon[878]: Withdrawing address record for fe80::20d:88ff:fe57:5aa8 on wlan0.
Oct 18 17:10:18 ubuntu avahi-daemon[878]: Withdrawing address record for 10.14.19.104 on wlan0.
Oct 18 17:10:18 ubuntu avahi-daemon[878]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.14.19.104.
Oct 18 17:10:18 ubuntu avahi-daemon[878]: New relevant interface wlan0.IPv4 for mDNS.
Oct 18 17:10:18 ubuntu avahi-daemon[878]: Registering new address record for 10.14.19.104 on wlan0.IPv4.
Oct 18 17:13:44 ubuntu avahi-daemon[911]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.14.19.114.
Oct 18 17:13:44 ubuntu avahi-daemon[911]: New relevant interface wlan0.IPv4 for mDNS.
Oct 18 17:13:44 ubuntu avahi-daemon[911]: Registering new address record for 10.14.19.114 on wlan0.IPv4.
Oct 18 17:13:44 ubuntu avahi-daemon[911]: Withdrawing address record for 10.14.19.114 on wlan0.
Oct 18 17:13:44 ubuntu avahi-daemon[911]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.14.19.114.
Oct 18 17:13:44 ubuntu avahi-daemon[911]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct 18 17:13:44 ubuntu avahi-daemon[911]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.14.19.114.
Oct 18 17:13:44 ubuntu kernel: [   14.328102] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 18 17:13:44 ubuntu avahi-daemon[911]: New relevant interface wlan0.IPv4 for mDNS.
Oct 18 17:13:44 ubuntu avahi-daemon[911]: Registering new address record for 10.14.19.114 on wlan0.IPv4.
Oct 18 17:13:46 ubuntu avahi-daemon[911]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct 18 17:13:46 ubuntu avahi-daemon[911]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.14.19.114.
Oct 18 17:13:46 ubuntu avahi-daemon[911]: Withdrawing address record for 10.14.19.114 on wlan0.
Oct 18 17:13:47 ubuntu avahi-daemon[911]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.14.19.114.
Oct 18 17:13:47 ubuntu avahi-daemon[911]: New relevant interface wlan0.IPv4 for mDNS.
Oct 18 17:13:47 ubuntu avahi-daemon[911]: Registering new address record for 10.14.19.114 on wlan0.IPv4.
Oct 18 17:13:47 ubuntu kernel: [   16.986892] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 18 17:25:55 ubuntu kernel: [   19.848900] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 18 17:25:55 ubuntu avahi-daemon[1002]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.14.19.114.
Oct 18 17:25:55 ubuntu avahi-daemon[1002]: New relevant interface wlan0.IPv4 for mDNS.
Oct 18 17:25:55 ubuntu avahi-daemon[1002]: Registering new address record for 10.14.19.114 on wlan0.IPv4.
Oct 18 17:25:55 ubuntu avahi-daemon[1002]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct 18 17:25:55 ubuntu avahi-daemon[1002]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.14.19.114.
Oct 18 17:25:55 ubuntu avahi-daemon[1002]: Withdrawing address record for 10.14.19.114 on wlan0.
Oct 18 17:25:56 ubuntu avahi-daemon[1002]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.14.19.114.
Oct 18 17:25:56 ubuntu avahi-daemon[1002]: New relevant interface wlan0.IPv4 for mDNS.
Oct 18 17:25:56 ubuntu avahi-daemon[1002]: Registering new address record for 10.14.19.114 on wlan0.IPv4.
Oct 18 17:25:56 ubuntu kernel: [   20.020682] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 18 17:38:23 ubuntu kernel: [   15.274679] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 18 17:38:23 ubuntu avahi-daemon[1153]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.14.19.114.
Oct 18 17:38:23 ubuntu avahi-daemon[1153]: New relevant interface wlan0.IPv4 for mDNS.
Oct 18 17:38:23 ubuntu avahi-daemon[1153]: Registering new address record for 10.14.19.114 on wlan0.IPv4.
Oct 18 17:38:23 ubuntu kernel: [   26.444366] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 18 17:51:23 ubuntu kernel: [   20.099688] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 18 17:51:23 ubuntu avahi-daemon[1087]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.14.19.114.
Oct 18 17:51:23 ubuntu avahi-daemon[1087]: New relevant interface wlan0.IPv4 for mDNS.
Oct 18 17:51:23 ubuntu avahi-daemon[1087]: Registering new address record for 10.14.19.114 on wlan0.IPv4.
Oct 18 17:51:23 ubuntu kernel: [   20.313106] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 18 18:09:11 ubuntu avahi-daemon[881]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.14.19.114.
Oct 18 18:09:11 ubuntu kernel: [   15.435705] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 18 18:09:11 ubuntu avahi-daemon[881]: New relevant interface wlan0.IPv4 for mDNS.
Oct 18 18:09:11 ubuntu avahi-daemon[881]: Registering new address record for 10.14.19.114 on wlan0.IPv4.
Oct 18 18:09:11 ubuntu avahi-daemon[881]: Withdrawing address record for 10.14.19.114 on wlan0.
Oct 18 18:09:11 ubuntu avahi-daemon[881]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.14.19.114.
Oct 18 18:09:11 ubuntu avahi-daemon[881]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct 18 18:09:11 ubuntu avahi-daemon[881]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.14.19.114.
Oct 18 18:09:11 ubuntu avahi-daemon[881]: New relevant interface wlan0.IPv4 for mDNS.
Oct 18 18:09:11 ubuntu avahi-daemon[881]: Registering new address record for 10.14.19.114 on wlan0.IPv4.
Oct 18 18:49:33 ubuntu dhclient: Listening on LPF/wlan0/00:0d:88:57:5a:a8
Oct 18 18:49:33 ubuntu dhclient: Sending on   LPF/wlan0/00:0d:88:57:5a:a8
Oct 18 18:49:33 ubuntu kernel: [   19.497143] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 18 18:49:33 ubuntu dhclient: Listening on LPF/wlan0/00:0d:88:57:5a:a8
Oct 18 18:49:33 ubuntu dhclient: Sending on   LPF/wlan0/00:0d:88:57:5a:a8
Oct 18 18:49:33 ubuntu dhclient: Listening on LPF/wlan0/00:0d:88:57:5a:a8
Oct 18 18:49:33 ubuntu dhclient: Sending on   LPF/wlan0/00:0d:88:57:5a:a8
Oct 18 18:49:37 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 18 18:49:37 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 18 18:49:43 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 18 18:49:43 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 18 18:49:57 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 18 18:49:57 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 18 18:50:09 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Oct 18 18:50:09 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Oct 18 18:50:25 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 18 18:50:25 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 18 18:50:35 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 18 18:50:35 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 18 18:50:38 ubuntu avahi-autoipd(wlan0)[1680]: Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 110).
Oct 18 18:50:38 ubuntu avahi-autoipd(wlan0)[1680]: Successfully called chroot().
Oct 18 18:50:38 ubuntu avahi-autoipd(wlan0)[1680]: Successfully dropped root privileges.
Oct 18 18:50:38 ubuntu avahi-autoipd(wlan0)[1680]: Starting with address 169.254.7.211
Oct 18 18:50:43 ubuntu avahi-autoipd(wlan0)[1680]: Callout BIND, address 169.254.7.211 on interface wlan0
Oct 18 18:50:43 ubuntu avahi-daemon[1012]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.7.211.
Oct 18 18:50:43 ubuntu avahi-daemon[1012]: New relevant interface wlan0.IPv4 for mDNS.
Oct 18 18:50:43 ubuntu avahi-daemon[1012]: Registering new address record for 169.254.7.211 on wlan0.IPv4.
Oct 18 18:50:47 ubuntu avahi-autoipd(wlan0)[1680]: Successfully claimed IP address 169.254.7.211
Oct 18 18:53:33 ubuntu dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 1724
Oct 18 18:53:33 ubuntu dhclient: Listening on LPF/wlan0/00:0d:88:57:5a:a8
Oct 18 18:53:33 ubuntu dhclient: Sending on   LPF/wlan0/00:0d:88:57:5a:a8
Oct 18 18:53:33 ubuntu avahi-daemon[1012]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct 18 18:53:33 ubuntu avahi-daemon[1012]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.7.211.
Oct 18 18:53:33 ubuntu dhclient: receive_packet failed on wlan0: Network is down
Oct 18 18:53:33 ubuntu avahi-autoipd(wlan0)[1680]: SIOCSIFFLAGS failed: Permission denied
Oct 18 18:53:33 ubuntu avahi-autoipd(wlan0)[1680]: Callout STOP, address 169.254.7.211 on interface wlan0
Oct 18 18:53:33 ubuntu avahi-daemon[1012]: Withdrawing address record for 169.254.7.211 on wlan0.
Oct 18 18:53:33 ubuntu kernel: [  259.730924] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 18 18:53:33 ubuntu dhclient: Listening on LPF/wlan0/00:0d:88:57:5a:a8
Oct 18 18:53:33 ubuntu dhclient: Sending on   LPF/wlan0/00:0d:88:57:5a:a8
Oct 18 18:53:37 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct 18 18:53:41 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 18 18:53:48 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 18 18:54:02 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 18 18:54:10 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 18 18:54:21 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Oct 18 18:54:38 ubuntu avahi-autoipd(wlan0)[2129]: Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 110).
Oct 18 18:54:38 ubuntu avahi-autoipd(wlan0)[2129]: Successfully called chroot().
Oct 18 18:54:38 ubuntu avahi-autoipd(wlan0)[2129]: Successfully dropped root privileges.
Oct 18 18:54:38 ubuntu avahi-autoipd(wlan0)[2129]: Starting with address 169.254.7.211
Oct 18 18:54:43 ubuntu avahi-autoipd(wlan0)[2129]: Callout BIND, address 169.254.7.211 on interface wlan0
Oct 18 18:54:43 ubuntu avahi-daemon[1012]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.7.211.
Oct 18 18:54:43 ubuntu avahi-daemon[1012]: New relevant interface wlan0.IPv4 for mDNS.
Oct 18 18:54:43 ubuntu avahi-daemon[1012]: Registering new address record for 169.254.7.211 on wlan0.IPv4.
Oct 18 18:54:47 ubuntu avahi-autoipd(wlan0)[2129]: Successfully claimed IP address 169.254.7.211
Oct 18 18:56:59 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct 18 18:57:03 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 18 18:57:11 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 18 18:57:22 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Oct 18 18:57:38 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Oct 18 18:58:39 ubuntu wpa_supplicant[901]: Could not get interface 'wlan0' flags
Oct 18 18:58:40 ubuntu kernel: [   19.142296] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 18 18:58:42 ubuntu dhclient: Listening on LPF/wlan0/00:0d:88:57:5a:a8
Oct 18 18:58:42 ubuntu dhclient: Sending on   LPF/wlan0/00:0d:88:57:5a:a8
Oct 18 18:58:45 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 18 18:58:51 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 18 18:59:05 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 18 18:59:20 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Oct 18 18:59:41 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 18 18:59:46 ubuntu avahi-autoipd(wlan0)[1695]: Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 110).
Oct 18 18:59:46 ubuntu avahi-autoipd(wlan0)[1695]: Successfully called chroot().
Oct 18 18:59:46 ubuntu avahi-autoipd(wlan0)[1695]: Successfully dropped root privileges.
Oct 18 18:59:46 ubuntu avahi-autoipd(wlan0)[1695]: Starting with address 169.254.7.211
Oct 18 18:59:52 ubuntu avahi-autoipd(wlan0)[1695]: Callout BIND, address 169.254.7.211 on interface wlan0
Oct 18 18:59:52 ubuntu avahi-daemon[896]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.7.211.
Oct 18 18:59:52 ubuntu avahi-daemon[896]: New relevant interface wlan0.IPv4 for mDNS.
Oct 18 18:59:52 ubuntu avahi-daemon[896]: Registering new address record for 169.254.7.211 on wlan0.IPv4.
Oct 18 18:59:56 ubuntu avahi-autoipd(wlan0)[1695]: Successfully claimed IP address 169.254.7.211
Oct 18 19:00:31 ubuntu dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 1809
Oct 18 19:00:31 ubuntu dhclient: Listening on LPF/wlan0/00:0d:88:57:5a:a8
Oct 18 19:00:31 ubuntu dhclient: Sending on   LPF/wlan0/00:0d:88:57:5a:a8
Oct 18 19:00:31 ubuntu avahi-daemon[896]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct 18 19:00:31 ubuntu avahi-daemon[896]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.7.211.
Oct 18 19:00:31 ubuntu avahi-autoipd(wlan0)[1695]: SIOCSIFFLAGS failed: Permission denied
Oct 18 19:00:31 ubuntu avahi-autoipd(wlan0)[1695]: Callout STOP, address 169.254.7.211 on interface wlan0
Oct 18 19:00:31 ubuntu avahi-daemon[896]: Withdrawing address record for 169.254.7.211 on wlan0.
Oct 18 19:00:32 ubuntu kernel: [  130.936310] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

Hopefully that gives someone more intelligent than I a better clue as to what is going on so I can fix this.

---

### Post by Strategist01 on 2010-10-19
Out of interest, have you checked your router settings? The DHCP settings on your router might be interfering/conflicting somehow?

---

### Post by NertSkull on 2010-10-19
I guess thats possible but I don't know how.  I know that I can connect with other laptops in the house.  I don't have the router automatically assigning IPs to any computer. 

Basically the router settings at my parents house are the exact same as the ones in my house.  As far as I can tell I have everything exactly the same (router settings, interface files, resolv.conf file) between my house and my parents.  And their install of ubuntu is only about 5 weeks old, so I can't believe too much can be messed up in that amount of time.

The router is the WRT54GS if there is something specific I should check.

So do I know for sure the dhcp in the router isn't the issue?  No.  But I'm pretty sure, since I can set up a static IP on the Win7 laptop.

---

### Post by chili555 on 2010-10-19
Have you tried both the encrypted and unencrypted PSK in your interfaces file? Is there any difference in the syslog before and after? Unfortunately, the syslog you gave us is when Network Manager was still installed and trying to get a DHCP address.

---

### Post by perspectoff on 2010-10-19
Try using Wicd instead.

Setting up wireless manually is a joyless task and will take a few years from your life.

I use Wicd instead of Network Manager routinely, and successfully use static IPs with wireless with it (unlike with Network Manager).

 sudo apt-get remove network-manager network-manager-gnome
 sudo reboot
 sudo apt-get install wicd

---

### Post by chili555 on 2010-10-19
> sudo apt-get remove network-manager network-manager-gnomeDone. Please read post #5.

---

### Post by NertSkull on 2010-10-21
Allright I'm at a loss of how to get it to work manually through the interfaces file.

BUT

I got it to work with wicd.  Its actually a pretty nice little program (must be since I was able to explain it to people at home and get it working).

So although I didn't solve the root problem, I found something that works.

So thanks all, I really appreciate it. 

I highly suggest wicd to anyone else trying to do static IPs.

---

