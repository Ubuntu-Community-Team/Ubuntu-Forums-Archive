---
title: "cant browse password protected windows shares"
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by tfpsound on 2009-08-17
Hello all.  I'm setting up 9.04 and I'm having a problem accessing the password protected shares on my wd-netcenter.  When I enter the username and password I get the message. "Can not mount share".  I turned off the password prtoection on one of the folders and it mounted fine so I'm believing it has something to do with the way it's sending the password?  I don't have any problems accessing with heron on my other pc, and it worls with the heron live cd.  I just change the workgroup name in the smb.conf file.  Is there something I'm not doing right or is ther a way to see what's going on in there durring the logon.  Any help would be appreciated.  Just try to make the answer idiot proof. 
Thank you.   Tim

---

### Post by dmizer on 2009-08-17
First, make sure that your Ubuntu username and password are added to wd-netcenter as a user. Also, take a look at the 6th link in my sig.

---

### Post by tfpsound on 2009-08-17
Thanks.  I was able to mount the drive with your cifs tutorial.  Next dumb question.  Since I mounted this folder on the desktop, I'm guessing I bypassed the places>network folder (sorry I don't know the name of the browser) as when I try to access it through Places>network I still get the same error.  Is there any way to access this through gnome without having to manually mount the drive through terminal or editing the fstab?

---

### Post by dmizer on 2009-08-17
> **tfpsound said:**
> Thanks.  I was able to mount the drive with your cifs tutorial.  Next dumb question.  Since I mounted this folder on the desktop, I'm guessing I bypassed the places>network folder (sorry I don't know the name of the browser) as when I try to access it through Places>network I still get the same error.  Is there any way to access this through gnome without having to manually mount the drive through terminal or editing the fstab?

Well, if you've been successful with mounting via /etc/fstab, then I highly suggest you stick with that, because then ALL your programs will be able to see the share, not just gnome aware software.

Is there some reason you're wanting to use places > network? Something about /etc/fstab that's not satisfactory? It should automatically mount every time you boot, and it should leave a link in your desktop, so really it *should* provide you with the same (and better) functionality as places > network.

---

### Post by tfpsound on 2009-08-17
Not really a big deal for the desktop machines other than the time it takes to set this up. (we have about a dozen shares and not all the machines have the same hardware.)
My big concern is we have several laptops and being able to access from gnome would be a great convenience.  It is nice however to know where the problem came from.  Did heron use a different mounting method for the protected shares than jaunty?  The western digital site said it uses cifs so I would think the lack of the other protocol would not have made a difference.  Just trying to learn something here.

---

