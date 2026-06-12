---
title: "Flash player problem"
date: 2008-06-16
forum: Multimedia Software
---

### Post by thewhiteraven on 2008-06-16
I have this problem while trying to install Flash Player 9...

```
----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Mozilla installation directory  = /home/janvi/.mozilla

Proceed with the installation? (y/n/q): y
cp: cannot stat `/libflashplayer.so': No such file or directory

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.

chmod: cannot access `/home/janvi/.mozilla/plugins/libflashplayer.so': No such file or directory

Installation complete.


Perform another installation? (y/n): y

```

How do I "remove the xpti.dat from the components directory of the Mozilla or Netscape browser"?? I use Mozilla 3.

Help!

---

### Post by gandaran on 2008-06-16
to to the hidden home .mozilla folder, you will find the file there.

---

### Post by thewhiteraven on 2008-06-17
Ok, I did that but I'm still getting the same message. Hmmm.

---

### Post by Bablefish on 2008-06-17
Strange I used this


 wget -c [http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.17ubuntu4_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.17ubuntu4_all.deb)
sudo dpkg -i gsfont*.deb
sudo dpkg -i flash*.deb


Then rebooted and and did a sudo apt-get update and had no problem

---

### Post by thewhiteraven on 2008-06-17
Um... Ok, maybe I should have mentioned that I'm a beginner. I didn't understand what you mean by > sudo dpkg -i gsfont*.deb
sudo dpkg -i flash*.deb

I tried typing that on the terminal and this is what I got:

```
dpkg: error processing gsfont*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 gsfont*.deb

```

Am I being unbearably stupid? :(

---

### Post by Pjotr123 on 2008-06-17
This is the easy way for 100 % multimedia support, including Adobe Flash:

Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

---

### Post by thewhiteraven on 2008-06-17
Awesome! Thanks, that was perfect... I like knowing what I'm doing on linux and how it works so that I can do it again if necessary but for once, blindly following instructions was great :)

---

### Post by colbobs on 2008-06-21
> **Pjotr123 said:**
> This is the easy way for 100 % multimedia support, including Adobe Flash:

Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

Done this too - so far no hellish warning messages or small singularities appearing in the corner of the room - oh wait it's not windows!
Thanks Pjotr123

---

### Post by Izula on 2008-06-21
Excuse me for jumping into this thread.

Running Ubuntu(Wubi)/Win XP Pro - followed those 2 guidelines;  all went well.

No video at youtube. I just get a quick black screen flash and nada..

---

### Post by Pjotr123 on 2008-06-21
> **Izula said:**
> Excuse me for jumping into this thread.

Running Ubuntu(Wubi)/Win XP Pro - followed those 2 guidelines;  all went well.

No video at youtube. I just get a quick black screen flash and nada..

Wubi is a great invention, but it has it's limitations. Perhaps that's the problem. Consider a normal dual boot installation:
[http://ubuntutip.googlepages.com/installationofubuntu](http://ubuntutip.googlepages.com/installationofubuntu)

---

### Post by Izula on 2008-06-23
> **Pjotr123 said:**
> Wubi is a great invention, but it has it's limitations. Perhaps that's the problem. Consider a normal dual boot installation:
[http://ubuntutip.googlepages.com/installationofubuntu](http://ubuntutip.googlepages.com/installationofubuntu)
Oh that's really unfortunate.  Thanks Pjotr123.

---

