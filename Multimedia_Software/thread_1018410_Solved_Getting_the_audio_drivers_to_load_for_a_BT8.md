---
title: "Solved: Getting the audio drivers to load for a BT878 card"
date: 2008-12-22
forum: Multimedia Software
---

### Post by arie_maron on 2008-12-22
Hello All,

I am using a generic bt878 based card for video capture.
The video drivers loaded automatically but, the audio drivers would not 
load.

This solution is based upon the info from this site:
[http://www.mythtv.org/wiki/index.php/Snd-bt87x](http://www.mythtv.org/wiki/index.php/Snd-bt87x)

I am assuming that your distro is either 8.4 or 8.10 both of them have the required modules by default. 
I am not sure about earlier distros. I haven't checked them.

_Step 1_: create a file in /etc/modprobe.d with the following 
**options snd-bt87x load_all=1**. 
I named the file snd_bt87x.modprobe but, the name can be anything.
All the files in /etc/modprobe.d are read.

_Step 2_: add the name of the module, **snd-bt87x** to the file /etc/modules.

You will need to restart the computer to automatically load the module.

If you are impatient you can load the module manually with the command:
**modprobe -r snd-bt87x; modprobe snd-bt87x load_all=1**

To verify that the sound drivers are loaded do
**cat /proc/asound/cards**

You should see that the bt878 audio devices are listed in the output.

---

### Post by dewmanstl on 2009-06-01
Hello,

I am trying to follow the wiki and it mentions to do the following:

```
Different Linux distributions use different configuration files to load and configure modules. Here's what you need to do for some distributions. 
 
[LIST]
[*] Mandriva
[LIST]
[*] 2007
[LIST]
[*] echo "snd-bt87x" >>/etc/modules # load the module on boot
[*] echo "options snd-bt87x load_all=1" >>/etc/modprobe.conf # OPTIONAL - if required for your bt87x card
[/LIST]
[/LIST]
[/LIST]

```

Umm...What do I do for Muthbuntu? I am not sure what it means to echo 

Thanks

---

### Post by dewmanstl on 2009-06-01
> **arie_maron said:**
> Hello All,

I am using a generic bt878 based card for video capture.
The video drivers loaded automatically but, the audio drivers would not 
load.

This solution is based upon the info from this site:
[http://www.mythtv.org/wiki/index.php/Snd-bt87x](http://www.mythtv.org/wiki/index.php/Snd-bt87x)

I am assuming that your distro is either 8.4 or 8.10 both of them have the required modules by default. 
I am not sure about earlier distros. I haven't checked them.

_Step 1_: create a file in /etc/modprobe.d with the following 
**options snd-bt87x load_all=1**. 
I named the file snd_bt87x.modprobe but, the name can be anything.
All the files in /etc/modprobe.d are read.

_Step 2_: add the name of the module, **snd-bt87x** to the file /etc/modules.

You will need to restart the computer to automatically load the module.

If you are impatient you can load the module manually with the command:
**modprobe -r snd-bt87x; modprobe snd-bt87x load_all=1**

To verify that the sound drivers are loaded do
**cat /proc/asound/cards**

You should see that the bt878 audio devices are listed in the output.

I tried modprobe and received the following....

```
@myth:~$ modprobe -r snd-bt87x; modprobe snd-bt87x load_all=1
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
FATAL: Error inserting snd_bt87x (/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-bt87x.ko): Operation not permitted
```

---

