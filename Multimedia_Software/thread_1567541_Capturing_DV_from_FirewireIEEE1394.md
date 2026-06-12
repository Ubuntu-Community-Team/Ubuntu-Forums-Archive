---
title: "Capturing DV from Firewire/IEEE1394"
date: 2010-09-03
forum: Multimedia Software
---

### Post by dodle on 2010-09-03
There has been only one way that I have been able to get kino and kdenlive to recognize and capture from my dv camcorder as a normal user.  But it doesn't seem like the best possible solution.  

First, here are some other methods that I tried:

[list]I tried using the commands that this user used:
> **ChasHutch said:**
> sudo modprobe dv1394
sudo modprobe video1394
sudo modprobe raw1394
sudo modprobe ohci1394 
to no avail.[/list]

[list]I also tried the method described on [https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire):
> [SIZE=4]Method 3. 'udev rule'[/SIZE]

As the most straight-forward method, simply add the raw1394 specific udev rule which was left out by Ubuntu's udev maintainers. Type this in a terminal:

```
echo 'KERNEL=="raw1394", GROUP="video", MODE="0664"' > /tmp/raw1394.rules
sudo cp /tmp/raw1394.rules /etc/udev/rules.d/
rm /tmp/raw1394.rules
```

Then unload and reload raw1394,

```
modprobe -r raw1394 && modprobe raw1394
```

and type in a terminal:

```
sudo /etc/init.d/udev restart
```

[size=4]In Ubuntu 10.04[/size]

Paste this in your terminal:

```
echo 'KERNEL=="raw1394", GROUP="video", MODE="0664"' |
sudo tee /etc/udev/rules.d/50-raw1394.rules
&& sudo restart udev
```

If the firewire device was connected already before having run the above, restarting udev is not sufficient but at least after a reboot things will work then. [/list]

Neither of these methods worked for me.  The only way I could capture from my camcorder was to change either the owner or group of /dev/raw1394:
```
sudo chown myusername /dev/raw1394
```
or (I like better):
```
sudo chgrp myusername /dev/raw1394
```

Then everything worked fine.  But, I don't think this is the best way because if my machine had multiple users, only my account could capture unless I made the other users part of my group.  What do you think?  Is there a better solution or did I just do something wrong in the earlier methods?

---

### Post by scorp123 on 2010-09-04
This works for me:

[http://ubuntuforums.org/showpost.php?p=3831001&postcount=19](http://ubuntuforums.org/showpost.php?p=3831001&postcount=19)

---

### Post by scorp123 on 2010-09-04
> **dodle said:**
>  First, here are some other methods that I tried:

sudo modprobe dv1394
sudo modprobe video1394
sudo modprobe raw1394
sudo modprobe ohci1394
 IMHO the order is wrong. And "ieee1394" is missing?

IMHO the correct order is:

ieee1394
ohci1394
raw1394
video139
dv1394

---

### Post by Catone on 2011-02-19
I do not know why or how, but just for history:
all suggestions and methods for fixing capturing video from firewire doesn't work for me - camera was not detected. One last chance was note on [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation) about new stack (firewire-* modules) requires libraw1394 version >=2.0.5, and it looks like that there were only 2.0.4 in repository. 
So I've cleaned up all experiments - it is important.
Downloaded latest version of libraw1394 from [http://sourceforge.net/projects/libraw1394/](http://sourceforge.net/projects/libraw1394/), extracted it
./configure && make && sudo make install
reboot system
sudo chmod a+rw /dev/fw0 - not really sure that it matters anything
plugged camera in, turned it on - and it was detected by os. 

now dvgrab works perfectly

Final configuration:
Kubuntu 10.04

catone:~$ lsmod | grep 1394
catone:~$ lsmod | grep fire
firewire_ohci          21226  0 
firewire_core          44638  1 firewire_ohci
crc_itu_t               1371  1 firewire_core

catone:~$ ls -la /dev/fw*
crw-rw-rw- 1 root catone 251, 0 2011-02-19 15:46 /dev/fw0

catone:~$ cat /etc/modules 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

catone:~$ cat /etc/modprobe.d/blacklist-firewire.conf 
# Select the legacy firewire stack over the new CONFIG_FIREWIRE one.

blacklist ohci1394
blacklist sbp2
blacklist dv1394
blacklist raw1394
blacklist video1394

#blacklist firewire-ohci
#blacklist firewire-sbp2

catone:~$ ls /etc/udev/rules.d/ | egrep '(fire|1394)'

---

### Post by HC48 on 2011-02-28
Hello Catone,
I have been seeking help with this problem :
[http://ubuntuforums.org/showthread.php?t=1528469](http://ubuntuforums.org/showthread.php?t=1528469)
[http://ubuntuforums.org/showthread.php?p=10482591#post10482591](http://ubuntuforums.org/showthread.php?p=10482591#post10482591)
I'm not very good at commands etc and have tried the usual things , as you mention above.
Your idea seems good and I have downloaded libraw 1394 version 2.0.5 and extracted it (I have the 2.0.4 version installed).
I'm not sure what to do next though and I suppose I should be in the absolute beginners thread for this part... however I would appreciate the Lucid Lynx for dummies version of 'cleaning up',
./configure && make && sudo make install etc. if you can spare the time...

I did this fix from the Kino site before:
blacklist ohci1394
blacklist sbp2
blacklist dv1394
blacklist raw1394
blacklist video1394

#blacklist firewire-ohci
#blacklist firewire-sbp2

but it didn't work.

I try to be careful but afraid to make a mess!!
Thank you anyway,
HC

Got the simple explanation how to install here [http://ubuntuforums.org/showthread.php?p=10562585#post10562585](http://ubuntuforums.org/showthread.php?p=10562585#post10562585)
 which is what you said (of course) ...

Latest version installed but still no change. I'm not sure if I should continue the commands as in Kubuntu above (sudo chmod etc...) as I'm not sure what it all does. I'm the only person who uses my computer so no need to create a group I think.  Dvgrab says no camera connected in the terminal, I tried forcing with this as in the documentation about firewire:
gksudo modprobe raw1394
gksudo modprobe dv1394

to no avail.I've tried everything else in the documentation and my camera works on another 
computer with the same OS. It is a Sony Handycam DCR-HC35E
I'd be grateful for any advice.
HC

---

