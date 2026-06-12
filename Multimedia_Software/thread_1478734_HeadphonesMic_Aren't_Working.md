---
title: "Headphones/Mic Aren't Working"
date: 2010-05-10
forum: Multimedia Software
---

### Post by JakeLawrence on 2010-05-10
The output of the code

```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```

is:

```
jake@jake-laptop:~$ uname -a
Linux jake-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
jake@jake-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jake@jake-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr 29 2010 for kernel 2.6.32-22-generic (SMP).
jake@jake-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Conexant CX20583 (Pebble HSF)

==> /proc/asound/card0/codec#2 <==
Codec: Intel G45 DEVCTG
```

I'm running a HP G60-507DX (AMD64).

I've already done sudo apt-get update and sudo apt-get upgrade (about a dozen times) and I've installed the alsa backports (sudo apt-get install linux-backports-modules-alsa-lucid-generic) and rebooted as well.

Thanks in advance for helping!

---

### Post by JackFlash79 on 2010-05-14
Try this post instructions by [Unreal223linux]("http://www.backports.ubuntuforums.org/member.php?u=321904"):  [http://www.backports.ubuntuforums.org/showthread.php?t=47342]("http://www.backports.ubuntuforums.org/showthread.php?t=473425")

I has also not having sound in my headphones and this  instructions worked perfectly  form me, for both 9.10 Karmic Koala and 10.04 LTS Lucid Lynxs
By the way I'm a noob.

This is my adaptation to the new alsa driver, all credits should go to [Unreal223linux]("http://www.backports.ubuntuforums.org/member.php?u=321904"):

Step one is you need the newest version of the alsa sound drivers. To do  that cut and paste each line of the below code box into the terminal  one at a time. Wait untill one function is done before pasting in the  next. The terminal is located in applications>  accessories>terminal.

```
sudo apt-get install build-essential linux-headers-$(uname -r)

wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2

tar -xjf alsa-driver-1.0.23.tar.bz2

cd alsa-driver-1.0.23

./configure

sudo make

sudo make install

```
Once through all of the commands reboot your computer.

-------------------

Once the computer is back up go back into the terminal and enter this:

```
sudo gedit /etc/modprobe.conf
```You will be prompted for your user account password. When you type it  will look like nothing is happening but thats just a security feature.

In the text file that pops up enter this and save it:

```
options snd-hda-intel model=6stack-digout
```Once saved reboot your computer

---------------------

Once your computer is back up go back into the terminal and enter

```
alsamixer
```Use the arrow keys to move around on this screen. On anything you see  double MM on press the M key and maximize the volume. Do this to  anything with the double MM.

Once you do your headphones should be working! Go to the volume control  panel and go to edit>preferences> and enable surround. From what I  have seen that is the one that adjusts your headphones.

Good luck!

---

