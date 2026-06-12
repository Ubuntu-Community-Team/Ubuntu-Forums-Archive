---
title: "Adding mtu in /etc/network/interfaces has no effect"
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by afeasfaerw23231233 on 2009-10-06
I have the following line in my /etc/network/interfaces
```

auto eth0
iface eth0 inet dhcp 
mtu 1400

```

But every time it boot up ifconfig always shows mtu = 1500.
I have to change it to 1400 manually by
```
sudo ifconfig eth0 mtu 1400 
```
Would anyone please tell me why adding **mtu 1400** in my /etc/network/interfaces doesn't work?

EDIT: Even though I run```
 sudo /etc/init.d/networking restart
``` 
it has no effect on the mtu. 
It shows the following (my wireless is off)
```

sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 3256
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:03:0d:af:c3:b5
Sending on   LPF/eth0/00:03:0d:af:c3:b5
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.123.1 port 67
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
ioctl[SIOCGIFFLAGS]: No such device
Could not get interface 'wlan0' flags
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIWRANGE]: No such device
ioctl[SIOCGIFINDEX]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWAP]: No such device
ioctl[SIOCGIFFLAGS]: No such device
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:03:0d:af:c3:b5
Sending on   LPF/eth0/00:03:0d:af:c3:b5
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.123.9 from 192.168.123.1
DHCPREQUEST of 192.168.123.9 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.123.9 from 192.168.123.1
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
bound to 192.168.123.9 -- renewal in 478913 seconds.
 * if-up.d/mountnfs[eth0]: waiting for interface wlan0 before doing NFS mounts
                                                                         [ OK ]
```

---

### Post by lloyd_b on 2009-10-06
Take a look in the file "/etc/dhcp3/dhclient.conf".  Most likely, DHCP is configured to request the MTU from the DHCP server (look at the "request" line, and you'll probably find "interface-mtu" included in the things it's requesting).

I'm no expert on DHCP, but I *think* that if you remove "interface-mtu" from the "request" line, it'll fall back to the MTU specified in the interfaces file.

If not, you may need to specify a "supercede" line, explicitly telling DHCP to use the MTU of 1400 rather than the server-supplied MTU.

Lloyd B.

---

### Post by afeasfaerw23231233 on 2009-10-06
Thanks for the suggestion. I have deleted /etc/dhcp3/dhclient.conf "interface-mtu" from the request line, restart the computer but the mtu is still 1500.

---

### Post by Iowan on 2009-10-06
The **mtu** option may only be available when using manual configuration in  */etc/network/interfaces.*

---

### Post by chili555 on 2009-10-06
You could try it in */etc/rc.local*:```
ifconfig eth0 mtu 1400
```

---

### Post by afeasfaerw23231233 on 2009-10-06
> **chili555 said:**
> You could try it in */etc/rc.local*:```
ifconfig eth0 mtu 1400
```

But it wouldn't work if I plug in the cable after the system has booted up.

---

### Post by lloyd_b on 2009-10-06
You can try adding the following to dhclient.conf (somewhere before the "request" line I think):```
default interface-mtu 1400;
supercede interface-mtu 1400;
```
As I stated before, I am not an expert on DHCP - just going off of the man page and the examples in the default dhclient.conf.  But there *should* be a way to handle this situation - if not, then there's something wrong with DHCP's design...

One note: if you have more than one interface in that machine, the above may need to be enclosed in a "interface {}" section:```
interface "eth0" {
    default interface-mtu 1400;
    supercede interface-mtu 1400;
}
```

Lloyd B.

---

### Post by afeasfaerw23231233 on 2009-10-07
There are some warning message while doing /etc/init.d/networking restart
```

Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

/etc/dhcp3/dhclient.conf line 25: semicolon expected.
    supercede interface-mtu 
              ^
/etc/dhcp3/dhclient.conf line 26: semicolon expected.
}
^
/etc/dhcp3/dhclient.conf line 32: unterminated interface declaration.

^

```
Here's my /etc/dhcp3/dhclient.conf
```

# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;

#new
interface "eth0" {
    default interface-mtu 1400;
    supercede interface-mtu 1400; **[COLOR="Red"]line 25[/COLOR]**
} **[COLOR="Red"]line 26[/COLOR]**
#new -- end here

request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
	netbios-name-servers, netbios-scope, interface-mtu,
	rfc3442-classless-static-routes, ntp-servers;**[COLOR="Red"] line 32[/COLOR]**

```

Is there something wrong with the syntax? Also, what is the problem in line 32?

> **Iowan said:**
> The **mtu** option may only be available when using manual configuration in  */etc/network/interfaces.*

Thanks for your reminder.

---

### Post by lloyd_b on 2009-10-07
Oops - spelling error on my part.  It's "supersede", not "supercede".  Try making that change, and see which of the errors it eliminates.  It's quite possible that spelling error is responsible for all the errors...

Lloyd B.

---

### Post by doas777 on 2009-10-07
you could add it to your ifup script, if you want to run the command everytime the cable is plugged in or otherwise brought up.

---

### Post by Dr_Free on 2009-10-08
I had a similar problem, my DSL connection required a lower MTU. Simply adding the "supercede interface-mtu xxxx" line to my /etc/dhcp3/dhclient.conf, **after** the request line worked for me (at least for my wlan connection):[INDENT]request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        netbios-name-servers, netbios-scope, interface-mtu,
        rfc3442-classless-static-routes, ntp-servers;

supersede interface-mtu 1460;
[/INDENT]Hope this helps!

---

