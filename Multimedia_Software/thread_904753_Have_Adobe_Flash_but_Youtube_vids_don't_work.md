---
title: "Have Adobe Flash but Youtube vids don't work"
date: 2008-08-29
forum: Multimedia Software
---

### Post by nouseforaname7 on 2008-08-29
I have the newest Flash (I think) but can't view youtube vids

Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.

???

Any ideas? 

Keep in mind I'm very, very, new to Linux

---

### Post by Crafty Kisses on 2008-08-29
Is it just a gray box, do you get audio?

---

### Post by nouseforaname7 on 2008-08-29
It gives the 'Click to download Latest Flash Player" thing

---

### Post by Crafty Kisses on 2008-08-29
> **nouseforaname7 said:**
> It give the 'Click to download Latest Flash Player" thing

What version of Ubuntu are you using?

---

### Post by nouseforaname7 on 2008-08-29
Hardy

---

### Post by Crafty Kisses on 2008-08-29
Try this in Terminal:
```
sudo apt-get remove flashplugin-nonfree
```
Then after that, do this:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by wolfen69 on 2008-08-29
sometimes a simple uninstall/re-install will do.
```
sudo apt-get purge flashplugin-nonfree
```
then
```
sudo apt-get clean
```
then
```
sudo apt-get autoremove
```
then
```
sudo apt-get install flashplugin-nonfree
```
make sure firefox is closed during this.

---

### Post by nouseforaname7 on 2008-08-29
Already tried

Maybe it's a javascript problem?

I have it ticked however

---

### Post by Crafty Kisses on 2008-08-29
Post the results of this command:
```
java --version
```

---

### Post by wolfen69 on 2008-08-29
if you do not do "clean" and "autoremove", you will just be re-installing the exact same package. (because the old one will remain on your computer) try what i wrote earlier.

---

### Post by nouseforaname7 on 2008-08-29
Okay, I did it again with FF closed and it works :)

---

### Post by Crafty Kisses on 2008-08-29
Nice, please mark the thread solved. :)

---

### Post by badguyMD on 2008-08-29
Oops, meant to go back and hit thanks on Codename's post before wolfen...

Anyway, thanks folks

---

### Post by Crafty Kisses on 2008-08-29
No problem, glad we could help.

---

### Post by Patrissimo on 2009-01-03
> **wolfen69 said:**
> sometimes a simple uninstall/re-install will do.
```
sudo apt-get purge flashplugin-nonfree
```
then
```
sudo apt-get clean
```
then
```
sudo apt-get autoremove
```
then
```
sudo apt-get install flashplugin-nonfree
```
make sure firefox is closed during this.

thanks Wolfen
this not only fixed youtube, but I can listen to Prairie Home Companion for the first time now

---

