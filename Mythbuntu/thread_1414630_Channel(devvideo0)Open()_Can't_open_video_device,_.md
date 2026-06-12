---
title: "Channel(/dev/video0)::Open(): Can't open video device, error &quot;Permission denied&quot;"
date: 2010-02-23
forum: Mythbuntu
---

### Post by lank23 on 2010-02-23
After a fresh install of Mythubuntu 10.04 alpha with Mythtv .23 from ppa's  "had to try out MythNetvision" using a PVR-150 all was working great for couple weeks until today when Watch TV and Recording stopped working.  Checking my  /var/log/mythtv/mythbackend.log I found this error.

```

lank23@MythServer:~$ cat /var/log/mythtv/mythbackend.log | grep /dev/video0
2010-02-23 14:16:02.117 Channel(/dev/video0)::Open(): Can't open video device, error "Permission denied"

```

Once I have the error I can no longer us my /dev/video0 but if I do

```

sudo chown root:mythtv /dev/video0

```

and then restart the mythtv backend I can then use the device until next reboot.

```

lank23@MythServer:~$ grep video /etc/group
video:x:44:mythtv

```

```

lank23@MythServer:~$ ls -l /dev/video*
crw-rw----+ 1 root video  81, 0 2010-02-23 16:16 /dev/video0
crw-rw----+ 1 root video  81, 3 2010-02-23 16:16 /dev/video24
crw-rw----+ 1 root video  81, 1 2010-02-23 16:16 /dev/video32

```

```

lank23@MythServer:~$ lspci | grep video
05:01.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

```

Thanks

---

### Post by azmyth on 2010-02-23
I'd probably do a udev 55-custom.rules custom file in your udev/rules.d folder.

KERNEL=="video[0-2]", SYSFS{vendor}=="0x4444", SYSFS{device}=="0x0016", SYMLINK+="pvr150", MODE="0666"

It's one of those things you do once and then you forget about it.

---

### Post by lank23 on 2010-02-24
I tried it and it works, but now seems mythtvbackend is starting before the udev demon does. So once machine reboots I have to kill mythtvbackend and it respawns and then the device is able to be used.

---

### Post by SiHa on 2010-02-24
Just a wild stab in the dark. Once upon a time, I ran Mythfrontend as root, by accident:```
sudo mythfrontend
```

And I got the message 'You must be a member of the mythtv group to run MythTV. Would you like to be added to that group?' To which I replied 'Yes', and rebooted as instructed.

Not sure why you have your problem, but it occurs to me that you might solve it by adding root to the mythv group. Not sure of the correct syntax to do it properly, but the above should work as a 'dirty' method.

---

### Post by lank23 on 2010-02-24
I tried that but does not work still get the errors.

But If you was to do it the correct way "add user to group", you would edit /etc/group file and find the line where "mythtv" is the first text and add the needed user(s) to this line separated by a comma like below but I don't think you would every need to run mythtv as root due it runs as user mythtv and group mythtv.

```

mythtv:x:105:mythtv,lank23,root

```

To add to this drama my Mythtv step up on 8.04 was working fine for couple years....

---

### Post by azmyth on 2010-02-24
Not elegant but you could restart the mythbackend service through the rc.local file or if that's still too early you could add a script to the .config/autostart folder that restarts mythbackend. The second way you'd probably have to add service to visudo. Don't know if the second way would start too late and cause mythfront to complain about the BE not running.

---

### Post by superm1 on 2010-02-25
This is caused by a buggy patch that's in the lucid package right now.  There is an updated patch in bzr that will be available in the next upload.

For now you can work around it by chowning the devices at bootup to mythtv or by disabling the permissions drop for mythtv.

---

### Post by lank23 on 2010-02-25
Thanks for the info.  Once I get the patch installed I will follow up on this thread.

---

### Post by lank23 on 2010-03-16
Well its been two weeks and a couple updates and I still have the issue,  so I figured it was time for me to get busy fixing the issue.

1: made a new udev rule for the PVR-150 that reads like below
```

KERNEL=="video[0-2]", SYSFS{vendor}=="0x4444", SYSFS{device}=="0x0016", MODE="0666"

```

2: Edit /etc/init/mythtv-backend.conf and change "start on" to read as below
```

start on (local-filesystems
          and net-device-up IFACE=lo
          and started udev
          and stopped udevtrigger
          and stopped udevmonitor)

```

This makes the mythtv-backend service start after the udev rules have been set

lank23

---

### Post by superm1 on 2010-03-16
> **lank23 said:**
> Thanks for the info.  Once I get the patch installed I will follow up on this thread.

The patch should have been present in recent autobuilds for a while.  Can you please post what version of the package you've needed to use that workaround for still?

---

### Post by lank23 on 2010-03-16
```

lank23@MythServer:~$ uname -a
Linux MythServer 2.6.32-16-generic #25-Ubuntu SMP Tue Mar 9 16:33:52 UTC 2010 i686 GNU/Linux

```

```

lank23@MythServer:~$ lsb_release -a 
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu lucid (development branch)
Release:	10.04
Codename:	lucid

```

```

lank23@MythServer:~$ mythfrontend --version
Please include all output in bug reports.
MythTV Version   : 23736
MythTV Branch    : trunk
Network Protocol : 56
Library API      : 0.23.20100310-1
QT Version       : 4.6.2
Options compiled in:
 linux profile using_oss using_alsa using_pulse using_jack using_pulseoutput using_backend using_dvb using_firewire using_frontend using_glx_proc_addr_arb using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmc_vld using_xvmcw using_bindings_perl using_bindings_python using_opengl using_vdpau using_ffmpeg_threads using_libavc_5_3 using_live using_mheg

```

```

lank23@MythServer:~$ mythbackend --version
Please include all output in bug reports.
MythTV Version   : 23736
MythTV Branch    : trunk
Network Protocol : 56
Library API      : 0.23.20100310-1
QT Version       : 4.6.2
Options compiled in:
 linux profile using_oss using_alsa using_pulse using_jack using_pulseoutput using_backend using_dvb using_firewire using_frontend using_glx_proc_addr_arb using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmc_vld using_xvmcw using_bindings_perl using_bindings_python using_opengl using_vdpau using_ffmpeg_threads using_libavc_5_3 using_live using_mheg

```

---

### Post by socholo on 2010-05-03
I also have observed what I think is the same problem after installing Mythbuntu 10.04 on the weekend.  Is there a fix that I can apply to resolve this issue, or do I need to follow the steps that lank23 outlined?

I see the following error in my backend log:
```

2010-05-03 21:43:21.166 Channel(/dev/video0)::Open(): Can't open video device, error "Permission denied"
2010-05-03 21:43:21.204 MythBackend, Error: No valid capture cards are defined in the database.
                        Perhaps you should re-read the installation instructions?

```Like lank23, if I simply stop the backend and restart it (I run the backend editor and then exit from the Application menu to accomplish this), then everything works fine.  However, I would like to avoid having to do this everytime I restart the system.

The following outlines my version information:
```

tyler@basil2:~$ uname -a
Linux basil2 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

``````

tyler@basil2:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04 LTS
Release:        10.04
Codename:       lucid

``````

tyler@basil2:~$ mythfrontend --version
xprop:  unable to open display ''
Please include all output in bug reports.
MythTV Version   : 24158
MythTV Branch    : branches/release-0-23-fixes
Network Protocol : 56
Library API      : 0.23.20100314-1
QT Version       : 4.6.2
Options compiled in:
 linux debug using_oss using_alsa using_pulse using_jack using_pulseoutput using_backend using_dvb using_firewire using_frontend using_glx_proc_addr_arb using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_libudev using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmc_vld using_xvmcw using_bindings_perl using_bindings_python using_opengl using_vdpau using_ffmpeg_threads using_libavc_5_3 using_live using_mheg

``````

tyler@basil2:~$ mythbackend --version
Please include all output in bug reports.
MythTV Version   : 24158
MythTV Branch    : branches/release-0-23-fixes
Network Protocol : 56
Library API      : 0.23.20100314-1
QT Version       : 4.6.2
Options compiled in:
 linux debug using_oss using_alsa using_pulse using_jack using_pulseoutput using_backend using_dvb using_firewire using_frontend using_glx_proc_addr_arb using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_libudev using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmc_vld using_xvmcw using_bindings_perl using_bindings_python using_opengl using_vdpau using_ffmpeg_threads using_libavc_5_3 using_live using_mheg

```

---

### Post by lank23 on 2010-05-04
> I also have observed what I think is the same problem after installing Mythbuntu 10.04 on the weekend. Is there a fix that I can apply to resolve this issue, or do I need to follow the steps that lank23 outlined?

Not yet.

Then main issue is that mythtbackend is started before udev finishes.

using my fix seems to work well...

lank23

---

### Post by socholo on 2010-05-05
I made the same changes to my system and it has resolved my problem too.

Thanks lank23!

---

### Post by teet on 2010-05-06
I'm running Ubuntu 10.04 lucid lynx.  I ran into the same problem after I upgraded from 9.10.  The workaround by lank23 seemed to fix it.  To clarify the first step in his guide I simply ran

```
gksudo gedit /lib/udev/rules.d/55-custom.rules
```

then added

```
KERNEL=="video[0-2]", SYSFS{vendor}=="0x4444", SYSFS{device}=="0x0016", MODE="0666"
```

saved it, and closed it.

Thanks for figuring this out!  I'm sure there a ton of users with PVR-150s out there that will run into the exact same problem.

-teet

---

### Post by lank23 on 2010-05-06
no problem.  glad I could help.

---

### Post by russell5 on 2010-05-09
Thanks Worked for me too after upgrading to 10.04.

---

### Post by StefanG on 2010-05-23
The changes are still necessary on my newly installed and fully updated system using the autobuilds.

/StefanG

---

### Post by Senkoboy on 2010-05-31
[QUOTE=

gksudo gedit /lib/udev/rules.d/55-custom.rules



KERNEL=="video[0-2]", SYSFS{vendor}=="0x4444", SYSFS{device}=="0x0016", MODE="0666"

2: Edit /etc/init/mythtv-backend.conf and change "start on" to read as below
Code:

start on (local-filesystems
          and net-device-up IFACE=lo
          and started udev
          and stopped udevtrigger
          and stopped udevmonitor)

This makes the mythtv-backend service start after the udev rules have been set

[/QUOTE]

Thanks guys, that seemed to have fixed my problem with my PVR 150 also.

---

### Post by gemini91 on 2010-07-23
Installed mythubuntu-10.4 with mythtv-23 a few days ago, Using a Hauppauge WinTV-HVR-1950. Worked until this morning, and now I have the same problem. Fix appears to work.

---

### Post by OldGaf on 2010-07-31
I have a 150 and a 500 in my backend and lank23's fix works great.

Thanks a lot.... this was really bugging me :D

---

