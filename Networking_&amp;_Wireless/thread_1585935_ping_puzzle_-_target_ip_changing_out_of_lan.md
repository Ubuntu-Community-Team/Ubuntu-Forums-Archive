---
title: "ping puzzle - target ip changing out of lan"
date: 2010-10-01
forum: Networking &amp; Wireless
---

### Post by holiday on 2010-10-01
Can anyone explain why the ping target IP changes in the snippet below?


stephen@vaio:~$ ping mbp
PING mbp (198.168.2.203) 56(84) bytes of data.
From 207.253.250.164 icmp_seq=1 Time to live exceeded
From 207.253.250.164 icmp_seq=2 Time to live exceeded

And nslookup cannot find any hostname for that IP address.

I must add that I used to be able to SSH to mbp from the other computers on my LAN and that I can SSH from mbp to the other computers. There is no active firewall on mbp, and no entries in /etc/hosts.deny

---

### Post by lloyd_b on 2010-10-01
> **holiday said:**
> Can anyone explain why the ping target IP changes in the snippet below?


stephen@vaio:~$ ping mbp
PING mbp (198.168.2.203) 56(84) bytes of data.
From 207.253.250.164 icmp_seq=1 Time to live exceeded
From 207.253.250.164 icmp_seq=2 Time to live exceeded

And nslookup cannot find any hostname for that IP address.

I must add that I used to be able to SSH to mbp from the other computers on my LAN and that I can SSH from mbp to the other computers. There is no active firewall on mbp, and no entries in /etc/hosts.deny

No clue as to why the IP address changes, but are you sure about the IP address on 'mbp'?  "198.168.2.203" looks like a typo for a reasonable "non-routable" address ("192.168.2.203").  Could it be a glitch with your nameserver?

Try ssh'ing to 192.168.2.203 and see if my guess is correct...

Lloyd B.

---

### Post by relay_man on 2010-10-01
The 207.253 address is a hop along the path towards your intended ping target.  When your ping request reached the router @ 207.253.XXX.XXX, its time to live had expired and it was dropped.
207.253 sent a message back to you to let you know that it had dropped your ping.  Rest assured that the IP address you intended to ping had not been changed.

---

### Post by holiday on 2010-10-01
> **lloyd_b said:**
> No clue as to why the IP address changes, but are you sure about the IP address on 'mbp'?  "198.168.2.203" looks like a typo for a reasonable "non-routable" address ("192.168.2.203").  Could it be a glitch with your nameserver?

Try ssh'ing to 192.168.2.203 and see if my guess is correct...

Lloyd B.

Nice guess, Lloyd! Thank You.  

My /etc/hosts for mbp was mis-typed on both ping clients. It was correct on mbp - for the other machines - so: puzzle solved.

I still want to understand that IP switch, though.

---

### Post by holiday on 2010-10-01
> **relay_man said:**
> The 207.253 address is a hop along the path towards your intended ping target.  When your ping request reached the router @ 207.253.XXX.XXX, its time to live had expired and it was dropped.
207.253 sent a message back to you to let you know that it had dropped your ping.  Rest assured that the IP address you intended to ping had not been changed.

You came in with this while I was working on Lloyd's suggestion - which got my machines all together again. 

Thanks for completing the solution to my puzzle.

---

