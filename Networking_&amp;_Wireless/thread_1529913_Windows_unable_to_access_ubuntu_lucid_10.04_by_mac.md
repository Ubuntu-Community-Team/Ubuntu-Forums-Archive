---
title: "Windows unable to access ubuntu lucid 10.04 by machine name, but able by IP address"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by darthwissen on 2010-07-12
Hello Everybody,

I am having problems trying to access my ubuntu computer from 2 Windows 7 computers. I am able to access by IP address, but unable to access by my ubuntu computer name. I need it to use printer sharing. It was working previously, no clue about what happened.

The only change I made was to set up samba to start after rc.local (or something like that) CUPS because I could access the computer but couldn't see the printers. (This is a known bug from ubuntu 10.04 and I used the proposed solution from linux bug tracker (or something like that)).

After this change it was still working fine, I have no idea what made it stop working. Maybe some linux updates, that is the only change I can remember.

Thanks in advance for your help,

Igor Campos

---

### Post by Iowan on 2010-07-12
Does the Lucid machine have static IP, or does it get it from DHCP server? IF DHCP, you might edit */etc/dhcp3/dhclient.conf* and change the line```
send host-name "<hostname>";
``` to use the real hostname.

---

### Post by darthwissen on 2010-07-12
Thanks for the response,

I tried that, no success after restarting machine. Any other ideas?

---

### Post by darthwissen on 2010-07-15
2 days without posts.

Could anyone in the ubuntu community help me?

---

### Post by darthwissen on 2010-07-15
Am I alone here? xD

Problem still not solved...

Thanks for any help that comes.

---

### Post by Iowan on 2010-07-16
What, if anything, are you using for local DNS? I suppose the real question is - Does the local DNS (which might be the router) have the name of the server? I presume you can't **ping** the machine by name, either...

---

### Post by darthwissen on 2010-07-16
Nope, the router name is volcano, the computer name is chocolate.

Thanks anyway

---

### Post by Iowan on 2010-07-16
Sorry - I didn't say what I meant... If you look in logs (on router) does it (the router) know what address is associated with **chocolate**? Can you ping **chocolate** (by name) from **volcano** (or any other machine)?

---

### Post by darthwissen on 2010-07-16
PING chocolate (192.168.0.102): 56 data bytes
64 bytes from 192.168.0.102: seq=0 ttl=64 time=0.408 ms
64 bytes from 192.168.0.102: seq=1 ttl=64 time=0.380 ms
64 bytes from 192.168.0.102: seq=2 ttl=64 time=0.366 ms
--- chocolate ping statistics ---
3 packets transmitted, 3 packets received, 0% packet loss
round-trip min/avg/max = 0.366/0.384/0.408 ms

Yes, the router sees it as chocolate

---

### Post by capscrew on 2010-07-16
> **darthwissen said:**
> PING chocolate (192.168.0.102): 56 data bytes
64 bytes from 192.168.0.102: seq=0 ttl=64 time=0.408 ms
64 bytes from 192.168.0.102: seq=1 ttl=64 time=0.380 ms
64 bytes from 192.168.0.102: seq=2 ttl=64 time=0.366 ms
--- chocolate ping statistics ---
3 packets transmitted, 3 packets received, 0% packet loss
round-trip min/avg/max = 0.366/0.384/0.408 ms

Yes, the router sees it as chocolate

I would install Wireshark.  Then you will see what name service is running.  Ultimately you should see NetBios over TCP unicasts and broadcasts.

---

