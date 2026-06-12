---
title: "Zune - again"
date: 2010-08-22
forum: Multimedia Software
---

### Post by watgrad on 2010-08-22
There are many Zune threads - all stating that zune won't work with ubuntu - so I get that.  But I am curious...
  
Why can I mount the zune player and see the files on the zune - and then when I try to add to the zune or remove them get an error message.  

Ubuntu can  see what is on the Zune, so why can't it copy/erase the files?

---

### Post by watgrad on 2010-08-23
Seems I found my answer:

> There's been some progress with libmtp, but files can only be displayed and deleted. Write-access is denied because the Zune waits for a secret handshake key from the Zune software to authenticate its connection. Until (a) Microsoft reveals something about the inner workings of this (not likely), or (b) someone analyzes the USB traffic between software and device enough to figure out how the handshake functions, you aren't going to be able to "sync" your Zune with Linux. I have VirtualBox with XP set up on my installation, pretty much solely for the purpose of syncing my Zune. But that's not a hack or a solution, it's just a workaround - and one that involves Windows. 

Just be patient...someone will figure it out.
[http://ubuntuforums.org/showthread.php?t=705136](http://ubuntuforums.org/showthread.php?t=705136)
:frown:

---

### Post by Preetit on 2011-01-04
Hi,
 
Is there any tool to monitor MTP traffic (Something equivalent to wpdmon in Windows..) ?. I am using libmtp library on Ubuntu.I want to check the commands exchanged when I connect my device to PC.
 
 
 
Regards
-Preeti

---

