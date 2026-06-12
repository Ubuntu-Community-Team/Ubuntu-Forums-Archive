---
title: "Amarok Nighty"
date: 2008-05-13
forum: Multimedia Software
---

### Post by Arkold Thos on 2008-05-13
Heya, some people -the ones who like a good music player- already seen that Amarok Team just released [Neon]("http://amarok.kde.org/en/node/482"). It contains the most recent build of Amarok 2 and is quite nice to test your favorite application, Amarok :D.

You need to add

deb [http://ppa.launchpad.net/project-neon/ubuntu](http://ppa.launchpad.net/project-neon/ubuntu) hardy main

and then install amarok-nighty package. Enjoy! :D

---

### Post by jackhynes on 2008-05-20
I'm getting:

```
Unpacking amarok-nightly (from .../amarok-nightly_20080519+svn809842-0amarok1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/amarok-nightly_20080519+svn809842-0amarok1_i386.deb (--unpack):
 trying to overwrite `/usr/share/applications/amarok-nightly.desktop', which is also in package amarok-nightly-tools
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/amarok-nightly_20080519+svn809842-0amarok1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Does anyone know why this is?

---

### Post by CarVac on 2008-05-20
I'm on Ubuntu, but I got the exact same problem. Examining it further, it seems the launcher comes both with amarok-nightly and amarok-nightly-tools.
dpkg's force options didn't help. Anyone have a solution?

---

### Post by jackhynes on 2008-05-20
> **CarVac said:**
> I'm on Ubuntu, but I got the exact same problem. Examining it further, it seems the launcher comes both with amarok-nightly and amarok-nightly-tools.
dpkg's force options didn't help. Anyone have a solution?

Yeah I'm on Ubuntu too, should have mentioned that.

---

### Post by nightrose on 2008-05-21
Hi,
we at Amarok are aware of the problem and are working on a fix.
Please be patient :)
Thanks for using Neon.

Oh and next time please ask on the Neon mailinglist or in our IRC channel as we are not checking the Ubuntu forum very often.

---

### Post by jackhynes on 2008-05-29
> **nightrose said:**
> Hi,
we at Amarok are aware of the problem and are working on a fix.
Please be patient :)
Thanks for using Neon.

Oh and next time please ask on the Neon mailinglist or in our IRC channel as we are not checking the Ubuntu forum very often.

This problem has been fixed in recent svn releases. Thanks for the quick response.

---

