---
title: "Bind not starting when I boot"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by shadowfirebird on 2009-03-09
I'm gradually getting my new 8.10 machine working properly.  I've had all sorts of network issues.

The current one is that when I boot, the DNS service does not come up.  

Typing "sudo named -u bind", on the other hand, works fine.  As does "sudo /etc/init.d/bind9 start".

Any ideas how I can find out what is going on?  Nothing in dmesg that I can see, at least, no lines with "named" or "bind" in them...

---

### Post by lensman3 on 2009-03-09
Add the following link:

"ln -s ../init.d/named S28named" in the "/etc/rcd.d/rc3.d" directory.

Or find the program the sets up services, like "chkconfig".  "chkonfig" does nothing but the above "ln -s".  It also adds the "Kill" part to the SYS5 style boot-shutdown sequences.

Hope this helps.

---

### Post by shadowfirebird on 2009-03-09
I appreciate the help, but that doesn't appear to be the cause of the problem.

There is already a link between /etc/init.d/bind9 and /etc/rc3.d/S15bind9.

---

### Post by jonobr on 2009-03-09
sounds like everything is ready to work, just not running.

My guess is you are going to run level 2 but not on to run level 3

type 

```
who -r
```

If it says run level 2, then your system is not going to 3 and exectuing the Bind stuff.

You could boot to the next level on startup, or move bind to Rc2

---

### Post by jonobr on 2009-03-09
shoould have added the command

```
telinit 3
```

If it runs, you knows its runlevel related

---

### Post by shadowfirebird on 2009-03-09
Erm, no.  I think I would have noticed if I weren't at runlevel 3, because then I would not be able to log in?  

Quite happily purring along at runlevel 5, ta.  Except for not bringing bind up automatically.

I'm beginning to think that it may be the /etc/init.d/bind9 script.  In which case, I will report back here tomorrow -- I may not understand networking, but shell scripts I *can* do.

---

### Post by shadowfirebird on 2009-03-10
Solved.

Because of earlier network problems I had paranoidly added "-4" to /etc/default/bind9.  Or I thought that I had. In fact I had added "-v" -- return version number instead of starting the DNS server.

I guess the version information doesn't get sent to the log, or if it did, I took it to be a startup message.  

(Next: getting Samba working as a PDC.  Expect blood.)

---

### Post by jonobr on 2009-03-10
mmmm must study my runstates again.......

---

