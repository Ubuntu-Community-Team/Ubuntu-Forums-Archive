---
title: "CIFS Errors On Shutdown"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by dbsoundman on 2008-12-23
I have a samba share set up between my openSUSE desktop computer and my Ubuntu laptop, with the desktop as the server. (Please, don't tell me I should use NFS instead of samba, samba works just fine). Everything works fine, automounting is  set up on the laptop and all that, aside from one thing: when I shut down the laptop, the ubuntu spash screen with the orange status bar appears as usual, times out, then a cursor appears, and two messages eventually show up. One says something like
```
CIFS VFS: server not responding
```
And the next one says something about "cmd 50". There are also some numbers listed in brackets before each message.

After a minute or so, this all times out and the laptop eventually shuts off, but I'm wondering what's causing this error and how I can fix it. It only happens when I've got the laptop in the network with the server; when it doesn't connect to the server, the message doesn't appear. Any ideas?

Thanks,
Dan

---

### Post by bryanl on 2008-12-23
The problem appears to be that the network shuts down before the shares are dismounted. There is a thread around here somewhere for how to modify the shutdown process to fix this but a search for it is giving me database errors.

Quick fix is to dismount the CIFS shares before you shutdown the laptop.

---

### Post by dmizer on 2008-12-24
Or you can have them unmount automatically: [http://ubuntuforums.org/showthread.php?t=293513](http://ubuntuforums.org/showthread.php?t=293513)

---

