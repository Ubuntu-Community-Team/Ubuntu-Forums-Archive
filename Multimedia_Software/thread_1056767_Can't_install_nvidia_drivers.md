---
title: "Can't install nvidia drivers"
date: 2009-02-01
forum: Multimedia Software
---

### Post by Beatngu on 2009-02-01
Hi all
I have problems installing nvidia drivers.
At installation umbutu in istalling nvidia drivers automatic,but the drivers are not working.When i start umbutu i get a error that the drivers are not working and i have to config to be able to start.I have to set it to low res and then start it with default drivers.I have tryed to uninstall the drivers and downloaded new drivers from nvidia this is the drivers i want to install NVIDIA-Linux-x86_64-180.22-pkg2.run.
When i type sudo sh NVIDIA-Linux-x86_64-180.22-pkg2.run i get a message cant open the file.I type it in terminal. Any suggestions?

I am a newbie so be gentle :)

---

### Post by DeMus on 2009-02-01
> **Beatngu said:**
> Hi all
I have problems installing nvidia drivers.
At installation umbutu in istalling nvidia drivers automatic,but the drivers are not working.When i start umbutu i get a error that the drivers are not working and i have to config to be able to start.I have to set it to low res and then start it with default drivers.I have tryed to uninstall the drivers and downloaded new drivers from nvidia this is the drivers i want to install NVIDIA-Linux-x86_64-180.22-pkg2.run.
When i type sudo sh NVIDIA-Linux-x86_64-180.22-pkg2.run i get a message cant open the file.I type it in terminal. Any suggestions?

I am a newbie so be gentle :)


Do this, it worked for me:
[http://ubuntuforums.org/showthread.php?t=1054842]()

---

### Post by Beatngu on 2009-02-01
Thank you for the fast reply!!
That was the tut i was trying out yesterday,but it did still not work.
everything was working until the last part installing the drivers then i get "can't open drivers"I think i have read about umbutu  server and umbutu desktop was using diffrent kernels.Maybe this is my problem that i first installed umbutu server and after i installed desktop?The main problem is really when i try to install the drivers i downloaded i allways get can't open file.I open it like this sudo sh and then the file name am i doing something wrong?

---

### Post by DeMus on 2009-02-01
> **Beatngu said:**
> Thank you for the fast reply!!
That was the tut i was trying out yesterday,but it did still not work.
everything was working until the last part installing the drivers then i get "can't open drivers"I think i have read about umbutu  server and umbutu desktop was using diffrent kernels.Maybe this is my problem that i first installed umbutu server and after i installed desktop?The main problem is really when i try to install the drivers i downloaded i allways get can't open file.I open it like this sudo sh and then the file name am i doing something wrong?

Can you write down exactly what you do and type? So we can try to figure out why it doesn't work.

---

### Post by splater on 2009-02-01
I would recommend you to uninstall the Nvidia driver you download on their web site

sudo nvidia-uninstall

and after install it from the ubuntu restricted driver tools...

hope this helps.
Splater

---

### Post by Beatngu on 2009-02-01
This is in short what im doin
sudo /etc/init.d/gdm stop
sudo rm -f /lib/modules/`uname -r`/kernel/drivers/video/nvidia.ko
sudo sh NVIDIA-Linux-x86_64-180.22-pkg2.run
sudo /etc/init.d/gdm start

Have allsow tryed other ways explainded in this forum.
The problem is i can't install the drivers from the repo or i can install them but after a reboot i get a error saying vdrivers not working and have to go back to default or start with low res.And the drivers in repo dont support my gfx card if im not wrong my gfx card is gtx260.And the latest drivers in repo are 177.

Ps when i type sudo nvidia-uninstall i get command not found....

---

### Post by Beatngu on 2009-02-03
Here is my error log maybe any1 sees whats wrong

---

### Post by Beatngu on 2009-02-04
Nobody knows what wrong?

---

### Post by Ross Bernard on 2009-02-05
I think I'm having the same problem:

Tried installing recommended nvidia driver (96) through "hardware drivers" ... got screen of death.

Reconfigured with: > sudo dpkg-reconfigure -phigh xserver-xorg

Downloaded the package from the nvidia website and tried to install it with: > sudo sh NVIDIA-Linux-x86-180.22-pkg1.rn 

Got some error about not having the right GPU or something? Anyways it didn't install.

Following other advice on here I've already tried ENVYNG, uninstalled all nvidia glx files through synaptic, and removed compiz and compiz-core.

sudo nvidia-xconfig kills my screen too.

Anything else I should try?

---

### Post by Ross Bernard on 2009-02-05
I think I'm having the same problem:

Tried installing recommended nvidia driver (96) through "hardware drivers" ... got screen of death.

Reconfigured with: > sudo dpkg-reconfigure -phigh xserver-xorg

Downloaded the package from the nvidia website and tried to install it with: > sudo sh NVIDIA-Linux-x86-180.22-pkg1.rn 

Got some error about not having the right GPU or something? Anyways it didn't install.

Following other advice on here I've already tried ENVYNG, uninstalled all nvidia glx files through synaptic, and removed compiz and compiz-core.

sudo nvidia-xconfig kills my screen too.

Anything else I should try?

---

### Post by MrCharles on 2009-02-05
Ross try this. It didn't work for me - but it may for you

[http://ubuntuforums.org/showthread.php?t=1054842](http://ubuntuforums.org/showthread.php?t=1054842)

---

### Post by MrCharles on 2009-02-05
I'm about to lose it myself.
Nvidia drivers are causing my x config to get all messed.
And I'm too much of a newb to troubleshoot.
What's the Ubuntu Tagline - Oh YEAH - "IT JUST WORKS".  right.

---

### Post by Ross Bernard on 2009-02-06
I tried that (thanks DeMus, and mrCharles) but still no luck. 

I'm using 8.10... if that helps. Would really appreciate some guidance.

For example, I installed envyng... is there something I have to do to get that to install the nvidia driver? or is the fact that it is installed enough?

also, the recommended driver seems to be different from the one I downloaded ... but neither of them work. Any advice there?

---

### Post by Tiyani on 2009-08-26
Hi All,
 
I have a similar problem.  I have installed Ubuntu LSTP Server to create a thin client environment that will see 6 screens connected to one PC.  I downloaded the NVIDIA-Linux-x86-173.14.20.pkg1.run file from a laptop running Windows since I can't connect to the internet on the desktop with Ubuntu installed on it.
 
I have tried everything suggested but still can't win.  I followed the folling steps common in  all comments shared in the forums on this problem:
[LIST=1]
[*]Entered a terminal mode through Cntrl + Alt + F1
[*]Disabled X Server
[*]cd Desktop
[*]sudo install NVIDIA-Linux-x86-173.14.20.pkg1.run /home (a folder I was installing from)
[/LIST]After step 4 I got the  thios code "Can't open that file" or "missing destination file p* after  "NVIDIA-Linux-x86-173.14.20.pkg1.run /home".
 
Even when I replace  with /usr/src in the above code I still get @can't open that file".
 
I am about to my hair out of my skull please save me.  Somebody! :confused:
 
Thanking you in anticipation.

---

### Post by raygj on 2009-08-26
> **Tiyani said:**
> Hi All,
 
I have a similar problem.  I have installed Ubuntu LSTP Server to create a thin client environment that will see 6 screens connected to one PC.  I downloaded the NVIDIA-Linux-x86-173.14.20.pkg1.run file from a laptop running Windows since I can't connect to the internet on the desktop with Ubuntu installed on it.
 
I have tried everything suggested but still can't win.  I followed the folling steps common in  all comments shared in the forums on this problem:
[LIST=1]
[*]Entered a terminal mode through Cntrl + Alt + F1
[*]Disabled X Server
[*]cd Desktop
[*]sudo install NVIDIA-Linux-x86-173.14.20.pkg1.run /home (a folder I was installing from)
[/LIST]After step 4 I got the  thios code "Can't open that file" or "missing destination file p* after  "NVIDIA-Linux-x86-173.14.20.pkg1.run /home".
 
Even when I replace  with /usr/src in the above code I still get @can't open that file".
 
I am about to my hair out of my skull please save me.  Somebody! :confused:
 
Thanking you in anticipation.
 
Instead of "[*]sudo install NVIDIA-Linux-x86-173.14.20.pkg1.run /home"
try this from inside the directory that contains the "NVIDIA install program"-->>

[*]sudo sh ./NVIDIA-Linux-86-173.14.20.pkg1.run

you cannot run a program in your current directory as ROOT USER(sudo command) without adding the prefix (./) to the program name IE. add "./" to "program" to form "./program"

---

### Post by xmx on 2009-08-26
I had a problem installing my nvidia drivers from the hardware driver software in system > "hardware drivers".  It would hang my computer up.  What I ended up doing was using synaptic package manager to install.

---

