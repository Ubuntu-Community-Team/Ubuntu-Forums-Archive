---
title: "Can't install Rakarrack 0.2.0"
date: 2008-10-01
forum: Multimedia Software
---

### Post by pterosky on 2008-10-01
I get this message from the package installer:

"Error: Dependency is not satisfiable: libasound2"

I have verified that I have libasound2 installed, and also libasound2-dev.

Version is 1.0.15-3ubuntu4 and I am running 8.04 rt.

Does anyone know why it wont install?

In the meantime I found an older version, [rakarrack_0.1.2-1_i386]("https://lists.ubuntu.com/archives/ubuntu-studio-users/2008-July/002815.html")
which works, I just want the latest version :D

Rakarrack really needs to be in the repositories, it is so much better and easier to use than JACK Rack.

---

### Post by Yellow Pasque on 2008-10-01
Someone may have built the .deb's control file to be too picky about the libasound2 version (using = instead of >=).

Just build from source instead. You'll need:
```
sudo apt-get install build-essential jackd libfltk1.1-dev libasound2-dev libxpm-dev libjack-dev aconnectgui
```
Then download and untar the source. Open a terminal, go to that directory and:
```
./configure
make
sudo make install
```

---

### Post by pterosky on 2008-10-01
It worked like a charm, thank you so much! I now have Rakarrack 0.2.0 installed on my computer :guitar:

For those interested, the source code can be downloaded here: [http://rakarrack.sourceforge.net/](http://rakarrack.sourceforge.net/)

---

### Post by interval1066 on 2009-08-23
Temüjin: your instruction helped me too, I had the exact same problem.

---

