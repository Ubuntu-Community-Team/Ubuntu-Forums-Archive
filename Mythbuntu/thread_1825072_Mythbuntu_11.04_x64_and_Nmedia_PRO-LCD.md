---
title: "Mythbuntu 11.04 x64 and Nmedia PRO-LCD"
date: 2011-08-14
forum: Mythbuntu
---

### Post by mille535 on 2011-08-14
Hello all,

So this weekend I decided to take the plunge convert my HTPC from Windows 7 Media Center to Mythbuntu 11.04 x64.  After lots of reading I finally got everything in my setup to work with the exception of my Nmedia lcd.  I have done tons of searching and most articles I find point me back to [this one]("http://www.mythtv.org/wiki/Nmedia_pro-lcd").  I have followed these instructions verbatim and when I try to test it with this command: ```
echo "Hello MythTV and good morning" > /dev/lcd0
``` I receive this error: ```
-bash: /dev/lcd0: Permission denied
``` I am not very knowledgeable with linux and am basically stuck.  Has anybody else gotten this to work? 

Thanks!

---

### Post by nickrout on 2011-08-14
try the following commands and tell us what the result is:

```
id
ls -l /dev/lcd0
```

---

### Post by mille535 on 2011-08-14
Just as a note I built the drivers using sudo before the command and tried sudo on the echo command as well.  

Output of id:
```
uid=1000(kirk) gid=1000(kirk) groups=1000(kirk),4(adm),20(dialout),24(cdrom),44(video),46(plugdev),116(admin),117(mythtv),118(sambashare),119(lpadmin)

```

output of ls -l /dev/lcd0:
```
ls: cannot access /dev/lcd0: No such file or directory
```

---

### Post by mille535 on 2011-08-14
I was running though some other steps and found when I run:
```
modprobe lirc_imon
```

I get the following error. 
```
FATAL: Error inserting lirc_imon (/lib/modules/2.6.38-10-generic/kernel/drivers/staging/lirc/lirc_imon.ko): Invalid module format
```

I don't remember seeing this before but thought that it may be usefull

---

### Post by nickrout on 2011-08-14
looks like the module has not been inserted.

---

### Post by mille535 on 2011-08-14
OK I don't know if it was working prior to doing updates (now on kernel 2.6.38-10-generic) but how I get the correct lirc_imon.ko to get this up and running?

---

