---
title: "Disabled wireless on Dell inspiron"
date: 2010-11-19
forum: Networking &amp; Wireless
---

### Post by hardyfan on 2010-11-19
RESOLVED - Thanks everyone.

Sorry but I disabled wireless networking on my Dell Inspiron running Ubuntu 10.04 (can't remember how).  The option to enable is greyed out, I assume I have to have root access to re enable.  Is there a command to bring up networking tools from terminal after running the sudo command ?

Thanks in advance for your help.

---

### Post by eatberrys on 2010-11-19
In terminal try this:

This will display all network interfaces up or down:
```
sudo ifconfig -a
```
 

To bring up an interface type
```
sudo ifconfig <interface> up
```

To bring down an interface type
```
sudo ifconfig <interface> down
```

Ubuntu man page on ifconfig: [http://manpages.ubuntu.com/manpages/lucid/man8/ifconfig.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/ifconfig.8.html)

---

### Post by hardyfan on 2010-11-20
The list gives:
eth0
lo
ppp0
wlan0

Doesn't see wireless at all ?

---

### Post by spiky001 on 2010-11-20
wlan0 is wireless try ```
sudo ifconfig wlan0 up
```

---

### Post by hardyfan on 2010-11-23
Thanks but that just returned:

SIOCSIFFLAGS: unknown error 132

I booted off USB running netbook version of 10.10 wireless networking was still disabled in that situation.

---

### Post by halj32 on 2010-11-23
have you tried the little switch on the side of your laptop that turns the wifi on & off???

---

