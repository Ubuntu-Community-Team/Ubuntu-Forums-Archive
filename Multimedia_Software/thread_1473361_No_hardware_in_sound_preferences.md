---
title: "No hardware in sound preferences"
date: 2010-05-05
forum: Multimedia Software
---

### Post by zeezam on 2010-05-05
Got this after upgrade to 10.04.
I have before manually upgraded the pulseaudio driver. Can that have something to do with it?

---

### Post by lidex on 2010-05-06
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by zeezam on 2010-05-06
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux

Advanced Linux Sound Architecture Driver Version 1.0.21.

Codec: VIA VT1708S

It's a desktop that I have built. Built in HDA Intel ADA ATI SB audio.

---

### Post by lidex on 2010-05-06
What is the output of:
```
aplay -l
```

---

### Post by zeezam on 2010-05-07
> **lidex said:**
> What is the output of:
```
aplay -l
```

aplay -l
aplay: device_list:223: no soundcards found...

---

### Post by lidex on 2010-05-08
OK. Update your kernel:
```
sudo apt-get update
sudo apt-get upgrade
```
Now reboot so we can work with the latest kernel.
Install alsa backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Reboot again.

Do 'Part A' here:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by zeezam on 2010-05-10
> **lidex said:**
> OK. Update your kernel:
```
sudo apt-get update
sudo apt-get upgrade
```
Now reboot so we can work with the latest kernel.
Install alsa backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Reboot again.

Do 'Part A' here:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

Done that. When I did Part A in the guide there were many files that didn't exist...

$ pulseaudio & pavucontrol
[1] 2716
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

---

### Post by lidex on 2010-05-11
Try this:
```
sudo apt-get install pulseaudio-esound-compat esound-clients esound-common
```
Restart

---

### Post by zeezam on 2010-05-12
> **lidex said:**
> Try this:
```
sudo apt-get install pulseaudio-esound-compat esound-clients esound-common
```
Restart

$ sudo apt-get install pulseaudio-esound-compat esound-clients esound-common
[sudo] password for johnny: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pulseaudio-esound-compat is already the newest version.
esound-clients is already the newest version.
esound-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.

---

### Post by Mujaheiden on 2010-06-03
We're on 9.10 and have and sound hardware keeps on disapearing.

$ aplay -l gives
```
**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: modem [VIA 82XX modem], device 0: VIA 82XX modem [VIA 82XX modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


I have all the suggested applications installed.

---

### Post by lidex on 2010-06-04
> **Mujaheiden said:**
> We're on 9.10 and have and sound hardware keeps on disapearing.

$ aplay -l gives
```
**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: modem [VIA 82XX modem], device 0: VIA 82XX modem [VIA 82XX modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


I have all the suggested applications installed.

What is the output of this command:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

Try this: ```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

---

### Post by Mujaheiden on 2010-06-05
ej my mistake, i was confused by all the audio preset, i initially didnt see the stereo duplex at the bottom of the prests list, so I selected some dolby duplex, which crashed after a few minutes. rebooting and selecting a decent preset makes everything okay. Thanks!

---

### Post by dfreelan on 2010-09-04
i'm on 10.4 having the same problem, i get a different output for 
aplay -l

**** List of PLAYBACK Hardware Devices ****
ALSA lib conf.c:594:(get_char_skip_comments) Cannot access file /home/freelan/.asoundrc.asoundconf
ALSA lib conf.c:1645:(snd_config_load1) _toplevel_:5:36:No such file or directory
ALSA lib conf.c:3425:(snd_config_hook_load) /home/freelan/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:3286:(snd_config_hooks_call) function snd_config_hook_load returned error: No such file or directory
ALSA lib conf.c:3671:(snd_config_update_r) hooks failed, removing configuration
aplay: device_list:232: control open (0): No such file or directory

---

### Post by lidex on 2010-09-04
> **dfreelan said:**
> i'm on 10.4 having the same problem, i get a different output for 
aplay -l

**** List of PLAYBACK Hardware Devices ****
ALSA lib conf.c:594:(get_char_skip_comments) Cannot access file /home/freelan/.asoundrc.asoundconf
ALSA lib conf.c:1645:(snd_config_load1) _toplevel_:5:36:No such file or directory
ALSA lib conf.c:3425:(snd_config_hook_load) /home/freelan/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:3286:(snd_config_hooks_call) function snd_config_hook_load returned error: No such file or directory
ALSA lib conf.c:3671:(snd_config_update_r) hooks failed, removing configuration
aplay: device_list:232: control open (0): No such file or directory

Try this: ```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.
Now run alsa-info script.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by dfreelan on 2010-09-05
Thanks for the help!

when I run the second remove statement i get
rm: cannot remove `/etc/asound.conf': No such file or directory

I should add that previously, i made an attempt to solve the problem, I had reinstalled everything alsa, and pulseaudio that was already installed on my system.

Error link below
Link: [URL="http://www.alsa-project.org/db/?f=608f1ba86ba100aae0f608d61edc1042088249db"]http://www.alsa-project.org/db/?f=608f1ba86ba100aae0f608d61edc1042088249db
[/URL] Thanks again!

EDIT: updated link

---

### Post by lidex on 2010-09-05
Use nautilus. Go to ~/ (your home folder) and look for anything starting with .asoundrc and delete it. Now reboot.
Next. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=ref 
```
Save. Close. Reboot. 
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

### Post by dparla on 2010-09-05
> **lidex said:**
> OK. Update your kernel:
```
sudo apt-get update
sudo apt-get upgrade
```Now reboot so we can work with the latest kernel.
Install alsa backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Reboot again.

Do 'Part A' here:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
I resolved my issue with the code you gave in this post. Thanks!:D

---

### Post by dfreelan on 2010-09-05
I followed the instructions, there was no (visible?).soundrc in my home folder (so i don't know why it was looking for it) but i ran rm /home/asound.rc, just to be sure.
Also i deleted the pulseaudio backup file i stored in there

I inserted the line of code successfully to the bottom of the file
went to the alsamixer, it appears everything was on full volume, pressed F3, no playback though...

 in sound preferences nothing was muted, and the hardware existed (and it exists as analog stereo duplex (1 output/1input))yay!!!

Good news: I can record stuff, the mic input shows it is receiving sound

However, I still have no playback, tried several sound file types. I tried to change the profile of the selected device to other options, but still no sound.

I tried to do research to see if i could find someone else who had the same problem, found nothing

Thanks for the help you have given me! 

I ran that link again in case it's useful
[http://www.alsa-project.org/db/?f=1fcb61f7609471a1e97074086f1a16ae70385749](http://www.alsa-project.org/db/?f=1fcb61f7609471a1e97074086f1a16ae70385749)

(P.S.) since my hardware is now showing up, does this actually qualify as a separate issue?

EDIT: also, when i insert my logitech headset, the computer freezes...

---

### Post by lidex on 2010-09-05
Getting there!
Run this command:
```
dpkg -l | grep "alsa"
```
If the output shows you have backports installed, please remove it from your system using synaptic. Then follow the alsa upgrade link in my sig to get the full 1.0.23

---

### Post by dfreelan on 2010-09-05
with the steps followed the mic still works, sound appears to have the same situation

When i run alsamixer, it doesnt show up in sound preferences under 'applications', however the "sound recorder" does (EDIT): the sound recorder appears both when recording and when playing what it recorded. Alsamixer shows my card is the one being used

let me know if you can still help or if u can direct me where to go 
Thanks again!

(here's the up to date link if it helps)
[http://www.alsa-project.org/db/?f=4c42b0c2c9e40ab91ce58d923fc1117850d7b180](http://www.alsa-project.org/db/?f=4c42b0c2c9e40ab91ce58d923fc1117850d7b180) 

EDIT: same problem is resent with logitech headphones, except the computer never completely  freezes. justs slows down to the point where nothing opens. Mouse remains active... i dont know if this helps at all >.<

I REALLY appreciate all help :-)

EDIT: next post has more information

---

### Post by dfreelan on 2010-09-06
I tried some of the troubleshooting on the upgrade site

typing "aplay" in the terminal does not do anything at all

Also when testing the soundcard with 
$ speaker-test -Dplughw:X,0 -c2
where X is my soundcard, leads the error
"Playback open error: -16,Device or resource busy"

double checked to make sure nothing was muted ;)

---

### Post by lidex on 2010-09-06
Click on the pulseaudio link in my sig. Follow the steps there to make sure it's set up correctly. But first post this output:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

---

### Post by dfreelan on 2010-09-06
Output:

$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  freelan    2499 F.... pulseaudio

---

### Post by dfreelan on 2010-09-06
Alright!

All instructions followed however I should note there were no instructions for "lucid linux" so I just used the instructions for the next most recent-- and did Section A  

no sound still.  

the install appears to be successful, i say this because in "pulse audio volume control" The application does plays audio and does list an entry in the Playback tab upon using an application playing audio.

Thanks again for the help!

and just in case it's useful
 [http://www.alsa-project.org/db/?f=1826e573c14556694d569182fba1b0b247fd353b](http://www.alsa-project.org/db/?f=1826e573c14556694d569182fba1b0b247fd353b)

---

### Post by dfreelan on 2010-09-08
IT'S FIXED!!!!!!!!!!!!!!!!!!!!

I changed the alsa-base.conf line you told me to change from 
options snd-hda-intel model=ref
to[FONT=Verdana]
[/FONT]options snd-hda-intel model=auto

and it worked!!!! victory!

Thanks so much for the help!

EDIT: Logitech headset still freezes computer, posted on unsolved thread [http://www.ubuntuforums.org/showthread.php?p=9803378]("http://gutsywww.ubuntuforums.org/showthread.php?p=9803378")
Also, google voice doesnt seem to recognize that i have its package installed, didnt happen before i updated to 10.04, likely unrelated

---

### Post by starrtennis on 2011-02-22
Hi. I have the same issue: Audio emits from my laptop speakers, but no devices or hardware are listed under system>preferences>sound.

I'm running lucid, as well. 10.04.

My alsa info:
[http://www.alsa-project.org/db/?f=9c89dd2d513093ab001cf06ca20fc2cbdd7b71b7](http://www.alsa-project.org/db/?f=9c89dd2d513093ab001cf06ca20fc2cbdd7b71b7)

I tried installing pulseaudio but it gave me some errors and I think the install failed:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a pax tar archive... gnutar
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gcc option to accept ISO C99... -std=gnu99
checking whether gcc -std=gnu99 and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -std=gnu99 -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking whether gcc -std=gnu99 needs -traditional... no
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking for gm4... no
checking for m4... no

Help? =/

---

### Post by lidex on 2011-02-23
> **starrtennis said:**
> Hi. I have the same issue: Audio emits from my laptop speakers, but no devices or hardware are listed under system>preferences>sound.

I'm running lucid, as well. 10.04.

My alsa info:
[http://www.alsa-project.org/db/?f=9c89dd2d513093ab001cf06ca20fc2cbdd7b71b7](http://www.alsa-project.org/db/?f=9c89dd2d513093ab001cf06ca20fc2cbdd7b71b7)

I tried installing pulseaudio but it gave me some errors and I think the install failed:


Pulseaudio is installed by default in lucid. You have a few configuration iussues. Try changing the model switch in alsa-base.conf:
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Now look for a line like this:
```
options snd-hda-intel model=3stack
```
Now change 3stack to thinkpad. Save. Close. Reboot.

---

### Post by king vash on 2011-10-10
Your instructions and the link to Part A (of pulseaudio setup) fixed my problem of no hardware under volume control!

Thanks!

I think the issue had to due with who started pulseaudio (user \ root) which affected who can change its settings.

---

