---
title: "How do I do this??"
date: 2008-07-14
forum: Multimedia Software
---

### Post by Richpickings on 2008-07-14
Hi chaps
I asked a while ago about getting my Creative SB XFi working. when I reported that it was unsupported the help sort of dried up.
I've now found a driver from the Creative website, but the instructions (to my Windows infested mind) appear to be gobbledygook.

I've pasted them below, could one of you fine gentlemen explain in fairly plain English what I need to do. I'm a near complete Linux novice.

I'm using Ubuntu 8.04




Quick install


=============




1) You must have the fully configured source for the Linux kernel and 

   ALSA which you
 want to use for this device driver. Partial installed 

   kernels (e.g. From distribution makers) may be unusable for this 

   action.





2) Run one of the following commands as root in the terminal:





   ./installer
   




   OR




   ./installer --with-alsainc=<ALSA_include_directory>





  * ALSA Source Tree




   
   On 2.6 kernels, the location of the ALSA source include directory


      is parsed automatically from the running kernel.


      If it is not in the standard place, specify the path via

   
   --with-alsainc=<ALSA_include_directory>.



 
   
  On 2.4 kernels, the location of the ALSA source include directory


      must be specified via --with-alsainc=<ALSA_include_directory>.





  * Note

      If integrated ALSA is to be used to build, --with-alsainc option


      must not be specified.

---

### Post by fenian on 2008-07-14
The driver from creative stinks,awful instructions and I don't believe it works with the newer versions of alsa.You should use the OSS driver from 4front-tech you can download it [here]("http://www.4front-tech.com/oss.html") ,they have forums where you can get more info.The downside is that the OSS driver may only give you 2.1 sound (when I used it several months ago this was the case but I sold that card and got a different one so I'm not 100% sure on the current staus.),but some sound is better than none.

---

### Post by Richpickings on 2008-07-15
Ok, maybe I'm getting somewhere. Stupid question now, how do I become root? I tried typing su into the terminal thingy but it asked for a password which I don't have. When I set up Ubuntu it only asked for a user password.

---

### Post by pmlxuser on 2008-07-15
> **Richpickings said:**
> Ok, maybe I'm getting somewhere. Stupid question now, how do I become root? I tried typing su into the terminal thingy but it asked for a password which I don't have. When I set up Ubuntu it only asked for a user password.

In ubuntu we don't use su we use $sudo <command>
when asked for password you use the password for the user password

---

### Post by Richpickings on 2008-07-15
OK. So I've got a file called oss-install in my tmp folder which I think is the one I need to install. What exactly would I type into the terminal thingy to get it to run?

---

### Post by Richpickings on 2008-07-15
Everything I try it says "This program must be run as the super user (root)"

---

### Post by Richpickings on 2008-07-15
Say what you like about Windows, but double clicking executables has it's advantages.

---

### Post by Richpickings on 2008-07-15
OK. I got it to run, but still no sound, all I got was "volume control quit unexpectedly". I'll try and re-boot and get back to you (If anyone is listening)

---

### Post by Richpickings on 2008-07-15
OK. Still no sound. Does anyone else have any suggestions. Maybe I downloaded the wrong package. Which one should I have used?

---

### Post by fenian on 2008-07-15
To install OSS on Ubuntu 8.04 (Hardy) follow the [instrucions in this post]("http://ubuntuforums.org/showpost.php?p=4874981&postcount=2").

---

### Post by Richpickings on 2008-07-18
Sorry for the delay in reply, I've been away and busy. Thanks for the tip, however I've come to a bit of a halt again on step 6. Here's what happens:

richard@richard-desktop:~$ sudo dpkg -i oss-linux_v4.0-1016_i386.deb
dpkg: error processing oss-linux_v4.0-1016_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 oss-linux_v4.0-1016_i386.deb
richard@richard-desktop:~$ sudo soundon

the DEB file is in my Home folder and on my desktop......

---

### Post by cariboo on 2008-07-18
Instead of trying to install the deb by hand why not just double click on it and use gdebi to install it.

Jim

---

### Post by Richpickings on 2008-07-18
Elaborate please.........

---

### Post by SunnyRabbiera on 2008-07-18
There is a application installer called gdebi that installs .deb files like windows .exe files.
If you double click a .deb file it will install with gdebi

---

