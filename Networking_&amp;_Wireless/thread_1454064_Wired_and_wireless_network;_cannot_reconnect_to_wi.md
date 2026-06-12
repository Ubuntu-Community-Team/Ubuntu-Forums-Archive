---
title: "Wired and wireless network; cannot reconnect to wireless"
date: 2010-04-14
forum: Networking &amp; Wireless
---

### Post by Diderik From on 2010-04-14
Hello, all!

I'm running 9.10 64bit on a large workstation that also functions as a small NFS&samba server for my other computer. I connect to the internet via wireless, and to my other computer via ethernet. My problem is that after a day or two (sometimes shorter, sometimes longer) wireless drops out and it is impossible to reconnect without rebooting. Reconnection is only possible if I take down the wired connection (which I need to be operable continuously).

[INDENT] sudo /etc/init.d/networking restart
[/INDENT] has no effect whatsoever. It does not even seem to break and reconnect my wired connection...

Contents of /etc/network/interfaces:
[INDENT] auto lo
iface lo inet loopback
[/INDENT] 
I tried editing it after instructions to:
[INDENT] auto lo
iface lo inet loopback
auto eth1
iface eth1 inet loopback
auto wlan0
iface wlan0 inet dhcp
[/INDENT] 
but that only made it worse.

This is becoming a huge headache for me as I need to run processes on my Workstation that easily takes 30+ hours and need to be connected to the interent simultaneoulsy.

Can anyone help?

Diderik

---

### Post by iponeverything on 2010-04-14
This is ok:
> 
auto lo
iface lo inet loopback


This is Not ok:
> 
auto eth1
iface eth1 inet loopback


Does eth1 have a static address or is getting its address via dhcp. If its from dhcp, change the above to:

```

auto eth1
iface eth1 inet dpcp

```

If it is static, change it to:

```

auto eth1
iface eth1 inet static
      address 10.0.0.11
      netmask 255.255.255.0

```

Where the iface stanza is appropriate for your network. 

There is nothing wrong with this wlan0 stanza
```

auto wlan0
iface wlan0 inet dhcp

```

After you get your interfaces file straitened out, we can put together a basic watchdog script to bring the wireless back up when it drops.

---

### Post by Diderik From on 2010-04-14
Thanks a lot for your help!

I changed /etc/network/interfaces to
```
auto lo
iface lo inet loopback
auto eth1
iface eth1 inet static
      address 10.42.43.1
      netmask 255.255.255.0
auto wlan0
iface wlan0 inet dhcp
```(The eth1 ip is static and set to 10.42.43.1 with subnet mask 255.255.255.0.)

But when rebooting neither wired nor wireless connects according to the nautilus connection manager. It lists 'device not managed' under wireless and 'disconnected' and 'device not managed' under each of the wired (I have two network cards for wired networks, but I'm certain the ethernet cable is connected to eth1.) However, I can acces my NFS shares from my other computer, but firefox does not connect to the internet. 

$~> sudo /etc/init.d/networking restart gives
```
 * Reconfiguring network interfaces...
There is already a pid file /var/run/dhclient.wlan0.pid with pid 1954
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1e:e5:21:1d:1b
Sending on   LPF/wlan0/00:1e:e5:21:1d:1b
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 1.1.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1e:e5:21:1d:1b
Sending on   LPF/wlan0/00:1e:e5:21:1d:1b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
                                                                         [ OK ]


```reverting to my old interfaces file, and issuing restart again gives

```
 * Reconfiguring network interfaces... 
Ignoring unknown interface eth1=eth1.
Ignoring unknown interface wlan0=wlan0.

```Another reboot connects both devices.

---

### Post by iponeverything on 2010-04-14
Diderik -- lets start from sqaure one.

> 
But when rebooting neither wired nor wireless connects according to the nautilus connection manager. It lists 'device not managed' under wireless and 'disconnected' and 'device not managed' under each of the wired (I have two network cards for wired networks, but I'm certain the ethernet cable is connected to eth1.) However, I can acces my NFS shares from my other computer, but firefox does not connect to the internet.

First off, the reason that you see 'device not managed' is because When a device is configured via /etc/network/interfaces it is no longer managed by Network Manager. This is not a big deal. This does not mean that the interface has not been configured. The way to tell would be to open a terminal and ping the IP address of another machine on the network. The fact that your can accesses your NFS share is pretty good indication that the ethernet interface is configured.

> but firefox does not connect to the internet.

 Next: You said you access the internet though wifi and we could tell that wlan0 didn't pick up an address via DHCP -- that explains that.  So, I think its pretty safe assumption that your you are connecting to secure network. That said configure your wlan0 like so:

```

iface wlan0 inet dhcp
 wpa-conf /etc/wpa_supplicant.conf

```

Create a /etc/wpa_supplicant.conf with something like this except for your network (encryption, passphrase, etc.):

```

network={
     ssid="Kabul"
     proto=WPA
     group=CCMP
     pairwise=CCMP
     scan_ssid=1
     key_mgmt=WPA-PSK
     psk="My Super Secret Not So Random Pass Phrase"
}

```

Last, Are you routing other machines out through this machine to get to internet? If so, turn on IP Forward and and IP Masquerade.

To do that just add the following lines to your /etc/rc.local and reboot:

```

iptables -t nat -A POSTROUTING -s 0/0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/conf/all/forwarding

```

---

### Post by Diderik From on 2010-04-14
I will try this as soon as I get back to my office tomorrow morning. (I use these machines for my research, but our IT consultant won't help anyone with anything not Microsoft...)

I should probably have figured and told you; yes, I'm on a secure network. One that in addition to a username/password needs a security certificate.

(Network manager is supposed to be set up like so: [http://www2.usit.uio.no/it/wlan/bilder/nm2.png](http://www2.usit.uio.no/it/wlan/bilder/nm2.png))

Again, thanks a lot! I'll update this post first thing tomorrow morning.

---

### Post by iponeverything on 2010-04-14
> our IT consultant won't help anyone with anything not Microsoft...


This is probably a good thing, I have found that for things that fall outside their area of expertise, many consultants will tell you with great conviction that things are "not possible".

You can see some examples for wpa_supplicant.conf, if you do a:
 
```
man wpa_supplicant.conf
```

In the man page I found the following that seems to approximate your configuration.  As seen below, make sure that the cert is in the correct place and readable by the wpa_supplicant process and that the identity, password and ssid (in your case "uio") variables are set correctly. 

```

          ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=wheel
          network={
               ssid="example"
               scan_ssid=1
               key_mgmt=WPA-EAP
               eap=PEAP
               identity="user@example.com"
               password="foobar"
               ca_cert="/etc/cert/ca.pem"
               phase1="peaplabel=0"
               phase2="auth=MSCHAPV2"
}

```

wpa_supplicant does create enough debugging output in /var/log/ to generally find minor glitches in the configuration fairly easily.

Once the wlan interface is configured, creating a watchdog script to babysit it and bring it back up if drops is fairly trivial.

---

### Post by Diderik From on 2010-04-15
Wow! This seems to work! Just a few things:

$ cat /etc/network/interfaces
```
auto lo
iface lo inet loopback
auto eth1
iface eth1 inet static
      address 10.42.43.1
      netmask 255.255.255.0
iface wlan0 inet dhcp
       wpa-conf /etc/wpa_supplicant.conf

```$ cat /etc/wpa_supplicant.conf 
```
          ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=wheel
          network={
               ssid="eduroam"
               scan_ssid=1
               key_mgmt=WPA-EAP
               eap=PEAP
               identity="username"
               password="password"
               ca_cert="/etc/cert/AddtrustCARoot.pem"
               phase1="peaplabel=0"
               phase2="auth=MSCHAPV2"
}

```After a restart, I can access my NFS shares, and I can connect to the internet! Network manager states that the wired connection is not managed, but it still seems to handle the wireless. 

$ sudo /etc/init.d/networking restart
```
 * Reconfiguring network interfaces...                                                               RTNETLINK answers: No such process
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1e:e5:21:1d:1b
Sending on   LPF/wlan0/00:1e:e5:21:1d:1b
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 1.1.1.1 port 67
 * Reloading /etc/samba/smb.conf smbd only
   ...done.                                             [ OK ]

```After a delay, network manager breaks the wireless connection and reconnects.
If I disconnect wireless from network manager, and restart networking; I only get 
```
 * Reconfiguring network interfaces...                           [ OK ]
```and there is no internet connectitivity until I reenable it in network manager. It seems network manager handles my wireless connection but uses the configuration in wpa_supplicant.conf and /etc/network/interfaces. This is fine, but a bit (for me) unexpected?

I'm also slightly anxious about security. Previously, in network manager, anyone could just open the configuration and see my password. Now it is in wpa_supplicant.conf. Can I make this file readable only by root?

Thanks a million for you help!

---

### Post by iponeverything on 2010-04-15
Just a couple more things.. What version of Ubuntu are you running? Network Manager should not be touching the manually configured interfaces. Perhaps you can take it out of the picture all together by right-clicking on it and removing it from the panel. Might also need to remove the package.. it is odd.

In /etc/network/interfaces:

change:

```
auto eth1
```

to:

```
auto eth1 wlan0
```

Change the ownership of wpa_supplicant.conf to root.root and permissions to 700 and it should be fine.

Here is a simple watcher script that I put together, you can put in /usr/local/bin change the perms 755 and call it from cron every 5 minutes. You can add it to /etc/crontab and have it run as root. The default route next-hop must answer pings, if it doesn't, just hard-code something that does that will verify the integrity of the wifi link. 

```
#!/usr/bin/perl

open(DE,"route -n|");

while(<DE>){
    /^0\.0\.0\.0\s+(\d+\.\d+\.\d+\.\d+)/;
    $def=$1 if $1;
}

open(PING,"ping -c2 $def 2>/dev/null |");

while(<PING>){
    /\d+\sbytes\sfrom.*(ms)/;
    $res=$1 if $1;
}

exit if $res;

system("ifdown wlan0 > /dev/null 2>&1 ; ifup wlan0 > /dev/null 2>&1");
system("/usr/bin/logger Wireless Connection Restart");

```

---

### Post by Diderik From on 2010-04-15
I'm on Ubuntu 9.10. I'm not quire sure what happened previously, but I suspect Network manager was connecting independently to wlan as I suddenly could not connect anymore. I added wlan0 after auto eth1 as you suggested, and then right-clicked Network manager and unchecked 'Enable networking'. After restarting networking, both wired and wireless connects.

Also, I tried your script. I have no knowledge of perl, but if I stop networking, and then run the script, I'm reconnected! This is great! Finally I can connect to my workstation anytime via ssh and not worry about whether or not the network is down.

At the time, I'm not routing anything though this machine for internet access, but I plan to set up a headless linux box at home as a combined router/server, and I shall remember your advice.

Thank you ever so much!

---

### Post by iponeverything on 2010-04-15
For your home you might look at dd-wrt x86.

---

### Post by Diderik From on 2010-04-15
Thanks! I'll certainly look into dd-wrt x86!

---

