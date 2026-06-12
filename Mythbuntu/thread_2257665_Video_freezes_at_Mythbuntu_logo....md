---
title: "Video freezes at Mythbuntu logo..."
date: 2014-12-21
forum: Mythbuntu
---

### Post by killabee44 on 2014-12-21
Hi all,

I am having a problem with my mythbuntu machine freezing at the mythbuntu logo. This all started happening after some updates last week. There was an unmet dependency, and after booting, the problem started. I really don't know how to find what the unmet dependency was, or how to disable it if needed. I suspect my updates did not complete because of this, causing the boot issue.

I have tried installing the latest Nvidia driver to no avail. I now have instead installed Nvidia driver 304, but the problem persists. Please let me know what outputs you might need. I am no expert, but can work the command line.

After searching, I have tried: 

sudo apt-get install nvidia-current

sudo apt-get install --reinstall linux-generic

sudo apt-get -f install

sudo apt-get install nvidia-304

and nothing has worked so far. Thanks in advance for your help with this.

---

### Post by bapoumba on 2014-12-21
*Thread moved to **Mythbuntu**.*

---

### Post by killabee44 on 2014-12-21
Thanks for moving the thread. I didn't think it would matter that it was Mythbuntu, since it was a regular "freezing at ubuntu logo issue". I saw many of those from Ubuntu users.

---

### Post by bapoumba on 2014-12-21
Yeah, it may be related to your video drivers (but I do not have much skills regarding this).
It may help posting the output to the following to start with :
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by killabee44 on 2014-12-21
It's gonna be an issue posting long outputs like those since im posting here from another pc and those outputs are pages long. I can't cut and paste. I can maybe take a pic with my phone of the screen, but it will be only the last page displayed. Unless I can find a way to make the output scroll one page at a time, then I can take pics of each page and post them here.

---

### Post by bapoumba on 2014-12-21
Hmm OK. Does the update trigger a lot of errors or the upgrade ?

---

### Post by killabee44 on 2014-12-21
Neither triggers any errors that I could see.

---

### Post by khPWXxF on 2014-12-22
Has the nvidia install zapped your /etc/X11/xorg.conf by renaming it?
Phil

---

### Post by bapoumba on 2014-12-22
May be here ? [https://devtalk.nvidia.com/default/topic/734584/nvidia-driver-is-unable-to-load/](https://devtalk.nvidia.com/default/topic/734584/nvidia-driver-is-unable-to-load/)
I can move your thread back or to the hardware section if you wish :)

---

### Post by killabee44 on 2014-12-22
> **khPWXxF said:**
> Has the nvidia install zapped your /etc/X11/xorg.conf by renaming it?
Phil

It sure did. It renamed it xorg.conf.051...

I copied that file as xorg.conf but the problem persists. 

bapoumba,

I visited the link you provided and also went to and tried the other links provided within it. It tried all fixes listed to the letter in all links to no avail.  

Can you please move the thread? maybe if it gets more eyes in the forum that handles video issues someone might be able to shed some light.

---

### Post by killabee44 on 2014-12-22
Question.. If I re-install, is there a way to make sure all the same apps are still installed? I think I read somewhere that it's possible, but can't remember how.
EDIT:

Found it! makes a list of the apps you have installed, then, via one command, restores all your apps. Thanks oldfred! Here is the link in case anyone needed the info: 

[http://ubuntuforums.org/showthread.php?t=1911947&p=11625167#post11625167](http://ubuntuforums.org/showthread.php?t=1911947&p=11625167#post11625167)

[http://kvz.io/blog/2007/08/03/restore-packages-using-dselectupgrade/](http://kvz.io/blog/2007/08/03/restore-packages-using-dselectupgrade/)

 Also, for future reference.. Is there a way to prevent the video driver from being ever updating? Other than always picking through each update, that is..

---

