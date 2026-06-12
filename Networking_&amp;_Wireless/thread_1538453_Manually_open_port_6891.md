---
title: "Manually open port 6891"
date: 2010-07-25
forum: Networking &amp; Wireless
---

### Post by KristofferAG on 2010-07-25
I recently installed aMSN in favor of Pidgin, and want to try out the webcam feature. However, due to connectivity issues, it wont let me. It says I'm either firewalled or behind a router.

I was under the impression that, by default, all ports were open in Ubuntu. And that's the answer I've found most places. I've found some commands to be entered into the terminal, regarding iptables and ufw, but neither has worked. 

Is there anyone that can help an absolute ubuntu noob a bit here? I've got the latest update, Lycid Lynx.

Cheers

---

### Post by iponeverything on 2010-07-25
If your not blocking a port, it is open. Having a ports open is not a big deal if there is not a service listening.

This will tell you have rules in place:

```
sudo iptables -L

```

---

### Post by KristofferAG on 2010-07-25
Well, they all are set to ACCEPT, but it still says I'm either firewalled or behind a router. Any other solutions?

---

### Post by Iowan on 2010-07-25
Is that from the machine itself, or from another machine (same network or external)?

---

### Post by KristofferAG on 2010-07-25
I'm not sure I get your question. This computer I'm on is connected to the internet through a wireless router, I think. It's currently the only computer on my network. aMSN is telling me I'm behind a firewall or router, when I test the connection through the Preferences in the program. It's using that port to send files and webcam.

---

### Post by iponeverything on 2010-07-25
Setup your wireless router to forward 6891 to the box running amsn. The mechanism or process for doing this is usually different on every type of wireless router. Download and reference or google for instructions on your particular unit.   

From [http://amsn.sourceforge.net/wiki/tiki-index.php?page=FAQ](http://amsn.sourceforge.net/wiki/tiki-index.php?page=FAQ) :

> 
Q: I'm using amsn behind a firewall, or using IP-Masquerade. Sending files
won't work, can I fix it?
A: Maybe the firewall is blocking incoming connections. File transfers work
this way: When you want to send someone a file, you send an invitation with
your IP address and a port number. Then the remote client must connect to
your IP:port to start the transfer.
The used port is usually 6891, 6892 and so on (first transfer is on port 6891,
but if you start a new file transfer while the first one hasn't finished yet,
then it will use 6892, and so on).
So, if using a firewall, you must make sure that it allows incoming
connections to port 6891 (and next ones if you want to be able to make more
than one transfer at the same time).
If you're inside a private network with private addresses, like 192.168.0.x,
then it's more difficult to make file transfers work. You need to send the
real internet address (you can enter it manually or tell amsn to guess it
from a web page), instead of the internal address, and tell the gateway (the
computer with direct connection to the internet) to forward incoming
connections to port 6891 to your computer inside the private network.


---

