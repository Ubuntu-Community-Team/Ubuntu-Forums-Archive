---
title: "Ubuntu 10.10 IPv4 connectivity?"
date: 2011-09-29
forum: Networking &amp; Wireless
---

### Post by naragam on 2011-09-29
Hi all,

I just got a dual boot (Windows 7 / Ubuntu) PC that connects fine in Windows 7, but fails to find the DNS server on Ubuntu. Is this because of Ubuntu 10.10 automatically configures IPv6? The university network has not gone to IPv6 yet and I need to disable IPv6 stuff on Ubuntu. I have already registered my MAC addr and my ethernet port is enabled with DHCP. Any help on getting my Ubuntu find the default DNS server on our network?

TiA,

Nash

---

### Post by An Sanct on 2011-09-29
Which version of Ubuntu are you using?

You can disable IPV6 if you edit your network connection. Just put your IPV6 mode to "Ignore" and IPV4 to "Automatic DHCP", also check the "Require IPV4 addressing for this connection to complete" checkbox.

---

### Post by naragam on 2011-09-29
I did disable IPv6 and enabled IPv4 by providing the missing MAC address and rebooted. Now Firefox browser comes up in offline mode, but still no connection to DNS server for name resolution. I can't ping even the unc.edu ... what now?

Nash

---

### Post by An Sanct on 2011-09-29
What missing MAC ???

Modifying the MAC/Cloned MAC may be *harmful** :) unless you know what you are doing.

*I'll explain "harmful" now - If your network is MAC locked, then modifying the mac maked the router think you are a *different* machine, and it refused to "DHCP" you an IP and DNS. Ubuntu takes your actual MAC by default, no need to modify it (98% of the time ;))

---

### Post by Loosewheel on 2011-09-29
> **naragam said:**
> Hi all,

I just got a dual boot (Windows 7 / Ubuntu) PC that connects fine in Windows 7, but fails to find the DNS server on Ubuntu. Is this because of Ubuntu 10.10 automatically configures IPv6? The university network has not gone to IPv6 yet and I need to disable IPv6 stuff on Ubuntu. I have already registered my MAC addr and my ethernet port is enabled with DHCP. Any help on getting my Ubuntu find the default DNS server on our network?

TiA,

Nash

Did you check /etc/resolv.conf?
You should have an "nameserver 192.168.1.1" entry, or what ever you router IPv4 addr is.

---

### Post by aura7 on 2011-09-29
Check Connect Automatically when you specify the details of the type of connection

---

### Post by naragam on 2011-09-29
> **An Sanct said:**
> What missing MAC ???

Modifying the MAC/Cloned MAC may be *harmful** :) unless you know what you are doing.

*I'll explain "harmful" now - If your network is MAC locked, then modifying the mac maked the router think you are a *different* machine, and it refused to "DHCP" you an IP and DNS. Ubuntu takes your actual MAC by default, no need to modify it (98% of the time ;))

By MAC I meant the MAC addr (ethernet).... nothing to do with iMac...lol

There was nothing in the MAC addr field when I looked at the system->Network Connections dialog. That's why I had to put my MAC addr and reboot. Doesn't matter...it still doesn't work.

Is this something that the IT network dudes have control of and I have to involve them? I'm an old Unix (BSD and System V days!) guy and too many things have changed since Linux and all other free s/w dev guys have been upgrading and updating the Linux versions. 

So far, all the obvious things that should have happened with Ubuntu have not happened.....*sigh*....this should not be this difficult.

Nash

---

### Post by naragam on 2011-09-29
> **aura7 said:**
> Check Connect Automatically when you specify the details of the type of connection

Yes...it has been checked! Still no go....

Nash

---

### Post by naragam on 2011-09-29
> **Loosewheel said:**
> Did you check /etc/resolv.conf?
You should have an "nameserver 192.168.1.1" entry, or what ever you router IPv4 addr is.

Well as I mentioned, things have changed from the original Unix. There is no resolv.conf... It is now resolvconf w/o the period. It has a subdir called update-libc.d which has a single executable called avahi.daemon....Huh?? Have no idea what this is !

I don't know where the nameserver entry is and where I should look...???

Nash

---

### Post by An Sanct on 2011-09-29
> **naragam said:**
> By MAC I meant the MAC addr (ethernet).... nothing to do with iMac...lolNash

I talked about *Media Access Control ...* no apple pie here ;)

If MAC is empty, leave it so - empty means "default" - default means HW assigned. (no need to interfere ...)

---

