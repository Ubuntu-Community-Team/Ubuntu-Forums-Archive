---
title: "Fax server"
date: 2009-08-21
forum: Networking &amp; Wireless
---

### Post by Willn21 on 2009-08-21
Hi Friends,
I set up my modem thanks to [HotShotDJ]("http://ubuntuforums.org/member.php?u=196293") he was very helpful.
Now I need help setting up my fax server.
I installed hylafax.  I want it to save the faxes into pdfs onto a harddrive.
When I do faxstat I get this
> root@ubuntu:~# faxstat
HylaFAX scheduler on ubuntu: Running
Modem ttySHSF0 (5555555555): Running and idle

so how do I get it to receive incoming faxes

---

### Post by cariboo on 2009-08-21
Try calling the number the modem is connected to and see if it answers, it should answer automatically.

---

### Post by Willn21 on 2009-08-22
> **cariboo907 said:**
> Try calling the number the modem is connected to and see if it answers, it should answer automatically.

I did It didn't pick up

---

### Post by Willn21 on 2009-08-23
bump

---

### Post by Willn21 on 2009-08-23
bump

---

### Post by Willn21 on 2009-08-24
bump

---

### Post by jonobr on 2009-08-24
you probably need help from your fax modem vendor to figure out how to set auto answer on for your modem.

open to correction but As far As I can see its not really an ubuntu question yet.

With the old Hayes acura at command set on older modems, you could take a look at the response from the ati4 command issued to the modem.
It would tell you how the modem was set up.
If you look for ats0 and the number after it, it would tell you what autoanswer was set to

ats00 meant auto answer was off 
1-255 meant on and set to a certzain number of rings.

---

### Post by cariboo on 2009-08-24
WHen you ran sudo faxaddmodem what port did you setup for the modem? to setup the port correctly open a terminal and type:

```
ls -l /dev/modem
```

you should get something like this:

```
/dev/modem -> 536ep0
```

536ep0 is the device set up for the Intel modem I installed. you now have to link it to a tty. In my case the command looks like this:

```
ln -sf /dev/536pe0 /dev/tty15
```

After doing the above running faxsetup detects the modem properly and sets it up for hylafax to use.

---

### Post by Willn21 on 2009-08-27
Ok I linked it to tty15.
```

root@ubuntu:~# faxstat
HylaFAX scheduler on ubuntu: Running
Modem tty15 (+1.999.555.1212): Running and idle

```

It still doesn't pick up the call.  I even tested the cable on a real fax machine and it worked fine.

---

