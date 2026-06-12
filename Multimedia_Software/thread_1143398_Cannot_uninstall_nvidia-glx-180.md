---
title: "Cannot uninstall nvidia-glx-180"
date: 2009-04-29
forum: Multimedia Software
---

### Post by Wylkar on 2009-04-29
Hello,
I recently upgraded to jaunty and I installed the nvidia graphics driver (nvidia-glx-180), which had uninstalled xorg. Today when I restarted my computer I was sent to the command interface, I tried to uninstall ithe nvidia driver but I got an error, and I cannot install xorg without removing it.
Any help would be greatly appreciated.

---

### Post by Wylkar on 2009-05-06
The issue has been resolved, the problem was that the nvidia driver had installed incorrectly. In order to remove it aptitude had to find the files to remove, one was missing so it could not be unistalled. So I created the file and was able to uninstall the nvidia driver and reinstall xorg. I did this with the help of someone more experienced with linux than myself, and without their help it would have taken me much longer to resolve this issue.

---

### Post by JovianMisteri on 2009-05-16
I'm having the exact same problem, could you explain in detail what you and your friend did? What file was missing? How did you create it?

---

### Post by Wylkar on 2009-05-17
I cannot remember the exact name of the file but I believe it was something like libGL.so and so to create it I ran 'touch libGL.so'The touch command checks to see if a file is in a location, and if not, it creates an empty one. The problem was that I was missing the file and apt needed to find it in order to uninstall the nvidia driver, the error message was something like 'EE:etc/libGL.so no such file' so if you get a message similar then you may want to try 'touch (whatever file it says you are missing)'

---

### Post by JovianMisteri on 2009-05-17
YES! Awesome, it totally worked! I'm so glad to have a GUI back, I totally fail at console. 

Here is my extensively detailed story, for anyone *newbies* who may need it: 

My problem originally hatched while upgrading from intrepid to jaunty. The computer shutdown unexpectedly near the end of the upgrade (my hptx1000z tends to overheat often, thankfully switching from windows to ubuntu made this a rarity), and after rebooting it forced me into tty/console, even under recovery mode, with the error: 
```
kinit: no resume image, doing normal boot...
``` 
and I had no idea how to get the gui back. Xfix (program in recovery mode that fixes the x display) wasn't even an option. While in console I tried to finish the upgrade in aptitude, 
```
sudo apt-get update
sudo apt-get upgrade
```
which automatically set the removal of nvidia-glx-180, but it refused to remove. The error was something along the lines of
```
dpkg-divert: /usr/lib/xorg/modules/extensions/libGLcore.so no such file or directory
```
I couldn't install anything new until 180 had uninstalled, so I was screwed. BUT then I found this post on my trusty blackberry, and learned here the link between nvidia, xorg and the missing libGLcore.so. As instructed, I made the directories of the file that was missing (only /usr/lib/xorg existed),
```
cd /usr/lib/xorg
mkdir modules
cd modules
mkdir extensions

```
and used the touch command to create libGLcore.so
```
cd extensions
touch libGLcore.so
sudo reboot

```
and thus I was greeted with a normal login screen!
Solved!

Thanks again! (I would've never figured this out, I owe you my life!)

---

### Post by Wylkar on 2009-05-17
No problem, glad I could help.

---

