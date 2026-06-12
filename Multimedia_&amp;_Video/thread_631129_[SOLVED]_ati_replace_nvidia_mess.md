---
title: "[SOLVED] ati replace nvidia mess"
date: 2007-12-04
forum: Multimedia &amp; Video
---

### Post by d3ni5 on 2007-12-04
gutsy 7.10

i had nvidia videocard and replaced it with ati videocard.... and here the hell starts... some of teh GL libraries are messed up by nvidia driver. (I uninstalled most of the pakages including xserver xorg) and then reinstalled them to make sure that nvidia dependencies removed.

Now for example if I tri to start glxinfo I got Segmentation fault.
I started to analyze fault stacktrace from core and realized that GL libraries still has references to nvidia libraries - that why I got Segmentation fault.

As far as I understand I have only 2 options:
- reinstall ubuntu 
- find wrong dependencies and resolve them, file bug against ubuntu and steps to reproduce

How it is possible that nvidia drivers left libraries reference after uninstallation?

---

### Post by vikramsharma on 2007-12-04
You can reconfigure your xorg, you can try sudo dpkg-reconfigure xserver-xorg.  That might help you out.

---

### Post by d3ni5 on 2007-12-04
dpkg-reconfigure xserver-xorg just will create new /etc/X11/xorg.conf 

do you belive that this plain text file will resolve library mess / wrong and missing libraries ?

---

### Post by harold4 on 2007-12-04
When uninstalling the nvidia driver, did you apt-get remove **--purge**?

-------------------------------------------------
Hard to say why libs are all banged up. 
-------------------------------------------------

---

### Post by d3ni5 on 2007-12-04
yep, and all packages were downloaded from internet (which take a while).
That why I was sure that no nvidia dependencies is stored.

---

### Post by vikramsharma on 2007-12-04
> **d3ni5 said:**
> dpkg-reconfigure xserver-xorg just will create new /etc/X11/xorg.conf 

do you belive that this plain text file will resolve library mess / wrong and missing libraries ?

No it wont but you would be able to boot into graphic mode, what kind of ATI card do you have.  I would say that you could download the latest version of ATI linux driver from ATI's website and run it.  What libraries are missing, it is difficult to say anything otherwise.  Heres a link to the [article]("http://ubuntuforums.org/showthread.php?t=574302&highlight=ATI") .

---

### Post by d3ni5 on 2007-12-04
I'm able to boot X with both fglrx and ati , but glxinfo and fglrxinfo is fail with segmentation fault due to reference to GL libriries messed from time nvidia was installed.

So im looking for a way realize how to resolve this wrong reference and how to correct gl to reference to ati drivers.

---

### Post by d3ni5 on 2007-12-05
dirty magic - I again purged-removed all GL related packages including xorg and xserver, and 

then: started to search for nvidia related files 

sudo find  /  -name "*nvid*"


and found that script : /usr/bin/nvidia-install exist

then I started this script in the uninstall mode - this script replace links to libraries and even fix some header files.

So seems that script removed references to nvidia mess.

Again reinstalled xserver, xorg, gnome, GL packages and voila!

Now no wrong references to Nvidia libraries.

Hope this story can help someone.

---

### Post by vikramsharma on 2007-12-06
> **d3ni5 said:**
> dirty magic - I again purged-removed all GL related packages including xorg and xserver, and 

then: started to search for nvidia related files 

sudo find  /  -name "*nvid*"


and found that script : /usr/bin/nvidia-install exist

then I started this script in the uninstall mode - this script replace links to libraries and even fix some header files.

So seems that script removed references to nvidia mess.

Again reinstalled xserver, xorg, gnome, GL packages and voila!

Now no wrong references to Nvidia libraries.

Hope this story can help someone.

Thanks a lot man, sorry could not help you out.  We have this thread for future references.

---

