---
title: "on hardy, if-pre-up.d and if-post-down.d scripts not executed"
date: 2011-02-28
forum: Networking &amp; Wireless
---

### Post by greenmoss on 2011-02-28
Hello all,

I have a host running Ubuntu Hardy/8.04.4, and have some custom firewall save/restore scripts that I added in /etc/network/if-pre-up.d and /etc/network/if-post-down.d. These are very close to the ones found at [the Ubuntu iptables howto]("https://help.ubuntu.com/community/IptablesHowTo#Solution%20#2%20/etc/network/if-pre-up.d%20and%20../if-post-down.d").

I've verified that manually running ifup and ifdown runs my save/restore scripts. Also, when I **manually** run "/etc/init.d/networking stop" and "/etc/init.d/networking start", the scripts are executed. However when I **reboot**, the scripts are **not** executed. 

Why is this?

---

### Post by kevdog on 2011-02-28
I don't think network manager (I assume you are using this to connect to your network rather than the command line or other utility) reads these files.  They read a similar file (found way in the depths of directories, which for the life of me I can't remember right know.  Its in the Ubuntu wiki however).

---

### Post by greenmoss on 2011-02-28
Hardy doesn't start networking using /etc/init.d/networking start?

---

### Post by nutznboltz on 2011-03-01
You should post your /etc/network/interfaces file to explain how your network is configured.

---

### Post by greenmoss on 2011-03-01
I hacked my /etc/init.d/networking file to let me see how/when it was being invoked. The result shows that /etc/init.d/networking is **never** invoked at shutdown, but is invoked normally at system start. Looking in the /etc/rc*.d symlinks confirms this; there is only 

```

$ ls -lrt /etc/rc*.d/*net*
lrwxrwxrwx 1 root root 20 Sep 17  2009 /etc/rcS.d/S40networking -> ../init.d/networking

```

This is not what I was expecting. Is this normal for Hardy? If so, how does Hardy unconfigure its network interfaces and/or run network shutdown scripts? Or is this perhaps a bug in Hardy?

---

### Post by greenmoss on 2011-03-01
On later Ubuntu releases I **am** seeing additional symlinks which get invoked on shutdown:

```

$ ls -l /etc/rc*.d/*networking*
lrwxrwxrwx 1 root root 20 2010-10-31 18:22 /etc/rc0.d/S35networking -> ../init.d/networking
lrwxrwxrwx 1 root root 20 2010-10-31 18:22 /etc/rc6.d/S35networking -> ../init.d/networking

```

I added these two missing symlinks on my Hardy host, rebooted, and my shutdown scripts were executed properly. I will go file a Launchpad bug. 

So this issue is "worked around" for me.

---

### Post by greenmoss on 2011-03-01
Launchpad link: [on Hardy, missing symlinks for run levels 0 and 6]("https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/727470")

---

