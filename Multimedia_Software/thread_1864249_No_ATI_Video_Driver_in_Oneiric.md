---
title: "No ATI Video Driver in Oneiric?"
date: 2011-10-18
forum: Multimedia Software
---

### Post by osarusan on 2011-10-18
Running Oneiric x64 with an AMD Radeon HD 4770...

On a fresh install it loads the open source drivers with no problems.

After installing fglrx and having a hell of a time trying to get it to work properly, I decided to go back to the open source ati drivers. However, after removing fglrx driver (following the instructions at [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)) I'm having some major video issues. glxinfo fails to load with "glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory" and System Info gives me a blank line on the "Video Driver" section. So clearly the open source drivers are not installed correctly.

The thing is I don't know how to get them back now. I've followed all the instructions on that wiki, though it seems it applies to Natty, and there must be something more I have to do in Oneiric. any ideas?


---Edit---

I forgot to mention that it boots to my desktop successfully, both of my displays working at full resolution, although Unity fails to load. I can run things with no problem, just no Unity, and apparently no glx.

---

### Post by HydroMX on 2011-10-18
Perform this portion step by step.  I have an HD3200 and had to use this.  When you are done then go to your Additional Drivers and install ATI/AMD proprietary FGLRX graphics driver.

Problem: Need to fully remove -fglrx and reinstall -ati from scratch
Here is a more aggressive recipe which removes both -fglrx and -ati, and reinstalls the latter:


  sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg

---

### Post by osarusan on 2011-10-19
Unfortunately that's the same set of instructions I tried before. I tried it again, and no luck. I'm getting this response from System Info. As you can see there is nothing listed under Graphics.

Purging/reinstalling seems to have no effect at all. This has worked for me before on Natty, but it hasn't worked for me yet on Oneiric.

---

### Post by osarusan on 2011-10-19
Okay, I figured it out (I think). I installed the mesa swx11 package (which required me to uninstall the other mesa packages). This replaced the missing file, though, and now I have a working desktop using MESA. Strange, but good enough for me for now.

---

### Post by hrudaireddy on 2011-10-19
thanx a lot..i almost thought of re-installing from sratch. u made my day.thanx man

---

### Post by papampi on 2011-10-19
I have almost the same problem with my ati HD 4250 and oneiric 
i tried this guide [[edit] Installing Proprietary Drivers a.k.a. Catalyst/fglrx ]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide") also i tried swx11 from this post and i have plenty of problems !

payam@PAYAM-UBUNTU:~$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  138 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13

here is what i done and shell output : 
[http://pastebin.com/sxhnFew2](http://pastebin.com/sxhnFew2)

any idea how to solve this ????

---

### Post by papampi on 2011-10-19
as this thread is marked as solved, I'm posting a new one !!
by the way if you want to install from additional drivers :

You must have jockey-common and jockey-gtk (or jockey-kde for Kubuntu) packages installed. 
then go to the Additional Drivers Manager (System -> Administration -> Additional Drivers) and activate the "ATI/AMD proprietary FGLRX graphics driver" (or double-click the "available driver" notification icon). Ubuntu will then install and configure the driver for you.

---

