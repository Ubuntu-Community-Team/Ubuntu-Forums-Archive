---
title: "DVD probs"
date: 2009-05-19
forum: Multimedia Software
---

### Post by thedoctor81877 on 2009-05-19
I am having difficulty burning DVD's. I have a few avi's and some rmvb's. I tried the following on todisc, then tovid, with no luck. Can someone please tell me what I am doing wrong???

thedoctor@thedoctor-laptop:~/dw.s04.d03$ todisc -files dw.s04.d03_01_01.mpg dw.s04.d03_02_01.mpg \ -titles "The Poison Sky" "The Doctor's Daughter" \ -out Doctor_Who_Season_4_Disc_3
grep: /usr/bin/tovid-init: No such file or directory
--------------------------------
todisc
Generate a DVD filesystem with animated thumbnail menus
Part of the tovid suite, version 0.31
[http://www.tovid.org](http://www.tovid.org)
--------------------------------
`/tmp/todisc-work.0' -> `/home/thedoctor/dw.s04.d03/todisc-work.0'
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

***
thedoctor@thedoctor-laptop:~/dw.s04.d03$ ls
dw.s04.d03_01_01.mpg  dw.s04.d03_menu_0.xml   dw.s04.d03.xml
dw.s04.d03_02_01.mpg  dw.s04.d03_menu2_0.mpg
thedoctor@thedoctor-laptop:~/dw.s04.d03$ makexml -menu dw.s04.d03_menu2_0.mpg dw.s04.d03_01_01.mpg dw.s04.d03_02_01.mpg \ -out Doctor_Who_Season_4_Disc_3
grep: /usr/bin/tovid-init: No such file or directory
--------------------------------
makexml
A script to generate XML for authoring a VCD, SVCD, or DVD.
Part of the tovid suite, version 0.31
[http://www.tovid.org](http://www.tovid.org)
--------------------------------
Adding a titleset-level menu using file: dw.s04.d03_menu2_0.mpg
grep: /usr/bin/tovid-init: No such file or directory
    dw.s04.d03_menu2_0.mpg has aspect 133 (standard).
Adding title: dw.s04.d03_01_01.mpg as title number 1 of titleset 1
grep: /usr/bin/tovid-init: No such file or directory
    dw.s04.d03_01_01.mpg has aspect 177 (widescreen).
    Calculating the duration of the video with:
        idvid -terse "dw.s04.d03_01_01.mpg"
    This may take a few minutes, so please be patient...
grep: /usr/bin/tovid-init: No such file or directory
    The duration of the video is 00:44:27
Adding title: dw.s04.d03_02_01.mpg as title number 2 of titleset 1
grep: /usr/bin/tovid-init: No such file or directory
    dw.s04.d03_02_01.mpg has aspect 177 (widescreen).
    Calculating the duration of the video with:
        idvid -terse "dw.s04.d03_02_01.mpg"
    This may take a few minutes, so please be patient...
grep: /usr/bin/tovid-init: No such file or directory
    The duration of the video is 00:38:02
The file  -out was not found.  Exiting.
thedoctor@thedoctor-laptop:~/dw.s04.d03$

---

