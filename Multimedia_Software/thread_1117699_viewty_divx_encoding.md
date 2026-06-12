---
title: "viewty divx encoding"
date: 2009-04-06
forum: Multimedia Software
---

### Post by seldon77 on 2009-04-06
someone might find this useful:

to encode a whole directory of .avi video files into a format suitable for mobile phones (a viewty at least), similar to 3gp, you can use this at a bash prompt:

```
mkdir mobile; IFS=$'\n' ; for f in `ls -1 *.avi` ; do FILE=$(basename "$f" .avi) ; mencoder "$FILE.avi" -oac lavc -lavcopts acodec=libmp3lame:abitrate=64 -ovc lavc -lavcopts vcodec=mpeg4:vpass=1:vbitrate=200 -ffourcc DX50 -vf scale=400:240 -o "mobile/$FILE.avi"; sleep 30; mencoder "$FILE.avi" -oac lavc -lavcopts acodec=libmp3lame:abitrate=64 -ovc lavc -lavcopts vcodec=mpeg4:vpass=2:vbitrate=200 -ffourcc DX50 -vf scale=400:240 -o "mobile/$FILE.avi"; rm "frameno.avi"; rm "divx2pass.log"; sleep 30; done
```

---

### Post by Francis 24/24 on 2009-11-03
Yes, very useful indeed ! Many, many thanks !

I would suggest to use 320x240 instead of 400x240, in order to get a less
distorded picture.

It works great also for .mp4 source files, providing they are renamed as
.avi  . 

Note : the following errors have apparently no effect and can be disregarded :
"ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header."

Thanks again !

---

### Post by mdurham on 2009-11-04
Thanks for the info, it would be very useful if I knew how to upload stuff to the phone (LG KU990). How do you guys do that without using Windows and installing PC Suite?
Cheers, Mike

---

### Post by Francis 24/24 on 2009-11-16
I installed a Micro SDHC card in the phone. When I connect the phone to the computer using the usb cable, this card appears as a disk.The phone has created directories and they appear using the usual linux commands. Uploading is only a matter of copying files into the right directory.It seems that one can only access this card, and no other place in the phone.
Although the phone only supports 2GB Micro SDHC card, I use a 4GB card.But,
as stated in several forums, DONT FORMAT a larger than 2GB card with the phone, or you will end up with a 2GB card whatever the real capacity of the card. My card came already formatted and I did not do anything beside inserting it in the phone.

---

### Post by mdurham on 2009-11-16
Thanks for the info Francis 24/24, that's a great help.
Cheers, Mike

---

