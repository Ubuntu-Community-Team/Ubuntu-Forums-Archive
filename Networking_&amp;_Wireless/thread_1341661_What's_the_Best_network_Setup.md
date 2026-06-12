---
title: "What's the Best network Setup"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by inobe on 2009-11-29
when i had 9.04 on these machines samba was blazing fast, now all these machines have a clean installed 9.10 but samba only transfers around 150 kbps.

i tried some stuff obviously and had the same issues, now i am looking for tricks on the best network setup that works for you, nfs' whatever, any tips you guys could give would be greatly appreciated :)


here is a thread i started just to give an idea what on what i am dealing with, thanks

[http://ubuntuforums.org/showthread.php?p=8389820#post8389820](http://ubuntuforums.org/showthread.php?p=8389820#post8389820)

---

### Post by jacobs444 on 2009-11-29
I personally get rid of samba and use ftp, you can have anonymous logins if you are behind a router, though still technically this is insecure if you give anonymous a lot of permission. Though the same is true of any type of file server.

---

### Post by jacobs444 on 2009-11-29
Oh, i recommend pure-ftpd, is easy to configure and rather fast.

---

### Post by Roasted on 2009-11-30
Keep in mind, NFS doesn't work with Windows to Linux. From what I understand, Samba is the only way to share files between Linux/Windows/Mac.

Sure, you could use FTP, but I prefer having an ACTUAL file server with actual logins and actual security set in place, which is relatively easy to put in play.

I can't offer anymore insight, cause I stuck with 9.04 and didn't upgrade to 9.10. Have you tried reinstalling Samba itself?

---

### Post by inobe on 2009-11-30
> **Roasted said:**
> Keep in mind, NFS doesn't work with Windows to Linux. From what I understand, Samba is the only way to share files between Linux/Windows/Mac.

Sure, you could use FTP, but I prefer having an ACTUAL file server with actual logins and actual security set in place, which is relatively easy to put in play.

I can't offer anymore insight, cause I stuck with 9.04 and didn't upgrade to 9.10. Have you tried reinstalling Samba itself?

hi

these boxes all have fresh installs, samba is all from scratch, the setup was error free, all of it was just perfect even the os.

the samba install is simply flawless including the security, it's just very slow.

i think i am just not sure what to examine that may be causing this.

thanks

---

