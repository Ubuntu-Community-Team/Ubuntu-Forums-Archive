---
title: "can't play videos in MPlayer of VLC"
date: 2009-09-06
forum: Multimedia Software
---

### Post by sajhak on 2009-09-06
Hi all, 
Im using Ubuntu 9.04 .. im new to Ubuntu n Linux.. 

tried of playing some .avi, .flv movie files using VLC and MPlayer... but the player just closes (disappears) without any notification or failure whn the movie is loaded .. no errors are displaying ... 

Is it an issue with the codecs ? please help me in this issue .. 

if i describe more about the file formats n codecs , one of the file i tried to open is having its type as 'Flash video (video/x-flv)" - its Codec is : On2 VP6 Video .. 

Another one's type is "AVI video (video/x-msvideo)"  and its Codec is : XVID MPEG-4 .. 

please tell me if i need to download any other packages ... 

thank s a lot in advace 
Sajith

---

### Post by sajhak on 2009-09-06
Hi all, 

There after i tried running those files in the command line using the command "vlc" .... then i got some of the error messages .. 

one of the messages i got is :
Error: BadAlloc (insufficient resources for operation) 11
  Extension:    132 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x3c00005


Another one is :

[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82
Segmentation fault


From those i think it will be easy to guess where the failure is .. 
please help me, 

Thanks 
Sajith

---

### Post by wojox on 2009-09-06
Got Medibuntu:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by sajhak on 2009-09-06
yoooooooooooo ...........  i got it solved .. :) 

The problem was i had been using the video out put mode the "default" one ... i changed it to "X11" .... now its workinnnnnnnnnnggggggggggggg :) :) 


Thanks all

---

