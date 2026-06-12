---
title: "Nvclock compiling from CVS"
date: 2008-01-04
forum: Multimedia &amp; Video
---

### Post by scizzo on 2008-01-04
Hello,

I have today been looking around for fixes with the 100% fan problems on the drivers 169.07 that is being the latest stable driver for nvidia. Had some problems when it came to compile the nvclock fixes from CVS though and thought I might add a few comments here.

**Remember: This was done on Hardy Heron**

First of all we need the packages for compiling:
```

# sudo apt-get install cvs build-essential xserver-xorg-dev libx11-dev
# sudo ldconfig && sudo updatedb

```

Second we need the nvclock packages from cvs. (There is no password so just click enter)
```

# cvs -d:pserver:anonymous@nvclock.cvs.sourceforge.net:/cvsroot/nvclock login
# cvs -z3 -d:pserver:anonymous@nvclock.cvs.sourceforge.net:/cvsroot/nvclock co -P nvclock

```

Enter the CVS directory and type:
```

# ./configure
# make
# sudo make install

```

This will now install nvclock. Remember that you need to use sudo to change the fan speed.

Here is a example I used on the Nvidia GeForce 8800GTS card that I am using:
```

# sudo nvclock -f -F auto

```

Hope this helps you with the 100% fan problems on nvidia cards using drivers 169.07. According to nvidia they have found the problem and will fix this in later stable releases.

---

