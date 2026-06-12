---
title: "Installing k9copy on Gusty  -  INSANE!!!!"
date: 2008-01-31
forum: Multimedia &amp; Video
---

### Post by modmidget on 2008-01-31
I have a PC that IS NOT connected to the internet and probably never will be.  I've downloaded a K9COPY deb package and tried to install it.  Of course I immediately got an error because dependency packages were not installed.  I've downloaded about 40 dependency files and installed them but when I try to install the mencoder file I get more dependency errors.  It looks like the one file wants me to download and install about 30 or 40 other dependency files.  THIS IS CRAZY!!!!  This could lead to hundreds of sub-dependency installs. 

Isn't there just one file I can download that would install all of the dependencies the K9COPY wants?

At the rate I'm going it could take hours just to install this one little program.

---

### Post by Mze on 2008-01-31
Please connect "machine" to internet to have peace of mind or you will for sure go "CRAZY".

---

### Post by modmidget on 2008-01-31
I wish I could hook it to the internet, but I can't.

---

### Post by Mze on 2008-01-31
well, then there's [this to conside]("http://beans.seartipy.com/2006/05/06/update-or-install-applications-on-debianubuntu-without-an-internet-connection/")r possibly using a machine that is connected to the net. Ubuntu requires it's regular internet fix so I don't know how it's going to survive.

[AptOnCD]("http://blog.mypapit.net/2007/03/put-apt-get-repository-on-dvdcd-ubuntudebian.html") is another option to check out

Cheers.

---

### Post by modmidget on 2008-01-31
Thank you for the suggestions Mze.  I downloaded the APTonCD program and tried to install it on my Ubuntu computer (which is not connected to the internet).  The install instantly halted because of a dependency issue.  It's looking for MKISOFS, so I did a search and found that file and discovered it wants 5 other dependency files.  ](*,)

** edit **

Just discovered all of the sub-dependencies for MK!SOFS were already installed, so I installed MKISOFS and got APTonCD working.

---

