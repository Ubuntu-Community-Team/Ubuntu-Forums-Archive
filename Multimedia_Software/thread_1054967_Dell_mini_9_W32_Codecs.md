---
title: "Dell mini 9 W32 Codecs"
date: 2009-01-30
forum: Multimedia Software
---

### Post by catch22 on 2009-01-30
Hi

I hope this is the right place....

Iam unable to install the w32 codecs, i have added the mediaubuntu software source and added the key but when i try to install i get the following error;

Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

I have also tried updating the software sources to include the multiuniverce packages but these return 404 errors.

---

### Post by mc4man on 2009-01-30
Do you know if you have a 64bit install?, if so then you'd need to get w64codecs. (of limited value compared to w32codecs

---

### Post by Papo1988 on 2009-01-30
As far as im aware the dell mini 9 has an intel atom n270 processor (32-bit), so im assuming the w32codecs package is what you need. I know it sounds daft but have you run the command:

"sudo apt-get update"

since you added the repo? if not run that, then run:

"sudo apt-get install w32codecs"

Let us know how you get on.

Papo1988

---

### Post by wolfen69 on 2009-01-30
> **Papo1988 said:**
> As far as im aware the dell mini 9 has an intel atom n270 processor (32-bit), so im assuming the w32codecs package is what you need. I know it sounds daft but have you run the command:

"sudo apt-get update"

since you added the repo? if so run that then run:

"sudo apt-get install w32codecs"

Let us know how you get on.

Papo1988

if that does not work, try
```
sudo dpkg --configure -a
```then
```
sudo apt-get install -f
```then try to install w32codecs.

---

### Post by binbash on 2009-01-30
> **catch22 said:**
> Hi

I hope this is the right place....

Iam unable to install the w32 codecs, i have added the mediaubuntu software source and added the key but when i try to install i get the following error;

Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

I have also tried updating the software sources to include the multiuniverce packages but these return 404 errors.

did you do update? sudo apt-get update

---

### Post by mc4man on 2009-01-30
> As far as im aware the dell mini 9 has an intel atom n270 processor (32-bit)

If that's the case then you could in this instance just  install directly (good for hardy and intrepid

[http://packages.medibuntu.org/intrepid/w32codecs.html](http://packages.medibuntu.org/intrepid/w32codecs.html)

---

### Post by catch22 on 2009-01-30
Thanks for the help,
In the end i had to download and install with the package manager, everything else that i tried came back with the same error.

I am now off to try and get five ondemand to work so i may be back :D

---

