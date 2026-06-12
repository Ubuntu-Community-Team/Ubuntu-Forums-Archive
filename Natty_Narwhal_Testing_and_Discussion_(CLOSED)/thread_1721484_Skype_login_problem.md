---
title: "Skype login problem"
date: 2011-04-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by phoenix49 on 2011-04-04
Hello!

I'm using latest updated Ubuntu Natty 64 bit. I've managed to install skype and actually run it. But there's a problem with connection, "signing in" takes forever, and never ends. Does anybody had this problem before?

I have all lib32 libraries needed, as well as libqt4 ones.

In terminal I get only GTK related errors.

Thanks!!

---

### Post by awam66 on 2011-04-04
I have no problems but I'm using 32 bit on 64bit computer.

---

### Post by cariboo on 2011-04-04
There is a Maverick 64-bit version of Skype available [here]("http://archive.canonical.com/pool/partner/s/skype/"), just download it, and use dpkg, gdebi or the Software Center to install it.

---

### Post by lonniehenry on 2011-04-04
Maverick 64 bit Skype works ok on my Natty.  First sign-in was real slow, but now opens on login as fast as wireless comes up.

---

### Post by cariboo on 2011-04-04
I just installed it to check the login time, as lonniehenry said, the first time seems to take a while, but after that it seems to be OK. I've noticed the same thing in Windows 7, the first time takes a while but after that it's OK too.

---

### Post by phoenix49 on 2011-04-05
Seems like there was some mixing in my installation, I downloaded several versions from skype.com, from archive, installed i386 version, then removed, purged everything.

Last thing I did, is added maverick repo for "partner", and installed skype from there.

Now it works ok :)

P.S. Installed amd64 version, however, it is really 32bit version anyway.

---

