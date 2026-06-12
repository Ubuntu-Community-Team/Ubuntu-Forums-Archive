---
title: "Webcam with Mercury Messenger"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by hasansahin on 2007-11-27
Hi all,

I setup my webcam as correctly. already installed gspca-source,spca-source,sane-utils and camorama. when I use camorama my webcam working as correctly. no problem. But when I use with mercury, getting error message as disconnected in webcam settings in the global settings section.  I could't understand.

---

### Post by allartk on 2008-02-06
hi,

Maybe you solved already, but after some searching I found out the folowing method:
- download jmf from [http://java.sun.com/products/java-media/jmf/2.1.1/download.html](http://java.sun.com/products/java-media/jmf/2.1.1/download.html) to your home folder -> /home/yourusername/
- make the file /home/yourusername/jmf-2_1_1e-linux-i586.bin executable (right mouse click permissions)
- run the file by entering ./jmf-2_1_1e-linux-i586.bin on the terminal
- then copy the file: sudo cp /home/yourusername/JMF-2.1.1e/lib/libjmutil.so /usr/lib/jvm/java-6-sun/jre/lib/i386/libjmutil.so

works on ubuntu 7.10 i386 install.

---

### Post by mocoloco on 2008-03-16
Thanks allartk I was lost with all that JMF stuff.  Installing it in /usr/lib worked, in that I no longer get the error message about libjmutil.so.  However Mercury doesn't find my integrated webcam on my Dell Inspiron 1420, it just says there were no video capture devices know to the JMF :(  The camera's recognized by lots of other apps.  So I guess I still need to tinker with JMF a bit.

---

### Post by pmcsilva on 2008-03-25
Just one word... Thanks!

---

### Post by putozao on 2008-03-25
creating: JMF-2.1.1e/
   creating: JMF-2.1.1e/bin/
  inflating: JMF-2.1.1e/bin/jmfinit  
  inflating: JMF-2.1.1e/bin/jmfregistry  
  inflating: JMF-2.1.1e/bin/jmstudio  
   creating: JMF-2.1.1e/doc/
  inflating: JMF-2.1.1e/doc/attributions.html  
  inflating: JMF-2.1.1e/doc/formats.html  
  inflating: JMF-2.1.1e/doc/readme.html  
   creating: JMF-2.1.1e/lib/
  inflating: JMF-2.1.1e/lib/libjmcvid.so  
  inflating: JMF-2.1.1e/lib/libjmdaud.so  
  inflating: JMF-2.1.1e/lib/libjmfjawt.so  
  inflating: JMF-2.1.1e/lib/libjmg723.so  
  inflating: JMF-2.1.1e/lib/libjmgsm.so  
  inflating: JMF-2.1.1e/lib/libjmh261.so  
  inflating: JMF-2.1.1e/lib/libjmh263enc.so  
  inflating: JMF-2.1.1e/lib/libjmjpeg.so  
  inflating: JMF-2.1.1e/lib/libjmmpa.so  
  inflating: JMF-2.1.1e/lib/libjmmpegv.so  
  inflating: JMF-2.1.1e/lib/libjmmpx.so  
  inflating: JMF-2.1.1e/lib/libjmutil.so  
  inflating: JMF-2.1.1e/lib/libjmv4l.so  
  inflating: JMF-2.1.1e/lib/libjmxlib.so  
  inflating: JMF-2.1.1e/lib/jmf.properties  
  inflating: JMF-2.1.1e/lib/jmf.jar  
  inflating: JMF-2.1.1e/lib/mediaplayer.jar  
  inflating: JMF-2.1.1e/lib/multiplayer.jar  
JavaSound Capture Supported = true
JavaSoundAuto: Committed ok
Name = v4l:USB 2.0 Camera:0
Trying 4 320 240
Trying 3 160 120
Trying 3 320 240
Trying 3 640 480
Trying 3 176 144
Trying 3 352 288
Trying 3 768 576
Trying 4 160 120
Trying 4 320 240
Trying 4 640 480
Trying 4 176 144
Trying 4 352 288
Trying 4 768 576
Trying 5 160 120
Trying 5 320 240
Trying 5 640 480
Trying 5 176 144
Trying 5 352 288
Trying 5 768 576
Trying 6 160 120
Trying 6 320 240
Trying 6 640 480
Trying 6 176 144
Trying 6 352 288
Trying 6 768 576
Trying 7 160 120
Trying 7 320 240
Trying 7 640 480
Trying 7 176 144
Trying 7 352 288
Trying 7 768 576
Trying 8 160 120
Trying 8 320 240
Trying 8 640 480
Trying 8 176 144
Trying 8 352 288
Trying 8 768 576
Trying 9 160 120
Trying 9 320 240
Trying 9 640 480
Trying 9 176 144
Trying 9 352 288
Trying 9 768 576
Trying 10 160 120
Trying 10 320 240
Trying 10 640 480
Trying 10 176 144
Trying 10 352 288
Trying 10 768 576
Trying 11 160 120
Trying 11 320 240
Trying 11 640 480
Trying 11 176 144
Trying 11 352 288
Trying 11 768 576
Trying 12 160 120
Trying 12 320 240
Trying 12 640 480
Trying 12 176 144
Trying 12 352 288
Trying 12 768 576
Trying 13 160 120
Trying 13 320 240
Trying 13 640 480
Trying 13 176 144
Trying 13 352 288
Trying 13 768 576
Trying 14 160 120
Trying 14 320 240
Trying 14 640 480
Trying 14 176 144
Trying 14 352 288
Trying 14 768 576
Trying 15 160 120
Trying 15 320 240
Trying 15 640 480
Trying 15 176 144
Trying 15 352 288
Trying 15 768 576
java.lang.Error: Can't open video card 1
java.lang.Error: Can't open video card 2
java.lang.Error: Can't open video card 3
java.lang.Error: Can't open video card 4
java.lang.Error: Can't open video card 5
java.lang.Error: Can't open video card 6
java.lang.Error: Can't open video card 7
java.lang.Error: Can't open video card 8
java.lang.Error: Can't open video card 9
Done.

I fallow the steps but doesn't work here!! :-(

sorry copypast

---

### Post by allartk on 2008-04-29
Hi,

This large output is normal, you will see a new folder with the file in one of its subfolders (see my description).

To get it working on hardy heron you will need to read this:
[http://forum.java.sun.com/thread.jspa?threadID=733794&messageID=4226173](http://forum.java.sun.com/thread.jspa?threadID=733794&messageID=4226173) 

and you will have to remove openjdk and install sun-java-jre instead (via synaptic).

nb I subsribed myself to this topic :)

---

