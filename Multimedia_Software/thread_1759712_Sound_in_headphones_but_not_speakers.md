---
title: "Sound in headphones but not speakers"
date: 2011-05-16
forum: Multimedia Software
---

### Post by ForrestB on 2011-05-16
I have a Compaq 320 and was using 10.04, but I started to  have  the  problem of no sound from speakers but am able to get it through  headphones.   This has happened to me before and usually I fixed it  using, the instructions here:

 [http://monespaceperso.org/blog-en/20...id-lynx-10-04/]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/") 

But the last time it didn't work.   So I though an update to 11.04 would  just clear the whole problem,  so I did a fresh install,  but the same  problem persists.  No sound for built-in speakers, but there is sound  from the headphones.    


Here is the link to my info from: wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh


[http://www.alsa-project.org/db/?f=d8...82da3ebc7a26f8]("http://www.alsa-project.org/db/?f=d81011161f4f08276b8bf9388982da3ebc7a26f8")


Any help would be greatly appreciated.
Thanks

---

### Post by ForrestB on 2011-05-17
I've tried to follow the script in:  
[http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

but i doesn't seem to work well, 

but my terminal skill aren't too refined yet. 

 If somebody could post clearer directions that would be sweet.

---

### Post by lidex on 2011-05-17
Try removing that hp-m4 model from alsa-base.conf
Reboot and run the alsa-info script again

---

### Post by ForrestB on 2011-05-18
Try removing that hp-m4 model from alsa-base.conf
Reboot and run the alsa-info script again
__________________


Seemed to have worked. Sound working from speakers on start up.  
Thanks a lot, you rule.

Here is the  alsa-info link just in case you see anything that needs fine tuning
[http://www.alsa-project.org/db/?f=703493be638e1f1135aea272c01f3558841c61f5](http://www.alsa-project.org/db/?f=703493be638e1f1135aea272c01f3558841c61f5)

Thanks a lot

---

### Post by Aaron_Carter on 2011-05-18
Hello, Guys
I have the same problem and did everything that all of you wrote before and still have something like an "EXO". The signal is too weak and I hardly can hear the people at the end of the line.Thanks in advance

Aaron,

---

### Post by lidex on 2011-05-18
OK, let's close this thread then.
@ForrestB
Please mark this thread solved using 'Thread Tools' up top.

@Aaron_Carter
Please begin a new thread and post your exact problem details as well as the link to the output of alsa-info script.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

You can PM me the link to your thread, I don't mind that. Need to curb the megathreads.

---

