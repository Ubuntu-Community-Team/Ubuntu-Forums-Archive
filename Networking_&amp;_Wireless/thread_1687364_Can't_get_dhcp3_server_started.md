---
title: "Can't get dhcp3 server started"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by voidman on 2011-02-13
I'm trying to netboot my old lappy following  [http://ubuntuforums.org/showthread.php?t=1413126&page=2](http://ubuntuforums.org/showthread.php?t=1413126&page=2) tutorial.

The problem is I can't start dhcp3 server. 

```
sudo /etc/init.d/dhcp3-server status
Status of DHCP server: dhcpd3 is not running.
```
```

 sudo /etc/init.d/dhcp3-server start
 * Starting DHCP server dhcpd3                                                         * check syslog for diagnostics.
                                                                               [fail]
```

```
dmesg | tail
[11120.621196] r8169 0000:08:00.0: eth0: link down
[11124.934793] r8169 0000:08:00.0: eth0: link up
[12100.022648] r8169 0000:08:00.0: eth0: link down
[12114.213795] r8169 0000:08:00.0: eth0: link up
[12304.990651] r8169 0000:08:00.0: eth0: link down
[12308.827628] r8169 0000:08:00.0: eth0: link up
[12321.827620] r8169 0000:08:00.0: eth0: link down
[12325.424925] r8169 0000:08:00.0: eth0: link up
[12339.918338] r8169 0000:08:00.0: eth0: link down
[12342.546202] r8169 0000:08:00.0: eth0: link up
```


If I replace my internet cable with cable to my old lappy i got another dmesg
```

Feb 14 00:47:42 sva dhcpd: No subnet declaration for eth0 (0.0.0.0).
Feb 14 00:47:42 sva dhcpd: ** Ignoring requests on eth0.  If this is not what
Feb 14 00:47:42 sva dhcpd:    you want, please write a subnet declaration
Feb 14 00:47:42 sva dhcpd:    in your dhcpd.conf file for the network segment
Feb 14 00:47:42 sva dhcpd:    to which interface eth0 is attached. **
```

My /etc/default/dhcp3-server

```
INTERFACES="eth0" 
```

and 
/etc/dhcp3/dhcpd.conf

```
ddns-update-style none;

default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;
#subnet declaration
subnet 192.168.2.0 netmask 255.255.255.0 {
   range 192.168.2.2 192.168.2.255;
   option subnet-mask 255.255.255.0;
   option broadcast-address 192.168.2.255;
   filename "pxelinux.0";
   next-server 192.168.2.100;
}
# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;
```

I've found this [http://superuser.com/questions/149949/fedora-dhcpd-fails-to-start](http://superuser.com/questions/149949/fedora-dhcpd-fails-to-start) which is probably solution needed but i can't understand 

> I added a 5 second delay ('sleep 5') into the beginning of the start function in dhcp3-server's init.d script, this giving the network manager ample time to get the network interfaces set up (although of course there is still no guarantee) - and it worked.
- I see no start function in my /etc/init.d/dhcp3-server

somebody, please I really in need for help.

---

### Post by MezzFA0 on 2011-10-02
I know this is an old thread but as this was the thread that Google bought up while looking for an answer to the same problem, I'm posting the work around instructions for completeness.

The work around is trivial and hinted to by the OP.

The problem occurs because the dhcp server starts before the network interface is ready hence you get the 0.0.0.0 error.  This will vary depending on what hardware you have and I guess in some cases it just works.

For those of us who have the problem, edit your dhcp init script to wait for 5+ seconds.  Its not an elegant work around but it works.  You might have to wait for longer than 5 if you have really slow networking.

sudo vi /etc/init.d/dhcp3-server

On Line 73/74, you get to the service start line which is where you need to make the change. The lines should be:

[PHP]case "$1" in
    start)
        test_config
        <!-- snip --!>
[/PHP]

Add in sleep 5 before test_config, add some comments so that you know why its there in future.  I'm not sure exactly how init scripts and updates are handled but I would guess if dhcp is upgraded you might lose you changes to this file.

So after changes this section of your init script will be:

[PHP]case "$1" in
    start)
        # Work around for DHCP starting before network is ready
        sleep 5; # increase if necessary
        # End of work around
        test_config
        <!-- snip --!>
[/PHP]

As for the OP I hope you got it sorted before now.

---

### Post by jonobr on 2011-10-03
Excellent response post,

I wanted to add two more things

one is that I think his original range declaration is wrong
range 192.168.2.2 192.168.2.255
should be 
range 192.168.2.2 192.168.2.254 (255 is the broadcast range)

and his next server is down as range 192.168.2.2 192.168.2.100
If this is correct and an operational server it would have to be excluded and/or reserved in case this address is handed out.

Excellent post though!

---

