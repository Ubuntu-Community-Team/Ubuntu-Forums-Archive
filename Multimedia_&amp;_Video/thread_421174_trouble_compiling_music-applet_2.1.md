---
title: "trouble compiling music-applet 2.1"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by Schalken on 2007-04-24
I am trying to compile the latest version of music-applet (2.1.0), because the one in the repos is very old (0.9.2).

It configures, compiles and makes a debian package with checkinstall very well. However when it tries to install the package I get this:
```
Selecting previously deselected package music-applet.
(Reading database ... 160660 files and directories currently installed.)
Unpacking music-applet (from .../music-applet_2.1.0-1_i386.deb) ...
dpkg: error processing /home/jesse/Desktop/music-applet-2.1.0/music-applet_2.1.0-1_i386.deb (--install):
 trying to overwrite `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so', which is also in package libgconf2-4
dpkg-deb: subprocess paste killed by signal (Broken pipe)
```

Why would it try to overwrite a file that belongs to libgconf?

Using Feisty Fawn on a PC. If someone has already compiled an i686 .deb for feisty please let me know.

---

### Post by dakota1 on 2007-04-24
I can't even get it to compile. It complains that it can't I don't have libpanelapplets-2.0, which I do!

---

### Post by Schalken on 2007-04-24
You need to development package(s), unless you have those as well.

---

### Post by dakota1 on 2007-04-25
Thanks, I installed the dev packages for libpanelapplet, and it configured, so I ran Make, and make install.

No errors but it doesn't appear in the add panel window.

---

### Post by Sionide on 2007-04-25
I'm having the same problem... Installed music-applet from the repos in the end because I couldn't get to compile properly and it doesn't appear in the add panel dialogue. :(

---

### Post by lagartoflojo on 2007-04-25
Maybe the official music-applet website helps?
[http://www.kuliniewicz.org/music-applet/faq.html](http://www.kuliniewicz.org/music-applet/faq.html)

Are any of you running Feisty? Under Edgy, music-applet in the repostitories worked for me. Now, in Feisty, not even that one works: it doesn't detect that Rhythmbox is running, and if it is not, clicking on the applet does not open rhythmbox either (yes, it's selected as my preferred music player in the applet's preferences).
I tried compiling and I got the same error message as Schalken when I tried checkinstall. I then decided to just do "sudo make install" and the applet installed successfully, and even appeared in the "Add To Panel" dialog. Unfortunately, when I tried adding it, it said that it couldn't (didn't specify a reason) and asked me if I wanted to delete the applet. Regardless of my answer, the applet does not show, and I don't even know why. Is there a log file where I could see the error? Anyway, I just got rid of the panel by issuing "sudo make uninstall".
Well, that's all I know. My post about this ( [http://ubuntuforums.org/showthread.php?t=423156](http://ubuntuforums.org/showthread.php?t=423156) ) in the "General Help" area of the forums  has not turned out any answers either...

---

### Post by CarpKing on 2007-05-15
Yeah, I've been having these same sorts of problems.

---

