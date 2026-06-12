---
title: "how to connect through a tunnel on adiffrent server"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by hanansela on 2011-07-19
Hi
I use two Ubuntu machines, one at home and one at work. In order to connect to the machine at work from home I need to connect through a "tunnel server" that controls all the traffic to the machines at work.   I am able to connect with ssh to the tunnel server and from the tunnel server ssh my own machine at work. My question is how do I retrieve files form my work machine to the home machine. How do I sync  folders between the machines using rsync  when the "tunnel server" is in between?
Thank you

---

### Post by jmoorse on 2011-07-19
I would recommend you talk to your office's IT dept.  This is probably controlled for a reason.

As far as I can tell with the information provided, you will not be able to establish a direct connection between your office machine and your home machine to do this.

There is always good old sneakernet: USB drive

---

### Post by hanansela on 2011-07-19
Thank you for the replay, USB flash drive is the solution I use now. In the IT department site there are instructions how to establish this connection to Win users but not to Linux. They recommend using _**[B]winscp**  [/B]_with sftp protocol. This tunnel also connects to buckup storage that I canot reach in other ways. I can always talk to IT guys, but this forum is more patient than them.
Thank you

---

### Post by jmoorse on 2011-07-19
Fair enough, i've been on both sides of the desk so I understand both parties :)

Ok, so for sftp you would be pulling files from some separate repository.  Are the files stored here or just on your desktop?

Perhaps you could ask them to break you off a port / ip from the firewall direct to your office machine?  It could be something like this:

wan ip tcp/22222 ---> office box tcp/22

You could also look into something like FreeNX:

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

Again, I don't condone any of this without checking that it isn't against your IT use policies.

---

