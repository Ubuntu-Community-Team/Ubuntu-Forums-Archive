---
title: "Need help with Deja-Dup restore not working"
date: 2019-02-16
forum: MINT
---

### Post by jowi-krause on 2019-02-16
Hi!
My system is Linux Mint19.1 Cinnamon 64bit.
Before I upgraded, I did a full backup of my /home folder with Deja-dup. 
However, when I try to restore my data, deja-dup spends a lot of time "preparing", then I get an error:

Wiederherstellung fehlgeschlagen
 Mit unbekanntem Fehler fehlgeschlagen
 Details:
 Traceback (innermost last):
   File "/usr/bin/duplicity", line 1555, in <module> with_tempdir(main)
File "/usr/bin/duplicity", line 1541, in with_tempdir fn()
File "/usr/bin/duplicity", line 1393, in main do_backup(action)
File "/usr/bin/duplicity", line 1476, in do_backup list_current(col_stats)
File "/usr/bin/duplicity", line 704, in list_current for path in path_iter:
File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 354, in combine_path_iters refresh_triple_list(triple_list)
File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 341, in refresh_triple_list new_triple = get_triple(old_triple[1])
File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 327, in get_triple path = path_iter_list[iter_index].next()
File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 239, in sigtar2path_iter for tarinfo in tf:
File "/usr/lib/python2.7/tarfile.py", line 2510, in next tarinfo = self.tarfile.next()
File "/usr/lib/python2.7/tarfile.py", line 2352, in next raise ReadError("unexpected end of data")
ReadError: unexpected end of data

Is there anyone who can explain, what this means? Does anyone have an idea how I can retrieve my data, at least partially?
I have looked into the ManPage of duplicity, but that is too complicated for me.

Can anyone help me?
Thx

---

### Post by dragonfly41 on 2019-02-16
I found a match for one of your lines 

[COLOR=#000000]File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 239, in sigtar2path_iter for tarinfo in tf:

[/COLOR]here ..

[https://bugs.launchpad.net/duplicity/+bug/1725829](https://bugs.launchpad.net/duplicity/+bug/1725829)


[Later edit] And another reference found here ...

[http://www.linuxforums.org/forum/debian-linux/210476-deja-dup-failed-restore.html](http://www.linuxforums.org/forum/debian-linux/210476-deja-dup-failed-restore.html)

Which version of Duplicity? Which version of Python?

---

### Post by coffeecat on 2019-02-16
*Thread moved to the **MINT** sub-forum.*

---

