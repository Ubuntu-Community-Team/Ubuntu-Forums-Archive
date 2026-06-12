---
title: "Sound-card issues"
date: 2007-07-25
forum: Multimedia &amp; Video
---

### Post by Robynsveil on 2007-07-25
Hi,

I want to compose MIDI music - used to use a program in Windows called Cakewalk Pro Audio 8. To that end I've installed Rosegarden via Synaptic Package Manager, which created a menu item under Applications -> Sound & Video for Rosegarden. However, it won't open at all... nothing happens - the program simply doesn't run.
I have managed to install qsynth and JACK and have them running. I've also installed Timidity, and can play back MIDI files. I have established that I have a second sound card installed on the system - the one on the motherboard, which I **_disabled in the BIO_**S - which unfortunately _ALSA still recognizes_ and sets up as the default sound card.

Been following several threads here, and ran:
```
robyn@Flight:~$ sudo asoundconf list
Password:
Names of available sound cards:
Audigy2

```
so it seems to me that *officially* at least, Linux isn't seeing the card. However, ALSA *is*.

I subsequently did this:
```
robyn@Flight:~$ sudo asoundconf set-default-card Audigy2
```

but when I opened GnomeALSAMixer I got an error:
[IMG]http://www.tightbytes.com/images/ubuntu/ALSAError.jpg[/IMG]

and then:
[IMG]http://www.tightbytes.com/images/ubuntu/GnALSAMixer.jpg[/IMG]

The error was:
> Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Master": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Master": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Bass": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Bass": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Treble": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Treble": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-3D_Control_Sigmatel_-_Depth": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-3D_Control_Sigmatel_-_Depth": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-PCM": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-PCM": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-PCM_Center": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-PCM_Center": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-PCM_Front": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-PCM_Front": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-PCM_LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-PCM_LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-PCM_Side": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-PCM_Side": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-PCM_Surround": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-PCM_Surround": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Front": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Front": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Surround": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Surround": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Center": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Center": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Side": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Side": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Synth": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Synth": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Line": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Line": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Line2": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Line2": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-CD": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-CD": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Mic": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Mic": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Phone": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Phone": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-IEC958_Optical": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-IEC958_Optical": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-PC_Speaker": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-PC_Speaker": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Aux": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Aux": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Aux2": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Aux2": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Analog_Mix": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Analog_Mix": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Audigy_CD": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Audigy_CD": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-HD_Analog_Center_LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-HD_Analog_Center_LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-HD_Analog_Front": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-HD_Analog_Front": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-HD_Analog_Rear": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-HD_Analog_Rear": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-HD_Analog_Side": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-HD_Analog_Side": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-HD_SPDIF_Center_LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-HD_SPDIF_Center_LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-HD_SPDIF_Front": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-HD_SPDIF_Front": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-HD_SPDIF_Rear": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-HD_SPDIF_Rear": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-HD_SPDIF_Side": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-HD_SPDIF_Side": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-Tone": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-Tone": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-3D_Control_-_Switch": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-3D_Control_-_Switch": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-Mic_Boost___20dB_": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-Mic_Boost___20dB_": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-IEC958_Optical_Raw": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-IEC958_Optical_Raw": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-Audigy_Analog_Digital_Output_Jack": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-Audigy_Analog_Digital_Output_Jack": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-External_Amplifier": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-External_Amplifier": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-HD_channel_Capture": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-HD_channel_Capture": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-HD_source_Capture": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-HD_source_Capture": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-Sigmatel_4-Speaker_Stereo": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-Sigmatel_4-Speaker_Stereo": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-Sigmatel_Surround_Phase_Inversion_Playback_": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-Sigmatel_Surround_Phase_Inversion_Playback_": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_mixers/SigmaTel_STAC9721,23": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_names/SigmaTel_STAC9721,23": `,' is an invalid character in key/directory names

My settings in /etc/modules are:
> # /etc/modules: kernel modules to load at boot time.
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line.
lp
sbp2
fuse
raw1394
video1394

...which were the recommended settings for Cinelerra and Kino, my video capture and editing software.

The /etc/modprobe.d/alsa-base file contains:
> # autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
mpu_port=0x330

Any way to definitively disable this sound card in Ubuntu? Interestingly, AlsaMixer (run from Terminal) sees the my AudigyZS soundcard as a card, and the Sigmatel STAC9721,23 as a chip. Even though it's disabled in the BIOS, the Sigmatel still shows up in Ubuntu.

So, in summary, what I want to do is disable (in Linux) the on-board sound - which was already done in the BIOS - and use only the Audigy card?
Thanks to all who respond...
Cheers,
Robyn

---

### Post by variona on 2007-07-26
I'm running Ubuntustudio with 3 soundcards - and that's no problem. Maybe you should run rosegarden from within a terminal so you'll see what errors it produces. The same with alsamixer - try man alsamixer to find out which options it accepts - and how to access each card.

variona

---

### Post by Robynsveil on 2007-07-26
Thanks, Variona, for your suggestion - I'm such a newbie I never would have thought of that. Here's what I got:
> robyn@Flight:~$ rosegarden
trying to create local folder /home/robyn/.kde/share: Permission denied
trying to create local folder /home/robyn/.kde/share: Permission denied
trying to create local folder /home/robyn/.kde/share: Permission denied
trying to create local folder /home/robyn/.kde/socket-Flight: Permission denied
trying to create local folder /home/robyn/.kde/socket-Flight: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/robyn/.kde/socket-Flight/kdeinit__0'
ERROR: KUniqueApplication: Can't setup DCOP communication.


...so I signed on as root and did this:
> root@Flight:/home/robyn# chmod 777 .kde/share
root@Flight:/home/robyn# chmod 777 .kde/share/config


and then:
> 
robyn@Flight:~$ rosegarden


...which then gave me several pages of stuff, which I've got [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.tightbytes.com/Stuff/1st.html").

So I shut the system down, and brought it back up. This time, when I ran Rosegarden from the terminal I got [**_[COLOR="Blue"]this output[/COLOR]_**]("http://www.tightbytes.com/Stuff/2nd.html")... and this message came up:
[IMG]http://www.tightbytes.com/images/ubuntu/Rosegdn.jpg[/IMG]

I feel 'way out of my depth here...

---

### Post by dabl on 2007-07-26
I'm not expert with Rosegarden, although I use an integrated STAC chip for audio, but I think this might indicate a bigger problem than you think:

> robyn@Flight:~$ rosegarden
trying to create local folder /home/robyn/.kde/share: Permission denied

First, are you running Kubuntu?  Because it looks like Rosegarden was trying to write its default configuration in the /home/username/.kde folder, which is the K Desktop settings folder. I'm not sure what that would be doing in a Ubuntu home folder, unless you have also installed the *kubuntu-desktop* metapackage.

Moreover, the fact that you (the user) were denied permission to your own KDE settings folder is also a bad thing -- it almost looks like you installed yourself while working in "root user" mode, such that you now are not allowed to modify your own settings when running in normal user mode.

:confused:

---

### Post by variona on 2007-07-26
Actually it would be better to chown -R robyn:robyn the .kde directory instead of making it accesible and writeable for all.  chmod 700 for yourself and noone else 
Not sure about Feisty kernel maybe rosegarden is right. Ubuntustudio Linux version 2.6.20-16-lowlatency works fine.
head up

variona

PS: rosegarden writes its rc file to .kde/ also in ubuntustudio

---

### Post by Robynsveil on 2007-07-26
> **variona said:**
> Actually it would be better to chown -R robyn:robyn the .kde directory instead of making it accesible and writeable for all.  chmod 700 for yourself and noone else 
Not sure about Feisty kernel maybe rosegarden is right. Ubuntustudio Linux version 2.6.20-16-lowlatency works fine.
head up

variona

PS: rosegarden writes its rc file to .kde/ also in ubuntustudio

Thanks for that, Variona - those are all commands I need to become a bit more familiar with, I guess. I have done so per your suggestion. There is no question that there is a lot that I need to understand - as in: study - with respect to Linux commands.

I was able to get Jack up and running, and QSynth up and running, and then (from the command-line) Rosegarden finally displaying, but the Terminal output leaves me with the feeling that there is still a fair bit of tweaking I need to do. I am reluctant to recompile the kernel, since I had to run a script to do that for my NVidia card - the GUI manager was rebooting sporadically which the upgraded driver (and tailoring the kernel) appeared to resolve. Still, there appear to be issues - you know how the system will run an integrity check on volumes after so many days - well, I noticed that when it went to the non-splash screen mode and displayed what was happening, there were a fair few error messages in what appears to be my /etc/modules.d/alsa-base file. Are these error messages being saved to some sort of log? I might need to address these first before I do anything else.

Thanks for your patience with me...
Cheers,
Robyn

---

### Post by Robynsveil on 2007-07-26
> **dabl said:**
> I'm not expert with Rosegarden, although I use an integrated STAC chip for audio, but I think this might indicate a bigger problem than you think...

I agree, Dabl... and the hidden error messages might hold the clue.

> **dabl said:**
> First, are you running Kubuntu?
No, Feisty Fawn...

> **dabl said:**
> ...it looks like Rosegarden was trying to write its default configuration in the /home/username/.kde folder, which is the K Desktop settings folder.
I'm a bit puzzled about that myself... I *did* try to install applications that (as it turned out) were KDE-specific utilities - it might have generated that folder. I've since uninstalled those apps, since they generated errors and wouldn't run.

> **dabl said:**
> Moreover, the fact that you (the user) were denied permission to your own KDE settings folder is also a bad thing -- it almost looks like you installed yourself while working in "root user" mode
I installed in the default mode - whatever mode that was. I had installed Edgy Eft first in that mode, and upgraded to Feisty in the same mode - it kept asking me for a password, so I know I wasn't in root mode.
Cheers,
Robyn

---

### Post by variona on 2007-07-27
> **Robynsveil said:**
> Are these error messages being saved to some sort of log? I might need to address these first before I do anything else.

Robyn

logs are written to /var/log/. There's a graphical syslogviewer somewhere in the sytem menu. 
to find things it is easier to 
less /var/log/FILENAME | grep WHAT_YOU_WANT_TO_FIND
alas I just found out on launch pad
```

Bug description 
logd is currently not running in feisty; which means both /var/log/boot isn't filled AND that output is spat all over the getty by default.
```
Also [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/94120](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/94120)

which probably means that you have no log of boot messages (neither have I). What I'll do next:
sudo gedit /etc/default/bootlogd
and there I'll  enable it with YES - then I reboot and then we'll see?
till then
variona

---

### Post by variona on 2007-07-27
After the first reboot:nothing
then:
sudo update-rc.d -f bootlogd defaults
Second reboot: nothing logged

No bootlogging until the logd bug is fixed

but you can still sudo /etc/init.d/alsa-utils restart
and maybe see the display of errors (if any) there

HTH

variona

---

### Post by Robynsveil on 2007-07-27
> **variona said:**
> logs are written to /var/log/. There's a graphical syslogviewer somewhere in the sytem menu. 
to find things it is easier to 
less /var/log/FILENAME | grep WHAT_YOU_WANT_TO_FIND
alas I just found out on launch pad
```

Bug description 
logd is currently not running in feisty; which means both /var/log/boot isn't filled AND that output is spat all over the getty by default.
```
Also [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/94120](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/94120)

which probably means that you have no log of boot messages (neither have I). What I'll do next:
sudo gedit /etc/default/bootlogd
and there I'll  enable it with YES - then I reboot and then we'll see?
till then
variona

Hi Variona,
I've been having a read of the system logs in the System Log Viewer, but I'd be lying if I said I even understood a tenth of what's going on. Now, setting logging on bootlogd to 'yes' would make no difference to the file I'd be wanting to see: this bootLog affected by the gedit /etc/default/bootlogd file because of a bug in Feisty, right? 

...and also, was able to restore my sound with:
```
sudo /etc/init.d/alsa-utils reset

```

I can't help but feel that the whole problem stems from not being able to disable the Sigmatel onboard sound card in Linux - already done so in the BIOS.

Cheers,
Robyn

---

### Post by variona on 2007-07-27
Bios is obviously not in charge of your onboard soundcard - meaning it is not powering the soundcard off. I don't know if it should - maybe it's faulty? May be you are better off turning it in the Bios on? ICould you imagine that the Bios simply cripples it? Really don't know.
But then if you insist on not using a soundcard under linux:
aplay -l 
to find out the cardnumber (or look in /proc/asound/)
sudo /etc/init.d/alsa-utils stop CARDNUMBER
or blacklist the driver you don't want to be loaded
/etc/modprobe.d/blacklist
if it is the default card you will have to use apps that can be configured to use explicitly the other card. Or set a new default card. (asoundconf is your friend)
bye for now and good luck

variona out

---

### Post by Robynsveil on 2007-07-28
Hi Variona,

I do have to admire your patience with my fumbling around in all this. Your suggestions are being followed to the letter. 

The first thing I did was enable the on-board sound-card in the BIOS. In terminal, **aplay -l**  gave me:
> robyn@Flight:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
[COLOR="Purple"]card 0: SI7012 [SiS SI7012][/COLOR], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[COLOR="Purple"]card 1: Audigy2 [Audigy 2 ZS [SB0350]][/COLOR], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
...


and further down:
> card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
...
  Subdevice #7: subdevice #7
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

So what I read here is that my Audigy2 card reigns supreme as far as playing stuff is concerned.
However, when I bring up my Gnome-ALSA-Mixer utility, I see this:
[IMG]http://www.tightbytes.com/images/ubuntu/gam.jpg[/IMG]

Since the Realtek tab wasn't there before, I'm going to assume this is my on-board sound-card. However, I have no idea what the SigmaTel card is - I'm pretty sure it's not another name for the Audigy2 chip, as googling the two names identifies the two as separate entities... so it must be the on-board sound - so I've got two on-board sound-cards? And why doesn't the Audigy card show up as an option? In the BIOS, when I enabled the on-board card earlier, it identified the sound-card as Realtek AC97, so I'm pretty sure that first tab refers to that card... and this is despite this entry in the **/etc/modprobe.d/blacklist** file:
> ... other blacklisted stuff...
# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187
# disable the on-board sound-card so Audigy2 has total control
blacklist SI7012


Seems Linux is going to circumvent any effort to disable this card... and Gnome-ALSA-Mixer can't even see the Audigy2 card. Here's my sound preferences selection:
[IMG]http://www.tightbytes.com/images/ubuntu/soundpref1.jpg[/IMG]
[IMG]http://www.tightbytes.com/images/ubuntu/soundpref2.jpg[/IMG]

Thanks again for studying this perplexing sound conundrum...
Robyn

---

### Post by variona on 2007-08-06
> **Robynsveil said:**
> Hi Variona,

I do have to admire your patience with my fumbling around in all this. Your suggestions are being followed to the letter. 

The first thing I did was enable the on-board sound-card in the BIOS. In terminal, **aplay -l**  gave me:


and further down:

So what I read here is that my Audigy2 card reigns supreme as far as playing stuff is concerned.

[IMG]http://www.tightbytes.com/images/ubuntu/soundpref2.jpg[/IMG]
Thanks again for studying this perplexing sound conundrum...
Robyn

In your 2nd picture you have all the devices listed that aplay -l gave you. If you choose ALSA the first soundcard will be used (i.e card 0) - I'm sure whatever you blacklisted it wasn't a proper modulename! Find out which modules are loaded with lsmod (or filter lsmod | grep snd) - my guess is Realtek is your onboard and Sigma... your Audigy (modulue: emu10k1) card. As I wrote before: sudo /etc/init.d/alsa-utils stop CARDNUMBER (in your case CARDNUMBER  would be 0) should shut down your onboard card until next reboot.

Patience is my middle name ;) 
variona

---

