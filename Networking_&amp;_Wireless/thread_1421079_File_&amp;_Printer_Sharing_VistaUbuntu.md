---
title: "File &amp; Printer Sharing Vista/Ubuntu"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by tacantara on 2010-03-03
I had a file/print sharing setup using my Vista laptop as a server.  I was able to access the printer and files on the hard drive using my Ubuntu laptop, until today.  When I attempt to connect to the Vista machine via Nautilus, nothing happens.  I've checked the IPA of the server, so I know it's not a wrong number that I'm using.  I can ping the server, yet I can't connect.

To make it more interesting, I set up my home folder as a shared folder.  I can access it from the Vista machine, so I know that the connection is working in at least one direction.

Again, I was able to connect to the Vista machine from Ubuntu until today.  I wonder if it was an update that broke something in Samba.  I can't put my finger on it.  Any ideas?

---

### Post by johnson.d on 2010-03-04
1) You can try the following command to check whether the Ubuntu machine recognizes the shares present in the Windows machine.

```
$ smbclient -L <ip-address of the Windows machine>
```

2) You can also try mounting the shared folder in the Ubuntu machine by using the command:

```
$ mount -t cifs //<ip-address>/<share-name>/ /<mount-point>/ -o user=<user-id>
```

The output of this command may be helpful in troubleshooting further.

---

