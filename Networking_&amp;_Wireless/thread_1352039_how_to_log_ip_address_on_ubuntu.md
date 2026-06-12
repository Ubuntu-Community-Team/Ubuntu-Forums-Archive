---
title: "how to log ip address on ubuntu ?"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by ubfu on 2009-12-11
I wanted to keep track of what ip address connected from ISP since it's a dynamic ip address.

Is there any script or application that can keep track and log ip address connected to the internet ?

Thank you

---

### Post by byStanderone on 2009-12-11
...are you not using firestarter?

---

### Post by Iowan on 2009-12-11
[This]("http://www.whatsmyip.org/") will tell you your external IP address. 
I remember a thread asking how to find external IP address from command line - I'll need to search for it (or you can ;))
You can also check a service like [dyndns.com]("http://www.dyndns.com/") or [no-ip.com]("http://www.no-ip.com/").

---

### Post by ubfu on 2009-12-14
> **byStanderone said:**
> ...are you not using firestarter?
Does it log ip address ? 


> **Iowan said:**
> [This]("http://www.whatsmyip.org/") will tell you your external IP address. 
I remember a thread asking how to find external IP address from command line - I'll need to search for it (or you can ;))
You can also check a service like [dyndns.com]("http://www.dyndns.com/") or [no-ip.com]("http://www.no-ip.com/").

I mean I wanted to log my ip address so next time I am able to trace back at certain date on certain day which IP address I connected

---

### Post by x33a on 2009-12-14
```
grep -i "ppp" /var/log/messages
```this will show your all your entries, till the log gets rotated.

though this'll work only if you are using bridged mode.

---

### Post by ubfu on 2009-12-16
I am usinga router which it get ip address automatically

---

### Post by indigene on 2009-12-23
x33a - this grep command does not show external IP address - it shows this:
Dec 20 13:15:15 XXX-desktop kernel: [    0.902574] PPP generic driver version 2.4.2
Dec 21 09:02:36 XXX-desktop kernel: [    0.902581] PPP generic driver version 2.4.2
Dec 22 06:27:28 XXX-desktop kernel: [    0.906573] PPP generic driver version 2.4.2
Dec 23 07:02:17 XXX-desktop kernel: [    0.906559] PPP generic driver version 2.4.2

Or am I missing something in the command?

---

### Post by x33a on 2009-12-23
@ indigene,

are you manually connecting to the net? it'll only work in that case.

does ifconfig show the ip address?

---

### Post by indigene on 2009-12-23
No I'm not manually connecting. I have broadband on ADSL.

if config only shows the local IP address (inet addr:192.168.5.100  Bcast:192.168.5.255  Mask:255.255.255.0) not the external.

---

