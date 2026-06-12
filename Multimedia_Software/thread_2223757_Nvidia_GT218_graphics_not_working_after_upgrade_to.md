---
title: "Nvidia GT218 graphics not working after upgrade to 14.04"
date: 2014-05-12
forum: Multimedia Software
---

### Post by hughcharlesparker on 2014-05-12
I have an Acer Aspire Revo r3700.  lspci reports its graphics card to be a VGA compatible controller: NVIDIA Corporation GT218 [ION] (rev a2).

It's my HTPC, so it's connected to my TV with an HDMI cable.  After I upgraded to 14.04, I got the startup sequence, and then nothing on the TV except a flashing cursor.  Uninstalling the Nvidia drivers and just using Nouveau worked, but left me with a very poor resolution.  After reinstalling nvidia-331, I get a message to say that "The system is running in low-graphics mode.  Your screen, graphics card, and input device settings could not be detected correctly.  You will need to configure these yourself".  I'm then given some options:

 - If I "run in low-graphics mode, just for one session", I just get the flashing cursor.
 - If I click "reconfigure graphics", I get asked whether I want to use my default (generic) configuration or my backed-up configuration, both of which just cause the same dialog box to reappear.

When I look in the logs, it says that the Nvidia kernel module failed to start.  At the suggestion of one of the comments on this thread:
[http://askubuntu.com/questions/399153/after-apt-get-upgrade-system-always-boot-to-low-graphics-mode](http://askubuntu.com/questions/399153/after-apt-get-upgrade-system-always-boot-to-low-graphics-mode)
...I tried running sudo modprobe nvidia-331, followed by sudo lightdm start.  This starts the display in the correct display resolution, but without sound.

I've attached my kern.log and Xorg.0.log.

I'd be very grateful for any help or advice.

---

### Post by papibe on 2014-05-12
Hi hughcharlesparker.

Try this:
[LIST]
[*]Get the list of Nvidia packages currently installed:```
dpkg -l  | grep nvidia
```
[*]Star purging the nvidia-* packages using this command:```
sudo apt-get purge nvidia-something
```
[*]Remove all packages separately except for these two:```
nvidia-cg-toolkit
nvidia-common
```
[*]Then reconfigure nvidia common:```
sudo dpkg-reconfigure nvidia-common
```
[*]At this point you can reboot, and you'll be using by default the Open Source driver (nouveau).
[*]Make sure you have your headers installed:```
sudo apt-get install linux-headers-generic
```
[*]Go to 'Additional drivers' and reinstall the recommend Nvidia driver from there.
[*]When finish, create a new X conf file:```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo nvidia-xconfig
```
[/LIST]
Now restart so that the Nvidia driver can take effect.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by hughcharlesparker on 2014-05-19
Thanks, and sorry it's been a week until I've found the time to look at this again.

I've tried your suggestions, as far as possible, but I can't get them to work.  I purged all of the nvidia- packages on the system.  neither nvidia-cg-toolkit or nvidia-common were installed.  I've tried with version 331.38 and version 304.117 of the proprietary drivers, but still the same result.

Any further suggestions, or should I give up and go back to 13.10?

---

### Post by papibe on 2014-05-19
Could you run this command and post back the results?
```
df -h

df -i
```
Regards.

---

### Post by hughcharlesparker on 2014-05-19
```
hugh@callimachus:~$ df -h
df: â/run/user/1001/gvfsâ: Permission denied
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        19G  5.1G   13G  29% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            991M  4.0K  991M   1% /dev
tmpfs           201M  1.3M  199M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1001M  468K 1001M   1% /run/shm
none            100M   36K  100M   1% /run/user
/dev/sda2       125G  4.7G  114G   4% /home
hugh@callimachus:~$ df -i
df: â/run/user/1001/gvfsâ: Permission denied
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/sda1      1250928 205892 1045036   17% /
none            256171      2  256169    1% /sys/fs/cgroup
udev            253479    512  252967    1% /dev
tmpfs           256171    538  255633    1% /run
none            256171      3  256168    1% /run/lock
none            256171      5  256166    1% /run/shm
none            256171     26  256145    1% /run/user
/dev/sda2      8273920  54745 8219175    1% /home
hugh@callimachus:~$
```

---

### Post by papibe on 2014-05-19
Thanks. That was in case you were runing out of space (happened to me once).

I would try to boot using the **nomodeset** option. Check the section 'How to temporarily set kernel boot options on an installed OS' in this [thread]("http://ubuntuforums.org/showthread.php?t=1613132") for details.

If that works, follow the steps on the next section (How to permanently set kernel boot options on an installed OS) in order to set the option for every subsequent boot.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by hughcharlesparker on 2014-05-19
I just tried that, with nomodeset set both on install of the restricted driver, and on reboot after install, and it doesn't seem to have made any difference at all.

---

### Post by papibe on 2014-05-19
Could you run this command and post the output?
```
lspci -nnk | grep -iA2 vga
```

At this point, we could try to  to upgrade both your Xorg and Nvidia driver to a more current versions using a well-known ppa.

Try this one first:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```
Then restart and see how it goes installing/updrading the nvidia-driver.

If that doesn't work either, there's another ppa with bleeding-edge versions:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```
Same idea.

Let us know how it goes.
Regards.

---

### Post by hughcharlesparker on 2014-05-21
```
hugh@callimachus:~$ lspci -nnk |grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT218 [ION] [10de:0a64] (rev a2)
        Subsystem: Acer Incorporated [ALI] Device [1025:047a]
01:00.1 Audio device [0403]: NVIDIA Corporation High Definition Audio Controller [10de:0be3] (rev a1)
```

I tried installing 331.38 again, but this time from ppa:ubuntu-x-swat/x-updates - no luck.

I then tried some drivers from ppa:xorg-edgers/ppa:
 - 331.67 - no luck
 - 337.19 - win!

Fantastic.  Thanks very much for your help.

It seems there's something fairly important wrong with the main repositories.  Do you think I should report a bug, or is it likely to have been reported already?

---

### Post by papibe on 2014-05-21
:) Glad you found a solution that works for you!

When you have the chance, please mark the thread as solved ([here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how).
> **hughcharlesparker said:**
> ...NVIDIA Corporation GT218 [ION] [10de:**[COLOR="#FF0000"]0a64[/COLOR]**]...
Do you think I should report a bug, or is it likely to have been reported already?

Yes. According to the docs provided by Nvidia (/usr/share/doc/nvidia-331/README.txt.gz), your card should be fully supported:
```
Appendix A. Supported NVIDIA GPU Products
...

A1. NVIDIA GEFORCE GPUS
    NVIDIA GPU product                    Device PCI ID*     VDPAU features
    ----------------------------------    ---------------    ---------------
    ...
    Second Generation ION                 **[COLOR="#FF0000"]0x0A64[/COLOR]**             C
```
I would file this bug against nvidia-331 on launchpad. Be sure to include the proper logs (the one you attached on post #1 ).
Regards.

---

### Post by hughcharlesparker on 2014-05-21
Done.  Thanks.

---

