---
title: "my mp3s wont work"
date: 2012-04-09
forum: Multimedia Software
---

### Post by nightinjail on 2012-04-09
i probably shuld have used the search button... but des anyone know why i can play my mp3s? i clicked on them and opened up rhymebox and it wont play them i tried to install the plugins but im not sure why they wont install . im on the new ubuntu 12.04 i believe beta 2 if that makes a difference i also used wubi to install.. just sayin i love wubi so simple

---

### Post by Yellow Pasque on 2012-04-09
Try this first: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by dylan07 on 2012-04-09
Do you have the Ubuntu-Restricted-Ectras installed? That contains the .mp3 codec, needed. To install run:

```
sudo apt-get install ubuntu-restricted-extras
```in a terminal ( ctrl + alt + T )

EDIT: The link in the above post does not mention support for 11.10 (oneric) nor 12.04 (precise). I do not know if it will work or not.

---

### Post by nightinjail on 2012-04-09
> **dylan07 said:**
> Do you have the Ubuntu-Restricted-Ectras installed? That contains the .mp3 codec, needed. To install run:

```
sudo apt-get install ubuntu-restricted-extras
```in a terminal ( ctrl + alt + T )

EDIT: The link in the above post does not mention support for 11.10 (oneric) nor 12.04 (precise). I do not know if it will work or not.


no it doesnt work termial said invalid operation install

---

### Post by dylan07 on 2012-04-09
It works for me (but I already have it)

```
geek@geek-machine:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for geek: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  libaccess-bridge-java libx264-116 python-central libaccess-bridge-java-jni
  libept1 libvpx0 libmusicbrainz4c2a
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by nightinjail on 2012-04-09
> **Temüjin said:**
> Try this first: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
  

genious..

---

### Post by Yellow Pasque on 2012-04-10
> **nightinjail said:**
> genious..
So is your problem solved?

---

### Post by nightinjail on 2012-04-11
yes thanks :D

---

