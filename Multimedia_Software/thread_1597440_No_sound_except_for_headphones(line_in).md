---
title: "No sound except for headphones(line in)"
date: 2010-10-15
forum: Multimedia Software
---

### Post by Dan9996 on 2010-10-15
Hi, I completely new to Ubuntu did a first time Install (Dual Boot) on Dell OptiPlex GX620 (old business type computer) I have no sound on the internal speakers but when I plug-in something in the headphone jack the sound is blaring! 

I really like Ubuntu, but this problem is annoying me.
Any help would be greatly appreciated!

---

### Post by .... on 2010-10-15
Check your volumes in alsamixer (you may need to install alsamixer, I forget). Make sure nothing's muted (and you can turn down your headphones if you wish).
```
alsamixer
```

---

### Post by Dan9996 on 2010-10-15
I tried alsamixer it but it didn't work... headphones turned down a bit though....:)

---

### Post by TBABill on 2010-10-15
Did you actually have a setting in alsamixer for speaker? Sometimes that is missing or muted and causes a problem. If it's missing then it is a configuration issue similar to what I have on an HP Touchsmart. It uses the Intel HD for sound and I have to add a line to my alsa-base.conf file to get it to recognize that card every time I install or upgrade any Linux distro.

---

### Post by Dan9996 on 2010-10-16
> **TBABill said:**
> Did you actually have a setting in alsamixer for speaker? Sometimes that is missing or muted and causes a problem. If it's missing then it is a configuration issue similar to what I have on an HP Touchsmart. It uses the Intel HD for sound and I have to add a line to my alsa-base.conf file to get it to recognize that card every time I install or upgrade any Linux distro.

You are CORRECT! :P But how do I edit the alsa-base.conf file:confused:?

---

### Post by lidex on 2010-10-16
> **Dan9996 said:**
> You are CORRECT! :P But how do I edit the alsa-base.conf file:confused:?

First, what do you have? 
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by Dan9996 on 2010-10-17
```
Linux ubuntu 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:05:27 UTC 2010 x86_64 GNU/Linux

```

```
card 0: ICH7 [Intel ICH7], device 0: Intel ICH [Intel ICH7]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH7 [Intel ICH7], device 4: Intel ICH - IEC958 [Intel ICH7 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA

```
```
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

```

---

### Post by lidex on 2010-10-17
Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by Dan9996 on 2010-10-18
> **lidex said:**
> Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

One Question, I have speakers that are plugged in through the headphone jacks and the sound is fine (better than the internal speakers). Should I still update the Driver modules?

---

### Post by lidex on 2010-10-19
> **Dan9996 said:**
> One Question, I have speakers that are plugged in through the headphone jacks and the sound is fine (better than the internal speakers). Should I still update the Driver modules?

Yes.

---

### Post by Dan9996 on 2010-10-19
> **lidex said:**
> Yes.
```
[sudo] password for dan: 
Sorry, try again.
[sudo] password for dan: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 4E9F485BF943EF0EABA10B5BD225991A72B194E5
gpg: requesting key 72B194E5 from hkp server keyserver.ubuntu.com
gpg: key 72B194E5: public key "Launchpad Ubuntu Audio Dev team PPA" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
dan@ubuntu:~$ sudo apt-get install linux-alsa-driver-modules-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-alsa-driver-modules-2.6.32-25-generic

```
I got the error message^

---

### Post by lidex on 2010-10-20
> **Dan9996 said:**
> ```
[sudo] password for dan: 
Sorry, try again.
[sudo] password for dan: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 4E9F485BF943EF0EABA10B5BD225991A72B194E5
gpg: requesting key 72B194E5 from hkp server keyserver.ubuntu.com
gpg: key 72B194E5: public key "Launchpad Ubuntu Audio Dev team PPA" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
dan@ubuntu:~$ sudo apt-get install linux-alsa-driver-modules-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-alsa-driver-modules-2.6.32-25-generic

```
I got the error message^

Probably no alsa-modules available for that kernel. What is this output:
```
head -1 /proc/asound/card0/codec97#0/ac97#0-0 
```

---

### Post by Dan9996 on 2010-10-22
> **lidex said:**
> Probably no alsa-modules available for that kernel. What is this output:
```
head -1 /proc/asound/card0/codec97#0/ac97#0-0 
```

```
0-0/0: Analog Devices AD1981B
```

---

### Post by lidex on 2010-10-22
I apologize - should have asked for this at first. If you would please use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Dan9996 on 2010-10-23
> **lidex said:**
> I apologize - should have asked for this at first. If you would please use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```**Choose the upload option and provide a link for the output.**
[Terminal="Applications->Accessories->Terminal"]
Pardon me?
```
dan@ubuntu:~$ wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
--2010-10-23 13:22:55--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org... 212.20.107.51
Connecting to www.alsa-project.org|212.20.107.51|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh [following]
--2010-10-23 13:22:55--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh
Resolving git.alsa-project.org... 212.20.107.51
Reusing existing connection to www.alsa-project.org:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [  <=>                                  ] 27,026      74.2K/s   in 0.4s    

2010-10-23 13:22:56 (74.2 KB/s) - `alsa-info.sh' saved [27026]

ALSA Information Script v 0.4.59
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

Newer version detected: 
To view the ChangeLog, please visit http://www.alsa-project.org/alsa-info.sh.changelog
The original file alsa-info.sh will be overwritten!
If you do not like to proceed, press Ctrl-C now..

```What am I supposed to do?
I hit enter then got this
```
ALSA-Info script has been updated. Please re-run it.
```Should I re-run this script?```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```?

---

### Post by lidex on 2010-10-24
Interesting. I just tried it and it ran without a hitch. You must have an older version already downloaded. V. 0.4.59 has been out since Feb.

Try deleting the file 'alsa-info.sh' from your user folder and run it again. If you get the same result just run this command:
```
bash alsa-info.sh
```

---

