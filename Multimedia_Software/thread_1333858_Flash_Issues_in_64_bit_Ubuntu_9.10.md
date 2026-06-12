---
title: "Flash Issues in 64 bit Ubuntu 9.10"
date: 2009-11-21
forum: Multimedia Software
---

### Post by A4orce84 on 2009-11-21
Hey Guys,

Read about some users having issues with flash video sites like Youtube and Hulu in Firefox on the 64 bit platform. Well looks like count one more person who is experiencing these struggles.

I recently read about a script that could be used to fix the issue, but do not know the exact steps / commands to run it. (I'm still a bit of a Linux newb!)

If anyone could help me out, I would greatly appreciate it!

Thanks.

--Asif

---

### Post by space-litter on 2009-11-21
Here is my thread about how to upgrade your flash version from being "wrapped" to 32-bit to just the latest 64-bit:

[http://ubuntuforums.org/showthread.php?t=1332870](http://ubuntuforums.org/showthread.php?t=1332870)

That got youtube and hulu (most sites really) working. However, now with Flash I have sound but no video on some sites (mostly when I try to stream sports on justintv or atdhe). So it is not a perfect fix and if that is something you do frequently be forewarned.

---

### Post by blueridgedog on 2009-11-25
Attached is the script that I used.  You simply need to save it someplace then run it.  

Let's assume you saved it to your Desktop.  To run it you would first open a terminal and make the file executable:

```
chmod o+x ~/Desktop/native-64bit-flash-installer.sh
```

(note that that is the letter o followed by a plus sign then an x.  This means that the owner also has execute permissions on the file.

Next, in the same terminal, you can execute the scrip:

```
~/Desktop/native-64bit-flash-installer.sh
```

This script downloads the alpha flash plugin from Adobe and installs it.  I am satisfied with it, but it is not perfect.

---

