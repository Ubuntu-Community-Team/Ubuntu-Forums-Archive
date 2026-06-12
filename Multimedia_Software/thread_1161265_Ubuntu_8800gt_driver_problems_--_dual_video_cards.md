---
title: "Ubuntu 8800gt driver problems -- dual video cards"
date: 2009-05-16
forum: Multimedia Software
---

### Post by The_Giver on 2009-05-16
Not sure what section of the forum this belongs to:


So I have been trying to install the nvidia drivers for the longest time... I can't even get one video card to work correctly. The saddest thing is this worked out of the box inside a VM.. all monitors worked nicely.... sigh.


Anyway, I'm using the x64 bit version of 9.04.

I tried doing a lot of things, including installing from the command line using the nvidia drivers found:

[http://www.nvidia.com/object/linux_d...64_180.51.html](http://www.nvidia.com/object/linux_d...64_180.51.html)




I followed this tutorial:

[http://ubuntuforums.org/showthread.php?t=747210](http://ubuntuforums.org/showthread.php?t=747210)


I also tried this:


[http://www.thinkingserious.com/2008/...n-rc1-upgrade/](http://www.thinkingserious.com/2008/...n-rc1-upgrade/)




I also tried this:

[http://ubuntuforums.org/showthread.php?t=1054842](http://ubuntuforums.org/showthread.php?t=1054842)




So with all of them, doing startx or nvidia-settings or gdm start.. gives me crap about either "fatal error, no screen found" or... some variation of that.


My xorg.conf file is really mostly empty.. I don't even see resolutions for the display. I would post the xorg.conf file of each step.. but that means no xserver .



Thanks

---

### Post by inobe on 2009-05-16
i don't know what changes you have made' but what i am about to suggest works with a mere reboot.

[http://ubuntuforums.org/showthread.php?p=7206602#post7206602](http://ubuntuforums.org/showthread.php?p=7206602#post7206602)

the repo will install the latest stable nvidia driver

:note: it's **for 9.04 only**

though i don't know the affects after so many changes you made, there is a chance of modifications due to the changes to get it to work.

---

### Post by The_Giver on 2009-05-16
Cool, not perfect, but getting somewhere.

At least now I can choose to make one of my other monitors a secondary monitor. before I could only mirror them


Problems that still remain:

1) The resolution on the secondary monitor is way too low.... 
2) My other 2 monitors are not even being shown on the Display utility.
3) nvidia-settings does not work.... complains about not having an nvidia driver in use.. maybe because under devices it is labeled as "nv"


=======================================

Here is my xorg.conf file:


Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
        SubSection "Display"
                Virtual 2880 1200
        EndSubSection
EndSection

Section "Module"
        Load    "dri"
        Load    "GLcore"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nv"
EndSection


=======================================


Thanks a ton.

PS: A while back when I did this in the past... I had to use some weird tool that allowed me to lay out my monitors in a graphical interface... not a standard tool, but it seemed to work pretty well, the name escapes me now though.

---

### Post by inobe on 2009-05-16
lets make sure you have all the listed components, open synaptic an search **nvidia**

heres what i have installed, you can make a comparison.

[B]nvidia-settings
nvidia-180-kernel-source
nvidia-common
nvidia-180-modealiases
nvidia-glx-180
jockey-common
jockey-gtk[/B]

:note: you need to make sure the current driver description shows 180.51 !

if for any reason they are 180.44 you must remove those components and select 180.51's 

you may have issues removing 180.44 components, if so' restart to remove the rest.

---

### Post by The_Giver on 2009-05-16
What I don't have:

vidia-180-kernel-source
nvidia-glx-180


I have 173 version of this:

nvidia-180-modealiases



I'm going to try to upgrade and install missing stuff..

---

### Post by The_Giver on 2009-05-16
So now  I can't startx or gdm.. =-(

---

### Post by inobe on 2009-05-17
try this [http://ubuntuforums.org/showthread.php?t=1139101](http://ubuntuforums.org/showthread.php?t=1139101)

i was hoping this issue would have been fixed, you can use the repo in conjunction .

---

### Post by The_Giver on 2009-05-24
Almost there!!!!!!!!!!


So it mostly works.. except ... I need to rotate two my of displays =-(

Since I have four screens.. I'm using twinview + xinerama...  but I need to rotate two of those screens  =-(



I tried looking up stuff on xrand but it seems I can't use xineram stuff with that =-(

---

### Post by The_Giver on 2009-05-25
Anyone =-(

---

### Post by The_Giver on 2009-05-26
please help  =(

---

