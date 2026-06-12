---
title: "Samba needs restart"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by johnhenry on 2010-02-21
My Ubuntu 9.10 works well with the network through samba, but only if I first run -

sudo service samba restart

Then all is fine. I don't understand this.

How can I avoid having to do this? Or alternatively where can I best put this command so that it will be run on boot-up.

Any help would be gratefully received.

---

### Post by Iowan on 2010-02-21
Is Samba running (ie - is a _restart_ required, or would _start_ suffice)? If it's not running, you may be able to add it to System>Preferences>Startup Applictions.

---

### Post by johnhenry on 2010-02-21
Yes, excellent. Thank you. Starting Samba through the System > Preferences > Start up seems to work perfectly. So all is now well. I think I was misled because running "sudo service samba restart" got two OKs, for stopping and for restarting.

So I am not really sure whether Samba was already running, but imperfectly, or not. Anyway, it is running OK now, and giving full access to printer and shared directories.

Thanks again. Much appreciated.

---

