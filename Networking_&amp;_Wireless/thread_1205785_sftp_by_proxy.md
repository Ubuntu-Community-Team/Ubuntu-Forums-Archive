---
title: "sftp by proxy"
date: 2009-07-06
forum: Networking &amp; Wireless
---

### Post by apocalypse80 on 2009-07-06
I use a few university servers.
They allow ssh connections and I also mount my directory through sftp (via the "Connect to server" dialog);
It all works fine when I am on the university lan.

The same servers do not allow direct connections from the outside world.
I have to ssh to an intermediate server (which does not have access to my directory) then ssh from that to one of the internal servers.
It all works well, but I can't mount my directory through the "connect to server" dialog - and that is a huge inconvenience.

How would I go about mounting my directory in this scenario?

---

### Post by jonobr on 2009-07-06
Hello


Im not sure if this will help, but there is a utility called tssh which is a wrapper which tunnels ssh through untrusted machines.

if you go to nixbit.com and search for tssh you will find it.

I do use it to connect to several machines but I do it via command line, im not sure if this can be inserted some how into the gui?
But via command line you could invoke tscp to copy again through unknown/untrusted intermediate points

---

