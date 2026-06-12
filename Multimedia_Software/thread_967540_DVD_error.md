---
title: "DVD error"
date: 2008-11-02
forum: Multimedia Software
---

### Post by simonlugi on 2008-11-02
I have been trying to follow the instructions provided for playing DVD's.
I got as far as "sudo /usr/share/doc/libdvdread3/install-css.s"

At the bottome of the terminal I get a message as shown below.

checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [build-stamp] Error 77

Can anyone help me solve this problem.

---

### Post by Kevbert on 2008-11-02
Rather than doing that first run
```
sudo apt-get install -f
```
to repair any damaged packages then install Quickstart which will sort out all your codecs - see my signature below.

---

### Post by simonlugi on 2008-11-03
Unfortunately the suggestion does not work. Using Totem I get an error that says "Could not read from resource"
I tried using gxine and get Error message "Error opening vtsN=-1, domain=2."

---

### Post by xc3RnbFO8P on 2008-11-03
Do:
> sudo apt-get install build-essential
and try again.

---

### Post by simonlugi on 2008-11-03
Ringi. I have tried your suggestion. No luck same error messaage as before. Could it be the regional settings

---

### Post by xc3RnbFO8P on 2008-11-03
Did you install Medibuntu?
Your computer, 32 or 64 bit?

---

### Post by simonlugi on 2008-11-05
Medibuntu is installed and the computer has AMD 64 and Nvidia

---

