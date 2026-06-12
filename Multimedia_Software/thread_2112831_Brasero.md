---
title: "Brasero"
date: 2013-02-05
forum: Multimedia Software
---

### Post by jdwaugh on 2013-02-05
I want to copy a CD, but when I go to burn it I get an error that read "Installing from packages by files isn't supported"  which is completely opaque.  THe log is as follows:

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1739)
Unsupported type of task operation
Session error : An internal error occurred (brasero_burn_record brasero-burn.c:2856)

WHat the heck is going on?

---

### Post by mandarke on 2013-02-06
installing brasero-cdrkit apparently fixes this issue.

---

### Post by jdwaugh on 2013-02-06
I already have that package installed on my machine.

---

### Post by offgridguy on 2013-02-06
Brasero is not known to be the best disk burner.  Try some of the 
others from the software center. k3b or xfburn.

---

### Post by faflu on 2013-10-03
Check if you have installed also:
cdrdao,
cue2toc.

---

### Post by craig10x on 2013-10-03
Brasero, even when working, is pretty bad...i find it takes forever to burn a disc with it...i think the problem is that it isn't being maintained....so unfortunately, it remains a poor choice as the default burner for ubuntu....

As mentioned K3b is the best but that does bring in a lot of the kde libraries with it....so an alternate choice (that DOES work very well) is XF-Burn....that works very well and is FAST...

---

