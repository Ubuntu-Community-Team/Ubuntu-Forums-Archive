---
title: "ipod wont work in amarok, HELP PLS!!"
date: 2008-05-13
forum: Multimedia Software
---

### Post by n00d1ek1ng on 2008-05-13
ipod wont mount automatically, i looked at other posts, and might have messed up my amarok...

i think i tried installing libgpod and sum other thing but still doesn't work...

pls help, really wanna use the ipod (ipod nano 4gb 3rd gen video)

tried installing ipodlinux and rockbox but i couldn't get that to work either, has an encrypted firmware so it doesn't work right?? jus wanna make sure, i really wanna get it to work but im pretty sure it wont....

but anyone kno how to get amarok to work with ipod?

thnx in advance

---

### Post by n00d1ek1ng on 2008-05-13
bump....anyone??

---

### Post by n00d1ek1ng on 2008-05-13
so i did this 

[http://ubuntuforums.org/showthread.php?t=658523&page=8](http://ubuntuforums.org/showthread.php?t=658523&page=8)

and this

[http://ubuntuforums.org/showpost.php?p=4898179&postcount=7](http://ubuntuforums.org/showpost.php?p=4898179&postcount=7)

but was unable to do this:

* note: the /media/IPOD is the default mounting point of Ipod in Ubuntu (change with yours if different)

Add to SysInfo file the following line and save the file:
Code:

FirewireGuid: 0xffffffffffffffff

* change the ffffffffffffffff value with the value grabbed above with the lsusb command



ipod still doesn't mount on amarok tho it does on rhythmbox....

any ideas??

---

