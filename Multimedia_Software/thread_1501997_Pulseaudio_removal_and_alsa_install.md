---
title: "Pulseaudio removal and alsa install"
date: 2010-06-05
forum: Multimedia Software
---

### Post by grumpy.biatch on 2010-06-05
Hi,

I have removed pulseaudio and installed alsa. I cant get the sound working, the sound applet is a miss too. 

Below please find the terminal OP  :confused:

xxxxx@xxxxx-desktop:~$ sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
[sudo] password for xxxxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gstreamer0.10-pulseaudio* indicator-sound* libcanberra-pulse*
  libcanberra-pulse-dbg* padevchooser* paprefs* pulseaudio* pulseaudio-dbg*
  pulseaudio-esound-compat* pulseaudio-esound-compat-dbg*
  pulseaudio-module-bluetooth* pulseaudio-module-bluetooth-dbg*
  pulseaudio-module-gconf* pulseaudio-module-gconf-dbg*
  pulseaudio-module-jack* pulseaudio-module-jack-dbg* pulseaudio-module-lirc*
  pulseaudio-module-lirc-dbg* pulseaudio-module-raop*
  pulseaudio-module-raop-dbg* pulseaudio-module-x11*
  pulseaudio-module-x11-dbg* pulseaudio-module-zeroconf*
  pulseaudio-module-zeroconf-dbg* ubuntu-desktop*
0 upgraded, 0 newly installed, 25 to remove and 0 not upgraded.
After this operation, 12.9MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 206363 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing gstreamer0.10-pulseaudio ...
Removing indicator-sound ...
Removing libcanberra-pulse-dbg ...
Removing libcanberra-pulse ...
Removing padevchooser ...
Purging configuration files for padevchooser ...
Removing paprefs ...
Purging configuration files for paprefs ...
Removing pulseaudio-module-zeroconf-dbg ...
Removing pulseaudio-module-raop-dbg ...
Removing pulseaudio-module-raop ...
Removing pulseaudio-module-zeroconf ...
Removing pulseaudio-module-x11-dbg ...
Removing pulseaudio-module-x11 ...
Removing pulseaudio-module-lirc-dbg ...
Removing pulseaudio-module-lirc ...
Removing pulseaudio-module-jack-dbg ...
Removing pulseaudio-module-jack ...
Removing pulseaudio-module-gconf-dbg ...
Removing pulseaudio-module-gconf ...
Removing pulseaudio-module-bluetooth-dbg ...
Removing pulseaudio-module-bluetooth ...
Removing pulseaudio-esound-compat-dbg ...
Removing pulseaudio-esound-compat ...
Removing pulseaudio-dbg ...
Removing pulseaudio ...
 * PulseAudio configured for per-user sessions
Purging configuration files for pulseaudio ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_SG.utf8.cache...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
xxxxx@xxxxx-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
xxxxx@xxxxx-desktop:~$ sudo apt-get install alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base alsamixergui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-base is already the newest version.
alsa-utils is already the newest version.
alsa-utils set to manually installed.
alsa-oss is already the newest version.
linux-sound-base is already the newest version.
alsamixergui is already the newest version.
The following NEW packages will be installed:
  alsa-tools alsa-tools-gui
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 349kB of archives.
After this operation, 1,196kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  alsa-tools alsa-tools-gui
Install these packages without verification [y/N]? y
Get:1 [http://mirror.internode.on.net/pub/ubuntu/ubuntu/](http://mirror.internode.on.net/pub/ubuntu/ubuntu/) lucid/universe alsa-tools 1.0.22-0ubuntu1 [83.6kB]
Get:2 [http://mirror.internode.on.net/pub/ubuntu/ubuntu/](http://mirror.internode.on.net/pub/ubuntu/ubuntu/) lucid/universe alsa-tools-gui 1.0.22-0ubuntu1 [265kB]
Fetched 349kB in 8s (43.2kB/s)                                                 
Selecting previously deselected package alsa-tools.
(Reading database ... 205978 files and directories currently installed.)
Unpacking alsa-tools (from .../alsa-tools_1.0.22-0ubuntu1_i386.deb) ...
Selecting previously deselected package alsa-tools-gui.
Unpacking alsa-tools-gui (from .../alsa-tools-gui_1.0.22-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_SG.utf8.cache...
Processing triggers for menu ...
Processing triggers for python-support ...
Setting up alsa-tools (1.0.22-0ubuntu1) ...
Setting up alsa-tools-gui (1.0.22-0ubuntu1) ...

Processing triggers for menu ...
xxxxx@xxxxx-desktop:~$ sudo apt-get install esound esound-clients esound-common libesd-alsa0 gnome-alsamixer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
esound-clients is already the newest version.
esound-common is already the newest version.
gnome-alsamixer is already the newest version.
The following NEW packages will be installed:
  esound libesd-alsa0
0 upgraded, 2 newly installed, 0 to remove and 5 not upgraded.
Need to get 23.0kB of archives.
After this operation, 98.3kB of additional disk space will be used.
Get:1 [http://mirror.internode.on.net/pub/ubuntu/ubuntu/](http://mirror.internode.on.net/pub/ubuntu/ubuntu/) lucid/universe esound 0.2.41-6ubuntu1 [22.2kB]
Get:2 [http://mirror.internode.on.net/pub/ubuntu/ubuntu/](http://mirror.internode.on.net/pub/ubuntu/ubuntu/) lucid/universe libesd-alsa0 0.2.41-6ubuntu1 [826B]
Fetched 23.0kB in 2s (10.3kB/s)    
Selecting previously deselected package esound.
(Reading database ... 206054 files and directories currently installed.)
Unpacking esound (from .../esound_0.2.41-6ubuntu1_i386.deb) ...
Selecting previously deselected package libesd-alsa0.
Unpacking libesd-alsa0 (from .../libesd-alsa0_0.2.41-6ubuntu1_all.deb) ...
Processing triggers for man-db ...
Setting up esound (0.2.41-6ubuntu1) ...
Setting up libesd-alsa0 (0.2.41-6ubuntu1) ...

**(After restart)................**

xxxxx@xxxxx-desktop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'
gstreamer-properties-Message: Error running pipeline 'ALSA - Advanced Linux Sound Architecture': Could not open audio device for playback. [gstalsasink.c(691): gst_alsasink_open (): /GstPipeline:pipeline0/GstAlsaSink:alsasink1:
Playback open error on device 'default': Connection refused]
gstreamer-properties-Message: Error running pipeline 'ALSA - Advanced Linux Sound Architecture': Could not open audio device for playback. [gstalsasink.c(691): gst_alsasink_open (): /GstPipeline:pipeline1/GstAlsaSink:alsasink2:
Playback open error on device 'default': Connection refused]

xxxxx@xxxxx-desktop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'
gstreamer-properties-Message: Error running pipeline 'ALSA - Advanced Linux Sound Architecture': Could not open audio device for playback. [gstalsasink.c(691): gst_alsasink_open (): /GstPipeline:pipeline0/GstAlsaSink:alsasink1:
Playback open error on device 'default': Connection refused]
gstreamer-properties-Message: Error running pipeline 'ALSA - Advanced Linux Sound Architecture': Could not open audio device for playback. [gstalsasink.c(691): gst_alsasink_open (): /GstPipeline:pipeline1/GstAlsaSink:alsasink2:
Playback open error on device 'default': Connection refused]
xxxxx@xxxxx-desktop:~$ sudo apt-get install gnome-alsamixer
[sudo] password for xxxxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-alsamixer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
xxxxx@xxxxx-desktop:~$ sudo apt-get install alltray
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  alltray
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 60.4kB of archives.
After this operation, 262kB of additional disk space will be used.
Get:1 [http://mirror.internode.on.net/pub/ubuntu/ubuntu/](http://mirror.internode.on.net/pub/ubuntu/ubuntu/) lucid/universe alltray 0.69-1ubuntu4 [60.4kB]
Fetched 60.4kB in 4s (12.8kB/s)  
Selecting previously deselected package alltray.
(Reading database ... 206073 files and directories currently installed.)
Unpacking alltray (from .../alltray_0.69-1ubuntu4_i386.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_SG.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up alltray (0.69-1ubuntu4) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
xxxxx@xxxxx-desktop:~$

---

### Post by grumpy.biatch on 2010-06-05
asoundrc is missing. How do i get one.

---

### Post by hxcobd on 2010-06-05
Not generally the best idea to remove one or the other in a Ubuntu install, as they are highly interdependent upon each other...

If you must remove one of them, use a guide such as this:

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

There are changes to scripts that must be made for audio to continue working properly.

---

### Post by grumpy.biatch on 2010-06-05
> **hxcobd said:**
> Not generally the best idea to remove one or the other in a Ubuntu install, as they are highly interdependent upon each other...

If you must remove one of them, use a guide such as this:

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

There are changes to scripts that must be made for audio to continue working properly.

I do not need pulseaudio on 32 bit system. It works well on 64 bit. I need to install alsa since it is lightweight.

---

### Post by Yellow Pasque on 2010-06-05
> **grumpy.biatch said:**
> asoundrc is missing. How do i get one.
Try reinstalling the alsa packages:
```
sudo apt-get install --reinstall alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base alsamixergui
```

EDIT: Useful page for asound configuration: [http://linuxconfig.dyndns.org/lazy/LazyLinuxWiki/Audio_&_Video/Sound_config_%28Slackware%29](http://linuxconfig.dyndns.org/lazy/LazyLinuxWiki/Audio_&_Video/Sound_config_%28Slackware%29)

---

### Post by grumpy.biatch on 2010-06-05
> **Temüjin said:**
> Try reinstalling the alsa packages:
```
sudo apt-get install --reinstall alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base alsamixergui
```

EDIT: Useful page for asound configuration: [http://linuxconfig.dyndns.org/lazy/LazyLinuxWiki/Audio_&_Video/Sound_config_%28Slackware%29](http://linuxconfig.dyndns.org/lazy/LazyLinuxWiki/Audio_&_Video/Sound_config_%28Slackware%29)

I am in windows atm, will give it a go later.

Thanks,

Dave

---

### Post by avenue.max on 2010-06-05
> **grumpy.biatch said:**
> I am in windows atm, will give it a go later.

Thanks,

Dave


I tried that but no luck still.

---

### Post by Yellow Pasque on 2010-06-05
EDIT: nvm

---

### Post by avenue.max on 2010-06-05
> **Temüjin said:**
> You may need to add your user to the audio group: (NOTE: those are backticks, not apostrophes)
```
sudo usermod -G audio `whoami`
```

Hi,

Got it working somehow, yet to figure out how it showed up. I wish to remove all sound entries such as 'sound' from system - preferences

---

### Post by avenue.max on 2010-06-05
> **avenue.max said:**
> Hi,

Got it working somehow, yet to figure out how it showed up. I wish to remove all sound entries such as 'sound' from system - preferences

Grumpy is my ID as well.......

---

### Post by medevacs on 2010-06-06
> **Temüjin said:**
> You may need to add your user to the audio group: (NOTE: those are backticks, not apostrophes)
```
sudo usermod -G audio `whoami`
```

Congrats dude! You have just f*cked up every linux newbie's system!

Do you actually know what execution of this command is going to do? Well, I will enlighten you. Your main user account will be added to the group "audio". Is that what you meant? That is great but there is one small argument missing. As far as I know, there should also "-a" inside, otherwise the command you suggested not only will add you to audio group but also WILL REMOVE YOU FROM ANY OTHER GROUP! Thanks to this, you won't be able to execute for example sudo commands.

For any newbie user who is now deep inside of the dark *** with his/her system, like I was few hours before, because I used this command trusting too much in others' linux knowledge and not checking by myself the command before I use it, here is the way to bring your system back to quite normal state.
1. Boot in a recovery mode and go to root console (when starting computer keep pressing ESC or (right) SHIFT to get GRUB screen, chose recovery mode and from next menu chose last option (root something)).
2. Go to /etc/ and edit file group or restore your backup (if you have it) or use the system backup (I had a file named "group-"). Remember about adding proper read/write/execute attributes if restoring/copying backup file instead of existing group file.
3. Reboot system normally, sudo and other things should be working now (you can just reset computer or type "init 6" or "reboot now").

BTW, adding your user to this audio group doesn't solve the problem. I am trying to deal with not working audio via HDMI on my Radeon HD 4350 (old PCI version) with radeonhd drivers. Just "arghhhh!". Nothing is working for me now.

---

### Post by Yellow Pasque on 2010-06-06
^My apologies. I did mean to include the -a :(

---

### Post by medevacs on 2010-06-08
Sorry for my post, I overreacted a little bit. But seriously, please check the suggested command next time before publishing. Newbies are not able to see this kind of mistakes.

BTW, any other ideas how to solve problem from this thread?

---

