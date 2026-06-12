---
title: "GEFORCE 6600 Problems"
date: 2009-10-10
forum: Multimedia Software
---

### Post by malibu3 on 2009-10-10
Well, this has been a nightmare of epic proportions, not sure which way to go at this point. I had Ubuntu 8.04 installed, and when I did install it, I had problems getting the video to work. Basically it would only allow a 640X440 resolution. I was able to get that fix, but for the Linux class I am in, my instructor wanted me to update my box. I went to 8.10 then to 9.04...Problem is with my video again. When the machine boots, it shows that it fails to load nvidia kernel, but it would allow me to operate in low resolution mode. I messed around with some of the suggestions I found on the forums trying to update the kernel, and the last one was 180.60, I did the update through symantic and when my machine came back up, not it will only go into ttyl. I decided to try and throw an old ATI card that I had in it to see if I can just get that to work. I really only want to use this machine to write some perl scripts etc for class, and it would be nice to just use the editor the GUI has instead of VI. Just not sure where I should go from here, I am certainly at a loss. Thanks for any help you may be able to provide.
Shawn Bland

---

### Post by wojox on 2009-10-10
Have you looked at this thread to help with nvidia: [http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)

I used it to upgrade my 173.xxx and it worked quite well. Just download the latest driver for your card and go from there.

Worst case nano is easier to use than vi I think.

---

### Post by malibu3 on 2009-10-11
Alright, so I researched the forums some more, and I found a step by step, a good one :) at that post that I followed to remove all the nvidia drivers etc.  Once I did that my display is working again, however just in 800 by 600 resolution as expected because no drivers are loaded.  I followed the instructions to try and complete the installation of the drivers, however it does not appear that they are installing.  The thread I am following is this:
 
[http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)
 
The problem I am having is after downloading the driver.  It says to perform command
sudo sh /usr/src/nvidia-driver  And follow the instructions.
 
First issue, was that I did not have that folder, so i created that folder and put the nvidia.run file in it.  I try to run that command again and I do not get an error, but the thread says to follow the instructions.  It just goes to the next command line almost instantly, like no action took place.  I checked and it still does not look like it is loading anything.  
 
Any help would be appreciated, I am sure something I am missing.
 
Thanks again! 
Shawn

---

