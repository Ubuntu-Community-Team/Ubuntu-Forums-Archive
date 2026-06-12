---
title: "auto-syncing my docs and stuff"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by davbren on 2008-12-15
Hey, I was wondering is there a way of setting up a system thats used specifically for syncing my docs from my laptop to that system wirelessly and automagically...?

---

### Post by jonobr on 2008-12-15
Hello


Are you going from Ubuntu to windows, vice versa or Ubuntu to ubuntu?

Im partial to using rsync,
if your using a windows client you can use cwrsync,

however, you can automate it so that it will run every once in a while or when you run it manually and it will compare what you have copied to whats on the remote system,
it will copy the difference,
You can do more then that if you look at the options, 

If your using a windows box you could also investigate using Samba, I would research both to see which suits your needs

you can google both 
heres a few links

man pages for rsync
[http://www.samba.org/ftp/rsync/rsync.html](http://www.samba.org/ftp/rsync/rsync.html)
cwrsync (windows) website
[http://www.itefix.no/i2/node/10650](http://www.itefix.no/i2/node/10650)
samba wiki pages
[http://en.wikipedia.org/wiki/Samba_(software](http://en.wikipedia.org/wiki/Samba_(software))

[http://rsync.samba.org/](http://rsync.samba.org/)

---

### Post by davbren on 2008-12-15
I'm using Ubuntu --> Ubuntu...

Also, can you define different folders for different users??

---

