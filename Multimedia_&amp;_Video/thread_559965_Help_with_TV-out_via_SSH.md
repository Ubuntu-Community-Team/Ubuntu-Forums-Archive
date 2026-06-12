---
title: "Help with TV-out via SSH"
date: 2007-09-25
forum: Multimedia &amp; Video
---

### Post by sadowjo on 2007-09-25
Hello everyone.  I have never posted before but thiese forums have been invaluable for taking the edge off the Linux learning curve.  In general I am a pretty quick study and have been able to figure out everything I needed to know by searching around.  

But now I am stumped.

I have an Ubuntu Server set up on some pretty decent hardware in my basement.  3TB software RAID, fast dual-core Intel CPU, 7600 series GeForce Video with component out.  Up until now I havent been using the video card at all as all my videos and such are stored on the RAID array and I watch them on my laptop using Samba.  Now I have run 3 RG6 cables terminated with RCA plucgs from the server to my Hi-Def TV along with audo cables.  I know that the physical setup is working because when I boot up the server I see the POST and the initial Ubuntu splash screen nice and clear on the TV.

Here is the goal:  I would like to be able to ssh into the server and run a script that would play a specified file to the component TV out on the card.  Seems like it should be simple, but it has me stumped.   I tried messing around with xorg.conf while sitting at the server and was able to get output going to the TV instead of the monitor and I am sure i could get it working from there with a little more tinkering but is this even the right way to proceed?  How would I then get the output working with a remote ssh session?  Is there some way to send video to the TV out from the CLI without even bothering with X11?

For those that are wondering, I don't really want to go the MythTV route in the sense that I don't want a second Linux Box in my entertainment cabinet if possible.

Thanks in advance for the help!

John

---

