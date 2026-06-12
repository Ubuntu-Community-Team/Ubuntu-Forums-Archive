---
title: "Synaptics Package Manager"
date: 2007-05-16
forum: Multimedia &amp; Video
---

### Post by wow20 on 2007-05-16
Hi 

Im very new to Ubuntu operating system so pls help me..

I was trying to install the looking glass 3d effect for my desktop but its failed and when i tried to install any new applications or use the synaptic package manager i couldnt access it.
This occured:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i tried using the terminal but it said that "dpkg" was accessible to only superusers.
pls help...

---

### Post by DracoPsycho on 2007-05-16
do ```
 sudo dpkg --configure -a 
``` when it asks for password, you must provide password you gave ubuntu when installing.

---

### Post by wow20 on 2007-05-16
Thanks 
but i still cant open synaptics. this occurs:
E: The package lg3d-jdk needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

 and i don noe what to do

---

### Post by DracoPsycho on 2007-05-16
Well, it looks bad. I don't know if you can reinstall apt-get or something, I guess we have to wait until someone else come here. Plus we don't know what you actually did when synaptic broke.

---

### Post by wow20 on 2007-05-16
o well..thanks anyway

---

