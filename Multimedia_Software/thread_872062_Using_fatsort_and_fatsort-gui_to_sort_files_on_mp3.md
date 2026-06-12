---
title: "Using fatsort and fatsort-gui to sort files on mp3 devices"
date: 2008-07-27
forum: Multimedia Software
---

### Post by henriquemaia on 2008-07-27
Disclaimer: 
 I post this because **it works for me**. Use it if it suits you. If any information hereby contained ruins your device/your collection/your computer or creates a big black hole where we are all sucked in, blame it on providence, bad luck or lack of wisdom - not me.
 
 Ok, that being said, here's what you need:
 
 
[LIST=1]
[*]fatsort (it's on the repositories)
[*][fatsort-gui]("http://laxu.de/code/fatsort-gui.py")
[*]an mp3 device without rational sorting of files (yeah!)
[/LIST]

 Optional:
 
[LIST=1]
[*]nautilus-actions (it's on the repositories)
[*]too much time on your hands (?)
[/LIST]

 **For the console freaks:**
 Install **fatsort**. Use apt-get or aptitude for that. Since you're a console freak, I don't even write the command for that. **fatsort** It's very easy to use and understand. man fatsort. RTFM. Google for it if you're in trouble (using links). 
 
 You're done. Skip the rest of this guide and get on with your life. If you have the **2. **in the optional part, you can extend your pleasure a bit more by downloading the latest version of this utility and compile it yourself. You can even change the code and submit a patch if you're really into it.
 
 
 **For the normal crowd:**
 Open synaptic and look for fatsort. Install it. 
 
 Download **fatsort-gui**. If you're confused where to find it, it's here: [http://laxu.de/software.php](http://laxu.de/software.php)). Check for its properties and make it executable. Save it where it pleases you most (in your $HOME/bin, for instance). Copy files to your [stupid] mp3 device [without rational sorting of files] and then run **fatsort-gui**. 
 
 **Remember** that fatsort-gui assumes that you have your mp3 device umounted, so **you have to unmount your device** and then run fatsort-gui. Also, **you have to run it as root** - so run it with gksudo, so you can have root power! It's straightforward to understand how it works - the good part of fatsort-gui is that it's in German... but you just have to click the device you want to sort the files, click ok, and fatsort does the rest. 
 
 Now you can enjoy your music on your [stupid] mp3 device properly sorted out. If you're a lazy folks (like me) you can create a nautilus-action with nautilus-action-config. Install nautilus-actions with synaptic and then run nautilus-actions-config to create a new action. What I did was to create a simple entry poiting out to fatsort-gui, so that I have a very simple shortcut to it. Don't forget to put the gksudo before fatsort-gui command to grant fatsort permissions to sort out the files on the [stupid] mp3 device.
 
 
 **For the lazier folks:**
 Since I'm even more lazy than that, I changed the code of fatsort-gui a bit (just a tiny tiny bit - yay GNU/GPL!) in order to run fatsort in force mode - in this way you don't have to unmount the device (yeah!). Also, I added gksudo before the fatsort command, so it's all there. Oh, and I translated it, so it's in English! (I'm too lazy to read in German). I've uploaded the modified version of fatsort-gui for your lazy pleasure.
 

 Now enjoy your [stupid] mp3 device!


**note**: on a more serious tone. To check the order on which the files were copied to the device, you can use the command (on a terminal) **ls -RU **on the base folder of your device (e.g. /media/T60).

The ls is issued with 2 options, the -R is the recursive option and the -U the unsort option. If you check with this command before and after running fatsort, you'll notice the difference.

**testing environment:**
Ubuntu 8.04, iRiver T60
Ubuntu 8.10, iRiver T60
Ubuntu 9.04, iRiver T60

---

### Post by Roelski on 2008-08-08
Henrique,

It's worth mentioning that a number of flat-tv's suffer the same problem when displaying jpg-files.  I posted a thread on this earlier this week and came up with more or less the same solution.

Please check: [http://ubuntuforums.org/showthread.php?t=881645]("http://ubuntuforums.org/showthread.php?t=881645")

Thanks for the translation of the GUI and manual though.  Very helpful.

Best regs,


Roelski,
Antwerp

---

### Post by cnbiz850 on 2008-10-04
I did with the gui version as well as the non-gui version of fatsort on a USB flash disk on Hardy.  Either way trashed the file system on the disk.  I can't figure out how it may work.

---

### Post by henriquemaia on 2008-10-04
> **cnbiz850 said:**
> I did with the gui version as well as the non-gui version of fatsort on a USB flash disk on Hardy.  Either way trashed the file system on the disk.  I can't figure out how it may work.

Can you give more details on what was your trouble? I use this all the time and all the time with the same result - success. I even tried this on a [stupid] car radio I have with an SD card reader that played all files out of order - now it plays the files on the card well.

---

### Post by henriquemaia on 2009-05-25
Every time I have to install a new Ubuntu system where I don't have my backups available, I come here and check this thread to set up fatsort and fatsort-gui. Still works like a charm on 9.04.

---

### Post by ethanay on 2010-01-29
fatsort was a lifesaver for me when I got my T60 for use with Ubuntu (ogg support!).  I like listening to albums all the way through in their original order (call me nostalgic?), and the random order was frustrating.

Back in 7.10 I had it working with a launcher icon I could simply click after uploading all my files.

But via terminal it is simple:
identify the device path (for me it is /dev/sdb1)
then unmount the file system (via GUI)
then execute fatsort:  ```
sudo fatsort /dev/sdb1
```

it takes literally a couple of seconds to complete, and all my files are in order!

unfortunately, i seemed to have "bricked" my T60 recently, and it is giving a "file check error" and won't play.  I think it is toast unless I can get a disk image of a working T60 :(  Are there no Ogg players that use AAA batteries anymore????  So many disposable devices!

---

### Post by henriquemaia on 2010-01-30
> **ethanay said:**
> fatsort was a lifesaver for me when I got my T60 for use with Ubuntu (ogg support!).  I like listening to albums all the way through in their original order (call me nostalgic?), and the random order was frustrating.

Back in 7.10 I had it working with a launcher icon I could simply click after uploading all my files.

But via terminal it is simple:
identify the device path (for me it is /dev/sdb1)
then unmount the file system (via GUI)
then execute fatsort:  ```
sudo fatsort /dev/sdb1
```

it takes literally a couple of seconds to complete, and all my files are in order!

unfortunately, i seemed to have "bricked" my T60 recently, and it is giving a "file check error" and won't play.  I think it is toast unless I can get a disk image of a working T60 :(  Are there no Ogg players that use AAA batteries anymore????  So many disposable devices!

Have you tried formatting it? On mine worked. Please keep us updated (for a possible solution).

---

### Post by ethanay on 2010-01-30
I started a new thread here:

[http://ubuntuforums.org/showthread.php?p=8749875](http://ubuntuforums.org/showthread.php?p=8749875)

---

### Post by Endolith on 2010-03-23
I try to run this and it just says 

> ~> sudo fatsort /dev/sdb
FATSort Utility 0.9.8.3 by Boris Leidner <fatsort(at)formenos.de>

check_bootsector: Boot sector does not begin with jump instruction!
read_bootsector: This is not a FAT bootsector!
sort_fs: Failed to read boot sector!
main: Failed to sort file system!


---

### Post by henriquemaia on 2010-03-23
> **Endolith said:**
> I try to run this and it just says

You forgot the specific number of your device's partition. Run "sudo fdisk -l" to know that.

The command line should be something along the lines "sudo fatsort /dev/sdb**1**".

---

### Post by Endolith on 2010-03-23
Yes, I figured that out last night.  It works now.  :)

---

