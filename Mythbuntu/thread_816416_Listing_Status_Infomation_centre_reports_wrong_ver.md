---
title: "Listing Status Infomation centre reports wrong version of mythtv"
date: 2008-06-02
forum: Mythbuntu
---

### Post by db260179 on 2008-06-02
Hello,

The mythtv version reports as the original changeset 16838 and not the updated version i.e weekly fixes version 17392

In the Listing Status page.

Is this normal?

---

### Post by jb5 on 2008-06-03
I don't know if this is normal, but it is the same for me.

Also, I have EPG data for the next 11000 days or so, ie guide data up to something like 2038!

Not a problem as such, but it would be nice to "fix" it!

---

### Post by ian dobson on 2008-06-03
> **jb5 said:**
> I don't know if this is normal, but it is the same for me.

Also, I have EPG data for the next 11000 days or so, ie guide data up to something like 2038!

Not a problem as such, but it would be nice to "fix" it!

Sounds as if you has a corrupt entry in the programs table. If you have myPhpadmin (or is it PHPmyAdmin) installed just edit your programs table and delete the "future" programs.

For me EPG works like a dream (Mixed Analog/DVB-C) I even have a munin plugin that monitors the status of MythTV for me :lolflag:

Regards
Ian Dobson

---

### Post by jb5 on 2008-06-03
Right, nice, I will try and give that a go when I'm next on my myth-box.

The EPG actually works fine, it's just the info page has the incorrect date for the updates available.

---

### Post by laga on 2008-06-03
I've figured out the versioning problem - the version string is updated with the wrong revision during the package build.

I'll take care of it. Thanks for reporting :)

---

### Post by jb5 on 2008-06-04
> **ian dobson said:**
> .....just edit your programs table and delete the "future" programs.


Wow. I downloaded phpmyadmin. If that's the EASY way to manage mysql dbs then I'm in trouble. :)

Do you have any tips or sites that I should look at. I will continue digging myself, but at the moment it seems like more trouble than it's worth for a merely "cosmetic" problem, particularly if I manage to foobar my db.
........................

Thanks Iaga.

........................
db260179 - In the meantime if you want to see the current version 
```
apt-cache policy mythtv-common
```
from [here](http://ubuntuforums.org/showthread.php?t=736528) will work.

---

### Post by db260179 on 2008-06-04
Glad i can help 

> **laga said:**
> I've figured out the versioning problem - the version string is updated with the wrong revision during the package build.

I'll take care of it. Thanks for reporting :)

:cool:

---

