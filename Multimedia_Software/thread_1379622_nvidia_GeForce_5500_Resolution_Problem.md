---
title: "nvidia GeForce 5500 Resolution Problem"
date: 2010-01-12
forum: Multimedia Software
---

### Post by terrapin893 on 2010-01-12
Hi, 

So I had installed 9.10 on an older computer and everything worked perfectly . . . . except for my video drivers.  No matter what I did I couldnt get a resolution over 800x600 8 bit.  So after doing some research I came to the conclusion that it was my Intel Integrated Graphics chip. 

So the advice I got from many people was to go ahead and get a nvidia video card because the driver works well with Linux.  So I went ahead and got a nvidia GeForce 5500 video card.  I installed the driver under Hardware Drivers . . . . and low and behold things got worse.  Now I only get the choice of 640x480 or 320x240.  What do I need to do?  I really could use some help here.

---

### Post by Revolutionary101 on 2010-01-12
Have you tried to install the Graphics Driver?

---

### Post by terrapin893 on 2010-01-12
OK this may be a very simple minded response . . . . but thats what I thought I was doing when I activated the proprietary driver in "Hardware Drivers" 

Is there something else, look for a linux driver for the actual video card?

---

### Post by Revolutionary101 on 2010-01-12
I would suggest going to the Nvidia website and downloading the official driver. The proprietary drivers in "Hardware Drivers" don't always work the best.

---

### Post by terrapin893 on 2010-01-12
OK, thanks for the direction.  Ill report back with my progress.

---

### Post by terrapin893 on 2010-01-12
OK, so I downloaded the driver from nvidia's site and I cant seem to install it! 
sh: Can't open NVIDIA-Linux-x86-173.14.22.pkg1.run

I dont have any idea what is going on here.

---

### Post by Revolutionary101 on 2010-01-12
Put the driver in your /home/username folder. Then in terminal type ```
sudo sh NVIDIA-Linux-x86-173.14.22.pkg1.run
```
That should at least start the installation process.

---

### Post by terrapin893 on 2010-01-12
Nope, I get the same error 
sh: Can't open NVIDIA-Linux-x86-173.14.22.pkg1.run

Ive even tried installing the driver using envy and I have the exact same problem (highest available resolution is 640x480).  I cant believe I still cant figure this out.  Im just about ready to try reinstalling Ubuntu or maybe trying a different version.

---

### Post by Revolutionary101 on 2010-01-12
Move the .run file onto your desktop and copy this into terminal.
```
cd ~/Desktop
chmod +x NVIDIA-Linux-x86-173.14.22.pkg1.run
sudo ./NVIDIA-Linux-x86-173.14.22.pkg1.run
```
That should work.

---

### Post by terrapin893 on 2010-01-13
Yeah I was starting to think it might be a permissions issue.  But before I saw this I stumbled upon the resolution to the problem.  First off I did a clean install of Ubuntu.  I had installed it while using an integrated video chip and I had installed java . . . I didnt know if any of those things would cause problems or not so I just reloaded.  

Then I stumbled upon a post, I think it was somewhere here, saying that things detect better if you disable X Server.  So I gave it a shot 
```

sudo /etc/init.d/gdm stop 

```Then I logged into my desktop 
Changed the directory to the directory with the driver file 
Then I ran the driver and it installed 
Launched X Server again 
```

sudo /etc/init.d/gdm start 

```So this installed the driver, but then I got an error message that said the input was out of the range of my monitor.  I have been using a HDTV with a VGA input as a monitor.  Never struck me that it would cause an issue.  So I hooked it up to an old CRT to test it.  Worked perfectly.  
 
I am even able to get the HDTV to work.  If I boot the computer up with the CRT then switch to the HDTV the monitor in the NVIDIA settings stays with the CRT and I can change the resolution.  

So now Im finally using Ubuntu for all its worth.  Persistence pays off.

---

### Post by Revolutionary101 on 2010-01-13
Indeed it does. Glad I could help.

---

