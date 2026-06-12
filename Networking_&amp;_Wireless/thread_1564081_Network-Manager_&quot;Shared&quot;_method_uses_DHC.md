---
title: "Network-Manager &quot;Shared&quot; method uses DHCP range 10.0.0.0"
date: 2010-08-30
forum: Networking &amp; Wireless
---

### Post by jasonbrisbane on 2010-08-30
Hello All,

I am setting up a gateway Ubuntu box and trying to do this the easiest way possible.

Using Network Manager in LL 10.04 I have eth1 (usb) accessing the net and eth0 (wired) set up and working.

eth1 has a static IP address of 192.168.0.2 and the USB box has 192.168.1.1.
This works and I have no issues with eth0.

In order to allow eth1 to "share" the connection I have gone toIPv4 and change the method to "Shared to this computer".

Network-Manager automatically starts a dhcp server and assigns ip's from the 10.x.x.x class of IP's.

My question?
WHERE IS THIS SET????

I want to change the assignable ip range to come from 192.168.1.x.

I have figured out that it is set in the dnsmasq-base package as uninstalling this and using:

> >sudo service network-manager restart
shuts down the eth0 completely - no IP can be assigned!

Reinstall dnsmasq-base and it assigns it back with a 10.42.43.1 IP. (and all other PC's on the network are set to the 10.42.43.x range.

Where is the dhcp range set?


HELP!
(please?)

---

### Post by jasonbrisbane on 2010-08-30
OK, some extra info.

the package dnsmasq-base has the following files:
> /.
/usr
/usr/sbin
/usr/sbin/dnsmasq
/usr/share
<snip>


So WTF? Why bother with dnsmasq if the program is in the 'base" package??

So the question is where is it called?

A ps -ax | grep dnsmasq helps a litle...

> 3397 ?        S      0:00 /usr/sbin/dnsmasq --no-hosts --keep-in-foreground --bind-interfaces --except-interface=lo --clear-on-reload --strict-order --listen-address=10.42.43.1 --dhcp-range=10.42.43.10,10.42.43.100,60m --dhcp-option=option:router,10.42.43.1 --dhcp-lease-max=50 --pid-file=/var/run/**nm-dnsmasq-eth0.pid**


So, it appears the network manager is calling this directly (see bold part).

Where is this being called?

A search of messages log reports that Avahi is to blame and a google of avahi dnsmasq shows the following link:
[http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBIQFjAA&url=https%3A%2F%2Fbugs.launchpad.net%2Fubuntu%2F%2Bsource%2Flibvirt%2F%2Bbug%2F231060&rct=j&q=avahi%20starts%20dnsmasq&ei=Eax7TNGNNtKwccb77YwG&usg=AFQjCNEEiOuVTIKRBOO6CqfARntS80GdMw&cad=rja](http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBIQFjAA&url=https%3A%2F%2Fbugs.launchpad.net%2Fubuntu%2F%2Bsource%2Flibvirt%2F%2Bbug%2F231060&rct=j&q=avahi%20starts%20dnsmasq&ei=Eax7TNGNNtKwccb77YwG&usg=AFQjCNEEiOuVTIKRBOO6CqfARntS80GdMw&cad=rja)

Which basically reports at the end that dnsmasq is being called with its own set of rules and NO config file info.

How do I report this as an error?

Surely if dnsmasq-base is installed then that is ok, but if you have an /etc/dnsmasq.d/dnsmasq.conf file then that is to be used......


Who wrote this code and how do I fix it?

---

### Post by jasonbrisbane on 2010-08-31
OK, so going through the source code there is no checking for an existing config file - NM simply creates its own settings and runs it. 

How stupid.


Now I find the VNC server is broken since the inclusion of extra gnome keyring code in vnc-server (refer:[http://www.google.com/url?sa=t&source=web&cd=5&ved=0CCUQFjAE&url=http%3A%2F%2Fwww.mail-archive.com%2Fubuntu-bugs%40lists.ubuntu.com%2Fmsg2269236.html&ei=HxB9TO6yFMSecb3sgKcF&usg=AFQjCNFAO13_SUWKFkdLDlQfwE_THJ8rzQ](http://www.google.com/url?sa=t&source=web&cd=5&ved=0CCUQFjAE&url=http%3A%2F%2Fwww.mail-archive.com%2Fubuntu-bugs%40lists.ubuntu.com%2Fmsg2269236.html&ei=HxB9TO6yFMSecb3sgKcF&usg=AFQjCNFAO13_SUWKFkdLDlQfwE_THJ8rzQ))

Well,

Since this is now so broken that I can no longer us it, I am ditching Ubuntu for Windows 7 that came with the new server, since at least the programs will work.

Well done Ubuntu, youve lost a Linux preacher to the Windows Evil.

Contact me if you want to fis this and win back one convert,m but I doubt you will... If you let basic functionality like this get included in the core OS then youve obviously no checking, or morals either.

Microsoft doesnt need Steve Balmer to put the knife in Linux,... He only needs Canonical to do horrid stuff like this....

:disappointed beyond belief:

---

### Post by pricetech on 2010-08-31
Have a nice day.

---

### Post by aintu on 2010-09-30
can someone plz locate this settings ????????????

---

### Post by theonislair on 2012-03-23
This is a pretty easy fix, however it does require that you uninstall NetworkManager and reinstall it by compiling from source code (with your edits).  There are two files that define this.

```

[root@vh1 NetworkManager-0.8.1]# grep "10.42.43" src/*
src/nm-device.c:    guint32 start = (guint32) ntohl (0x0a2a2b01); /* 10.42.43.1 */

```

This is the source code that defines the 10.42.43.1 IP address for the shared device, assigning this IP address to the shared device as the default gateway.  This definition is not in base10 or base2, but base16 as noted by:

```

ntohl (0x0a2a2b01); /* 10.42.43.1 */

```

You change the code 0a2a2b01 to whatever you wish to change the default gateway's IP address.  For easy conversions, use [http://www.kloth.net/services/iplocate.php](http://www.kloth.net/services/iplocate.php) and convert a "Dotted quad" into "Hex".  Should be cakewalk.  Make backups of the file first then make sure to save the changes.

A different file defines the actual address space used by DHCP:

```

[root@vh1 NetworkManager-0.8.1]# grep -r "dhcp-range" ./
./src/dnsmasq-manager/nm-dnsmasq-manager.c:    s = g_string_new ("--dhcp-range=");

```

Here is the excerpt from the file:

```

        s = g_string_new ("--dhcp-range=");

        /* Add start of address range */
        addr.s_addr = nm_ip4_address_get_address (tmp) + htonl (9);
        if (!inet_ntop (AF_INET, &addr, &buf[0], INET_ADDRSTRLEN)) {
                nm_log_warn (LOGD_SHARING, "error converting IP4 address 0x%X",
                             ntohl (addr.s_addr));
                   goto error;
        }
        g_string_append (s, buf);

        g_string_append_c (s, ',');

        /* Add end of address range */
        addr.s_addr = nm_ip4_address_get_address (tmp) + htonl (99);
        if (!inet_ntop (AF_INET, &addr, &buf[0], INET_ADDRSTRLEN)) {
                nm_log_warn (LOGD_SHARING, "error converting IP4 address 0x%X",
                             ntohl (addr.s_addr));
                   goto error;
          }
    g_string_append (s, buf);

```

There are only two lines that need to be changed here:

```


        /* Add start of address range */
        addr.s_addr = nm_ip4_address_get_address (tmp) + htonl (9);

```

and

```

        /* Add end of address range */
        addr.s_addr = nm_ip4_address_get_address (tmp) + htonl (99);

```

This code produces an IP address range of 10-100.  I know what you're thinking, 9 and 99?  Remember that .1 is already taken.  So in essence if you want an IP address range of 200 - 254, insert 199 and 253 into the start and end lines respectively.  Take the starting IP address and subtract 1, then take the ending IP address and subtract 1.

PLEASE NOTE:

These files are from the NetworkManager source code available from a .src.rpm for EL6 (CentOS).  However I am quite sure that all of the file sources are pretty much the same (depending on the version of NetworkManager being used).  I hope this helps.

---

### Post by lavacano on 2012-04-03
against precise current

```
--- network-manager-0.9.4.0.orig/src/nm-device.c
+++ network-manager-0.9.4.0/src/nm-device.c
@@ -1585,7 +1585,7 @@ release_shared_ip (gpointer data)
 static guint32
 reserve_shared_ip (void)
 {
-	guint32 start = (guint32) ntohl (0x0a2a0001); /* 10.42.0.1 */
+	guint32 start = (guint32) ntohl (0xc0a80001); /* 192.168.0.1 */
 	guint32 count = 0;
 
 	while (g_hash_table_lookup (shared_ips, GUINT_TO_POINTER (start + count))) {
--- network-manager-0.9.4.0.orig/src/dnsmasq-manager/nm-dnsmasq-manager.c
+++ network-manager-0.9.4.0/src/dnsmasq-manager/nm-dnsmasq-manager.c
@@ -308,7 +308,7 @@ create_dm_cmd_line (const char *iface,
 	s = g_string_new ("--dhcp-range=");
 
 	/* Add start of address range */
-	addr.s_addr = nm_ip4_address_get_address (tmp) + htonl (9);
+	addr.s_addr = nm_ip4_address_get_address (tmp) + htonl (1);
 	if (!inet_ntop (AF_INET, &addr, &buf[0], INET_ADDRSTRLEN)) {
 		nm_log_warn (LOGD_SHARING, "error converting IP4 address 0x%X",
 		             ntohl (addr.s_addr));
@@ -319,7 +319,7 @@ create_dm_cmd_line (const char *iface,
 	g_string_append_c (s, ',');
 
 	/* Add end of address range */
-	addr.s_addr = nm_ip4_address_get_address (tmp) + htonl (99);
+	addr.s_addr = nm_ip4_address_get_address (tmp) + htonl (253);
 	if (!inet_ntop (AF_INET, &addr, &buf[0], INET_ADDRSTRLEN)) {
 		nm_log_warn (LOGD_SHARING, "error converting IP4 address 0x%X",
 		             ntohl (addr.s_addr));
```

gives us 192.168.0.1 range 192.168.0.2-192.168.0.254

---

### Post by lavacano on 2012-04-03
Disabled tests...

[http://ubuntuone.com/1dXkfwqDEbkf5Bsf84CZcL](http://ubuntuone.com/1dXkfwqDEbkf5Bsf84CZcL)

amd64 build with the above specs

---

### Post by jpthompson23 on 2013-01-10
> **theonislair said:**
> This is a pretty easy fix, however it does require that you uninstall NetworkManager and reinstall it by compiling from source code (with your edits).  There are two files that define this.

```

[root@vh1 NetworkManager-0.8.1]# grep "10.42.43" src/*
src/nm-device.c:    guint32 start = (guint32) ntohl (0x0a2a2b01); /* 10.42.43.1 */

```

This is the source code that defines the 10.42.43.1 IP address for the shared device, assigning this IP address to the shared device as the default gateway.  This definition is not in base10 or base2, but base16 as noted by:

```

ntohl (0x0a2a2b01); /* 10.42.43.1 */

```

You change the code 0a2a2b01 to whatever you wish to change the default gateway's IP address.  For easy conversions, use [http://www.kloth.net/services/iplocate.php](http://www.kloth.net/services/iplocate.php) and convert a "Dotted quad" into "Hex".  Should be cakewalk.  Make backups of the file first then make sure to save the changes.

A different file defines the actual address space used by DHCP:

```

[root@vh1 NetworkManager-0.8.1]# grep -r "dhcp-range" ./
./src/dnsmasq-manager/nm-dnsmasq-manager.c:    s = g_string_new ("--dhcp-range=");

```

Here is the excerpt from the file:

```

        s = g_string_new ("--dhcp-range=");

        /* Add start of address range */
        addr.s_addr = nm_ip4_address_get_address (tmp) + htonl (9);
        if (!inet_ntop (AF_INET, &addr, &buf[0], INET_ADDRSTRLEN)) {
                nm_log_warn (LOGD_SHARING, "error converting IP4 address 0x%X",
                             ntohl (addr.s_addr));
                   goto error;
        }
        g_string_append (s, buf);

        g_string_append_c (s, ',');

        /* Add end of address range */
        addr.s_addr = nm_ip4_address_get_address (tmp) + htonl (99);
        if (!inet_ntop (AF_INET, &addr, &buf[0], INET_ADDRSTRLEN)) {
                nm_log_warn (LOGD_SHARING, "error converting IP4 address 0x%X",
                             ntohl (addr.s_addr));
                   goto error;
          }
    g_string_append (s, buf);

```

There are only two lines that need to be changed here:

```


        /* Add start of address range */
        addr.s_addr = nm_ip4_address_get_address (tmp) + htonl (9);

```

and

```

        /* Add end of address range */
        addr.s_addr = nm_ip4_address_get_address (tmp) + htonl (99);

```

This code produces an IP address range of 10-100.  I know what you're thinking, 9 and 99?  Remember that .1 is already taken.  So in essence if you want an IP address range of 200 - 254, insert 199 and 253 into the start and end lines respectively.  Take the starting IP address and subtract 1, then take the ending IP address and subtract 1.

PLEASE NOTE:

These files are from the NetworkManager source code available from a .src.rpm for EL6 (CentOS).  However I am quite sure that all of the file sources are pretty much the same (depending on the version of NetworkManager being used).  I hope this helps.

Is Canonical serious?  Instead of making this easy for the user to configure, they put it in the SOURCE CODE OF NETWORK MANAGER??????? ARE THEY FREAKING SERIOUS??? THIS IS THE DUMBEST THING I HAVE EVER SEEN!

---

### Post by lion1969 on 2013-08-07
This is really crazy!!!!!!!
A simple thing still unsolved after all these years.
Canonical please change for a better pusher.

---

### Post by bab1 on 2013-08-07
> **lion1969 said:**
> This is really crazy!!!!!!!
A simple thing still unsolved after all these years.
Canonical please change for a better pusher.

There is nothing to fix.  dnsmasq-base is just for network manager.  Using the full DNSmasq will allow you to configure all aspects of the operation.

Try not to post to old posts.  The information is just that; OLD!

---

### Post by papibe on 2013-08-07
Please don't reply on old threads. It is much better to create a new one. Feel free to link this one if you want.

From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

**Thread Closed**.

---

