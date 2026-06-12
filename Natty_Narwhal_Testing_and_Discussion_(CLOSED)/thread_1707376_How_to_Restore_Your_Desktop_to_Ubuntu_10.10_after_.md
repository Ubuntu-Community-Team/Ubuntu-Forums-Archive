---
title: "How to Restore Your Desktop to Ubuntu 10.10 after upgrading to ubuntu 11.04 natty"
date: 2011-03-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ravitejamulpuri on 2011-03-15
Hi , recently i upgraded my 10.10 to 11.04 natty  .After restarting my computer  and selecting grub options i am getting a blank screen with brown top ..i tried to recover the grub using second option in grub menu...everything went fine but it is showing me a command line after selection of "proceed with normal boot"....Dont know why this has happened...i can't use ubuntu anymore..

Is there any way to restore back to 10.10 without using a LIVECD??

---

### Post by ravitejamulpuri on 2011-03-15
Hi , recently i upgraded my 10.10 to 11.04 natty  .After restarting my  computer  and selecting grub options i am getting a blank screen with  brown top ..i tried to recover the grub using second option in grub  menu...everything went fine but it is showing me a command line after  selection of "proceed with normal boot"....Dont know why this has  happened...i can't use ubuntu anymore..

Is there any way to restore back to 10.10 without using a LIVECD??

---

### Post by s.fox on 2011-03-15
Thread moved to [Natty Narwhal Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=394")

---

### Post by 3177 on 2011-03-15
I dont think so. Im pretty sure you need to re-install 10.10.
This is why you dont put pre-releases on production machines.

---

### Post by Mark Phelps on 2011-03-15
3177 is correct -- there is no "downgrade" or "rollback" option to restore older Ubuntu version.

And, in future, you would do best to avoid Ubuntu releases that are still in the "Alpha" testing stage.  Those are buggy, some stuff simply doesn't work, and it's no simple matter getting your old installation back.

---

### Post by coffeecat on 2011-03-15
The only way of going back to 10.10 is by re-installing. But now that your thread has ended up in the Natty forum, do you want to try to repair your Ubuntu 11.04? If so, post details of your hardware, especially the graphics card and whether you were using a proprietary driver in 10.10.

Also, I don't follow what you've done with grub but in case that's gone wrong, boot up with the 10.10 live CD and post the output of the boot script from this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Full instructions in that link. Please don't forget to use the code tags for the RESULTS.txt file.

---

### Post by ravitejamulpuri on 2011-03-15
[IMG]http://img233.imageshack.us/img233/7463/capturesce.png[/IMG]
[COLOR=SeaGreen]
**I have 128 mb Nvidia geforce graphic card....i think ( not sure)  i installed natty desktop server edition ...Now when i rebooted it i am getting a command line with out any UI...any idea why this is happening??**[/COLOR]

---

### Post by coffeecat on 2011-03-15
> **ravitejamulpuri said:**
> [COLOR=SeaGreen]
**I have 128 mb Nvidia geforce graphic card....**[/COLOR]

If you look at other threads in this subforum, you'll see that nvidia graphics is very problematic at this stage of development of Natty. It will get better but I think you might be better off simply reinstalling Maverick and avoiding upgrading to a testing version in future.

By the way, [starting duplicate threads]("http://ubuntuforums.org/showthread.php?t=1707379") is considered bad netiquette and annoys people trying to help you.

---

### Post by cariboo on 2011-03-15
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by xx58 on 2011-03-15
:rolleyes: Smart people, before they upgrade or go to different Ubuntu version, make backup at working version. 
Ubuntu 10.10 - use REMASTERSYS 2.0.18-1 and 15 minutes you have back exactly your version.
So, if you not have, then need start over from 0.
    Natty Narwal Ubuntu 11.04 have problems with first time booting. I had to 2 times reinstall Natty Narwal and had 2 times problem with boot.
So, what [COLOR=Red](helped me)[/COLOR]
[COLOR=Black]Before new install Ubuntu 11.04, disconnect all your USB drives, extrenal hard drives ect.ect.ect. and then start brand new installation. When finish installation, then boot your computer and when everything go like accepted, then connect all USB drives. It help me 2 times, with Ubuntu 11.04 and also Ubuntu 10.10.

[/COLOR]

---

### Post by rajeev1204 on 2011-03-15
> **ravitejamulpuri said:**
> [IMG]http://img233.imageshack.us/img233/7463/capturesce.png[/IMG]
[COLOR=SeaGreen]
**I have 128 mb Nvidia geforce graphic card....i think ( not sure)  i installed natty desktop server edition ...Now when i rebooted it i am getting a command line with out any UI...any idea why this is happening??**[/COLOR]


Server edition does not come with a GUI.As far as grub is concerned, if you scroll down a bit you will find an option to boot with command prompt and networking , you can try that if you know what you are doing.So it will give you a black screen with command prompt .

---

