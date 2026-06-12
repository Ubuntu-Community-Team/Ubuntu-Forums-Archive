---
title: "Upgrade to 9.10, Can't Resolve Hostname"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by null77 on 2009-11-02
Hi,

Have two connections done with connection manager, one with ICS and one with static IP. I can access the box from it's ip (192.168.1.8) but not it's hostname, which means it doesn't show up in Window's network. 

I read some threads that talked about a DNS server, so I messed around with dnsmasq but that didn't seem to help.. I notice right now I have both bind and dnsmasq running. /etc/hostname is set properly, and in /etc/hosts I have my hostname bound to 127.0.1.1. 

So what's the deal, any help? Other than adding the IP manually to every computer's hosts file?

Thanks.

---

### Post by houstonbofh on 2009-11-02
How does your network do name resolution?  That is where you have to go for the fix.

---

### Post by Sasayaki on 2009-11-02
Same problem here for me, although for me I also swapped out my modem. I can ping and SSH by hostname to my various Ubuntu boxes from my one Windows box, but I can't ping it nor any other Ubuntu machine by hostname from an Ubuntu box.

Very frustrating, since it was 'just working' before I swapped out the modem- and pinging from within Windows works, so it must be an Ubuntu issue...

Edit: Browsing by samba shares works just fine from all sides, it's only ping/ssh that don't.

---

### Post by houstonbofh on 2009-11-02
> **Sasayaki said:**
> Same problem here for me, although for me I also swapped out my modem.
Your modem was probably doing name resolution.  Now it isn't.  This is not an ubuntu problem.

---

### Post by Iowan on 2009-11-02
> **null77 said:**
>  I notice right now I have both bind and dnsmasq running.  Too many bosses - one should go. I have **dnsmasq** on my server, and it seems to work as advertised. I can **ping** (by name) any machine that provides **dnsmasq** it's hostname when it requests a DHCP lease.
> **Sasayaki said:**
>  and pinging from within Windows works... What is Windows using for DNS setting?

---

### Post by Sasayaki on 2009-11-02
> **houstonbofh said:**
> Your modem was probably doing name resolution.  Now it isn't.  This is not an ubuntu problem.

Well, it's working under Windows, as I said- my laptop (tymanther) can be pinged by name from my Windows 7 box (akanul), but tymanther can't ping akanul by name, nor aglarond (an Ubuntu server). Windows 7 can ping all of them.

> **Iowan said:**
> What is Windows using for DNS setting?

I'll be able to tell you as soon as I get home from work (six hours or so).

---

### Post by null77 on 2009-11-02
> **Iowan said:**
> Too many bosses - one should go. 

This seems like good advice -- but I notice one is a special one for use with ICS, while the named service seems to be just vanilla. I don't know how the ICS stuff works though, so not sure how to get rid of the dnsmasq that is used automatically.

---

### Post by null77 on 2009-11-02
Ok, I tried uninstalling bind9, and enabling dnsmasq, and completely disabling my ICS connection, but this doesn't seem to do anything. Also tried disabling ufw. Is it possible that the problem might be related to a service like avahi or nmbd? 

How does a computer make it's hostname known to other computers on the network? I mean, how do my windows and mac boxes know about each other, while my ubuntu box can't detect either of them?

---

### Post by null77 on 2009-11-02
Solved the problem. It was because I had not replaced my smb.conf when I upgraded, and kept my old one. For some reason removing my smb.conf and restarting samba fixed the problem, I guess because Samba acts as a WINS server and this is how the hostname gets propagated.

edit -- the problem may have just been samba was not started. sigh.

---

### Post by Sasayaki on 2009-11-03
> **Iowan said:**
>  What is Windows using for DNS setting?

Windows is using "Obtain DNS servers automatically".

Some output which might help:

> **"/etc/dhcp3/dhclient.conf"]
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

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8 said:**
> 


[quote="/etc/nsswitch.conf"]
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns wins
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis


Any thoughts? Once again, it works perfectly fine in Windows...

Edit: BTW samba is running, and browsing by Samba shares (smb://algarond) works just fine.

---

### Post by Sasayaki on 2009-11-03
Weird.

I reflashed the modem (A Dlink DSL-504T) from its original firmware to a RouterTech firmware and the issue went away. I'll chalk it up to some weird thing in the way the modem was handling internal DNS.

---

