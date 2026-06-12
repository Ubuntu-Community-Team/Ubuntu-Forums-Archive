---
title: "smb share path from command line"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by GandalfTheNerd on 2009-07-18
I've setup a network share between two Jaunty machines.  It works like a dream, though I do have a question.

Can I address the share from a command line?  I have a script to do backups across the network, but using the new Jaunty method, the path (in Nautilus) is of the form "smb://<machine name>/<share name>".  This is fine in Nautilus, but doesn't seem to work from the command line.  I get "No such file or directory" errors if I try!

Is there some way to get around this?

---

### Post by swerdna on 2009-07-18
You can get ftp-like access with "smbclient". Have a look at "man smbclient". The command is like: smbclient //server/sharename

---

### Post by GandalfTheNerd on 2009-07-18
Thanks for that.  It would let me write a script, yes.  My current method involves using rsync, which I don't think can be made to work that way.  Perhaps I need to re-think how I keep my machines synchronized!

---

### Post by doas777 on 2009-07-18
i think it shoudl work. just use smbclient to mount the share on the local filesystem, then write the rsynch command to target that directory. the technology used to facilitate the mount shoudl be hidden from any application that uses that mount point.

---

### Post by GandalfTheNerd on 2009-07-18
Now I'm catching on.  I'll give that a go!  Many thanks for the help.

---

### Post by swerdna on 2009-07-18
You can use a cifs mount to mount a Samba share in a directory on the client, as if it was a partition attached to the client, and rsynch to that.

---

### Post by GandalfTheNerd on 2009-08-07
I tried CIFS and it worked a treat.  Thanks for the help!

---

