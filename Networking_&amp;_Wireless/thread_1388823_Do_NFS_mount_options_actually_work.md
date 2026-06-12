---
title: "Do NFS mount options actually work?"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by movieman on 2010-01-23
I have a bunch of nfs mounts from my MythTV backend to my netbook, both running 9.10. Due to the lousy Atheros wireless driver, it typically loses connection at least every half hour.

The nfs mounts are mounted soft,intr, so programs should get an error trying to talk to a server they can't contact, and the request should be interruptable. Instead, they just lock up, can't be interrupted, and the netbook can't even shut down after the network failure because it hangs trying to clean up before shutting down.

So do these nfs options actually work in Ubuntu? 'mount' shows the nfs directory mounted with the correct options, so it doesn't seem to be any kind of configuration problem... it just doesn't do what I'm telling it to do.

---

### Post by dvrvm on 2010-04-05
I second that question.
I use both "soft" and "bg" options, and neither seems to change anything at all. Do I misunderstand what these options are doing, or have I not set up things correctly? What am I doing wrong?

---

### Post by Automaton111 on 2010-05-06
+1

What's going on with this?  I'm using 9.10 as well, and can't get soft-mounted NFS requests to time out.  ](*,)

---

