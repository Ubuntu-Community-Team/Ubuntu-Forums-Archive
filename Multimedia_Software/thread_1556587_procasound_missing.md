---
title: "proc/asound missing"
date: 2010-08-19
forum: Multimedia Software
---

### Post by sylosis on 2010-08-19
I am having some trouble with my sound card and have found that in /proc there is now asound folder, anyone know why?

---

### Post by tjones00 on 2010-08-19
To check that alsa is installed.

```
cat /proc/asound/version
```

If it isn't installed install it.

```
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

If it's installed make sure your user is part of the group audio.

```
groups
```

If not add them.

```
sudo usermod -a -G audio username
```

You must logout/reboot in order for groups to be refreshed.

---

### Post by sylosis on 2010-08-19
did that and got this

```
damien@ubuntu:~$ cat /proc/asound/version
cat: /proc/asound/version: No such file or directory
damien@ubuntu:~$ sudo apt-get install linux-sound-base alsa-base alsa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-sound-base is already the newest version.
alsa-base is already the newest version.
alsa-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
damien@ubuntu:~$ groups
damien adm dialout cdrom audio plugdev lpadmin admin sambashare
damien@ubuntu:~$ sudo usermod -a -G audio damien
damien@ubuntu:~$ 



```

logged out and in and groups still displayed the same, as did cat: /proc/asound/version :(

---

### Post by tjones00 on 2010-08-19
Wow lol that's weird.

whats the output from 

sudo cat /proc/asound/version

try reinstalling it

sudo apt-get --reinstall install linux-sound-base alsa-base alsa-utils

reboot after the reinstall

---

### Post by sylosis on 2010-08-19
sudo cat /proc/asound/version gave this

```
damien@ubuntu:~$ sudo cat /proc/asound/version
[sudo] password for damien: 
cat: /proc/asound/version: No such file or directory

```

i reinstalled but it still gave the same output

---

### Post by tjones00 on 2010-08-19
Wow again.

So alsa is installed but it is not setting up any sound system.

What is the output from lspci? Perhaps your hardware isn't recognized as a sound card.

What type of soundcard is it?

Unfortunately this is beyond my noobish hack skills. You might need someone experienced in hardware probing.

---

### Post by sylosis on 2010-08-20
sound card is being recognised as it returns this

01:07.0 Multimedia audio controller: Creative Labs SB X-Fi

however, its not the easiest sound card to get working :/ thanks for trying anyways man :]

---

### Post by sylosis on 2010-08-20
anyone else got any ideas?

---

### Post by gerard187 on 2010-09-24
I'm having the the same problem and I have the the same sound card. Let me know if you resolve this.

---

### Post by darkscorp777 on 2010-10-02
Same problem here, however different sound card...:confused:

Edit: solved by using the [AlsaupgradeScript.sh]("http://ubuntuforums.org/showthread.php?p=6589810")
with the -d option first for downloading, then again with -c to compile then again with -i to install. All preceded by sudo.
Reboot and it worked!

---

### Post by Ewix on 2010-11-01
I've been tying long and hard to get my sound card to work. I didn't have a /proc/asound folder, even though I did install the alsa drivers.
I don't know exactly what I have tried along the way, but in the end the:

sudo apt-get --reinstall install linux-sound-base alsa-base alsa-utils

did the trick. Thanks!

Ubuntu 10.10 working on
Asus N53JN laptop

Audio:
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
        Subsystem: ASUSTeK Computer Inc. Device 1113
        Flags: bus master, fast devsel, latency 0, IRQ 48
        Memory at d9c00000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

---

### Post by dabraude on 2011-10-17
Hi I'm getting the same problem since updating to 11.10 with this hardware

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)


The script cannot run the compile part

edit:

I have now also tried purging to no success
there is no mention of my sound card or ALSA in /var/log/udev or dmesg
I have tried updating the ALSA kernal as per instructions found here: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
Just to add confusion when I run from the disk the audio works fine

---

### Post by Azriphale on 2011-10-18
I don't have any experience with this particular audio controller (or with 11.10).

Try reinstalling (if you removed them) the alsa packages:
$ sudo apt-get --reinstall install linux-sound-base alsa-base alsa-utils

And then try making sure the correct master channel is selected (and not muted) using alsamixer on the command line. Use <left> and <right> to move between items and press 'm' to mute/unmute. I have had problems before where after installation some controls are muted and this was all that was required to get things working.

If you want to use the alsa compiling script posted above, make sure you have build-essential installed: 
$ sudo apt-get install build-essential

I'm not sure I can be of much more help.

---

