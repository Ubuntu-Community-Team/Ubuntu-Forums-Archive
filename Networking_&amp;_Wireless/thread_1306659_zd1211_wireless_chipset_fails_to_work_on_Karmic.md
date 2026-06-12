---
title: "zd1211 wireless chipset fails to work on Karmic"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by ctw on 2009-10-30
Hi,

Anybody knows if the zd1211 chipset works in Karmic?

I can see my wireless hotspot,i can connect, but automatically it restarts and i lost the connection.

I saw by google that there is a bug about this chipset.

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1732615.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1732615.html)

With Ubuntu Jaunty and older my wireless card works without problems.

Anybody had a solution?

Thanks

---

### Post by marfal on 2009-10-31
I am currently testing Karmic on my old desktop with a Zyxel G202, which under jaunty works out thebox. signal 80-100% speed 36-54 mbps.
Under karmic it does work out the box but signal no more than 44% speed 1 mbps.
I have added to a bug report regarding this.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/445989](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/445989)

So YES it works but not well.

---

### Post by madsmaddad on 2009-11-04
I am using the ZD1211 chipset in a 3Com USB stick. It has worked fine in Kubuntu 7* and 8* and 9.04, but now does not connect. Network manager has allowed me to set it up, and if I select 'connect to other network' I can see other wireless networks in my neighbourhood. But I don't have/can't get a connection to my router. 

Without wireless I cannot upload anything either, unless I boot XP on that box.

---

### Post by SteveDee on 2009-11-04
I'm using a SafeCom USB Wfi and the zd1211rw driver which works, but suffers the same problem as Marfal, and is being discussed here: [http://ubuntuforums.org/showthread.php?t=1310176](http://ubuntuforums.org/showthread.php?t=1310176)

---

