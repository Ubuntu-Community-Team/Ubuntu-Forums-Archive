---
title: "Rsync via UbubtuOne"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by manugupt1 on 2010-02-04
Can I use rsync along with ubuntuOne

---

### Post by superprash2003 on 2010-02-04
here is a tutorial with dropbox , but it should work with ubuntuone as well [http://tdrusk.blogspot.com/2009/03/dropbox-with-rsync-my-simple-script-to.html](http://tdrusk.blogspot.com/2009/03/dropbox-with-rsync-my-simple-script-to.html)

---

### Post by capron on 2010-02-04
Why wood you like too rsync ?  I am new too ubuntuone but dosent it sync your
files automatic ?  If you do a change in ubuntuone folder it will kind off rsync 
after that.

---

### Post by chipschap on 2012-04-28
There are many reasons to do rsync instead of the automatic sync that Ubuntuone provides. These are my two main reasons:

1) The rsync method allows me to control when backups take place. This ensures that, for instance, something in draft doesn't get saved when I don't wish it to be saved. It prevents many inadvertent overwrites. Since Ubunutone doesn't currently (4/2012) do versioning, this can be a big deal. (The downside is that if I forget to sync, it doesn't happen, of course.)

2) I use the rsync backup option so if something gets overwritten I save the old copy. Used with time/date stamps in the backup name, this is a primitive but lifesaving versioning system (at the cost of some local disk storage).

When Ubuntuone has versioning, of course, I may change my approach.

---

