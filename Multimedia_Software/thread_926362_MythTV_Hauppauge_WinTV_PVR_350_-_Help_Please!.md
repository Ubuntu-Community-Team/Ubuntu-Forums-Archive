---
title: "MythTV Hauppauge WinTV PVR 350 - Help Please!"
date: 2008-09-21
forum: Multimedia Software
---

### Post by Hawk__0 on 2008-09-21
Hi I believe I have set it up correctly, apparently it seems to be connecting to the database and everything but when I go into mythtv and click "Watch TV" the screen goes black briefly, then back to the main menu.  Whats wrong?

---

### Post by Hawk__0 on 2008-09-22
bump, please help

---

### Post by seeker5528 on 2008-09-22
Try running mythfrontend from a terminal window and see what output is left on the screen after the problem occurs.

Also look in the log file, if it is the same in Ubuntu as in Debian it should be /var/log/mythtv/mythbackend.log.

Later, Seeker

---

### Post by Hawk__0 on 2008-09-22
```
steve@steve-desktop:~$ tail /var/log/mythtv/mythbackend.log
2008-09-22 06:52:26.110 TVRec(1): Changing from None to WatchingLiveTV
2008-09-22 06:52:26.114 TVRec(1): HW Tuner: 1->1
2008-09-22 06:52:27.280 SG(Default) Error: FindNextDirMostFree: '/home/steve/Videos/MythTV' does not exist!
2008-09-22 06:52:27.341 TFW, Error: Opening file '/home/steve/Videos/MythTV/1002_20080922065226.mpg'.
			eno: Permission denied (13)
2008-09-22 06:52:27.343 TVRec(1) Error: RingBuffer '/home/steve/Videos/MythTV/1002_20080922065226.mpg' not open...
2008-09-22 06:52:27.344 TVRec(1) Error: CreateLiveTVRingBuffer() failed
2008-09-22 06:52:27.344 TVRec(1) Error: Failed to create RingBuffer 2
2008-09-22 06:52:27.358 TVRec(1): Changing from WatchingLiveTV to None
2008-09-22 06:52:27.359 AutoExpire: ERROR: Filesystem Info cache is empty, unable to calculate necessary parameters.

```

But the directory does exist!
```
steve@steve-desktop:~$ ls -la Videos/MythTV/
total 8
drwxr-xr-x  2 steve steve 4096 2008-09-21 19:01 .
drwxr-xr-x 38 steve steve 4096 2008-09-21 18:59 ..


steve@steve-desktop:~$ ls -la Videos | grep MythTV
drwxr-xr-x   2 steve steve      4096 2008-09-21 19:01 MythTV

```

---

### Post by Hawk__0 on 2008-09-22
bump

---

### Post by wolfen69 on 2008-09-22
did you select the correct modules? the default is V4L. you need to select pvr during setup. i too had a problem getting live tv to work after installing myth tv. i "fixed" it by wiping my drive and installing mythbuntu.(then installing ubuntu-desktop) tv then worked perfect.

---

### Post by seeker5528 on 2008-09-23
> **Hawk__0 said:**
> ```
2008-09-22 06:52:27.341 TFW, Error: Opening file '/home/steve/Videos/MythTV/1002_20080922065226.mpg'.
			eno: Permission denied (13)
2008-09-22 06:52:27.343 TVRec(1) Error: RingBuffer '/home/steve/Videos/MythTV/1002_20080922065226.mpg' not open...
2008-09-22 06:52:27.344 TVRec(1) Error: CreateLiveTVRingBuffer() failed
2008-09-22 06:52:27.344 TVRec(1) Error: Failed to create RingBuffer 2
```

But the directory does exist!


I don't know if having the directory you want to record to in your home directory is going to work. By default the stuff in your home directory is intended to be private, mythtv accesses stuff as the user mythtv.

I have a separate partition that I only use for Myth TV. I create a group with a name like avmedia and a numerical ID 1005 or something high enough that I can expect it has not been used yet so I can be sure I will be able to create this in any distribution I install on my machine. If you create a directory on this partition named mythrecordings it should be pretty identifiable

If you don't want to mess with seperate partitions you can do the same thing in /home, there is already a mythtv home directory, so like the example above you would probably want to use mythrecordings or something.

In the utility for managing user and groups, I usually use kuser for this if I want a GUI, so don't know what's stock in Ubuntu proper, add mythtv and steve to the avmedia group. 

For the manual method you can open a terminal window and type:

sudo gedit /etc/groups

: and look for a line like:

```
mediauser:x:1005:
```

: and add the users to it:


```
avmedia:x:1005:steve,mythtv
```

: Then you need to change the ownership of the mythrecording directory, from the command line:

sudo chown -R */path/to/*mythrecordings

: and since I am not very good at this numerical permissions thing I use the filemanager for that:

sudo "nautilus --browser" 

: browse to the location where mythrecordings are, view it's properties, and the permissions I use are 'rwx' enable for the owner, 'rx' enabled for the group, 'rx' enabled for others, and the 'set-group' flag set under special flags.

If you want to watch the programs from outside of myth tv, you might want to look into mythvfs.

Later, Seeker

---

### Post by Hawk__0 on 2008-09-23
seeker, you are right.  I was looking through other threads and I noticed most people have theirs set to something liek /usr/lib/mythtv/.  Since I've changed that, I now get an error message! I consider it progress though.

MythTV Says:
Unable to initialize video

Command line (Front end) says:
```
2008-09-23 19:32:27.696 TV: Attempting to change from None to WatchingLiveTV
2008-09-23 19:32:27.697 Using protocol version 40
2008-09-23 19:32:29.609 DPMS Deactivated 
2008-09-23 19:32:29.704 Opening audio device 'default'. ch 2(2) sr 44100
2008-09-23 19:32:29.705 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2008-09-23 19:32:29.754 AudioOutput Warning: Mixer attach error -2: No such file or directory
			Check Mixer Name in Setup: '/dev/mixer'
2008-09-23 19:32:29.761 NVP: Enabling Audio
2008-09-23 19:32:29.825 IVD: ivtv version 1.1.0
2008-09-23 19:32:29.826 IVD Error: Failed to locate framebuffer
			Did you load the ivtv-fb Linux kernel module?
2008-09-23 19:32:29.826 VideoOutput, Error: Not compiled with any useable video output method.
2008-09-23 19:32:29.826 Unable to initialize video.

```

MythTV Backend log says:
```
2008-09-23 19:32:27.701 TVRec(1): Changing from None to WatchingLiveTV
2008-09-23 19:32:27.706 TVRec(1): HW Tuner: 1->1
2008-09-23 19:32:28.938 MPEGRec(/dev/video0) Warning: Audio sample rate 32000 Hz
			is not supported by ivtv driver, using 48000 Hz instead.
2008-09-23 19:32:28.942 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-09-23 19:32:49.655 TVRec(1): Changing from WatchingLiveTV to None
2008-09-23 19:32:49.865 Finished recording Unknown: channel 1002

```

Edit:
Thre strange thing is, running "mplayer /dev/video0" brings up channel 2 on my cable just fine....

---

### Post by seeker5528 on 2008-09-24
It looks like the options chosen during setup were to send the video output over the PVR 350 to the TV.

Which I am not familiar with, but if that is what you want you at the least probably need to edit /etc/modules to add ivtvfb to it, since it is complaining about that module not being loaded. Then it should load during boot up.

To load it manually in a terminal window type:

sudo modprobe ivtvfb

: If you don't want to output through the PVR 350 then you need to check the output configurations in the front end. 

Under 'Utilities/Setup --> Setup --> TV Settings --> Playback' there is a checkbox on page 9 to enable/disable the use of the TV out on the PVR 350.

If you still get complaints about the audio after dealing with the above stuff.....

If you need to mess with the audio settings, I use alsa output and have gone to the command line and done:

asoundconf unset-pulseaudio

: In Myth Frontend the settings are in 'Utilities/Setup --> Setup --> General'

Where relevant I use 'alsa:default' or 'default' for everything. I only have a PVR 250, which doesn't do output to the TV so I don't know what extra audio options show up if you want to send the audio to the TV.

Later, Seeker

---

### Post by Hawk__0 on 2008-10-29
Guys thanks for all your help but I caved and installed mythbuntu.

I set it so that my card is wintv pver x50 (I cant remember the exact option, as i am at work).  When I go to watch live TV, all channels are fuzzy (sparkling gray and black dots/static).  I don't know how to get it to work! It is now hooked up to my tv in the living room with the cable attached to it (TV coax cable)

---

