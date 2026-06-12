---
title: "System bug?!"
date: 2015-07-20
forum: Multimedia Software
---

### Post by houshdaran on 2015-07-20
Hello.
When I tried the last two times to listen to my audio lessons, my system hanged  (I ran VLC and tried to adjust it). So the problem is two-fold:
1-sound problem
2-occasional system hangs due to sound problem.

---

### Post by dino99 on 2015-07-20
it should be usefull to know a bit about your ubuntu version, the session opened (unity or else), the graphic card/chipset and the driver installed
then your might find some warnings/errors logged either inside Xorg.0.log and/or /var/log/dmesg

---

### Post by ajgreeny on 2015-07-20
I have moved your thread to the Multimedia Software support forum; it may get more and better answers here.

What file type are these lessons, or are they streamed in some way from the web, as flash, perhaps?

Does this problem occur with all audio or just some file types?

---

### Post by houshdaran on 2015-07-21
> **ajgreeny said:**
> I have moved your thread to the Multimedia Software support forum; it may get more and better answers here.

What file type are these lessons, or are they streamed in some way from the web, as flash, perhaps?

Does this problem occur with all audio or just some file types?

I don't have  many audio files.

Yes, they are downloaded from a Coursera course website.

The files are of .mp4 types

---

### Post by houshdaran on 2015-07-21
> **dino99 said:**
> it should be usefull to know a bit about your ubuntu version, the session opened (unity or else), the graphic card/chipset and the driver installed
then your might find some warnings/errors logged either inside Xorg.0.log and/or /var/log/dmesg


There are many lines in /var/log/dmesg
My ubuntu version is 14.04 LTS, as far as I know (I  don't know the commands to get things that you asked)

---

### Post by ajgreeny on 2015-07-22
Have you installed any of the codecs needed to decode mp4 audio files?

For a start see what success you get by installing **ubuntu-restricted-extras** (or xubuntu, lubuntu, kubuntu-restricted-extras, depending on your actual OS) which you can find from command ```
lsb_release -dc && echo "Desktop:	$DESKTOP_SESSION" && uname -mrn
```
When installing that package you may find everything comes to a halt because there is a EULA window behind the terminal or software -centre waiting for you to agree the terms, which you can do by using Tab to highlight the "Yes" or "OK" (I can't remember which shows) then hitting Enter.

---

### Post by houshdaran on 2015-07-27
> **ajgreeny said:**
> Have you installed any of the codecs needed to decode mp4 audio files?

For a start see what success you get by installing **ubuntu-restricted-extras** (or xubuntu, lubuntu, kubuntu-restricted-extras, depending on your actual OS) which you can find from command ```
lsb_release -dc && echo "Desktop:    $DESKTOP_SESSION" && uname -mrn
```
When installing that package you may find everything comes to a halt because there is a EULA window behind the terminal or software -centre waiting for you to agree the terms, which you can do by using Tab to highlight the "Yes" or "OK" (I can't remember which shows) then hitting Enter.
This is all I got:> 
soheil@soheil-desktop:~$ lsb_release -dc && echo "Desktop:$DESKTOP_SESSION" && uname -mrn
Description:    Ubuntu 14.04.2 LTS
Codename:    trusty
Desktop:gnome
soheil-desktop 3.13.0-57-generic i686
soheil@soheil-desktop:~$ 


No window appeared

---

### Post by NathanRodriguez on 2015-07-29
The window should appear when you try to install ubuntu-restricted-extras package with extra codecs.

Can be done via command line:

$ sudo apt-get install ubuntu-restricted-extras

---

