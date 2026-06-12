---
title: "Device ttyS1 is locked by pid 1691"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by Bartender on 2010-02-05
What the heck does "locked by pid###" mean??

I'm beating myself up trying to get online with a USR 5610B internal hardware modem.  

I know my ISP works with Linux.  I've been getting online for months now with a USR 5686E external.  I'd read that the 5610's were a little more difficult to set up than the externals.  I'm in above my head apparently.

Every time the PC restarts the modem is lost.
  
**GNOME-PPP**
Gnome-ppp just can't find it, even after I point it to ttyS1.  

**pppconfig**
pppconfig finds it, either by typing in "pon" several times, or going into pppconfig, editing the connection, and telling it to find a modem.  It finds a modem at ttyS1, I save the settings, it dials out.

**wvdial**
If I run wvdial from the terminal, it also can't find a modem.  If I set up wvdial.conf, it finds a modem at ttyS1 and dials.

If I use pppconfig or wvdial to find the modem, then close the application, gnome-ppp dials out.

As soon as the PC is restarted, it's all lost.

If I just start typing "pon", I get error messages, as described [here]("http://ubuntuforums.org/showthread.php?p=8771337#post8771337").  Every time I start the PC the pid # is different.

If someone can explain what pid is and how to address the problem that would be great.  I'd really like to figure out how to get the 5610's working.

---

### Post by Bartender on 2010-02-05
Well, it seems to be related to ownership and permissions somehow.  I haven't had to deal with either very much so kinda lost.

```
setserial -bg /dev/ttyS1
```

says device not available.  Or busy.  I can't remember now.

```
sudo setserial -bg /dev/ttyS1
```

give me feedback - "/dev/ttyS1 is a 15660" or something like that.  

```
ls -l /dev/ttyS1
``` gives me

crw-rw- 1 root dialout 4, 65 2010-02-05 /dev/ttyS1

I already went into Users and Groups and changed permissions for root and for me, then went into groups and made sure tty and dialout were configured similarly.  I was just guessing here but figured it couldn't hurt.

Found a post on Linux Questions where the OP did this 

```
chmod o+rw /dev/tty/S1
```

which changed output of ls -l /dev/ttyS1 to:

crw-rw-rw-  1 root dialout 4, 65 2010 etc. etc.

and gnome-ppp dialed out.  I thought I'd gotten somewhere but when I rebooted the modem was lost AGAIN and ls -l /dev/ttyS1 was back to crw-rw-

I'm pretty sure that I've somehow manged to fumble towards an answer.  Anyone with knowledge of how to change ownership of /dev/ttyS1 permanently?  Or know of a better solution?

---

