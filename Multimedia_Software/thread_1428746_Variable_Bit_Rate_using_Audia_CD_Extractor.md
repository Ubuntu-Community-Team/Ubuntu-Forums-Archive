---
title: "Variable Bit Rate using Audia CD Extractor?"
date: 2010-03-13
forum: Multimedia Software
---

### Post by oxf on 2010-03-13
A couple of weeks ago I upgraded and did a clean installed of Karmic. 
 
In previous versions of Audio CD Extractor you could edit a string in the "edit preferences" to set the variable bit rate for MP3 ripping. Specifically you could set the option "VBR=4" (Lame New Algorthym) to select variable bit rate. However, now the "VBR=xx" option is no longer there!
 
Searching around a bit reveals some indications that using a newer realease of Lame this might no longer necessary? But its at all clear. Please could someone clarify whats what?
Do I need to insert VBR=4 or not?
and if I do just to be safe would there be any negative effect if it's not actually needed ?
 
Many thanks

---

### Post by oxf on 2010-03-13
Any ideas?

---

### Post by Yellow Pasque on 2010-03-13
If you don't set vbr=, then you'll get cbr.

---

### Post by oxf on 2010-03-14
> **Temüjin said:**
> If you don't set vbr=, then you'll get cbr.

OK ... My confusion was that unlike previous versions the "vbr=" part of the string was ommited this time. Before I had a choice of:
vbr=0   (cbr)
vbr=2   (vbr using old Lame algorithm)
vbr=3   (average bitate)
vbr=4   (vbr New Lame algorith)

However, this time by default there simply is no VBR= part of the string

---

### Post by Yellow Pasque on 2010-03-14
CBR is the default setting, so the vbr= got removed when you did a clean install

---

### Post by oxf on 2010-03-15
> **Temüjin said:**
> CBR is the default setting, so the vbr= got removed when you did a clean install

OK that explains it. Thanks!

---

