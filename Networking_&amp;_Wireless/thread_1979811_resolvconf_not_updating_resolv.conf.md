---
title: "resolvconf not updating resolv.conf"
date: 2012-05-14
forum: Networking &amp; Wireless
---

### Post by wocsnia on 2012-05-14
All,

I use resolvconf to update resolv.conf, to add various search domains to the auto-generated resolv.conf.

This used to work, but after upgrade to precise, the resolv.conf file does not contain the contents of /etc/resolvconf/resolv.conf.d/tail.

Restarting resolvconf (sudo /etc/init.d/resolvconf restart) seems to fix things, but its a pain to do this every time I undock my laptop.

Does anyone know if ubuntu now uses something other than resolvconf for updating resolv.conf and if so, can it add a custom domain search, without having to manually specify DNS servers?

---

### Post by jdthood on 2012-10-30
> **wocsnia said:**
> This used to work, but after upgrade to precise, the resolv.conf file does not contain the contents of /etc/resolvconf/resolv.conf.d/tail. Restarting resolvconf (sudo /etc/init.d/resolvconf restart) seems to fix things, but its a pain to do this every time I undock my laptop.

It sounds as if some other program is writing to /etc/resolv.conf. Are you using any networking-related applications from repos other than [FONT="Courier New"]main[/FONT]? E.g., are you using a third-party VPN client?

> Does anyone know if ubuntu now uses something other than resolvconf for updating resolv.conf and if so, can it add a custom domain search, without having to manually specify DNS servers?

There is a program called "openresolv" but it is not well integrated with Debian/Ubuntu. Resolvconf, on the other hand, has been available in Debian for many years and is now part of the Ubuntu base system.

With resolvconf you can add a search option using your interface configurer, generally ifup or NetworkManager.  For ifup you edit /etc/network/interfaces.  For NM you use the connection editor.

---

