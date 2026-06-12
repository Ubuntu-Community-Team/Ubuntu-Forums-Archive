---
title: "i need help on installing us robotics 9640 webcam for skype on ubuntu:("
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by barbaros on 2007-10-06
hi,

i've got the camera us robotics 9640 usr mini cam for skype, and it's delivered as compatible with mac also.

i need to set it up on my ubuntu, but my laptop even does not recognize it. 

i need help, i have to set it up in two days!

thank you

---

### Post by linuxwizard on 2007-10-06
Might want to try EasyCam

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by barbaros on 2007-10-07
i've already tried it: it just says, "no cameras, or no compatible camera"

---

### Post by robinjives on 2008-01-26
Hi Barbaros,

Have you figured out the answer to your webcam problem? I'm trying to use the same webcam on Linux Mint.

---

### Post by linuxwizard on 2008-01-26
Have you tried using you webcam with Ekiga or Camorama  ? I don't see that webcam listed here > [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

---

### Post by robinjives on 2008-01-26
Hi linuxwizard, 
I tried installing ekiga but it does not detect my webcam. I tries lsusb and my Webcam is shown as 0c45:6242 Microdia (t shows up in the list of nonworking webcams :( )

---

### Post by intel on 2008-01-27
**Microdia** 
(Webcam Support group for all Microdia chipsets under Linux)
Q) Is my webcam a "microdia"? 
A) Execute the following command 
    #lsusb
If you see any of the following numbers, you have a "microdia" webcam
0c45:6027, 0c45:608f, 0c45:60ec, 0c45:60fe, 0c45:6242, 0c45:6253, 0c45:6260, 0c45:6270, 0c45:60c0, 0c45:613b, 0c45:613c, 0c45:624f, 0c45:627b, 0c45:62c0, 0c45:8105
(basically 0c45:<xxxy> above is enough to conclude you have a microdia webcam) 

All of the above webcams are unsupported under Linux


https://groups.google.com/group/microdia

 
Please join this Group, to help each other get better support for these webcams from Linux.

---

### Post by vivalant on 2008-01-29
For webcams from Microdia try the SN9CXXX driver at [http://www.linux-projects.org](http://www.linux-projects.org) . Other projects are just words and won't work at all. Also read this:

[http://ubuntuforums.org/showthread.php?t=681051](http://ubuntuforums.org/showthread.php?t=681051)

---

