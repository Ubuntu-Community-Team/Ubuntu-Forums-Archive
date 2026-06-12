---
title: "WinFF not working after lucid update."
date: 2010-07-29
forum: Multimedia Software
---

### Post by Robin_216 on 2010-07-29
I recently updated lucid and since then i can´t use winff anymore.

When i tried it in a terminal i get the following output:
robin@robin-laptop:~$ winff

[WARNING] Out of OEM specific VK codes, changing to unassigned
[WARNING] Out of unassigned VK codes, assigning $FF
ConfigBase::load: config format is not valid
[profiles,default]: background_image is invalid
Usage: x-terminal-emulator [options]

x-terminal-emulator: error: Additional unexpected arguments found: ['&']
ConfigBase::load: config format is not valid
[profiles,default]: background_image is invalid
Usage: x-terminal-emulator [options]

x-terminal-emulator: error: Additional unexpected arguments found: ['&']


Does anybody else have this problem and/or a solution for this?

---

### Post by ron999 on 2010-07-29
Look in WinFF's edit > preferences > linux > set terminal options
Change it from e to x, or vice versa. Then try it again.

---

### Post by Robin_216 on 2010-07-29
Thanks, that fixed the problem!

---

### Post by drixxx on 2011-07-05
It solved my problem too !!
Thanks ;)

---

### Post by johnh10000 on 2011-09-01
> **ron999 said:**
> Look in WinFF's edit > preferences > linux > set terminal options
Change it from e to x, or vice versa. Then try it again.

cheers worked for me too!!

---

### Post by soixante4 on 2011-09-08
Great, it worked for me as well, thanks much ! :D

---

### Post by Tshann on 2012-09-19
I use Crunchbang Linux Waldorf - which uses terminator. So I had to put in /usr/bin/terminator. Also had to change the -e to -x, then she worked!

  Yup, worked for me too! Awesome! Thanks.

---

