---
title: "Cinelerra error mov"
date: 2007-07-27
forum: Multimedia &amp; Video
---

### Post by anarhell on 2007-07-27
hello ..


i am new in linux .. i'm install cinelerra , but when i want open archive .avi . this told me that error 

virtual int FileMOV::read_frame(VFrame*): quicktime_read_frame/quicktime_decode_video failed, result:

i dont know what is that.. 

i hope anyone help me :)

Thx :D

---

### Post by paparappa on 2007-07-31
I have the exact same problem :/

---

### Post by wkulecz on 2007-07-31
What format (codec) is the avi file you are trying to open?  I've only looked at Cinelerra, but it seems it wants its input DV files in the Quicktime format.  Kino can convert a DV avi file (as downloaded froma camcorder on windows) into the QT format which I then opened in Cinelerra.

If you are new to Cinelerra, I'd suggust downloading the dyne-bolic distribution and using its "CD dock feature" to get a working Cinelerra system easily.  In fact its the only Cinelerra setup I've actually been able to make do anything at all useful.

Maybe 7.04 or Studio fixes things, but doesn't sound like it from this thread.

--wally.

---

### Post by kelvin spratt on 2007-07-31
You have got version 2.1 installed its a downgrade as far as importing mov files i had the same problem, but Cinelerra will not admit they messed up i wrote two threads on how to install version 2.0 which does import mov and most everything  else and exports very high quality quicktime for Linux file, that can be played on movie player and most other linux player and play in windows media player with nero mp4 plugin and even better quality useing VLC player Windows version, they can be loaded into DeVeDe 3.0, Which will Author them and do the menu as well, i use this combination to make wedding Video's and never had a problem. but don't use with Beryl or compis running as they use so much resources that it will keep crashing. this is the links one if you have not installed Cinelerra, and the other if you have as you have to replace some Dependances'.
   [http://ubuntuforums.org/showthread.php?t=463275](http://ubuntuforums.org/showthread.php?t=463275)  
[http://ubuntuforums.org/showthread.php?t=464223](http://ubuntuforums.org/showthread.php?t=464223)
Good luck

---

### Post by Bablefish on 2007-07-31
I have tried as well, for nearly 3 months I have tried every trick to play Quicktime files and NOTHING WORKS!!!!!!!!!  If anyone with Ubuntu 7.04 can get them to run PM me with the instructions. By the way I did try those tricks kelvin spratt posted already and they don't work for me. I am going to experiment with a file conversion program to see if that works. If it doesn't all I can say is live those files to other OSs.

---

### Post by burnman99 on 2007-08-27
I get the same error also. But if you convert the video (I use kdenlive) to dv.avi then it works fine.

Rog

---

