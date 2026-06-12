---
title: "Custom uninstall MythTV"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by jboehm on 2007-04-25
Hi,

I compiled my own Myth and it in installed /usr/local/..   Now I need to uninstall the apt-get packages, but the tricky part is that there are config files that are shared between the apt-get package and my manually compiled version. I'm sure the automatic uninstaller will trash the config files too.  How would I uninstall the apt-get Myth package without blowing away the shared files?

Thank,
Jon

---

### Post by tgm4883 on 2007-04-25
back up the config files, after you uninstall mythtv, restore you config files

---

### Post by jboehm on 2007-04-25
There has to be a better way.  I could do that but first I need a complete list of the file that apt-get intends to remove.  Any idea on how I get this?

Jon

---

### Post by tgm4883 on 2007-04-25
If you do remove mythtv without using purge, your config files should be fine

also, if you use the -s option with apt-get it will simulate the operation and you will see what it is going to remove

---

### Post by tgm4883 on 2007-04-25
What you want to do is kinda risky, and someone with knowledge of the packages better could tell you what to do with more confidence. 

I am waiting to hear back from a friend who is better aquainted with the packages. You can stop by #ubuntu-mythtv for help too

---

### Post by jboehm on 2007-04-25
Can you explain how to do a remove without a purge?

---

### Post by tgm4883 on 2007-04-25
"apt-get remove" is without a purge, "apt-get remove -purge" would be with a purge

Im still waiting for superm1 to get back though

---

### Post by jboehm on 2007-04-25
What is #ubuntu-mythtv? Is this an IRC channel?

---

### Post by tgm4883 on 2007-04-25
yes

---

### Post by superm1 on 2007-04-25
Okay, here is the deal in terms of what you should do.

You need to backup /etc/mythtv.  The binary packages will store all configuration related items there.  Also be sure to backup the mysql database.

*purge* the packages:
```
sudo apt-get remove --purge mythtv-frontend mythtv-backend mythtv-common  mythtv-database
```

Restore /etc/mythtv/mysql.txt.  There are also other config files that may have been in there related to plugins.  You will have to restore those to the appropriate locations on your own.

You will likely need to fix permissions on your mysql database for the mythtv user.  You will also need to recreate the mythtv user, recreate an init script to use for mythtv-backend.
-----
All in all, it is a lot of work to switch over.  Are you sure that you want to be using source packages?

---

### Post by jboehm on 2007-04-26
So there is not custom unintall?  Something like a big that big (yes/no) list that shows up when compiling a kernel?

---

### Post by superm1 on 2007-04-26
I described the way to do an uninstall, you risk running into other troubles if you try to mix and match source and binary packages.


Why are you trying to mix them?

---

### Post by jboehm on 2007-05-03
> **superm1 said:**
> I described the way to do an uninstall, you risk running into other troubles if you try to mix and match source and binary packages.


Why are you trying to mix them?

Thats just it.  I want to remove all of the myth binaries with out touching the config files.  For example.  I don't want /etc/init.d/mythbackend removed or the ~/.mythtv folder.

Thanks,
Jon

---

