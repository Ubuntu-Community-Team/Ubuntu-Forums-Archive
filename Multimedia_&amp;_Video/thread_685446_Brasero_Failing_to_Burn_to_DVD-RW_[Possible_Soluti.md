---
title: "Brasero Failing to Burn to DVD-RW [Possible Solution]"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by garrett_curran on 2008-02-02
Hi ,

This is my first post on the forums so be kind :).

OS  : Xubuntu 7.10 ( Fresh install ) 

Problem : 

Attempting to burn a DVD-RW Disc ( Media brand Sony ) would fail after blanking. So I tested the commandline version of growisofs with 

growisofs -Z /dev/dvd -R somefiles  

This failed giving the suggestion to use "-dvd-compat -dvd-compat" so again i then tried 

growisofs -Z /dev/dvd -dvd-compat -dvd-compat -R somefiles  , and Success !!

So it looked to me like Brasero wasnt passing in the correct arguements when the DAO option was selected.

So i tried renaming the /usr/bin/growisofs to  originalgrowisofs and replaced growisofs with a 
bash script

#!/bin/sh
/usr/bin/originalgrowisofs -dvd-compat -dvd-compat $@

giving it the usual 755 permissions

Restart Brasero stick in the DVD-RW and attempt DATA Burn , and Success. 

Whats puzzling is Braseros logging shows , even before i made the changes that it takes in the arg

-dvd-compat  


and after the changes logging shows no change still showing

-dvd-compat 


But on the command line growisofs needed "-dvd-compat -dvd-compat" a single one wouldnt work. 

Maybe this can help people using other Guis which use growisofs . 

Anyways later.


EDIT : Another reason for the burn failing was if my disk label had spaces in it like the default eg "Data Disk x" failed , "Data_Disk_x" burned successfully

---

