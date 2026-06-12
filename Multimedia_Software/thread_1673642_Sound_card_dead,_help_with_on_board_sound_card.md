---
title: "Sound card dead, help with on board sound card"
date: 2011-01-22
forum: Multimedia Software
---

### Post by wastelander on 2011-01-22
Ok so my sound card ceased to function a few days back, no sound.
I have kubuntu and XP installed.In XP i just installed the drivers of the onboard sound card (Realtek? - i have an MSI motherboard).
In Linux, erm, i might need some help to use the onboard sound card.
I'm attaching a screencap of Phonon.
In testing each device, no sound is played.
Help?

---

### Post by Zorael on 2011-01-23
Does any sound play if you enter '**speaker-test -twav -c2**' in a terminal?

Also, what is the terminal output of '**aplay -l**'?

---

### Post by wastelander on 2011-01-23
> Does any sound play if you enter '**speaker-test -twav -c2**' in a terminal?


Nope,no sound.

Here's (part of ) the output.It was taking a long time so i Ctrl-Z'd it.Should i leave it to finish?

```

$ speaker-test -twav -c2

speaker-test 1.0.23

Playback device is default
Stream parameters are 48000Hz, S16_LE, 2 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 96 to 1048576
Period size range from 32 to 349526
Using max buffer size 1048576
Periods = 4
was set period_size = 262144
was set buffer_size = 1048576
 0 - Front Left

 1 - Front Right
Time per period = 19.498057
 0 - Front Left
 1 - Front Right
Time per period = 19.518006
 0 - Front Left
 1 - Front Right
Time per period = 19.517154
 0 - Front Left
 1 - Front Right
Time per period = 19.521878
 0 - Front Left

 1 - Front Right
Time per period = 19.517433
 0 - Front Left
 1 - Front Right
Time per period = 19.517237
 0 - Front Left
 1 - Front Right
Time per period = 19.517494
 0 - Front Left
 1 - Front Right
Time per period = 19.517341
 0 - Front Left                                                                                         
 1 - Front Right                                                                                        
Time per period = 19.517404                                                                             
 0 - Front Left                                                                                         
 1 - Front Right                                                                                        
Time per period = 19.517983                                                                             
 0 - Front Left
 1 - Front Right
Time per period = 19.517807
 0 - Front Left
 1 - Front Right
Time per period = 19.517319
 0 - Front Left
 1 - Front Right
Time per period = 19.517932
 0 - Front Left
 1 - Front Right
Time per period = 19.518295
 0 - Front Left
 1 - Front Right
Time per period = 19.516580
 0 - Front Left
 1 - Front Right
Time per period = 19.525049
 0 - Front Left
^Z
[1]+  Stopped                 speaker-test -twav -c2


```
> Also, what is the terminal output of '**aplay -l**'?```

:~$ aplay -l
aplay: device_list:235: no soundcards found...

```

---

### Post by wastelander on 2011-01-26
Any help?
Here's the audio - related output of lspci -v
```

$ lspci -v | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
05:02.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster


```
Soundblaster is dead,i want to install the 1st.

---

### Post by Zorael on 2011-01-26
I'm not entirely sure what to do when it's not loading the driver. You could try grepping the output of dmesg for alsa, or sound, or something - and see if there are any error messages.

And speaker-test needs to be interrupted/terminated to end, yes. If the Soundblaster card is truly dead, it may make things easier if you just physically remove it from your machine.

Googling Intel 82801I, I find [this page](http://www.thinkwiki.org/wiki/Intel_82801I_HDA), but I'm not sure if merely going by the 82801I chipset is enough to know if it matches your card. Is it listed as having the pci identifier **8086:293e**?

```
$ lspci -vnns 00:1b.0
```

I really doubt this will actually help though, but it can't hurt to try.

> **[SIZE="3"]Intel High Definition Audio[/SIZE]**
Intel audio controller embedded with the 82801I chipset ( ICH9 chipset )

**[SIZE="3"]Features[/SIZE]**
Chipset: 82801I
Interface: PCIe
PCI ID: 8086:293e

**[SIZE="3"]Linux ALSA driver[/SIZE]**
This sound chip is supported by the snd-hda-intel kernel module, even though it is not listed on the [Alsa Driver Page](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel).

**[SIZE="3"]Ubuntu[/SIZE]**
On Ubuntu 8.10, the following line needs to be added to **/etc/modprobe.d/alsa-base**:
```
 options snd-hda-intel enable_msi=1
```

---

### Post by wastelander on 2011-01-27
```
$ options snd-hda-intel enable_msi=1
options: command not found
```


```
$ lspci -vnns 00:lb.0
lspci: -s: Invalid slot number
```

and dmseg sound,alsa, returns nothing

Dammit.I"ll remove the dead card and see what happens.

---

### Post by lidex on 2011-01-27
Use this command to make that edit. 
```
echo "options snd-hda-intel enable_msi=1" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

No joy? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by wastelander on 2011-03-29
Been away...Should i open a new thread? Anyway:
Here's the error-rich output.
```

~$ wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
--2011-03-30 06:25:43--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org... 77.48.224.243
Connecting to www.alsa-project.org|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh [following]
--2011-03-30 06:25:43--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to www.alsa-project.org:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [  <=>                                                                                                           ] 27,247      72.9K/s   in 0.4s    

2011-03-30 06:25:44 (72.9 KB/s) - `alsa-info.sh' saved [27247]

ALSA Information Script v 0.4.60
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

cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/modules: No such file or directory
ls: cannot access /dev/snd/*: No such file or directory
grep: /proc/asound/cards: No such file or directory                                                                                                      
/sbin/alsactl: save_state:1504: No soundcards found...                                                                                                   
cat: /tmp/alsa-info.dcLWvdAjoY/alsactl.tmp: No such file or directory                                                                                    
Automatically upload ALSA information to www.alsa-project.org? [y/N] : y                                                                                 
Uploading information to www.alsa-project.org ...  Done!                                                                                                 

Your ALSA information is located at http://www.alsa-project.org/db/?f=c8d3778771bee71afb122f454781591b05f61bc7
                                                                                                                                                         
Please inform the person helping you.




```
And here's the link

[http://www.alsa-project.org/db/?f=c8d3778771bee71afb122f454781591b05f61bc7](http://www.alsa-project.org/db/?f=c8d3778771bee71afb122f454781591b05f61bc7)

---

### Post by lidex on 2011-03-29
Your alsa install needs help. 
Using a Terminal:
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

---

### Post by wastelander on 2011-03-30
^

That did it!
A million thanks!

---

### Post by lidex on 2011-03-31
You're welcome. Please mark thread solved using 'Thread Tools' up top.

---

### Post by wastelander on 2011-04-01
okie

---

