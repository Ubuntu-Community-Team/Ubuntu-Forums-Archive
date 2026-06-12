---
title: "Weird QDVDAuthor proccesing error-Help"
date: 2006-10-21
forum: Multimedia &amp; Video
---

### Post by mibadt on 2006-10-21
Hi,
I try to use QDVDAuthor (v 0.1.0) on my Kubuntu Dapper to create a DVD image from a DV file I've shot.
Initially, it proceeds OK till it gets stuck at the processig main menu..mpg stage. As can be seen from the following output, QDVDAuthor script results in a PATH which contains **TWO consectuve slashes**  afer the /tmp (instead of a single one) and thus can't find the file it's looking for.
After one such trial, I tried to manually edit the respective script lines (removed one of the slashs), yet, at run-time, **the second slash appears out of nowhere and causes a stuck.**

Please advise!  ;) 

TIA


-------output-----------

STAT: fixing VOBU at 4032MB (11505/11558, 99%)
STAT: fixing VOBU at 4037MB (11521/11558, 99%)
STAT: fixing VOBU at 4043MB (11537/11558, 99%)
STAT: fixing VOBU at 4048MB (11553/11558, 99%)
STAT: fixed 11558 VOBUS                         

INFO: dvdauthor creating table of contents
INFO: Scanning /media/sdb9//VIDEO_TS/vts_01_0.ifo
INFO: Creating menu for TOC

STAT: Processing /media/sda4/tmp//Slov2006/Main Menu VMGM_menu.mpg...
ERR:  Error opening /media/sda4/tmp//Slov2006/Main Menu VMGM_menu.mpg: No such file or directory

---

