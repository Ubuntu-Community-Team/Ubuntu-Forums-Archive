---
title: "Hauppauge HD-PVR, MythTV, VCR Setup Question"
date: 2009-12-27
forum: Multimedia Software
---

### Post by wdavro on 2009-12-27
I've just gotten an HD-PVR (and updated the firmware to 1.5.6) and just installed MythTV on my 9.10 linux (which I'm a newbie with) and I've been reading the MythTV user manual and pages and the Ubuntu forums for the last 6 hours so I'm a bit burnt.  I have installed ivtv and the last three lines of dmesg says:
```
[174371.691347] hdpvr 2-2:1.0: untested firmware version 0x12, the driver might not work
[174372.001752] hdpvr 2-2:1.0: device now attached to /dev/video0
[182369.949728]  CIFS VFS: Unexpected lookup error -26

```I only want to plug my VCR into the HD-PVR (using the front composite and audio connectors) and digitize a lot of old tapes.  There is no (digital) antennea (or anything else) plugged into the vcr.   When I try to setup MythTV input sources, it only seems to care about TV tuners and cable/satellite boxes.  I don't even know if what I'm trying to do will work.

I start the tape playing and at the terminal I do and get:
```
me@melinux:~$ cat /dev/video0 > test.ts
cat: /dev/video0: Input/output error
```I'm assuming this means the vid/audio signal isn't even reaching MythTV (although the MythTV backend is running - I assume, because it has a PID when I do ps -A).  I try: ```
sudo killall mythbackend
```but it apparently just restarts with a different pid.  
I started MyhTV-setup and that kills the backend, so while setup is running, I do another cat /dev/video0 > test.ts but still get the input/output error
Can anyone tell me if I can do what I'm trying to do (setup mythTV without access to a tv tuner)? 
 Any hints on making the input/output error go away (assuming this is the thing to start troubleshooting)?
I appreciate any help anyone can offer.

---

### Post by wdavro on 2009-12-28
Well, apparently I missed a reboot/restart somewhere (though I don't remember any instructions telling me to do so) because on a lark, I rebooted my system and suddenly cp /dev/video0 > test.ts works.  Sort of.  The video is there but there are only some crackling sounds and no other audio at all.
There is a forum message that says to enable Extra Audio Buffering in MythTV but I already had that enabled.  And I wasn't running MythTV frontend anyway when it exhibited the symptoms.  I'll change the setting, reboot and try again.

---

### Post by wdavro on 2009-12-28
After the reboot, now there is no video0 in the dev folder.
I suppose it's because I loaded it in Terminal before, but that doesn't explain why it reloaded after the last restart....?

Curiouser and curiouser...

---

### Post by wdavro on 2009-12-28
According to [http://www.mythtv.org/wiki/Hauppauge_HD-PVR](http://www.mythtv.org/wiki/Hauppauge_HD-PVR), I checked that sudo apt-get install build-essential mercurial linux-headers-`uname -r`
 was still loaded and it was.  Next I
sudo modprobe hdpvr
and got a completely different response in dmesg from a couple reboots ago:
[ 1559.508333] Linux video capture interface: v2.00
[ 1559.514934] usbcore: registered new interface driver hdpvr
as compared to my original posting, it's not the same,,, whatever it is... driver?

Alas, this would probably be much easier in Windows.  I want so much to move to Linux, but I find myself wasting so much precious time just trying to get things to work in Linux, nevermind actually being productive.

I give up for the night, I have to work tomorrow.

---

### Post by jeh727 on 2010-02-07
I am in the same boat, problems with composite input.  I can get "cat /dev/video0 > blah" to work by following what I found here.  I still haven't gotten mythtv to see it so any help would be great. 


  	 				 				**Re: hdpvr problems with driver, please help.** 			
 			 			 		   		 		 		Actually, the HDPVR does work with a non-hd source. By default the HDPVR sets itself to look for video via its component inputs which will contain nothing if you have a SVideo or Composite source hooked up. To change this, I typed in the following commands via a terminal window:

This command changes the input to the front composite input:
v4l2-ctl --device=/dev/video0 -l --set-input=2

This command changes the audio to the front audio inputs:
v4l2-ctl --device=/dev/video0 -l --set-audio-input=1

From then on, you should have better luck in getting it to work.

---

