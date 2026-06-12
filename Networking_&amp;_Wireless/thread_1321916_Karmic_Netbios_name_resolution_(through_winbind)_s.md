---
title: "Karmic: Netbios name resolution (through winbind) slow (in e.g. vinagre)"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by ghost_zero on 2009-11-10
Hi,

since I upgraded to karmic when using vinagre - actually I did a complete clean installation. I have a terrible Netbios name resolution speed. 
I did the same setup with winbind and nsswitch.conf as in Jaunty but it is terrible slow (it takes about 10-15 seconds; it work instantly in Jaunty).
However if I e.g. add ".local" at the end of the computer name (though of course this isn't Netbios name and that way won't work for all PCs) it works instantly.
Interesting though that when using ping it works nearly instantaneously though I use the Netbios name.

My guess is that there is either something wrong with my configuration or a bug in the new winbind version or something like this or it could also be a bug or misconfiguration in vinagre.

---

### Post by Iowan on 2009-11-10
I've heard/seen rumblings of **avahi** in Karmic - it seems to like the .local suffix.

---

### Post by dmizer on 2009-11-10
Do you have a local DNS server?

---

### Post by ghost_zero on 2009-11-11
No. I have no local DNS server (the router is forwarding the online DNS servers but that's it).

Futhermore it seems that ping instead of previously isn't resolving directly to just the IP address but actually is "pinging" the name with .local (though I didn't add the .local) at the end. I believe the option "dns proxy = yes" in smb.conf does help to avoid this BUT if I do so ping also takes longer.

@Iowan:
Is there some workaround for this?

---

### Post by Iowan on 2009-11-11
I'm sure the developers had good reason to include **avahi** in the mix, but it seems (to me, anyway) that **avahi** is more often connected with problems than solutions.  Perhaps its just because I don't know how it does (or should) work. Maybe there's a configuration option that lets you choose what (if any) suffix is added. I dunno what removing **avahi** would do...

---

### Post by ghost_zero on 2009-11-15
OK. I now found a solution to this that works perfectly for vinagre and ping.
Previously, I had found a solution that works for vinagre - though I didn't notice because I mainly tested with ping and that was actually already achieved by placing wins before dns in nsswitch.conf; though I thought I had done so already but seems like I didn't.
For ping to don't resolve to the .local suffix - which is a problem for some PCs, e.g. the Windows XP x64 one seems to don't like it; maybe I also configured something not completely correct there, I had to remove mdns4 at the end, the mdns4_minimal in the beginning can stay. It seems like for some reason that one (mdns4) gut used, although it was at the end of the line.
So my line looks like this now:
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns

That way it seems to work fine - or should I say the way I want it to work?

---

