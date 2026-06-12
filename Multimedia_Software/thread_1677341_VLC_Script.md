---
title: "VLC Script"
date: 2011-01-28
forum: Multimedia Software
---

### Post by nesrevig on 2011-01-28
Hello

I finally made a batch script to record a stream from my IP camera and split the stream like every hour, and add the date to the filename. But i have a little problem - After the loop, vlc just overwrite the file, instead of creating a new file and change the filename to the current date. Can somebody help me? Here is the script:

```
"c:\Program Files\VideoLAN\VLC\vlc.exe" http://admin:1234@192.168.1.120:9008/videostream.cgi --sout=#transcode{vcodec=h264,vb=1024,scale=1}:duplicate{dst=std{access=file,mux=mov,dst="C:\Users\xxx\Desktop\test-%date:~10,4%%date:~4,2%%date:~7,2%-%time:~0,2%%time:~3,2%%time:~6,2%.ps"}} --loop --run-time=10 
```

---

### Post by gordintoronto on 2011-01-28
This isn't a great place to get help with Windows. People will tell you the solution to all problems is to install Ubuntu 10.10.

---

### Post by nesrevig on 2011-01-28
The command for windows/linux is the same. I just need that single command that tells vlc to create a new file instead.

---

### Post by ShadowTek on 2011-01-29
It's probably that your evaluation of the date isn't recurring like you expect it to. It might only be set once, and then you just keep using that same date over and over again, which would just use the same name over and over.

For Windows, you could use a batch file where vlc runs for the alloted time, and then stops. Then have a call to that same script in the line after that, which would set up an endless loop. With each loop, the date would be evaluated anew.

BTW, vlc does have its own website with its own forums.

---

