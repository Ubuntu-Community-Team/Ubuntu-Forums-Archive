---
title: "webcam server to connect to zoneminder?"
date: 2012-05-05
forum: Multimedia Software
---

### Post by 65 mustang on 2012-05-05
I have a webcam on a ubuntu machine that i want to share to my zoneminder server on another computer.  I want to set the computer to share the webcam as a IP camera or in some form that the zoneminder computer can record.

All the guides i see refer to "webcam-server" which looks like its a depricated package in 12.04.

I see the packages "webcam" and "webcamd" would those work?

---

### Post by 65 mustang on 2012-05-05
Had good luck with "motion".  Just pointed server to the 8081 port and worked good.

---

### Post by dunwich42 on 2012-05-06
I have been wanting to do the same thing.
I looked at a few options but in the end wrote a small script (called from cron every minute) to grab the image using ffmpeg and then ssh it to my server and ZoneMinder grabs the image from there.
Not ideal but it works as a static image, and seems to be 'easier' than webcamd.

```
/usr/bin/ffmpeg -t 10 -f video4linux2 -s 640x480 -r 30 -i /dev/video0 -f oss -f mp4 $FILEVIDEO 
/usr/bin/ffmpeg -ss 9 -f mp4 -i $FILEVIDEO -s 640x480 -vframes 1 -an $FILEIMAGE

ping -c 1 -t 1 $SERVERIP;
if [ $? -eq 0 ]; then
    scp $FILEIMAGE username@$SERVERIP:$REMOTEPATH
fi
```

Now to have a look at 'motion'....!

---

### Post by UsamaA on 2012-07-29
I would recommend mjpeg-streamer 
Check out [http://blog.philippklaus.de/2012/01/compile-mjpg-streamer-from-source-on-ubuntu-11-10/]("http://blog.philippklaus.de/2012/01/compile-mjpg-streamer-from-source-on-ubuntu-11-10/") for best implementation make a cron job of it starting up with computer. 

Works great with zoneminder 
with source type: ffmpeg
and  source path: [http://xx.xx.xx.xx:abcd/?action=stream&ignored.mjpg](http://xx.xx.xx.xx:abcd/?action=stream&ignored.mjpg)

Hope this helps

---

