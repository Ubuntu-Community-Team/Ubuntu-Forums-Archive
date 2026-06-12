---
title: "error in accessing webcam stream using ffmpeg"
date: 2010-04-02
forum: Multimedia Software
---

### Post by sarosh on 2010-04-02
i have comnnected a usb webcam into my PC then  when i write down 





 ffmpeg -f video4linux2 -s 720x480 -r 30000/1001 -i /dev/video1 -f avi -vcodec mjpeg -s cif -r 30000/1001 -y  silver.avi
 
 
on terminal ... it gves error ,
 

[video4linux2 @ 0x99e0420][3]Capabilities: 5000001
[video4linux2 @ 0x99e0420]The V4L2 driver changed the video from 720x480 to 352x288
[video4linux2 @ 0x99e0420]Cannot find a proper format for codec_id 0, pix_fmt -1.
/dev/video1: Input/output error
 
 
i knw the /dev/vid1 path is correct.... what is this error codec _id=0 cannot find proper format?? plz explain how to fix this?ion
 my email is [EMAIL="sarosh.nust@hotmail.com"]sarosh.nust@hotmail.com[/EMAIL]
plzzz help i want a quick solution

---

