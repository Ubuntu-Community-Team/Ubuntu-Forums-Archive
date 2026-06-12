---
title: "No Sound in Ubuntu 11.10"
date: 2011-10-22
forum: Multimedia Software
---

### Post by jpb3 on 2011-10-22
I recently had a problem with sound on my main account. The speaker icon on the upper right shows the speaker with --- after it, and when I would click on it I would have no option to mute/unmute and when I clicked on the slider to increase the volume the menu would simply disappear. I did not have any problems with the audio in a second account I created.
Due partly to this I decided to reinstall Ubuntu 11.10, and my audio worked fine, until this morning I mounted my /home to a separate ntfs partition, and now I have the same problem again.
I tried running through some of steps in the sticky thread and this is what I got:

aplay -l

**** List of PLAYBACK Hardware Devices ****
Home directory /home/jp not ours.
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

alsamixer
Home directory /home/jp not ours.
ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused

cannot open mixer: Connection refused

Any help would be appreciated.

---

### Post by atluxity on 2011-10-22
Have you checked if this matches problems in [http://ubuntuforums.org/showthread.php?t=1863271](http://ubuntuforums.org/showthread.php?t=1863271) ?

---

### Post by jpb3 on 2011-10-23
Yes I've looked at that thread and gone through many of the steps there but it has not helped, in fact it has made it worse. There was a link to remove and reinstall alsa and pulse, which I did, but it seems that all it did was remove the speaker icon from all of my profiles, although I still have audio in the second account, I just have to use pavcontrol. 

I've thought for awhile the problem is with pulse, so before I found out how to use apt-get to install pulse I was trying to install pulse1.1 manually from a .tar.xz file. After downloading several libraries I finally got ./configure to run all the way through but when I got to the end it said my dbus and udev were not enabled. Can anyone help me reenable them?

There are steps in this thread [http://ubuntuforums.org/showthread.php?t=1145446](http://ubuntuforums.org/showthread.php?t=1145446) but when I run it I get:
update-rc.d: warning: /etc/init.d/dbus missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/dbus already exist.

and when I open /etc/init.d/dbus it says
The owner of /home/jp/.config/ibus/bus is not jp!

So I think the problem must be that I switched the /home partition. Is it because the partition is ntfs? How can I make myself the owner of /home/jp/.config/ibus/bus ?



Also I have tried using [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS) to try to install the alsa-hda-dksm, but when I go to the launchpad I only see options for tar.gz and .dsc I chose to download the tar file and I have extracted it, but do not know how to install if from here, as it says there is no ./configure file and if I run make it stops at
 make: *** No rule to make target `/home/jp/Downloads/recipe-0.201110221135/buildroot/unpatched-source', needed by `patched-source'.  Stop.

---

