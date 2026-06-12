---
title: "Sound Balster 16 and Ubuntu"
date: 2006-02-22
forum: Multimedia &amp; Video
---

### Post by Jay19 on 2006-02-22
(OK, just a warning here, but I'm a beginner...)

I'm using Ubuntu 5.10 and am having trouble setting it up to work with my Sound Blaster 16.  I've partially went through the "Sound troubleshooting checklist" ([http://linux.iuplog.com/default.asp?item=94639](http://linux.iuplog.com/default.asp?item=94639)) but am not able go get through it.  Here's what I've done (it's a mix of the troubleshooting checklist and the "Sound Problem Hoary Fix" ([https://wiki.ubuntu.com/SoundProblemsHoary):](https://wiki.ubuntu.com/SoundProblemsHoary):)

* Typed lspci in terminal.  It didn't list anything pertaining to sound.
* In the GUI, I selected System > Administration > Device Manager.  At the bottom of the list the "Creative Labs Sound Blaster 16" is listed.  On the opposite side, in the "Device" tab it lists the followinig:
Vender    Unknown
Device    Unknown
Status    Status
Bus Type    PNP
Device Type    Unknown
Capabilities    Unknown

In the "Advance" tab, it lists the following:
info.bus    string    pnp
info.parent    string    /org/freedesktop/Hal/devices/computer
info.product    string    Creative Labs Sound Blaster 16
info.udi    string    /org/freedesktop/Hal/devices/pnp_PNPb003
linux.hotplug_type    int    1(0x1)
linux.subsystem    string    pnp
linux.sysfs_path    string    /sys/devices/pnp1/01:01/01:01:00
linux.sysfs_path_device    string    /sys/devices/pnnp1/01:01/01:01:00
pnp.description    string    Creative Labs Sound Blaster 16
pnp.id    string    PNPb003


...now I went into the  "Sound Problem Hoary Fix" page and tried the steps listed there:
* Typed sudo gedit /etc/esound/esd.conf in the terminal, and set contents to:

[esd]
auto_spawn=0
spawn_wait_ms=100
default_options= -terminate -nobeeps -as 2

* Restarted machine and logged back on
* Selected System -> Preferences -> Multimedia System Selector.  Both the default sink and default source are ALSA.  When I selected the "Test" button, I get the following error:

"Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'"

* At this point I tried alsamixer but got the following:
alsamixer: function snd_ctl_open failed for default: No such file or directory

* At this point I fiished the suggestiion in the "SoundProblemsHoary" page and I went back to the "Ubuntu No Sound Troubleshoot" page

* Went back into the terminal and typed "sudo totem"  Totem started but I got the following error: "Totem could not startup.  The video output is in use by another application. Please close other video applications, or select another video output in the Multimedia Systems Selector."

In the terminal there was the following: 
(totem:6909): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:6909): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

* I went into the Multimedia Systems Selector and changed the video source but nothing I did fixed the error with Totem.  Since I'm  concerned about sound, not video, I moved on...

* Just for kicks, I typed in:
sudo chmod 666 /dev/dsp
...but got:
chmod: cannot access `/dev/dsp': No such file or directory

* The instructions then say to check whether the volume is mute.  In the menu bar is a speaker icon with a red and white 'X' next to it. (I'm assuming that the 'X' means it's not available).  I checked, and it's not muted.

* The instructions then state to run alsamixer.  I tried that again but got the same error again:
alsamixer: function snd_ctl_open failed for default: No such file or directory



...and that's where I'm at now and feeling a bit overwhelmend and a bit frustrated.  Any suggestions on what to do next or where to turn to?


Thanks,

Jay

---

### Post by az on 2006-02-22
[https://wiki.ubuntu.com/HowToSetupSoundCards](https://wiki.ubuntu.com/HowToSetupSoundCards)

sudo modprobe snd-sb16

---

### Post by Jay19 on 2006-02-23
It's still not working for me.  (a asside here: In order for ALSA to work, does the esd module need to be ruunning?)

Well, here's what I've done.

* I decided to start from scratch so I wiped my machine and reinstalled Ubuntu 5.10
* After it installed I went in to the Update manager and installed the updates to the system and then rebooted the machine (not necessary but just to be safe).
* In a terminal, I then typed:
sudo modprobe snd-sb16
...and nothing happened. (that was expected).  I also tried lpcsi and it didn't list any sound cards (also expected).
* Then I typed:
sudo apt-get install linux-sound-base alsa-base alsa-utils alsa-oss libesd-alsa0
* Next I typed:
sudo modprobe snd-sb16
...and nothing happed.  This was not expcted - I thought this would have configured the system to use the SB16.
* Next I selected from the menu System>Preferences>Sound.  The default sound card is set to "Sound Balaster 16" but when I change to the "Sound Events" tab, select one of the wave files and then press the "Play" button, nothing happens (no sound).
* The syetem is not muted because I right-clicked on the speaker icon in the menu bar (the speaker icon is there but it has a white and red 'X' next to it) and the mute menu item wasn't checked.  Also, I ran alsamixer and didn't notice anything being muted.
* I then ran the "Multimedia System Selector" and verified that the output and the input are set to ALSA.  When I pressed the output test button, I heard a tone but it was very scratchy.
* Next, back at the terminal window, I ran esd, and then went back into the Sound Prefference application, and was able to play (& hear) a wave file.  Is ESD required for ALSA?  Well, regardless, my system still isn't working.

Well, thanks in advance for any advice anyone can give,

Jay

---

### Post by mpvano on 2006-02-23
(Deleted)

---

### Post by az on 2006-02-23
Try booting into recovery mode, run modprobe snd-sb-16

Then run
init 2

and see if sound is working.  You need to restart gnome for it to configure the sound for you.  You can also just load the module and then run alsamixer to see if you have something to mix.

If it works, add that module to /etc/modules so that it gets loaded on boot, but before gnome runs.

If it does not work, show the last few lines from
dmesg
after you load the module.

Also, check your bios to see if you can identify the actual name of the sound hardware.

---

### Post by Jay19 on 2006-02-23
When I log in in safe mode, and then type modprobe snd-sb-16, I get the following:
FATAL: Module snd_sb_16 not found


When I type in modprobe snd-sb16, I get:
[4294800.682000] pnp: Device 01:01:01 activated

Then when I type in init 2, GNOME starts up.  The speaker icon in the corner looks like it's enabled now, but the sound is still very scratchy (almost like the speaker wire is lose or shorted (but that's not the case - that's just what it sounds like).

---

### Post by az on 2006-02-24
[QUOTE=Jay19]When I log in in safe mode, and then type modprobe snd-sb-16, I get the following:
FATAL: Module snd_sb_16 not found.[/QUOTE]
That would be because I can't type.


[QUOTE=Jay19]
When I type in modprobe snd-sb16, I get:
[4294800.682000] pnp: Device 01:01:01 activated

Then when I type in init 2, GNOME starts up.  The speaker icon in the corner looks like it's enabled now, .[/QUOTE]

Yay!  Add the module name to /etc/modules and you have sound.  


[QUOTE=Jay19]
but the sound is still very scratchy (almost like the speaker wire is lose or shorted (but that's not the case - that's just what it sounds like).[/QUOTE]
Perhaps you simply need to adjust some setting like this:
[http://ubuntuforums.org/showpost.php?p=640288&postcount=2](http://ubuntuforums.org/showpost.php?p=640288&postcount=2)

---

