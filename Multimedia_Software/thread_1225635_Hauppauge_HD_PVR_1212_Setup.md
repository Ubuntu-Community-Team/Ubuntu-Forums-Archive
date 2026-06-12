---
title: "Hauppauge HD PVR 1212 Setup"
date: 2009-07-28
forum: Multimedia Software
---

### Post by sparks13 on 2009-07-28
So I found this page: [http://www.mythtv.org/wiki/Hauppauge_HD-PVR](http://www.mythtv.org/wiki/Hauppauge_HD-PVR)

Everything seemed to go fine right up until the "sudo modprobe hdpvr" where my terminal outputs nothing. Was I supposed to get nothing? If so, the "cat /dev/video1 > test.ts" does not work for me. I only have /dev/video0 if that helps (I did substitute it for the above command to no avail). So just looking for some help on where to go from here. Thanks.

---

### Post by xzero1 on 2009-07-29
Your terminal outputting nothing is good. Post the output of 
```
dmesg | grep video
```What are video inputs are you using?

---

### Post by sparks13 on 2009-07-29
I am at work at the moment so I can't try anything. However, last night a friend helped me some and it seems the driver is loading alright. I am not sure why the "cat /dev/video0 > test.ts" command is not doing anything. It only creates an empty file. Is there another easy way to test video input? I have seen something about VLC, but have never used it for anything like this. Basically I am looking for an easy way to test this short of installing and setting up the 0.22 trunk development version of mythtv.

---

### Post by xzero1 on 2009-07-29
The device may not be using video0. The driver will default to using particular video and sound inputs. These inputs must have video and audio input for the device to capture anything. Once the cat command is working (it will create a playable h.264 ts file), then you can play live video with "mplayer /dev/videoN" once you know what N is.

To find N use ```
v4l2-ctl --device=/dev/videoN -l
```for different values of N.

Note N may change especially if you have multiple video devices each time you reboot.

Once you are all set I have a nice recording script that uses the hdpvr you may want to try.
See [http://ubuntuforums.org/showthread.php?t=1169204](http://ubuntuforums.org/showthread.php?t=1169204)

I also have a post that describes how to create HD DVDs on standard DVD material without transcoding.
See [http://ubuntuforums.org/showthread.php?t=943661](http://ubuntuforums.org/showthread.php?t=943661)

Karmic appears to have the hdpvr module built-in so there will be no more modprobe or header issues to worry about.:D

---

### Post by xzero1 on 2009-07-29
Warning: the Jaunty Ubuntu kernel recently been updated to 2.6.28-14. If you did not have this kernel when you compiled your module, then a normal system update will break the module and it will need to be recompiled. This will happen every time the Ubuntu kernel is updated.

See this thread for a possible solution:
[http://ubuntuforums.org/showthread.php?t=1013033](http://ubuntuforums.org/showthread.php?t=1013033)

---

### Post by sparks13 on 2009-07-29
So I turn on the hdpvr today and run "dmesg | grep video" to see my hdpvr driver is attached to /dev/video0. The "v4l2-ctl --device=/dev/video0 -l" gives me a list of variables, options, defaults, and their values (looks promising). I run "cat /dev/video0 > test.ts" and get this back: "cat: /dev/video0: Input/output error". I was fortunate enough to have compiled after the kernel update so that should not be an issue.

Then I realized my Playstation 3 which was feeding into it was turned off. I turn that on, ran "cat /dev/video0 > test.ts" which runs for a little bit before I <ctrl>-C it. Then I select to open the test.ts with mplayer and it works!

As far as I can tell, the only potential difference is I had to install ivtv-utils to run your v4l2-ctl command. So if anyone else is at this stage, you might try a simple "sudo apt-get install ivtv-utils" to see if it resolves your problems.

Thanks for your help xzero1. (P.S. I don't see any links from your forums profile)

---

### Post by xzero1 on 2009-07-29
Oops, I have edited the post. The links should work now. 
Btw, I also recommend using variable bit rate for recording. At the highest settings the quality is very good and it uses less space. Thats is one reason I use my recording script because after a few minutes I can predict the bitrate, filesize etc.

---

### Post by davidstoll on 2009-07-30
Just wanted to let people know that I made a recording script also.  I've been working on it for several months and it works quite well.  You basically put your recording in a cron job and it does everything else....imports and everything.

It's a perl script that has TONS of options (switches).  Check it out.  I'd love some feedback.

Messing with trunk was just a nightmare, so I use this instead.

It's not intended to allow you to select the tuner in your backend setup...it's an outside of Myth script that does it's thing and imports it right into Myth as if Myth did the recording.

As a cron job, you set it once and forget it.

---

### Post by shawnvdm on 2009-11-15
How have you been handling changing the source you record from? I tried as root  modprobe hdpvr default_video_input=0 but it kept recording from svideo  modprobe -o hdpvr default_video_input=0 returned the following error FATAL: Module default_video_input=0 not found  The only place that seemed to make a difference was putting this in options hdpvr under modprobe.conf  I was hoping for an easier way to change depending on which input I want to use.  Thanks

---

### Post by davidstoll on 2009-11-15
Check out my perl script.  You can change the input device via a switch along with LOTS of other options.

This is an example of what you would do to record...

./videodump.pl -i /dev/video1 -c 123 -t 60 -n "test video" -p mysqlpassword -o /location/of/mythrecordings -m 1

-c is channel
-p is mysql password
-t is minutes of record time
-o is the ouput folder where myth normally stores it's shows
-m tells it to input it into the mythtv linup or just dump the video (-m 1 is required if you use the -p switch, and visa versa), if you use -m 0, it just creates a video file, but doesn't import it into myth.

You can read about what all the switches are about...there are even more to customize what you want to do.  It even deals with conflicts.  The best thing to do is run a cron job (I use crontab...set it and forget it for weekly shows).

If you read the script in a text editor, you can read my comments to see what is default.  i.e. if you don't include the -i /dev/video1, it assumes /dev/video0.

[http://ubuntuforums.org/showthread.php?t=1115440](http://ubuntuforums.org/showthread.php?t=1115440)

It uses ffmpeg, so, as you may know there are about ten zillion versions of ffmpeg, and it can be kind of finiky.  Just give it a try.  Make sure your ffmpeg supports ac3 & aac and you should be fine.

If the concern is involving the fact that video0 might become video1 (or whatever) every time you reboot, make a symbolic link to something like...

ln -s /dev/video0 /dev/videoHDPVR

I'm no linux expert, but it seems that even if video0 changes to video1, the new videoHDPVR stays linked to the correct input.

You can probably do this with whatever the svideo device is too.



> **shawnvdm said:**
> How have you been handling changing the source you record from? I tried as root  modprobe hdpvr default_video_input=0 but it kept recording from svideo  modprobe -o hdpvr default_video_input=0 returned the following error FATAL: Module default_video_input=0 not found  The only place that seemed to make a difference was putting this in options hdpvr under modprobe.conf  I was hoping for an easier way to change depending on which input I want to use.  Thanks

---

