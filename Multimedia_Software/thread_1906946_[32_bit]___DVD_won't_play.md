---
title: "[32 bit]   DVD won't play"
date: 2012-01-10
forum: Multimedia Software
---

### Post by sallymc on 2012-01-10
Am desperate.  Spent hours trying to play DVD from Forum advice after 11.10 installation, but no luck.  :( Can anyone out there help please?  Terminal reads :

```

```

sally@Sally-Ubuntu:~$ sudo apt-get install vlc xine mplayer libdvdread3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'xine' has no installation candidate
E: Unable to locate package libdvdread3

Thanks in anticipation.
Sallymc

---

### Post by tersogar on 2012-01-10
Did you install Ubuntu restricted extras and
 ```

```sudo /usr/share/doc/libdvdread4/install-css.sh```

```

---

### Post by sallymc on 2012-01-10
> **tersogar said:**
> Did you install Ubuntu restricted extras and
 sudo /usr/share/doc/libdvdread4/install-css.sh

No.  Am a greenie.  How do I install Ubuntu restricted extras?
I tried installing libdvdread 4 and got the following advice :

sally@Sally-Ubuntu:~$ /usr/share/doc/libdvdread4 
bash: /usr/share/doc/libdvdread4: Is a directory

---

### Post by tersogar on 2012-01-10
Ubuntu restricted extras can be found in the software center.
Did you use sudo? If not try again using: sudo /usr/share/doc/libdvdread4/install-css.sh
The system will ask you to enter your password.

---

### Post by sallymc on 2012-01-10
> **tersogar said:**
> Ubuntu restricted extras can be found in the software center.
Did you use sudo? If not try again using: sudo /usr/share/doc/libdvdread4/install-css.sh
The system will ask you to enter your password.

I used the sudo and it works PERFECTLY.  Many thanks.  Such a lovely feeling!

How do I attach  SOLVED to this?

---

### Post by tersogar on 2012-01-10
> **sallymc said:**
> I used the sudo and it works PERFECTLY.  Many thanks.  Such a lovely feeling!

How do I attach  SOLVED to this?

Just go to Thread Tools and marked solve.

Glad to help

---

### Post by KayaE on 2012-01-10
same problem..but i cant solve it on this way above..
terminal reading is:

Preparing to replace libdvdcss2 1.2.9-2medibuntu4 (using .../dvdcss-DGS8g4/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
libdvdcss2 (1.2.10-0.3medibuntu1) kuruluyor...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place


so what can i try?

---

### Post by KayaE on 2012-01-11
ubuntu-restricted-extras 56

this package worked for me..

---

