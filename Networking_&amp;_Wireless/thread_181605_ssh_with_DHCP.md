---
title: "ssh with DHCP"
date: 2006-05-24
forum: Networking &amp; Wireless
---

### Post by pauljwells on 2006-05-24
I can connect by ssh between machines on my home network by specifying the IP address, fpr example:

```
ssh -X 192.168.2.2 -l username
```

However I have my network running everything on DHCP, so the IPs can change.

Can I set up something to allow ssh to use the host names instead of IPs, so that itdoesn't matter what the IP is? Or should I just swith to static IPs??

Thanks in advance!

---

### Post by 0MG on 2006-05-24
It would probably be in your best interest to set up a static IP scheme.

---

### Post by Iowan on 2006-05-24
It's possible to have clients report their hostname when they get a DHCP address.  There's a post about it here somewhere recently.

---

### Post by spd106 on 2006-05-24
It's here [http://www.ubuntuforums.org/showthread.php?t=177832]("http://www.ubuntuforums.org/showthread.php?t=177832")

Cheers for the clue Iowan

---

### Post by pauljwells on 2006-05-24
@ Iowan and spd106

Thanks! that looks like it might do it! I'll try it and report back...

---

### Post by pauljwells on 2006-05-24
WOW!!!

this is EXACTLY what I wanted!! I can now just type ssh -X hostname and it Just Works!

Thanks, guys!

I can now see all my network hosts properly named in the router's dhcp leases list. Before there were just weird names that looked like mac-address.belkin or somesuch.

---

### Post by spd106 on 2006-05-25
That's weird, it still doesn't work for me. The router client list shows hostnames now, but I still can't resolve them to ip addresses, ie ping won't work with hostnames.
Samba seems ok, I can browse names in nautilus. But that was working before, after I added netbios names to the smb.conf.

hmm, perhaps it's the belkin router? I've got an F5D7230-4

---

### Post by pauljwells on 2006-05-25
ping works for me

---

