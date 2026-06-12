---
title: "gtkpod trouble"
date: 2012-02-12
forum: Multimedia Software
---

### Post by tim_norman2003 on 2012-02-12
hi
im trying to set up my iphone 3gs (ios 5.0.1) with my music.

using gtkpod it shows all the songs and movies i have added to the phone (using my friends itunes) but the files dont show up on my phone.

can you please tell me how to remidy this problem, so i can listen to more than 1/4 of my music .

(on a side note when i try and put more tracks on my iphone it says it cant be done because of missing hashinfo files..)

this is the terminal output when i try to do something and the hashinfo file error message appears:


gtktim@tim-desktop:~$ gtkpod

(gtkpod:3430): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkImageMenuItem
libitdbprep: itdb_iphone_start_sync called with uuid=26d96e4ed8e4796790891c8a7e2b26b6fe00c630
itdb_iphone_start_sync: posted syncWillStart
itdb_iphone_start_sync: posted syncLockRequest
Locking for sync, attempt 0...
itdb_iphone_start_sync: posted syncDidStart

** (gtkpod:3430): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed
libitdbprep: itdb_iphone_stop_sync called
Could not delete '.status-com.apple.itdprep.command.runPostProcess'
Could not delete 'ddd.itdbm'
itdb_iphone_stop_sync: posted syncDidFinish
libitdbprep: itdb_iphone_start_sync called with uuid=26d96e4ed8e4796790891c8a7e2b26b6fe00c630
itdb_iphone_start_sync: posted syncWillStart
itdb_iphone_start_sync: posted syncLockRequest
Locking for sync, attempt 0...
itdb_iphone_start_sync: posted syncDidStart

** (gtkpod:3430): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed
libitdbprep: itdb_iphone_stop_sync called
Could not delete '.status-com.apple.itdprep.command.runPostProcess'
Could not delete 'ddd.itdbm'
itdb_iphone_stop_sync: posted syncDidFinish


any ideas?

thanks
Tim

---

### Post by tim_norman2003 on 2012-02-13
Bump

---

### Post by tim_norman2003 on 2012-02-18
bump

---

### Post by Rodney9 on 2012-02-18
Some of these sites may help

[http://news.softpedia.com/news/How-To-Sync-Your-iPhone-Device-in-Ubuntu-10-10-169608.shtml](http://news.softpedia.com/news/How-To-Sync-Your-iPhone-Device-in-Ubuntu-10-10-169608.shtml)

[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

[http://geeknizer.com/sync-iphone-linux/](http://geeknizer.com/sync-iphone-linux/)

Good Luck
Rodney

---

### Post by tim_norman2003 on 2012-02-19
none of them worked...
just got the same message about the missing hashinfo files...

---

### Post by Rodney9 on 2012-02-19
I have know idea, I know iStuff can be hard, seems lots of people have errors [http://goo.gl/9RJlRthat's](http://goo.gl/9RJlRthat's) , that's why I use Android. 

Are you using the latest gtkpod 2.1.0 in the software center or 2.1.1 from gtkpod and Ubuntu 11.10 ?

Rodney

---

### Post by tim_norman2003 on 2012-02-22
> **Rodney9 said:**
> I have know idea, I know iStuff can be hard, seems lots of people have errors [http://goo.gl/9RJlRthat's](http://goo.gl/9RJlRthat's) , that's why I use Android. 

Are you using the latest gtkpod 2.1.0 in the software center or 2.1.1 from gtkpod and Ubuntu 11.10 ?

Rodney

im running gtkpod 1.0.0, and ubuntu 11.04 (i was reccomended not to upgrade to 11.10, i had some problems previously, and apparently its common when upgrading from .04 to .10 to have trouble, so i kept with natty)

---

