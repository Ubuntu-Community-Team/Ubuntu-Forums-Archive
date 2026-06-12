---
title: "Linksys WUSB54GC USB Wireless-G Adapter Not Recognized 9.04/8.10"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by aherbert01 on 2009-04-24
I've been struggling with this for a few weeks now, figured I could make a fresh post since most of the others I've dredged up from the forums and help docs are two years old or so.  The problem is very simple:  My WUSB54GC wireless adapter is not functional out of the box and I lack the expertise to work it out myself.  If someone could point me in the right direction I would be greatly appreciative.  I am currently working with Ubuntu 9.04.

I've already exhausted these resources to no avail:

[http://ubuntuforums.org/showthread.php?t=279447](http://ubuntuforums.org/showthread.php?t=279447)

[http://ubuntuforums.org/showthread.php?t=170017](http://ubuntuforums.org/showthread.php?t=170017)

[https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC)

I can obviously provide more information if needed.

---

### Post by thomasaaron on 2009-05-04
Look at the model number on the back of the adapter. If it says ...ver. 3, it doesn't work yet.

---

### Post by aherbert01 on 2009-05-05
Thank you!  It is ver3, so I just reconfigured my setup so I have a wired connection on my Ubuntu box.  Only a mild annoyance in my case, but thanks for the information.

---

### Post by smacattack on 2009-05-10
Any idea when version 3 will get support? I got the WUSB54GC after reading it works out of the box only to find this out as well. 

Looks like I'll be stuck in windows for now...:(

---

### Post by mmatull on 2009-05-11
Yeah, me too.  I saw the note that says it works out of the box and had high hopes.  I too want to know when this will work before I decide to return it.
 
Mike

---

### Post by MorganTheDark on 2009-05-15
ver.3 works now.

Take a look at this thread, steps 7 and 8 have typos and you may need to do a bit of fanagaling to get "iwlist ra0 scan" to work, but you should be able to figure it out.

[http://ubuntuforums.org/showthread.php?t=1155941](http://ubuntuforums.org/showthread.php?t=1155941)

---

