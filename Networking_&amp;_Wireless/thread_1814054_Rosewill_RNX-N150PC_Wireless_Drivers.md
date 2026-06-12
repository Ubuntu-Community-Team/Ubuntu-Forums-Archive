---
title: "Rosewill RNX-N150PC Wireless Drivers"
date: 2011-07-28
forum: Networking &amp; Wireless
---

### Post by TSPARR on 2011-07-28
So, I tried to use this thread [http://ubuntuforums.org/showthread.php?t=1608095](http://ubuntuforums.org/showthread.php?t=1608095), but I'm extremely new to Linux and to be perfectly honest, it made absolutely no sense to me. I got to about step 3 and then got lost. Can anyone basically hold my hand and walk me through this? It would be very much appreciated.

---

### Post by chili555 on 2011-07-28
Dr. HandHold is here. Is this where you got stuck?> Next, open a terminal in the driver folder and type That simply means to direct the terminal to where to files are that you are going to build. Where did you download the file? To your desktop? What is it called? DPO_something? In the terminal, type:```
cd Desktop/DPO
```We are going to use a trick to fill in all the tricky name perfectly. Press Tab and let it fill in automagically. Press Enter. Now proceed with the remaining steps.

If you get an error, stop and ask. Warnings are OK. I'll be around to help if you get stuck.

---

### Post by TSPARR on 2011-07-28
So far you're the absolute best haha. That was the part I was stuck on, and it appears to be going well from here on out. I will definitely pop back in if I run into any more issues. Thanks a ton




EDIT: I was running into errors and I realized I forgot that I was stuck on a part in the readme file. I have to define the gcc and ld of my machine. These letters mean nothing to me, and though I flexed my google muscles as much as I could. I found nothing that helped.

---

### Post by chili555 on 2011-07-28
> I was running into errors and I realized I forgot that I was stuck on a part in the readme file. I have to define the gcc and ld of my machine. These letters mean nothing to me, and though I flexed my google muscles as much as I could. I found nothing that helped.You can skip that part. The file is built for Linux and the later versions of GCC. Other applications, embedded devices, etc. need that change and know what they need. In 95% of cases in this file, if you don't know what to do, you needn't do anything. Don't be shy to ask back.

---

### Post by TSPARR on 2011-07-28
I did the "sudo make" and "sudo make install" commands and near as I can tell they seemed to work fine, but when I do 
sudo modprobe rt3562sta

and now I can't figure out how to get out of this box, but when I do that
nothing happens at all. And on the next command    I get ra0: ERROR while getting interface flags: No such device
sudo ifconfig ra0 inet up




So....I restarted ubuntu and apparently somewhere in the mess of code it was running, something good happened. I'm up and running on wireless. Thank you so much for your help Chili.

---

### Post by chili555 on 2011-07-28
Awesome! Would you care to use thread tools at the top and Mark Solved.

---

