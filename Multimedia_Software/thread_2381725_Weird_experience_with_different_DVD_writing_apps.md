---
title: "Weird experience with different DVD writing apps"
date: 2018-01-04
forum: Multimedia Software
---

### Post by raphaell2 on 2018-01-04
Not sure if I should post this in Multimedia Software or in Hardware.

I  had a weird experience with different DVD writing apps under Xubuntu  16.04 today. I wrote a collection of files larger than 4GB to DVD using  Brasero, and it was very slow. When I first ordered the writing, my DVD  drive became very noisy and apparently accelerated to a very high speed,  but then it suddenly became mostly quiet, and only then did Brasero  tell me that the writing itself had started. It then continued to write at a  very low speed - when it had finished, it told me that the average  writing speed had been 1.4x. The DVD turned out fine, though. 

Then  I wrote another collection of files - this one between 3GB and 4GB - to  another DVD using Xfburn. This time, the writing process was very fast,  it finished quickly, and this DVD turned out fine, too. I used the same  DVD drive both times, and the DVDs were the same brand from the same  package.

Oh, and a few days ago, when I was still using Xubuntu  17.10, I had a problem with several attempts to write isos to DVD using  K3b that failed - it seemed to write fine for a while, and then suddenly  it told me that there was no disc in the drive. It wasn't a problem  with the hardware or the isos - Puppy then managed to write the same  isos to DVD using the same drive just fine.

---

### Post by Autodave on 2018-01-04
xfburn is what I always use.  I have had many problems with just about every other program, but xfburn just keeps working.

---

### Post by scdbackup on 2018-01-05
Hi, 

 what you describe with Brasero looks like a problem between drive and medium. High noise at the start is normal for high-speed DVD+R or DVD-R. But average speed 1.4x is not normal with any DVD type. What type exactly are you using ?

 There may be two backend burn programs involved: Xfburn uses libburn, Brasero uses libburn or growisofs (it depends on the plugin chosen), K3B uses growisofs (support for libburn based cdrskin might be upcomming). I am developer of libburn.

My local Brasero seems to use libburn for DVD+RW and growisofs for BD-RE, if both backends are installed. Regrettably it does not allow me to disable plugins and thus choose a backend without de-installing the other. On DVD-R media, growisofs and libburn might differ in the write types used (Disc-At-Once versus Incremental). Brasero offers in the configuration of the growisofs plugin to enable DAO. libburn will use DAO by default, if the medium shall not stay appendable (but application programs of libburn could override that default).

 Nevertheless, the good and less good behavior of a drive with particular burn software might just be incidential because of the individual DVD medium.

Have a nice day :)

Thomas

---

### Post by raphaell2 on 2018-01-05
Thank you.

> What type exactly are you using ?

A 16x 4.7 GB DVD-R in an internal drive called "HL-DT-ST DVDRAM GH24NS95 SCSI CdRom Device" by LG.

---

### Post by raphaell2 on 2018-01-05
> **Autodave said:**
> xfburn is what I always use.  I have had many problems with just about every other program, but xfburn just keeps working.

I like Xfburn myself, but IMO it's annoying that it doesn't do post-burn integrity checks.

---

