---
title: "[SOLVED] Workaround for bug in Hauppauge WinTV PVR-USB2 driver"
date: 2008-06-22
forum: Mythbuntu
---

### Post by danbodoh on 2008-06-22
I've found a bug, and a workaround, in the driver stack for the Hauppauge PVR-USB2.  Technical details are available at [http://svn.mythtv.org/trac/ticket/5462](http://svn.mythtv.org/trac/ticket/5462) and the thread "initialization of video_gop_size" at [http://www.isely.net/pipermail/pvrusb2/2008-June/001832.html](http://www.isely.net/pipermail/pvrusb2/2008-June/001832.html) .  

This bug only affects NTSC, not PAL.

Symptoms in mythtv include:

[LIST]
[*]Press 'i' during playback of a recording.  The total time of the recording will be displayed as 125% of the actual time (1:15 for a 1 hour show).
[*]During playback, save the current position with the space bar.  Exit, then restart playback.  The playback will start at a point before the marked position.
[*]Jerky motion; where it appears that the playback pauses several times a second (see [http://ubuntuforums.org/showthread.php?t=835935](http://ubuntuforums.org/showthread.php?t=835935) ).  I'm not completely sure that this workaround fixes the motion problem because I haven't watched enough recordings with the workaround.  *Edit: after watchng more programs, I've decided that this workaround DOES NOT fix the jerky motion.*
[/LIST]

For the workaround, record the directory name seen with this 'ls' command.  This directory name is the serial number of your pvr-usb2.  It should start with 'sn-' and be followed by digits.

```
ls /sys/class/pvrusb2
```

In the commands below, use this 'sn-' number place of 'SERIALNUMBER'.

Now find the current value of the parameter set for 'video_gop_size':

```
 cat /sys/class/pvrusb2/SERIALNUMBER/ctl_video_gop_size/cur_val
```

The reported value for NTSC should be 15, and for PAL it should be 12.  But due to a bug in the pvrusb2 driver stack in the 2.6.24 kernel, it's always 12, so NTSC video is encoded with a suboptimal value.

If you see '12' reported, you can set the correct value to 15:

```
 sudo echo 15 > /sys/class/pvrusb2/SERIALNUMBER/ctl_video_gop_size/cur_val
```

This should fix the issue for new recordings, but the new value won't survive a reboot.  One possible way to set this on a reboot is to put the 'echo' command in /etc/default/mythtv-backend.  However, this file might get overwritten if you upgrade mythtv.

```
sudo vim /etc/default/mythtv-backend
```
(or use your favorite editor instead of 'vim')
At the bottom of the file, add 
```
echo 15 > /sys/class/pvrusb2/SERIALNUMBER/ctl_video_gop_size/cur_val
```

Dan Bodoh

---

### Post by danbodoh on 2008-07-01
The latest version of the pvrusb2 driver (20080629) at [http://www.isely.net/pvrusb2/download.html](http://www.isely.net/pvrusb2/download.html) seems to fix this bug.  I assume that this new driver will be showing up in a future kernel.

---

