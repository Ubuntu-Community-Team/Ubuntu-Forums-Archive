---
title: "Importing CDs into Exaile"
date: 2010-08-05
forum: Multimedia Software
---

### Post by steveov on 2010-08-05
Hi! I'm on Xubuntu 10.04 and I'd like to import some CDs as MP3 via exaile. Right now, I'm getting this error:
[FONT=monospace]
[/FONT]```
Exception in thread Thread-12:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 532, in __bootstrap_inner
    self.run()
  File "/usr/share/exaile/plugins/cd/_cdguipanel.py", line 60, in run
    self.imp.do_import()
  File "/usr/share/exaile/plugins/cd/importer.py", line 71, in do_import
    outloc = self.get_output_location(tr)
  File "/usr/share/exaile/plugins/cd/importer.py", line 102, in get_output_location
    val = val.replace('"', '\\"')
AttributeError: 'NoneType' object has no attribute 'replace'
```I've installed xubuntu-restricted-extras, but it doesn't work. What dependency am I missing?

Thanks!

---

### Post by williamkray on 2010-08-06
i am also getting a similar error when trying to import a cd in exaile.  using linux mint 9 (an ubuntu 10.04 derivative) and trying to import the cd as .flac

after searching around, it seems like this error is more related to python than exaile, would reinstalling python fix it possibly?  and which packages should be reinstalled?

---

### Post by steveov on 2010-08-16
I wound up just downloading Sound Juicer. It seemed like the path of least resistance.

---

### Post by hans796 on 2010-11-22
I solved it with adding exaile devolopers repositorie:

[https://launchpad.net/~exaile-devel/+archive/ppa]("https://launchpad.net/~exaile-devel/+archive/ppa")

or easy way:

sudo add-apt-repository ppa:exaile-devel/ppa

sudo apt-get update

sudo apt-get upgrade

Now I can import cd:s  :p

---

### Post by GregC on 2012-05-06
> **hans796 said:**
> I solved it with adding exaile devolopers repositorie:

[https://launchpad.net/~exaile-devel/+archive/ppa]("https://launchpad.net/~exaile-devel/+archive/ppa")

or easy way:

sudo add-apt-repository ppa:exaile-devel/ppa

sudo apt-get update

sudo apt-get upgrade

Now I can import cd:s  :p
This worked for me. I can now import cd(s). Thanks!

Xubuntu 10.04
SONY DVD RW DRU-810A

---

### Post by oldos2er on 2012-05-06
Old thread closed.

---

