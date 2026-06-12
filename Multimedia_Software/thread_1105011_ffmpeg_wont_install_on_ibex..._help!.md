---
title: "ffmpeg wont install on ibex... help!"
date: 2009-03-24
forum: Multimedia Software
---

### Post by spyyked on 2009-03-24
when attempting to install ffmpeg...

spike@UltimateEdition:~$ sudo apt-get install ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ffmpeg: Depends: libavcodeccvs51 (>= 3:20060814) but it is not going to be installed
          Depends: libavutilcvs49 (>= 3:20060814) but it is not going to be installed
E: Broken packages




is my install corrupt? certainly what it sounds like, but any suggestions before i reload it would be greatly appreciated!

---

### Post by mcduck on 2009-03-24
Have you enabled Universe & Multiverse repositories?

If you are using Gnome, go to System/Preferences/Software Sources and on the "Ubuntu Software"-tab make sure both are enabled.

edit: also, make sure you run "sudo apt-get update" before trying to install anything..

---

### Post by spyyked on 2009-03-24
i wont be back on my machine till late tonight, but i will double check. 

there is an error when i run the update, says it misses something or other... cant remember off top of my head, but i will post it back on here later.  it didnt seem related, but then again, im still pretty new to ubuntu/linux.

thanks for the feedback! hope to hear more!

---

