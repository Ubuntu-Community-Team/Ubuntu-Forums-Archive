---
title: "Ati Drivers install"
date: 2010-04-25
forum: Multimedia Software
---

### Post by Eiodalin on 2010-04-25
I download the the linux installer for my ati card it's in a .run file and every time i run it in terminal like i was told be someone here before it doesn't run after it's done unpacking:(
it's frustrating the hell out of me if someone knows how to like do this i will very much like your advice because I'm stumped

---

### Post by taurolyon on 2010-04-25
first, you'll have to make it executable. Right click on the file, properties, permissions, check "allow executing file as a program"

put the file in your home folder and open Terminal.

Execute the following command to install it:

```

sudo ./ati-driver-installer-10-3-x86.x86_64.run

```

(that's for the 64 bit 10.3 catalyst drivers - update with your own file name)

---

### Post by Eiodalin on 2010-04-25
i did that and it comes up with

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-20-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.nUlUb0

---

### Post by anku247 on 2010-04-25
try this
put the file on your desktop


in terminal
cd Desktop

then chmod +x 
ati-driver-installer-10-3-x86.x86_64.run 

then sudo 
ati-driver-installer-10-3-x86.x86_64.run 
should work
like  [taurolyon]("http://ubuntuforums.org/member.php?u=1020146") said with what ever version you have

---

### Post by Eiodalin on 2010-04-25
yeah i got the same error as before changing the place of the object and modifying again in the same why didn't make it work

---

### Post by ShadowTek on 2010-04-25
What card do you have?

The proprietary drivers don't work for cards more than a few years old.

---

### Post by Eiodalin on 2010-04-26
the Radeon x1250/1200 lets just say it can be either one.

---

### Post by Mark Phelps on 2010-04-28
> **Eiodalin said:**
> the Radeon x1250/1200 lets just say it can be either one.

Those cards, along with lots of others, were left behind when ATI dropped Linux support for them over a year ago.  There is no ATI Linux driver that will work with those cards and any current versions of Ubuntu.

Doesn't matter HOW you try to install the fglrx drivers, they simply will not work with your card anymore.

Your only resort now is to use the open source drivers -- which are installed by default.

---

### Post by Eiodalin on 2010-04-28
THAT SUCKS NUTS DANM!!! At least it gives me a reason to upgrade my graphics chip

---

