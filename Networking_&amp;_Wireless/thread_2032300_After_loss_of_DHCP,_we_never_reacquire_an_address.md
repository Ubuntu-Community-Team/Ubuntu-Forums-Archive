---
title: "After loss of DHCP, we never reacquire an address"
date: 2012-07-23
forum: Networking &amp; Wireless
---

### Post by dave on 2012-07-23
Hi all,

I've been having weird issues lately with DHCP and the title is a summary.  I have a headless-server install in a data center that acquires it's IP via DHCP.  However, given the past couple weeks and having unstable DHCP, it seems that I've run into a problem.

If the DHCP server goes down, my machine will eventually go offline, as expected.  I assume it tries to re-acquire it's lease, failing to do so it drops the IP and now waits.  The problem here is that, even when DHCP comes back online, my machine never seeks out another address.  Ever.

Looking at syslog, I see

```

Jul 19 17:36:24 toaster dhclient: DHCPREQUEST of 129.21.49.9 on eth0 to 129.21.49.142 port 67
Jul 19 17:37:31  dhclient: last message repeated 7 times

```

(this sequence of REQUEST, and last message repeated x times, happens over and over until it I guess expires the lease and starts to DISCOVER)..at:

```

Jul 19 18:48:02 toaster dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3

```

... many DISCOVERS, until the last one, only 5 minutes later.

```

Jul 19 18:53:01 toaster dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
Jul 19 18:53:03 toaster dhclient: No DHCPOFFERS received.

```

Then, dhclient is silent.  Never again to attempt to obtain an address.

How does one solve potential long periods of loss of DHCP?

Thanks!
--
dave

---

### Post by papibe on 2012-07-23
Hi dave.

The first thing that cross my mind is that you need a static LAN IP as soon as possible because your server can't provide its services with an unreliable DHCP server.

BTW, static IPs should be the standard on a data center, IMO.

Just a thought.
Regards.

---

### Post by dave on 2012-07-23
I assume that's probably the best probable cause, I was just hoping that there was a way to say "check once every 10 minutes when you failed".

It's static-ish, and it's a personal machine in a makeshift data-center at a university learning facility, not a commercial one.

---

### Post by Cheesehead on 2012-07-23
To change the amount of time a dhcp client seeks the server, the settings are in /etc/dhcp/dhclient.conf

See man dhclient.conf
```
timeout time ;

       The timeout statement determines the amount  of  time  that  must  pass
       between the time that the client begins to try to determine its address
       and the time that it decides that it's not going to be able to  contact
       a  server.   By default, this timeout is 300 seconds.   After the time&#8208;
       out has passed, if there are any static leases defined in the  configu&#8208;
       ration  file,  or  any leases remaining in the lease database that have
       not yet expired, the client will loop through these  leases  attempting
       to validate them, and if it finds one that appears to be valid, it will
       use that lease's address.   If there are  no  valid  static  leases  or
       unexpired  leases  in  the  lease database, the client will restart the
       protocol after the defined retry interval.



retry time;

       The retry statement determines the time that must pass after the client
       has  determined  that  there  is no DHCP server present before it tries
       again to contact a DHCP server.   By default, this is five minutes.
```

---

