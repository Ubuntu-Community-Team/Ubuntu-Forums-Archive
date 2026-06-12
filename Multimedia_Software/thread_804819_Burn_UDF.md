---
title: "Burn UDF?"
date: 2008-05-23
forum: Multimedia Software
---

### Post by JohnLM_the_Ghost on 2008-05-23
Is it possible to burn an UDF DVD with Linux? ISO9660 won't allow 2Gb+ files.

---

### Post by xc3RnbFO8P on 2008-05-23
K3B

Install in Synaptic Package Manager:

libmad0
libmad0-dev
python-pymad

k3b
k3b-i18n
libk3b2
libk3b2-extracodecs
libk3b2-mp3
libk3b-dev

I install this to

dvd95
dvdauthor
liba52
liba52  dev
libdvdnav4
mkisofs

---

### Post by disturbedite on 2008-05-23
yes.  k3b will automatically select UDF if needed, assuming you have the needed packages installed.

---

### Post by JohnLM_the_Ghost on 2008-05-31
**K3b** really does burn UDF. But I got a feeling it mangles up my files!
My DVD's files didn't pass the **cmp** check!

Well some bytes mangled in Video file would make few glitches, but in binary file a single missing bit would produce different machine code. Scary!

Of course I can boot into Windows, It just isn't that convenient to reboot when DVD's need to be burnt.

EDIT: Well I tried to burn with very low speeds. Seems OK, now. Somehow **Nero** and **Alcohol** had better dynamic speed correction! Maybe I should mention this in some K3b dev forums? (though I reckon it wouldn't help much)

---

### Post by xc3RnbFO8P on 2008-05-31
I have had this speed problem with DVDs,
now I only use "auto" when I burn DVDs, never fails.

---

### Post by JohnLM_the_Ghost on 2008-05-31
Well 'Auto' was the one what failed me the first time!
I had to put 6x
But I've tried only once. Gotta do more tests.
And have to make a habit to cmp files after burn, just in case.

---

### Post by xc3RnbFO8P on 2008-05-31
You can check your burned DVDs with **dvdisaster**
In Add/Remove (all available application)

---

### Post by JohnLM_the_Ghost on 2008-06-16
Hmm... I have problems reading k3b burned UDF disks in XP.
I just have one UDF disk, so I don't know if this applies generally.

---

