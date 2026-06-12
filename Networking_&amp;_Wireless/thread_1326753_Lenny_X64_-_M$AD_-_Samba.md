---
title: "Lenny X64 - M$AD - Samba"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by Sniffer on 2009-11-14
Hi fellows,

Hope you can help me with this one:

My Situation:

VMWARE Workstation With 2 Guest:

WINDOWS 2008 R2 X64 ENTERPRISE SERVER CORE X64 (Domain Contr.)
DEBIAN LENNY X64 (File Server)

My host is WINDOWS 7  and it's outside the domain and anyone can ping everyone, even by name, dns are correct.

Debian is in the domain with the command:

net ads join -U administrator 

Debian can authenticate against the AD with:

kinit Administrator

Debian can get the users of the domain with:

wbinfo -g or -u

AND FINALLY I HAVE MADE the share on my SMB.CONF with:

[Share]
comment = Test Share
read only = no
path = /home/share
valid users = @"mydomain+domain users"

I have test with testparm and process the share and load service file OK.

THE PROBLEM:

I GO TO MY WINDOWS 7 BOX, EXPLORER, \\XXX.XXX.XXX.XX and i get network error...don't appear even the authentication box as it should...i ping debian and it pings right....

I have open iptables firewall, tough i think debian accept by default samba..without toutching iptables...

I have created a guest XP and try in explorer..obtain some error network error....

IT'S SOME KIND OF PROBLEM WITH SAMBA X64 OR WINDOWS 2008 R2 X64???!!!

I have tested this with Windows 2003 STD x86 and Debian Lenny X86 (UPDATE - MY MYSTAKE NOT LENNY X86 BUT ETCH X86, IN LENNY X86 DON'T WORK EITHER( AND IT F****C****G WORKS...in resume i'm becoming trashed by this one....

Thanks for all the help in advance.

Update: if i access the W2K8 DC by explorer with my windows 7 it works.

---

### Post by Sniffer on 2009-11-16
Not to Bump...it seems no one can help me on this one but in

UBUNTU 9.10 X64 the exact same configuration and it WORKS....

WHAT THE HELL IS HAPPENING IN LENNY, both X86 and X64 versions i can get to the share in explorer....

In ETCH it works also...can't understand...

---

