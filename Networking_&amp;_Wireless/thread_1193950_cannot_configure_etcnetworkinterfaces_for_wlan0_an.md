---
title: "cannot configure /etc/network/interfaces for wlan0 and eth0 and get internet access"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by kraymore on 2009-06-22
I use dnsmasq as a DNS cache here on my ubuntu box.  my /etc/resolv.conf file has the first line as 127.0.0.1 and the appropriate "dhcp3" line to append 127.0.0.1 to resolv.conf has been updated.  i use a /etc/nameservers to define my ISPs nameservers and point the /etc/dnsmasq.conf file to that file, and it works great, but i cannot remove wicd or network-manager-gnome and get any internet connectivity through /etc/network/interfaces whatsoever, however, using the connectivity i can establish, i can accesss my router administration page, just no internet :( my /etc/network/interfaces is as follows: 

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
gateway 192.168.1.1
dns-nameservers 127.0.0.1 68.94.156.1 68.94.157.1
broadcast 192.168.1.255
netmask 255.255.255.0
wpa-driver wext
wpa-ssid MyNet
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk 62f092f085d470095aa17f57db70eeb62373c1082553c1a6a95630ad6b467732

auto eth0
iface eth0 inet static
address 192.168.1.145
gateway 192.168.1.1
broadcast 192.168.1.255
netmask 255.255.255.0
dns-nameservers 127.0.0.1 68.94.156.1 68.94.157.1

i've tried just leaving dns-nameservers as 127.0.0.1 but that doesn't work either.  i've also tried setting dns-nameservers to my router/gateway ip 192.168.1.1 but that doesn't work, and i wanted to use my dns cache service anyway, which routes the dns servers from 127.0.0.1 to /etc/nameservers which are my ISPs nameservers, tried all sorts of things, but nothing works.  restarting /etc/init.d/networking restart doesn't help.  i believe i even tried just defining dns-nameservers to my ISPs nameservers explicitly, and that seems to have failed as well.  luckily I had a wicd deb that i could use to get back connectivity and get help here.

thanks so much for your help and consideration

---

### Post by T.J. on 2009-06-22
I wouldn't bother messing with your network files if you use Network Manager.  It will just overwrite them anyway.  If you want to use your own files regardless, you will need to remove it.

Did you test to see if your DNS works?

---

### Post by hal8000 on 2009-06-22
If you can ping your gateway,
ping 192.168.1.1

then the problem is with your dns servers.

Open a terminal, type
nslookup

then enter a name to resolve e.g.
bbc.co.uk

Example below
anc@orac:~$ nslookup 
> bbc.co.uk
Server:		212.23.6.100
Address:	212.23.6.100#53

Non-authoritative answer:
Name:	bbc.co.uk
Address: 212.58.254.252
> exit


In your case you will probably get an error host not responding or similar.

Your router should receive your ISP's DNS servers either via DNS or be set to fixed DNS servers.

It looks as though these cannot be reached, change your DNS line to use open DNS

[https://www.opendns.com/start/](https://www.opendns.com/start/)

Just use this line:
dns-nameservers 208.67.222.222 208.67.220.220.

Hal

---

### Post by kraymore on 2009-06-22
nslookup gives me this:

bobcat@whale:~$ nslookup [www.google.com](www.google.com)
;; connection timed out; no servers could be reached

and i actually want to use my ISP's nameservers.  they are quicker than OpenDNS.  they are defined in /etc/nameservers i have a entry in my /etc/dnsmasq.conf pointing to that file for upstream servers.  my /etc/resolv.conf file looks like this:

bobcat@whale:~$ cat /etc/resolv.conf
nameserver 127.0.0.1
nameserver 68.94.156.1
nameserver 68.94.157.1

dnsmasq.conf edits look like this:

# Change this line if you want dns to get its upstream servers from
# somewhere other that /etc/resolv.conf
resolv-file=/etc/nameservers

&

# Or which to listen on by address (remember to include 127.0.0.1 if
# you use this.)
listen-address=127.0.0.1

my /etc/dhcp3/dhclient.conf edits look like this:

#supersede domain-name "fugue.com home.vix.com";
prepend domain-name-servers 127.0.0.1;

and i cleaned up my /etc/network/interfaces file.  its still not working however:

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid MyNet
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk 62f0g2f085d470095aa17f57db70eeb62373c1082553c1a6a95630ad6b467732

auto eth0
iface eth0 inet static
address 192.168.1.145
gateway 192.168.1.1
dns-nameservers 127.0.0.1 68.94.156.1 68.94.157.1
netmask 255.255.255.0
broadcast 192.168.1.255

the output of my /etc/init.d/networking restart   is as follows:

bobcat@whale:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 10095
removed stale PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:e7:1d:e9:3c
Sending on   LPF/wlan0/00:18:e7:1d:e9:3c
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
RTNETLINK answers: No such process
SIOCDELRT: No such process
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:e7:1d:e9:3c
Sending on   LPF/wlan0/00:18:e7:1d:e9:3c
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
receive_packet failed on wlan0: Network is down
Terminated
Failed to bring up wlan0.
 * if-up.d/mountnfs[eth0]: waiting for interface wlan0 before doing NFS mounts
                                                                         [ OK ]

wicd deb i have is whats saving me, though i wish i could it to work through the interfaces file and forget about it once i had that figured out.  i'm open to any suggestions anyone might have.  nslookup google.com did return some results once under a cleaned up interfaces file it has 127.0.0.1 for the top two entries and at the bottom 3 entries, it showed the actual ips (non-authoritative) but then i rebooted, and all was lost, i'm not sure what happened there.  :(  

thank you all for your assistance

---

