---
title: "Resynthesizer plugin + Gimp 2.10 + Ubuntu 20.04 LTS = NOPE"
date: 2020-05-11
forum: Multimedia Software
---

### Post by lmku100 on 2020-05-11
I have tried absolutely everything to install the Resynthesizer plugin into Gimp and it cannot be done. 

I've reinstalled Gimp every way I can including flatpak. 

I've installed the plugin correctly every way imaginable.

I have even compiled the plugin from scratch and installed it.

It just does not work. 

This is a brand new ubuntu install of 20.04
I am using the plugin from the git: [https://github.com/bootchk/resynthesizer](https://github.com/bootchk/resynthesizer)

Thowing my hands up here in frustration. I just want to be able to use Enhance>Heal selection.

This is literally the only thing I need Gimp for and I can't get it done.

---

### Post by mc4man on 2020-05-12
Don't know how to test that plugin but maybe try this, won't particulary hurt anything..
```
sudo apt install python-is-python2
```

Then download these 2 eoan packages
[https://packages.ubuntu.com/eoan/python-gtk2](https://packages.ubuntu.com/eoan/python-gtk2)
[https://packages.ubuntu.com/eoan/gimp-python](https://packages.ubuntu.com/eoan/gimp-python)

Then install them with apt, either together or seperate, gtk one 1st.
Ex. from Here..
sudo apt  install /home/doug/Downloads/python-gtk2_2.24.0-6_amd64.deb  /home/doug/Downloads/gimp-python_2.10.8-2_amd64.deb

(- running gimp from cli don't see any plugin errors, just some warnings..

---

### Post by squaregoldfish on 2020-05-24
Worked for me (for a different plugin)

Thanks!

---

