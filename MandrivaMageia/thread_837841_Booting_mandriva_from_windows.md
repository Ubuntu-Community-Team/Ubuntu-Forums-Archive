---
title: "Booting mandriva from windows"
date: 2008-06-22
forum: Mandriva/Mageia
---

### Post by logos34 on 2008-06-22
Due to the issue described [here]("http://wiki.mandriva.com/en/Docs/SysAdmin/GrubInodeTransition"), people wishing to use windows NTLDR to boot Mandriva linux (_>_2008.1) will encounter a problem.

Here's the only two ways I've found that work:

1. (easiest)

Write grub to the mandriva root partition:

> **# grub-install /dev/sda3** (replace 'sda3' with your actual root)Then, 

**# dd if=/dev/sda3 of=grub.mbr bs=512 count=1**

Look in your home directory for 'grub.mbr' and copy it to windows **c:\**

Add the following to **c:\boot.ini**:

> c:\grub.mbr="Mandriva"
**OR**

2. (using **grldr**)

Download [grub4dos .zip]("http://download.gna.org/grub4dos/") and extract **grldr** to c:\

Make a **c:\boot\grub** directory.  Create a new file called **menu.lst** inside and paste this chainloader entry:

> 
timeout 0 
default /default

title Mandriva
root (hd0,2)
chainloader +1(again, the example is root on sda3. Remember, Grub starts counting at 0, hence the '2')

Add the following to boot.ini:

> c:\grldr="Mandriva"

---

