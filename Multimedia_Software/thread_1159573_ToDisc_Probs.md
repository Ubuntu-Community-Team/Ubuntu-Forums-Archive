---
title: "ToDisc Probs"
date: 2009-05-14
forum: Multimedia Software
---

### Post by thedoctor81877 on 2009-05-14
Hi. I am trying to burn a DVD using ToDisc. I have used ToVid to get my files into .mpg format, & then used ToDisc, but keep getting an error. Here is what I get when I ran ToDisc. Any thoughts???

thedoctor@thedoctor-laptop:~$ todisc -files doctor.who.s0403.mpg doctor.who.s0404.mpg doctor.who.s0405.mpg \ -titles "Planet of the Ood" "The Sontaran Stratagem" "The Poison Sky" \ -out Doctor Who_Season 1_Disc 2
grep: /usr/bin/tovid-init: No such file or directory
--------------------------------
todisc
Generate a DVD filesystem with animated thumbnail menus
Part of the tovid suite, version 0.31
[http://www.tovid.org](http://www.tovid.org)
--------------------------------
`/tmp/todisc-work.0' -> `/home/thedoctor/todisc-work.0'
Usage:
    todisc [OPTIONS] \
      -files File1.mpg File2.mpg ... \
      -titles "Title 1" "Title 2" ... \
      -out OUT_PREFIX
Input files must be MPEG, and the number of -files and -titles must be equal.
See the todisc manual page ('man todisc') for additional documentation.
=========================================================
***

Please provide at least one file and one title.

---

