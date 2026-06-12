---
title: "How to send popup or msg over home network 9.04"
date: 2009-06-30
forum: Networking &amp; Wireless
---

### Post by Ozdemon on 2009-06-30
I cannot find a way of sending messages, preferably popups, over my home network.  All connected pc's are running 9.04. I have root access to all.

I have read about programs that are meant for windows(!) such as Samba, or cli methods I don't understand such as gxmessage.

Is there a reasonably simple way of sending messages over a Ubuntu home network?

---

### Post by Iowan on 2009-06-30
There may be (probably are) other options, but check out the **wall** command (**man wall**).

---

### Post by MaindotC on 2009-06-30
[Zenity](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/) ftw

---

### Post by meshellwm on 2010-01-23
I manages to implement a 'net_send' script for Linux and I was able to get Samba to respond and display popup messages when sent to it by name, see below:

[http://home.earthlink.net/~meshellwg/w/www/html/LinSMB.html](http://home.earthlink.net/~meshellwg/w/www/html/LinSMB.html)

My problem is: If I send a broadcast message from a Windows PC using, say, 'net send * Hello', all of the Windows PC's get the message, but the Linux PC's, running Samba, ignore it. How can I get Samba to respond to the broadcast message?

---

