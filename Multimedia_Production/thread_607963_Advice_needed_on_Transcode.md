---
title: "Advice needed on Transcode"
date: 2007-11-09
forum: Multimedia Production
---

### Post by esoxLucius4 on 2007-11-09
I am transcoding MPEG into AVI and I need advice on quality settings. Output files are Xvid and are done in two passes. 

Example:

#Firs pass
transcode -V -i $ifile -x auto,null -y xvid,null -o $ofile -M 1 -w $quality,50,100 -Q 5 -G 1.5 -R 1

#Second pass
transcode -i $ifile -y xvid -o $ofile -M1 -w $quality,50,100 -Q 5 -G 1.5 -R2

Variable $quality is adjustable and usually within 1000 - 1500 range. What other options are there that could improve video quality of the output files?

thx

---

