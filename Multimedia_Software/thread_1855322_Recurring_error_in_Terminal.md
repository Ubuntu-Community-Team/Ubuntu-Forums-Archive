---
title: "Recurring error in Terminal"
date: 2011-10-05
forum: Multimedia Software
---

### Post by peter wilcox on 2011-10-05
I get the following error message when trying anything in the Terminal. I don't have a clue how to fix it. Can anybody help? I a a complete novice with Ubuntu.
                     p { margin-bottom: 0.21cm; }  "E: Malformed line 54 in source list /etc/apt/sources.list (dist parse) 
 E: The list of sources could not be read."

---

### Post by garvinrick4 on 2011-10-06
You can give this a go, open a terminal copy and paste one at a time and will remove,clean and make anew.
```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get clean all 
sudo apt-get update

```

---

### Post by peter wilcox on 2011-10-06
> **peter wilcox said:**
> I get the following error message when trying anything in the Terminal. I don't have a clue how to fix it. Can anybody help? I a a complete novice with Ubuntu.
                     p { margin-bottom: 0.21cm; }  "E: Malformed line 54 in source list /etc/apt/sources.list (dist parse) 
 E: The list of sources could not be read."
Thanks but I get the same error message 
E:Malformed line 54 in source list/etc/apt/sources.list (dist parse)

---

### Post by matt_symes on 2011-10-06
Hi

You have a problem with your sources.list file. 

To fix this the line needs to be removed but to make sure there are no other problems please open a terminal and type

```
cat /etc/apt/sources.list
```

Copy and paste the results back here for instruction on how to proceed.

Kind regards

---

### Post by peter wilcox on 2011-10-06
Thanks, this is what I got
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://www.debian-multimedia.org/oldstable](http://www.debian-multimedia.org/oldstable) main

---

### Post by matt_symes on 2011-10-06
Hi

> deb [http://www.debian-multimedia.org/oldstable](http://www.debian-multimedia.org/oldstable) mainThis is the offending line and need to be removed or commented oyut.

Open a terminal and type

```
sudo nano /etc/apt/sources.list
```Enter your password. It will not be echoed to the screen. Scroll down to the line 

```
deb [http://www.debian-multimedia.org/oldstable](http://www.debian-multimedia.org/oldstable) main
```and delete it.

Press ctrl + o to save and ctrl + x to exit.

Then type 

```
sudo apt-get update
```Kind regards

---

