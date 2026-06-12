---
title: "After fresh Xubuntu install, no selectable VIA 8237 driver (sound problem)"
date: 2009-05-03
forum: Multimedia Software
---

### Post by Anthalion on 2009-05-03
Hello,

I have this problem for few days now. Before I became a Xubuntu user, I used both Ubuntu regular, Ubuntu Studio, Kubuntu, Linux Mint...

It was all to slow for my machine, and yesterday, I decided to wipe out totally everything on my machine related to old data; I salvaged everything that matters to me on the USB disk, and I begun to install Xubuntu 9.04.

Anyway, VIA 8237 driver was by default selected in the live version when I runned the Xubuntu over my CD drive, and sound has worked for files.

HOWEVER, AFTER I installed Xubuntu on my HDD (in the process I have erased my old GNOME Ubuntu 8.10, and thats what I wanted, and I NEVER had any sound driver problems with it before), the ONLY driver I can chose, i C-Media ELectronics CMI9761A+ (OSS Mixer). This means, offcourse, that sound doesnt work for me cause this is not the driver I can use for my soundcard.

This NEVER happened to me previous on all my distributions I tried so far (Ubuntu, Kubuntu, Linux Mint, Ubuntu Studio etc...), and quie honestly, the only thing I want to do, is to download the drivers.

I installed ALSA mixer programs or something like that, from repository, however, ALSA Mixer (something like that; I reinstalled over Xubuntu Xubuntu now, and again the problem persists) is reporting to me that THERE IS NO DIRECTORY with ALSA mixers.

Which is funny, cause everything worked just fine while I runned the live version from the CD.


Oh, I also forgat to mention that AFTER I installed (both times) Xubuntu, and after I clicked on "installation is over, you need to reset your computer"  OK button, and whole Xubuntu was shutting down, for a brief second or two, just after the loading window for shutting down went away, there was brief 10-20 lines of I/O reading error's.


So, I suppose when I burnt/downloaded/installed Xubuntu, something went wrong cause CD couldnt read that particular information, maybe even that VIA 8237 file.
I have no other problems, so, is there a possibilty to DOWNLOAD VIA 8237 driver from somewhere??


I SEARCHED all over, but I couldnt find anywhere a possibility to download the VIA driver from repository, and, I actually think I even was able to do something similar to that over terminal day or two ago, but it reported to me that there isn't any directory with VIA driver !!



So, before I went through the trouble of downloading AGAIN whole damn Xubuntu, and ripping it AGAIN (from different computer) on CD, could it be a distro problem's, or do I really have to burn another CD ?

All the best and thanx on the answer,
-David

---

### Post by Anthalion on 2009-05-03
OK, I have reinstalled my ALSA drivers using the methods here:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

However, I still dont have an ALSA option !! wtf ??

---

### Post by Anthalion on 2009-05-03
People, dont forget about me !!

---

### Post by Anthalion on 2009-05-04
U forgat about meeeeeeeeeeeeeee

---

### Post by Anthalion on 2009-05-04
```
david@david-desktop:~$  
david@david-desktop:~$ mkdir src cd src
mkdir: Can't make directory `src': directory exists [this was on Croatian so I transtlated it]
david@david-desktop:~$       
david@david-desktop:~$ mkdir alsa
david@david-desktop:~$       
david@david-desktop:~$ cd alsa
david@david-desktop:~/alsa$       
david@david-desktop:~/alsa$ sudo apt-get install build-essential linux-headers-$(uname -r)
[sudo] password for david: 
Reading package lists... Done
building dependency tree       
reading state information... Done
build-essential is already the newest version.
Linux-headers-2.6.28-11-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
David@david-desktop:~/alsa$ alsamixer
alsa lib conf.c:2700:(snd_config_hooks_call) cannot open shared library libasound_module_conf_pulse.so
alsa lib control.c:909:(snd_ctl_open_noupdate) invalid ctl default

alsamixer: Function snd_ctl_open failed for default: No such file or directory
david@david-desktop:~/alsa$ sudo gedit /etc/modprobe.d/alsa-base 
[sudo] password for david: 
Sudo: Gedit: Command not found
david@david-desktop:~/alsa$ sudo mousepad /etc/modprobe.d/alsa-base 
david@david-desktop:~/alsa$ alsamixer
alsa lib conf.c:2700:(snd_config_hooks_call) cannot open shared library libasound_module_conf_pulse.so
alsa lib control.c:909:(snd_ctl_open_noupdate) invalid ctl default

alsamixer: Function snd_ctl_open failed for default: No such file or directory
david@david-desktop:~/alsa$ 
```

**what now ?????????**

---

### Post by Anthalion on 2009-05-04
[b]jesus christ, if no one responds now, i am switching to fedora.


Damn !!!!!!!!!!!!!!!![/b]

---

### Post by Anthalion on 2009-05-04
[B]Goodbye Ubuntu, you lost me !!!!!!!!!

No one helped; its obvious Ubuntu's helpdesk is catastrophic !!!!

GOODBYE UBUNTU



NO ONE HELPED ME[/B]

---

