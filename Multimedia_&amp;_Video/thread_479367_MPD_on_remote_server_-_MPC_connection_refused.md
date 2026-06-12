---
title: "MPD on remote server - MPC connection refused"
date: 2007-06-20
forum: Multimedia &amp; Video
---

### Post by infinitejones on 2007-06-20
I've got MPD running smoothly on my server, and the clients (MPC and GMPC) can connect to it fine from that machine. However, no clients can connect from my laptop which is connected via the LAN. 

When I run mpc or gmpc (or any client) from the command line on the laptop, I get :

error: problems getting a response from "localhost" on port 6600 : Connection refused

The laptop can ping the server, and everything else (ie. NFS sharing) is absolutely fine between the two machines. Both machines running feisty.

I searched through these forums for a couple of days and dug up just about every post related to mpd with no luck. Weirdly, when I do sudo dpkg-reconfigure mpd on the server, nothing happens - just a pause and the command line appears again.

The only two things I can think of are:

1) Do I need MPD running on the laptop? Surely not - I don't need to run Apache in order to browse the web.
2) Do I need to explicitly open a port on my router? Again, surely not - there's no traffic moving outside the network.

Any ideas? Thanks!

---

### Post by infinitejones on 2007-06-20
Any suggestions? Thanks!

---

### Post by infinitejones on 2007-06-21
Anyone feel like giving this one a go?

---

### Post by benlenarts on 2007-06-26
Have you tried disabling bind_to_address in /etc/mpd.conf?

---

### Post by crazybilly on 2007-08-03
that did it for me.  I commented out the bind_to_address line in /etc/mpd.conf on the server, restarted mpd and presto-boing-o: it worked.

---

