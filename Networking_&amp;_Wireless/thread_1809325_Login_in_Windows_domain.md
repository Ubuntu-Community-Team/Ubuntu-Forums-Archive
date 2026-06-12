---
title: "Login in Windows domain"
date: 2011-07-21
forum: Networking &amp; Wireless
---

### Post by Macrotus on 2011-07-21
Hi all

With Kerberos it's possible to join and login in Windows domain. The easiest way to do is [this]("http://www.bauer-power.net/2008/05/join-ubuntu-804-to-windows-domain.html") or I think so...

When installing likewise-open, it installs Kerberos also. I have no idea what are those realms and other stuff. There's some guides (also by Microsoft!), but it's gibberish for me. My native language isn't English, so half of those words go in one ear and out from the other.

I'm running Windows Server 2008 R2 Enterprise SP1 and I'm able to join the domain with my Windows clients. Now I want to join with Ubuntu but I have no idea what to do.

If you guys have any kind of ideas I'd like to hear them. Like

[LIST]
[*]what's FQDN
[*]how to find out domain's FQDN
[*]Whats Kerberos realm and what it should contain
[*]how to install Kerberos correctly
[*]and so on
[/LIST]

Thanks

I hope someone will reply, there's many questions that nobody never replied.

---

### Post by Macrotus on 2011-07-21
I succesfully installed likewise-open-gui and other needed packages, but when joining domain I got error.

> Lsass Error

9502 (0x251E) DNS_ERROR_BAD_PACKET - A bad packet was received from a DNS server. Potentially the requested address does not exist.

Details

Error code: CENTERROR_DOMAINJOIN_LSASS_ERROR (0x00080047)

Backtrace:
    main.c:335
    djmodule.c:323
    djauthinfo.c:843
    djauthinfo.c:1187


What's wrong? I'm able to join Windows clients but not this one.

---

