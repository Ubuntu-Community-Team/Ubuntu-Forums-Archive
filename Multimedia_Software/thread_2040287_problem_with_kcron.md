---
title: "problem with kcron"
date: 2012-08-10
forum: Multimedia Software
---

### Post by humble app on 2012-08-10
Hello,just new member in the forum.
I need to make a script for a  sort-of "recording sheduler..."  well...I was trying with mplayer 

mplayer  mms://streaming2.eu.radiomaria.org/peru -dumpstream -dumpfile file.mp3

and  

killall -KILL mplayer

when I tried to execute all this  in kconsole ...works...but no when I put this in Kcron....nothing  happen....
why?


Also I made a script



#!/bin/bash
nombreprograma="program1"
fecha=`date  +%y%m%d%X`
archivo=".mp3"
fecha1=$fecha$archivo
mplayer  mms://streaming2.eu.radiomaria.org/peru -dumpstream -dumpfile "$fecha1"



I  was setting all the options for a daily execution in some hour...with  kcron
but nothing...only works when I execute it in kconsole...

bash  /home/nuevo/Escritorio/usr/bin/script1.sh

Also ,the resulting  mp3 plays fine only with mplayer... others (real  player,windows media player,etc) can't play the file ...real player  tells "Unsupported document type".... only mplayer can play it...

by the way..,I have Lucyd Lynx...in a 14 GB partition

searching for some help....thanks in advance.

---

