---
title: "Installing Java for Mozilla Firefox"
date: 2010-03-03
forum: Multimedia Software
---

### Post by cmastrangelo on 2010-03-03
Hi.
I'm trying to install the new java from the website: [http://www.java.com/en/download/index.jsp](http://www.java.com/en/download/index.jsp)
I download it and it's a .bin file
when i try to execute it i receive a error message saying "Could not display 'PATH' the file is of an unknown type"

---

### Post by InsaneMonkey02 on 2010-03-03
Go into the Terminal and type in:

sudo chmod +x name.bin

This make the bin able to execute. Then type in:

sudo ./name.bin

Make sure you're in the .bin's containing folder while you do this.

---

### Post by Yellow Pasque on 2010-03-03
You're better off getting .debs from something like: [https://launchpad.net/~karmic-bleed/+archive/ppa](https://launchpad.net/~karmic-bleed/+archive/ppa)

---

### Post by hxcobd on 2010-03-04
I seem to recall adding JavaRE support to Firefox being a somewhat time-consuming process consisting of making at least one symbolic link.

I could be wrong.

---

