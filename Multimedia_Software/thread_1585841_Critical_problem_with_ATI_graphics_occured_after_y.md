---
title: "Critical problem with ATI graphics occured after yesterday's kernel update"
date: 2010-10-01
forum: Multimedia Software
---

### Post by alexpennos on 2010-10-01
Dear all!
First of all, iwould like to apologize for my bad english, since i am from Greece. Secondly, i must say that i am not a very experienced user which means i might need an extra help. But let me describe my problem.
Everything was fine until yesterday when some updates, having to do with the kernel, came up. After some errors occuring during the update (not of the kernel update) of the Fglrx drivers, my system became un-bootable. I had a purple screen after the splash screen. I managed to activate the GRUB and entered in graphics safe mode, where I made some changes in order to do my system bootable (through synaptics, i removed and installed some fglrx packages). Before the graphics crash, I had also the ati catalyst installed too. What i think i need is first of all check (i dont know how to do this) which driver i have installed in my system, remove it, and make a fresh install.
Any help would be great!

---

### Post by needastick on 2010-10-01
Hello, I'm also having similar problems, (post above). There is some information that may help you in synaptic. If you go to history in the edit column it will tell you everything that has been installed and when.

After you have the linux code you can then find it in the main box and right click properties. I'm assuming that you can't just open the information tab in the catalyst menu, ( preferences, ati ccc)

Hope this helps.

---

### Post by alexpennos on 2010-10-01
This info did cleared a bit the situation...Buta i still get an error trying to re install fglrx drivers...

---

### Post by alexpennos on 2010-10-01
I am also having this problem:
> alexandros@alexandros-laptop:/usr/share/ati$ sudo sh ./fglrx-uninstall.sh
[sudo] password for alexandros: 

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run ./fglrx-uninstall.sh (this is not recommended).
:(

---

### Post by driesv on 2010-10-01
I had the same error (with command *sudo sh ./fglrx-uninstall.sh*), but then I fixed it otherwise (see other [topic]("http://ubuntuforums.org/showpost.php?p=9911334&postcount=4")).

---

### Post by alexpennos on 2010-10-01
Yes, i saw your post...but the problem is that when i go to system->Administration->Hardware Drivers, the graphics card does not appear at all. So I cannot do any changes.

Moreover, can you tell me a way to delete o move those conf. files on X11 folder? I dont have acces from graphical environment and i hve to do it with the terminal....

---

### Post by driesv on 2010-10-01
> **alexpennos said:**
> Moreover, can you tell me a way to delete o move those conf. files on X11 folder? I dont have acces from graphical environment and i hve to do it with the terminal....
- *cd /etc/X11*
(type* ls* (not an I but a lower-case L) and you see the directory-content)
It's better to edit your Xorg.conf file, you can edit your Xorg.conf-file by using the command *nano*. If you want to delete it, I advise you only renaming it.
- *sudo nano xorg.conf*
(because you have to be root, to edit files in /etc)

---

### Post by alexpennos on 2010-10-01
Do you want to have a look an this
[http://yfrog.com/juselection038p]("http://yfrog.com/juselection038p")
Which one to edit?

---

### Post by alexpennos on 2010-10-01
I found the solution and posted it here:
[http://ubuntuforums.org/showthread.php?p=9911724#post9911724](http://ubuntuforums.org/showthread.php?p=9911724#post9911724)
Anyone could also find usefull info here:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

---

