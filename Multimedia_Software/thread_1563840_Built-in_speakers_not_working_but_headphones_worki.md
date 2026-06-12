---
title: "Built-in speakers not working but headphones working"
date: 2010-08-29
forum: Multimedia Software
---

### Post by mainak_sen on 2010-08-29
BACKGROUND (before running ALSA Upgrade Script):

Running Ubuntu Linux, the Ubuntu 10.04 (lucid) release.
	GNOME: 2.30.2 (Ubuntu 2010-06-25)
	Kernel version: 2.6.32-24-generic (#41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010)
	GCC: 4.4.3 (i486-linux-gnu)
	Xorg: unknown (21 July 2010  12:47:34PM) (21 July 2010  12:47:34PM)

Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
        Subsystem: Hewlett-Packard Company Device 1425
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at 94400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

This is in a brand new Compaq Presario CQ62 laptop, with a fresh install of Lucid. Everything was working fine except that there was NO SOUND from the built-in speakers but, SOUND WAS OK in headphones. I followed the advice from lidex (post #9 and post #16) in this link [http://ubuntuforums.org/showthread.php?t=1478602](http://ubuntuforums.org/showthread.php?t=1478602)
and was led to the ALSA Upgrade script thread 
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)


I have tried the ALSA upgrade script procedure 3-4 times and also with lidex's advice in post #13 of this thread [http://ubuntuforums.org/showthread.php?t=1531672&highlight=no+sound+from+speakers+but+headphones+work&page=2](http://ubuntuforums.org/showthread.php?t=1531672&highlight=no+sound+from+speakers+but+headphones+work&page=2)

CURRENT PROBLEM: AFTER running the ALSA Upgrade Script as per instructions in the respective thread in my laptop (Compaq Presario CQ62) the sound is completely broke... no sound from built-in speakers and/or headphones.

I am getting the following:

pkr@pkr-laptop:~$ cat /proc/asound/version
cat: /proc/asound/version: No such file or directory
pkr@pkr-laptop:~$ aplay -l
aplay: device_list:223: no soundcards found...
pkr@pkr-laptop:~$

Also, if I do System > Preferences > Sound
then Sound Preferences shows no hardware under the Hardware tab, and under the Output Tab, it shows "Dummy Output Stereo".

The latest (ALSA Update Script) log files are attached.

I shall greatly appreciate any help!

Thanks in advance.

PS: I have also posted this as a reply to the ALSA Update Script thread at
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)
for the sake of relevance.

---

### Post by lidex on 2010-08-29
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by mainak_sen on 2010-08-30
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

Thank you lidex for your continued support!

I have done what you asked for and uploaded the ALSA information. Here is the link:

[http://www.alsa-project.org/db/?f=6e966578a8b725f721e11ddb64631e454e7f5155](http://www.alsa-project.org/db/?f=6e966578a8b725f721e11ddb64631e454e7f5155)

Kindly advise. 

Thanks!

PS: I don't know if it made any difference but I was NOT asked for any passwords. But, it could be also because I used 'sudo' just before I used the command that you provided.

---

### Post by lidex on 2010-08-30
The upgrade did not work and alsa is broken. Try this. Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

---

### Post by mainak_sen on 2010-08-31
> **lidex said:**
> The upgrade did not work and alsa is broken. Try this. Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

Thanks for the response.

Well, I actually tried this even before I started this thread. The last time I sent you the Alsa-info, that was AFTER I tried it.

Anyway, as per your suggestion I tried this again. Expectedly perhaps, I have the same result...it is still broken. I ran the info script again and have uploaded the info link to
[http://www.alsa-project.org/db/?f=0058487d2078af8416a0dbf623f69efe20feaff3](http://www.alsa-project.org/db/?f=0058487d2078af8416a0dbf623f69efe20feaff3)

Please let me know what else I can try...

Thank you!

---

### Post by lidex on 2010-08-31
OK. Boot into a lower numbered kernel and use synaptic to re-install kernel and headers for 2.6.32-24. When that's done, reboot into the 2.6.32-24 kernel and post the output of these commands: ```
uname -a
aplay -l
dpkg -l | grep "alsa"

```

If you have alsa-backports installed, remove that first.

---

### Post by mainak_sen on 2010-08-31
> **lidex said:**
> OK. Boot into a lower numbered kernel and use synaptic to re-install kernel and headers for 2.6.32-24. When that's done, reboot into the 2.6.32-24 kernel and post the output of these commands: ```
uname -a
aplay -l
dpkg -l | grep "alsa"

```

If you have alsa-backports installed, remove that first.

I tried all that you suggested...but no luck :(

I did not have any backports installed. So I re-installed the kernels and headers as per your suggestion using synaptic:

> linux-headers-2.6.32-24 (version 2.6.32-24.41) will be re-installed
linux-headers-2.6.32-24-generic (version 2.6.32-24.41) will be re-installed
linux-image-2.6.32-24-generic (version 2.6.32-24.41) will be re-installed


and then rebooted. 
The output of the commands that you requested are:

> pkr@pkr-laptop:~$ uname -a
Linux pkr-laptop 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 i686 GNU/Linux
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ aplay -l
aplay: device_list:223: no soundcards found...
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-firmware-loaders                1.0.22-0ubuntu1                                 ALSA software loaders for specific hardware
ii  alsa-oss                             1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-source                          1.0.22.1+dfsg-0ubuntu3                          ALSA driver sources
ii  alsa-tools                           1.0.22-0ubuntu1                                 Console based ALSA utilities for specific ha
ii  alsa-tools-gui                       1.0.22-0ubuntu1                                 GUI based ALSA utilities for specific hardwa
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
pkr@pkr-laptop:~$





Being uncertain if I got all the necessary packages that you meant or not...i tried it again:

> linux-generic (version 2.6.32.24.25) will be re-installed
linux-headers-2.6.32-24 (version 2.6.32-24.41) will be re-installed
linux-headers-2.6.32-24-generic (version 2.6.32-24.41) will be re-installed
linux-headers-generic (version 2.6.32.24.25) will be re-installed
linux-image-2.6.32-24-generic (version 2.6.32-24.41) will be re-installed


and on running the commands that you asked...still exactly the same output as before (as quoted just above).

I also repeated your suggestions in your posts #4 and #2 earlier in this current thread...still same problem.

The latest info is in
[http://www.alsa-project.org/db/?f=9aca81e21529b82eeff5df2386a230aac6785761](http://www.alsa-project.org/db/?f=9aca81e21529b82eeff5df2386a230aac6785761)

Please advise. 
If you feel that it will be easier and/or quicker to just re-install Lucid and then try once more the ALSA update to solve the speaker problem, please let me know.

Thank you for your continued support!

---

### Post by lidex on 2010-08-31
Did you switch to OSS at some point?

```
dpkg -l | grep "OSS"
```

---

### Post by mainak_sen on 2010-09-01
> **lidex said:**
> Did you switch to OSS at some point?

```
dpkg -l | grep "OSS"
```

I do not really remember...
Here is the output:

```
pkr@pkr-laptop:~$ dpkg -l | grep "OSS"
ii  alsa-oss                             1.0.17-3                                        ALSA wrapper for OSS applications
ii  linux-sound-base                     1.0.22.1+dfsg-0ubuntu3                          base package for ALSA and OSS sound systems
pkr@pkr-laptop:~$
```

Let me know if this means anything...and what to try?

Thanks!

---

### Post by lidex on 2010-09-01
I may have missed something here. You need to re-install 2.6.32-24-generic #42, you're re-installing .41 and .25

---

### Post by mainak_sen on 2010-09-02
> **lidex said:**
> I may have missed something here. You need to re-install 2.6.32-24-generic #42, you're re-installing .41 and .25

Thanks. I did this allover again...after booting into s lower version kernel.

> linux-headers-2.6.32-24 (version 2.6.32-24.42) will be re-installed
linux-headers-2.6.32-24-generic (version 2.6.32-24.42) will be re-installed
linux-image-2.6.32-24-generic (version 2.6.32-24.42) will be re-installed


Then I rebooted. And ran the commands that you requested:

```
pkr@pkr-laptop:~$ uname -a
Linux pkr-laptop 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 i686 GNU/Linux
pkr@pkr-laptop:~$ uname -a
Linux pkr-laptop 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 i686 GNU/Linux
pkr@pkr-laptop:~$ aplay -l
aplay: device_list:223: no soundcards found...
pkr@pkr-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-firmware-loaders                1.0.22-0ubuntu1                                 ALSA software loaders for specific hardware
ii  alsa-oss                             1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-source                          1.0.22.1+dfsg-0ubuntu3                          ALSA driver sources
ii  alsa-tools                           1.0.22-0ubuntu1                                 Console based ALSA utilities for specific ha
ii  alsa-tools-gui                       1.0.22-0ubuntu1                                 GUI based ALSA utilities for specific hardwa
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
pkr@pkr-laptop:~$ dpkg -l | grep "OSS"
ii  alsa-oss                             1.0.17-3                                        ALSA wrapper for OSS applications
ii  linux-sound-base                     1.0.22.1+dfsg-0ubuntu3                          base package for ALSA and OSS sound systems
pkr@pkr-laptop:~$ dpkg -l | grep "OSS"
ii  alsa-oss                             1.0.17-3                                        ALSA wrapper for OSS applications
ii  linux-sound-base                     1.0.22.1+dfsg-0ubuntu3                          base package for ALSA and OSS sound systems
pkr@pkr-laptop:~$ clear

pkr@pkr-laptop:~$ uname -a
Linux pkr-laptop 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 i686 GNU/Linux
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ aplay -l
aplay: device_list:223: no soundcards found...
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-firmware-loaders                1.0.22-0ubuntu1                                 ALSA software loaders for specific hardware
ii  alsa-oss                             1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-source                          1.0.22.1+dfsg-0ubuntu3                          ALSA driver sources
ii  alsa-tools                           1.0.22-0ubuntu1                                 Console based ALSA utilities for specific ha
ii  alsa-tools-gui                       1.0.22-0ubuntu1                                 GUI based ALSA utilities for specific hardwa
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ dpkg -l | grep "OSS"
ii  alsa-oss                             1.0.17-3                                        ALSA wrapper for OSS applications
ii  linux-sound-base                     1.0.22.1+dfsg-0ubuntu3                          base package for ALSA and OSS sound systems
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ 

```

...so still the same problem.

I re-ran the ALSA info script...here is the link
[http://www.alsa-project.org/db/?f=a7afce2a3652091cf44a768bc6180023fab2b40d](http://www.alsa-project.org/db/?f=a7afce2a3652091cf44a768bc6180023fab2b40d)

Please advise.

Thanks again!

---

### Post by lidex on 2010-09-02
OK. Try removing some unneeded pkgs.
```
sudo apt-get purge alsa-firmware-loaders alsa-oss alsa-source alsa-tools alsa-tools-gui bluez-alsa
```
**Reboot**
Now re-install alsa:
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**

---

### Post by mainak_sen on 2010-09-02
> **lidex said:**
> OK. Try removing some unneeded pkgs.
```
sudo apt-get purge alsa-firmware-loaders alsa-oss alsa-source alsa-tools alsa-tools-gui bluez-alsa
```
**Reboot**
Now re-install alsa:
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**

Tried as per your advice. But still the problem remains!

The very last step automatically re-installed bluez-alsa:

```
pkr@pkr-laptop:~$ sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gdm is already the newest version.
The following packages were automatically installed and are no longer required:
  debhelper linux-headers-2.6.32-21 intltool-debian po-debconf debconf-utils libmail-sendmail-perl gettext linux-headers-2.6.32-21-generic cvs html2text fxload
  libsys-hostname-long-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  **bluez-alsa**
Suggested packages:
  apmd alsa-oss oss-compat
The following NEW packages will be installed:
  alsa-base alsa-utils bluez-alsa linux-sound-base ubuntu-desktop
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 41.4kB/1,464kB of archives.
After this operation, 2,925kB of additional disk space will be used.
Do you want to continue [Y/n]? 



```

I am still getting:

```
pkr@pkr-laptop:~$ uname -a
Linux pkr-laptop 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 i686 GNU/Linux
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ aplay -l
aplay: device_list:223: no soundcards found...
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ 

```

The latest alsa-info is at

[http://www.alsa-project.org/db/?f=55fbd28abc998527c4db94dbed407ce3dad3ff1c](http://www.alsa-project.org/db/?f=55fbd28abc998527c4db94dbed407ce3dad3ff1c)

Please advise!

TIA

---

### Post by lidex on 2010-09-02
OK. I am at a loss. If you are still willing to re-install ubuntu then please do. Hopefully that will get you back to a working configuration that we can then tweak to fix your speaker output.

---

### Post by mainak_sen on 2010-09-07
> **lidex said:**
> OK. I am at a loss. If you are still willing to re-install ubuntu then please do. Hopefully that will get you back to a working configuration that we can then tweak to fix your speaker output.

Thanks lidex. I was away and hence the delay...

I have reinstalled Lucid. Expectedly, I am back at where I started...there is no sound from the built-in speakers but headphones and external speakers work fine.

Here is the current info:

```
pkr@pkr-laptop:~$ uname -a
Linux pkr-laptop 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 i686 GNU/Linux
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ 
pkr@pkr-laptop:~$ 



```

I have run the alsa-info script again and uploaded the latest file here:

[http://www.alsa-project.org/db/?f=5995f14f953a0c7ce9545202d04c14b3d70eb3ba](http://www.alsa-project.org/db/?f=5995f14f953a0c7ce9545202d04c14b3d70eb3ba)

Please let me know what is your advise now so that I can get the speakers working.

TIA

---

### Post by mainak_sen on 2010-09-09
Please help!

---

### Post by lidex on 2010-09-15
Now try the alsa-upgrade script. Use the link in my sig.

---

### Post by ForrestB on 2011-05-09
Hey I am having a similar problem.  No sound from speakers but sound from headphones.  

So far I have done the following:   1. Check all obvious sound controllers, non that a know of are one mute
 2: Upgraded ALSA a number of times via the terminal.   
3. Reinstalled Ubuntu (this problem started in 10.04 and I though that If installed 11.04 it would all be ok, but so far no.    So now i'm reinstalling 10.04

This problem has been persistant, it used to happen periodically, (speaker failure but heaphones ok) then I would re-run the ALSA upgrade script and It would work again, but that hasn't worked this time.

Any help would be great.  i have an HP-Compaq 320 Notebook
Thanks

---

### Post by lidex on 2011-05-10
> **ForrestB said:**
> Hey I am having a similar problem.  No sound from speakers but sound from headphones.  

So far I have done the following:   1. Check all obvious sound controllers, non that a know of are one mute
 2: Upgraded ALSA a number of times via the terminal.   
3. Reinstalled Ubuntu (this problem started in 10.04 and I though that If installed 11.04 it would all be ok, but so far no.    So now i'm reinstalling 10.04

This problem has been persistant, it used to happen periodically, (speaker failure but heaphones ok) then I would re-run the ALSA upgrade script and It would work again, but that hasn't worked this time.

Any help would be great.  i have an HP-Compaq 320 Notebook
Thanks

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

