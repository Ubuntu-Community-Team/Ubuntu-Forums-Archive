---
title: "Help with enabling multi media please"
date: 2007-05-31
forum: Multimedia &amp; Video
---

### Post by the lemming on 2007-05-31
I'm trying to follow the How-To part of enabling multi media bit I'm confused by the following bit.  Could somebody please explain what I am supposed to do?

to open it in the Vim command line text editor

Add the following lines to add the Medibuntu repository to the file:


Quote:
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
Import the gpg key for the Medibuntu repository to ensure that the packages are installed without warnings/errors regarding trust:
To do this, run the following command from the terminal:

---

### Post by happy-and-lost on 2007-05-31
Don't use Vim. It's scary.

Open up a terminal and type/paste:

```
sudo echo "deb http://medibuntu.sos-sts.com/repo/ feisty free non-free" > /etc/apt/sources.list
sudo echo "deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free" > /etc/apt/sources.list
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install libdvdcss2 w32codecs
```

Then take it from there.

---

### Post by the lemming on 2007-05-31
> **happy-and-lost said:**
> Don't use Vim. It's scary.

Open up a terminal and type/paste:

```
sudo echo "deb http://medibuntu.sos-sts.com/repo/ feisty free non-free" > /etc/apt/sources.list
sudo echo "deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free" > /etc/apt/sources.list
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install libdvdcss2 w32codecs
```

Then take it from there.


Everything went tickity-boo untill I put a DVD into my computer and got the following error

An error occured.
Could not read from resource.

I also spotted this in the terminal



Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
frank@frank-desktop:~$ 



Any recomendations or suggestions to help me watch a DVD?

Cheers

---

### Post by happy-and-lost on 2007-06-02
Sorry, I haven't yet perfeted the echo command. Try this...

```

sudo su -c echo 'deb http://medibuntu.sos-sts.com/repo/ feisty free non-free >> /etc/apt/sources.list'
sudo su -c echo 'deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free >> /etc/apt/sources.list'
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install libdvdcss2 w32codecs
```

---

