---
title: "Symbolic links in Samba Share in 10.04"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by tacman2k on 2010-05-12
Hello,

I just upgraded to lucid.

On my mythtv-box, I previously had a samba share which had 4 symbolic links inside of the folder. They would be available to everyone on the network.

Since the upgrade, the links are still there and point to the right folders, but are not available over the network.

---

### Post by lvleph on 2010-05-12
Edit /etc/samba/smb.conf and add the following two lines to your [global] section
```

follow symlinks = yes
wide symlinks = yes

```

Then run
```

sudo /etc/init.d/samba restart

```

---

### Post by tacman2k on 2010-05-12
I get a command not found when I try to run /etc/init.d/samba.



I did notice there is a smbd service that I can start/stop, but this does not fix the issue.



Looking at the log:
/var/log/samba.log.smbd

Unknown parameter "wide symlinks"


I changed it to just "wide links" but that did not solve the problem.

---

### Post by arsenic23 on 2010-05-12
> **tacman2k said:**
> I get a command not found when I try to run /etc/init.d/samba.

That's because it should have been *init.d/smbd*, BUT even that isn't correct anymore.  You should be restarting services with the service command:
```
sudo service smbd restart
```


Do you still have your smb.conf file from your previous install?  I normally just keep mine and overwrite the new default.  That would be the easiest way to return your samba setup back to status quo.

---

### Post by lvleph on 2010-05-16
Just realized they changed one more thing in Lucid.
It is no longer
```

wide symlinks = yes

```
rather it is now
```

wide links = yes

```

Also, you will need one other item in the global section
```

unix extensions = no

```

---

### Post by zukakog on 2010-05-23
Yep, that did it. I just changed wide symlinks to wide links.

My smb.conf now reads: ```
[global]

follow symlinks = yes
wide links = yes
unix extensions = no
```

and then ran: ```
sudo /etc/init.d/smbd restart
```

Thanks a bunch!

---

### Post by Beelzebud on 2010-06-28
Very helpful thread guys.   Glad I found it.  I had my symbolic links working, with shares, in a snap!  :)   Thankee

---

### Post by sickanimations on 2010-07-17
Perfect. I was playing with permissions for about 20 mins before I thought this could be the problem. Perhaps tag this as [SOLVED] ?

---

### Post by TxRx on 2010-08-22
Just like to thank everyone for keeping this updated, worth noting that if samba gets any update which 'replaces' your smb.conf with a default you'll have to re-apply the above.

---

### Post by robbyf on 2010-08-25
This worked for me, I googled this for like 2 hours, thanks for this post.

---

### Post by wege on 2010-09-26
Thanks worked as described.

---

### Post by charithjperera on 2011-02-06
Thanks very much, that worked out fine! :KS

---

