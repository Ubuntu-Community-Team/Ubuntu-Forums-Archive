---
title: "will acpi problem be fixed ?"
date: 2010-12-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ivh90 on 2010-12-16
hey guys 
a while ago i bought a new laptop a Toshiba a505 model , 
i tried installing ubuntu several times and i failed , I then noticed I am not the only one with this problem:

now i have to boot with acpi="copy_dsdt" parameter and it is very annoying 
i mean booting is very slooooooooow , and i am missing lots of features (including my backlit keyboard which i paid extra 40$ to get)

guys please tell me that this is going to be solved in the next release , i am a big fan of linux and ubuntu , and i cant wait to get this problem solved

---

### Post by cariboo on 2010-12-16
We can't say whether your problem is going to be solved with this release, can you point us towards any relevant bugs?

---

### Post by ronacc on 2010-12-16
most dsdt's are only supplied with Windows in mind if they are properly inplemented even for that , google around on it and you will see , you may be able to find a linux friendly dsdt for your type/model that can be used to patch your factory supplied one .

---

### Post by Quackers on 2010-12-16
Sometimes re-compiling your existing dsdt can help. It's better to find some known fixes first though :-)

---

### Post by dino99 on 2010-12-17
first thing to do:

open synaptic and search for "tosh", then install the related packages

---

### Post by MacUntu on 2010-12-17
> **Quackers said:**
> Sometimes re-compiling your existing dsdt can help. It's better to find some known fixes first though :-)

Unless you also like to recompile the kernel this won't help, as you can't simply load changed DSDTs with recent kernels.

---

### Post by psusi on 2010-12-17
So instead of filing a bug report and tracking the status there, you ask on the forums if some random, unknown problem you are having that is almost certainly the result of broken bios will be fixed in the next release?  Of course not.

---

### Post by Slug71 on 2010-12-17
> **psusi said:**
> So instead of filing a bug report and tracking the status there, you ask on the forums if some random, unknown problem you are having that is almost certainly the result of broken bios will be fixed in the next release?  Of course not.

The acpi problem is a known issue.

---

### Post by ivh90 on 2010-12-18
thx guys 
I did install tosh packages but that didnt help , I tried other distros but they all fail to load from the live cd (same acpi problem) 
is there anything which can be done to get this fixed ?

---

### Post by psusi on 2010-12-19
I thought you said you used acpi="copy_dsdt" to get around it?  A quick look through the kernel change logs shows that option exists for the purpose of working around broken Toshiba laptop bioses that corrupt the dsdt.  You should be asking Toshiba to fix their broken bios.

---

