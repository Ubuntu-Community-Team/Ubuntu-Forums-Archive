---
title: "Kino &amp; Sony DCR-PC100E"
date: 2009-12-29
forum: Multimedia Software
---

### Post by goslings on 2009-12-29
Use my Sony DCR PC100E with XP no problems 
Now thought I would try this in my dual boot Ubuntu 8.10 

Just installed KINO and Edit pref - IEEE 
"1394 subsystem not responding" 
The raw 1394 module must be loaded and you must have r+w access to /dev/raw1394

Anyone any joy with this combination ?
or some pointers 
cheers
Happy New Year

---

### Post by 73ckn797 on 2009-12-29
A good search, better than the forum searching, is [http://www.uboontu.com/](http://www.uboontu.com/) .

Enter:
```
 1394 subsystem not responding
```And see what results you get. I have seen and experienced this issue before but do not have the info directly at hand.

---

### Post by goslings on 2009-12-29
> **73ckn797 said:**
> A good search, better than the forum searching, is [http://www.uboontu.com/](http://www.uboontu.com/) .

Enter:
```
 1394 subsystem not responding
```And see what results you get. I have seen and experienced this issue before but do not have the info directly at hand.

cheers will try 
tried [http://ubuntuforums.org/showthread.php?t=966472](http://ubuntuforums.org/showthread.php?t=966472)
but still no joy

---

### Post by goslings on 2009-12-29
> **goslings said:**
> cheers will try 
tried [http://ubuntuforums.org/showthread.php?t=966472](http://ubuntuforums.org/showthread.php?t=966472)
but still no joy

Used 
[https://help.ubuntu.com/community/HowToCaptureDigitalVideo](https://help.ubuntu.com/community/HowToCaptureDigitalVideo)

BUT just the bit about the Hack (-get used to it)
* at the prompt type gedit /etc/init.d/bootmisc.sh
* scroll down to the bottom of the document by pressing the down arrow
*copy the edit below to your clipboard (ctrl+c) 

# Begin Edit. 20041031 RCB - Added to hopefully get the raw1394 devicenode.
mknod /dev/raw1394 c 171 0
chown root:video /dev/raw1394
chmod 666 /dev/raw1394
#End Edit

worked for me !

---

### Post by goslings on 2009-12-29
Maybe not so fast 
Actually launched this from a root terminal window 
Launching from applications - same problem as before 

So the $64M question - how do you get this app to have all the root privs it clearly needs ???

thanks 
Ian

---

