---
title: "mencoder cyrillic"
date: 2009-04-19
forum: Multimedia Software
---

### Post by aquanim on 2009-04-19
Hi

i have been trying to configure my mediatomb in order to embed subtitles into my movies. However i ran into a small problem the script which i use in order to embed the subtitles uses mencoder and the string is 
mencoder -vf pp=de,scale=548:222 -oac copy -ovc lavc -lavcopts keyint=25:vcodec=mpeg4:vbitrate=679:vpass=1 -sub "subtitle.srt" -o "new file with embeded subtitles" "subtitle.avi" -subcp cp1251 

all is ok until i play the new file when all i can see instead of subtitles is "___ ____ ____." 

any help would be greatly appreciated

---

### Post by aquanim on 2009-04-28
no luck.......

hmmmm

---

