---
title: "Webcam not working"
date: 2013-02-04
forum: Multimedia Software
---

### Post by Tom6153 on 2013-02-04
I am having trouble getting the webcam to work properly
I installed cheese and the webcam showed my picture and I was able to take a photo but when i tried to record myself the program crashed.
now i am trying to fix it by following the instructions on this page
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)
however
ls /dev/video*
 ls /dev/audio*

gave me....
tom@tom-Monza-T200:~$ ls /dev/video*
/dev/video0

and....tom@tom-Monza-T200:~$ ls /dev/audio*
ls: cannot access /dev/audio*: No such file or directory

which is problem, no sound?????

so then i kept going and i opened vcr and tried to paste the video
thing in but....i got this....

 p, li { white-space: pre-wrap; }  [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'v4l2://dev/video0[/COLOR]
 [COLOR=#000000]'. Check the log for details.[/COLOR]
 [COLOR=#000000]
[/COLOR]
[COLOR=#000000]so i am a little stuck.....[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]please help[/COLOR]
[COLOR=#000000]
[/COLOR]

---

### Post by ajgreeny on 2013-02-04
I have never managed to get cheese to record video, with or without sound, but simply get a black video window, so I have given up on cheese and use guvcview in its place.

I have also used wxcam from [http://sourceforge.net/projects/wxcam/files/wxcam/](http://sourceforge.net/projects/wxcam/files/wxcam/) but that does not record sound from my separate mic, which guvcview does with no problem.

---

