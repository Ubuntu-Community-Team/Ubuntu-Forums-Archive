---
title: "no video player starts"
date: 2006-07-17
forum: Multimedia &amp; Video
---

### Post by linish on 2006-07-17
i have been using 5.10...after i upgraded to 6.06 ..my drivers stopped working..in the quest for downloading drivers i downloaded many modules and headerfiles..
i dont have much understanding of kernels and modules so all the things were left and right..
now the problem is my computer doesn't boot by default option..i have to go to the menu and select some other version of kernel to boot..
the other problem is no video player starts..totem quits unexpectedly..
mpalyer just comes for  a moment after bein called and closes in a blink..
same is the case with vlc..

i reinstalled all these video players with same result

my audioplayer like xmms is working..

i just cant understand what the problem is...
can any un help
....my glxinfo shows direct rendering as yes..

---

### Post by linish on 2006-07-17
when i start totem from terminal ..it closes with the error segmentation error..same is the case with vlc ..etal] (*,)

---

### Post by linish on 2006-07-17
okee i solved the problem :KS 


strace -fFopen vlc 

did the trick for me..i just knew then what exactly was going wrong ](*,) 
    :D

---

