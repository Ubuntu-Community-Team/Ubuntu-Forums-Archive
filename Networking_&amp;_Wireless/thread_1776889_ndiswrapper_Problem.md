---
title: "ndiswrapper Problem"
date: 2011-06-06
forum: Networking &amp; Wireless
---

### Post by bLym3 on 2011-06-06
Hi,
well first things first, i am a linux noob and i just finally managed to dual boot my system with windows 7 and ubuntu.
The problem i found out since i installed it is with my wireless network usb, I have a netgear WNA3100 and i followed the instructions on several threads on how to install the ndiswrapper but not a lot of luck so far.
I have to say i decided to change and support open source and its power but damn it makes it difficult....

Furthest i went with the process is here: [IMG]http://i134.photobucket.com/albums/q88/bloodymiros/Screenshot.png[/IMG]

any help is much appreciated..

---

### Post by mocoloco on 2011-06-06
Much easier:
If you installed from a CD, insert the CD and Ubuntu will ask you if you want to add the CD to your list of packages. Once you do that, go to System -> Administration -> **Synaptic Package Manager**.
Search for and install **ndisgtk**
If you get complaints about not being connected, go to Settings -> Repositories, and disable all the checkboxes on the first 3 tabs except for the cdrom entry on the second tab.  Close, you'll be asked to re-load the list of packages, then install ndisgtk.

Hopefully you understand that once that's installed you need your windows wireless driver as well.  So now go to System -> Administration -> **Windows Wireless Drivers**, and select to add a new driver.  Navigate to the folder where you driver is and the file you want to select is the .inf file.  Give it a sec and your wireless card should be recognized.

---

### Post by pfc2k8 on 2011-06-08
To get the WNA3100 working you need to compile ndiswrapper yourself!
First get the source from sourceforge and then follow this post:

[http://ubuntuforums.org/showpost.php?p=10904502&postcount=71](http://ubuntuforums.org/showpost.php?p=10904502&postcount=71)

at least thats the way it worked for me.
With the ndiswrapper from cd the driver was installed successfull but the WNA3100 could not find any networks.

---

