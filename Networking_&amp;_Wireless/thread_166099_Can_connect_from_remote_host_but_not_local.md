---
title: "Can connect from remote host but not local??"
date: 2006-04-25
forum: Networking &amp; Wireless
---

### Post by johnlon on 2006-04-25
I've got a machine that runs services, eg http.

I can connect to those services from other machines on the network, but if I'm on the machine itself I cannot connect to any of the local services?

A wierd situation.

eg hitting Apache just hangs - ie like you'd see if a firewall were in the way - but my firewall is wide open (I think).  Is there some other security facility thats in the way??

HELP

---

### Post by kingmonkey on 2006-04-25
this happens to me aswel when using an external web address on the local computer. weird. however aslong as it work ok for the rest of the world its ok by me. If I want to view it then I just use [http://localhost/](http://localhost/)

---

### Post by johnlon on 2006-04-26
Even localhost doesn't work.

It looks like no local app can connect to a local socket.
However, remote hosts can connect to those same sockets.

Other IPC's look ok like streams but not TCP ports.

---

### Post by kingmonkey on 2006-04-26
does your network ip work? or local host ip? 127.0.0.1?

If not look in /etc/hosts

---

### Post by johnlon on 2006-04-28
/etc/hosts lists 127.0.0.1 as localhost and also has an entry for the ip the eth0 uses.

I can connect to the outside world from my Ubuntu.
I can connect to Ubuntu from the outside world.
I cannot connect to Ubuntu from Ubuntu?


I'm guessing that this is something to do with the fact that Ubuntu is running in VMWare with the VMWare container in bridged mode to my physical network.

I've tried this sucessfully before though with Suse a couple of years ago so I have no idea if its a VMWare config issue or Ubuntu.:confused:

---

### Post by johnlon on 2006-04-28
I cant connect from the local machine to any local sockets.

I can connect from Ubuntu to remote and remote to Ubuntu but not Ubuntu to itself.

---

### Post by johnlon on 2006-05-03
Here's my twisted workaround.

Setup NAT on the VMWare adapter in the host OS (ie VMWare on windows).
Set NAT so that it redirects back into Ubuntu.

So to talk to local services from Ubuntu I actually direct the request at NAT on VMWare/Windows!

---

