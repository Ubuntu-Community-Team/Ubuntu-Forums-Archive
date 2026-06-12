---
title: "Kino capture problems"
date: 2009-12-16
forum: Multimedia Software
---

### Post by tropdoug on 2009-12-16
Seems I am destined to be plaugued with video and audio problems. 

I want to capture video from my canon digital camcorder. I have installed Kino, I have added myself to the disk and video group, I have killed pulseaudio, I have searched the net and all to no avail.

The camcorder is found on the firewire conection, the AV/C controls work to control the camera, but when I go to capture, and click the capture button, I see in the bottom left of the status bar this **"Waiting for DV 10**" and counts down to 0. When it is counting down the camera is working, although there is no display in the preview window (which is enabled) 
[B]But as soon as it reaches zero, the camera stops and kino stops. 
[/B]
If I press capture again, the same thing happens. 

In previous ubuntu versions, I have been able to get Kino working perfectly. Is this another Karmic issue? or does anyone have a fix.

---

### Post by ubu-lemon on 2009-12-22
i've got the same problem (with both my Sony digital camcorders (DCR-HC27E)
this same 'Waiting for DV 10' and the count down and the 'capture failed'

also tried all these suggestions
starting kino as root, and give myself access to video group  (that did solve the error 'raw1394 kernel module not loaded or failure to read/write /dev/raw1394 ' i had previously)

---

### Post by glibik on 2010-01-30
Has anyone found a solution to this problem as yet?  I am struggling with it myself.  None of the internet search internet search results I've found so far have an answer.  Many have similar problems but not solutions.

In my system, the relevant kernal modules load when the camera is connected and turned on (lsmod etc. show that).  Kino can see the camera.  My set up must be close to correct because Kino can start playback on the camera, stop it, pause, and rewind it.  The picture from the camera even appears in the Kino window.

When trying to start a capture, the status bar has a countdown from ten to zero "Waiting for DV 10 ...", then briefly shows "Capture failed" before going back to "AV/C Controls Enabled".  Also, when trying to start a capture the camera starts playback (as expected) and stops playing at the failure.

--------------

Have also tried using dvgrab, also without success.  All seems okay when dvgrab starts, ie: the camera starts playback and dvgrab says it is capturing, but it doesn't finish.  It has to be terminated with ^C.  One time I even let it run until the tape ended.  

glibik@venus:~/Videos$ dvgrab -format raw -duration 00:30.0 -size 10 Video01_
Found AV/C device with GUID 0x008088030740195e
Capture Started
^C"":     0.00 MiB 0 frames timecode 00:01:01.21 date 2010.01.24 09:25:28
Capture Stopped

---

### Post by glibik on 2010-02-01
> **tropdoug said:**
> 
<snip>
In previous ubuntu versions, I have been able to get Kino working perfectly. Is this another Karmic issue? or does anyone have a fix.

tropdoug, 
Which versions would those be?

Moderators, 
It would be nice to extract some kind of response to tropdoug's questions from the relevant Ubuntu developer(s).  

After all there are a number of us users spending a lot of time trying to work out a solution to this.  If we knew there is no solution, we could stop wasting time and effort and go to an earlier version of Ubuntu until a new version of Ubuntu is released where this is fixed.

---

### Post by visionary on 2010-02-02
After fighting a war for 4 days, finally i managed to solve this problem in Ubuntu...

The cause: Ubuntu has actually blacklist firewire-ohci
The solution: edit with sudo (admin) rights this file

/etc/modprobe.d/blacklist-firewire.conf

Anything without # means it has been blacklisted.
If you realised that firewire-ohci has been blacklisted, simply add # infront so that i looks as #blacklist firewire-ohci

Save the file, reboot and start Kino with sudo rights.
Click on capture and all should work fine now

Good luck!

Cheers!

---

### Post by geoff07 on 2010-02-18
Unfortunately the blacklist idea didn't work for me. But maybe I can pin down the problem a little more.  

My symptom is that kino can see and control the camera via firewire, but no video is seen in the capture window or saved.

Output from dvgrab: (retyped)
Found AV/C device with GUID ..............
""    0.00 MiB 0 frames
Capture Stopped
Error: no DV
- but dvgrab does start and stop the camera playback correctly

Output from ./firewire_tester (app taken from mythtv)
Action: Test broadcast 1 time, node 0 channel 63
Broadcast: Testing...Dropped 1179648 packets(s)
Success, 278 packets
- for this I have to start and stop the playback. It also works for many batches of packets if I enter -n 100, say. 

Conclusion:
The desktop is able to see, control and collect data from the camera, but something is preventing dvgrab from seeing the packets.  I have tried loads of chmod, sudo, group, blacklist and other adjustments as per many posts. But nothing seems to let dvgrab see the packets, even though it can control the camera.

Does anyone actually know how this is supposed to work and can provide a complete list of all the possible things that could be set wrongly?

I have reinstalled Karmic only a few days ago from the desktop CD so have a clean recent and up to date system.

Help gratefully received before I go spare!

---

### Post by visionary on 2010-02-18
The blacklist editing method was used because Kino was not able to detect the camera altogether.

As for your problem, Kino seems to detect the camera but you are not able to capture or view i suppose.

I am not too sure here, but your problem can be related to some missing codecs which may be needed by Kino eg ffmpeg codecs

You can try this
[http://ubuntuforums.org/showthread.php?t=845327](http://ubuntuforums.org/showthread.php?t=845327)


cheers

---

### Post by geoff07 on 2010-02-18
Thanks for that. I use ffmpeg a lot and I think I have all the codecs!  I was thinking it might be a permissions issue myself, tho I cannot figure out where it might be. Weird.  I have another machine with firewire and Karmic, I think I will have to test on that.

---

### Post by bayvista on 2010-03-26
I am using Karmic and Kino with a Canon 630i. Kino recognises the camera which I am using to convert VHS video to DV. The video plays in the preview window. The capture button seems to work OK but I am only capturing 1 sec of video. Any suggestions welcome.

---

### Post by Mariane on 2011-05-16
I had the same problem. I had to give back the camera or pay another 120 euros for another day of renting it. Now I have rented a small video player which plays these tapes (64 euros per day). 

If we had warning messages during install such as "The capture function of this program will not work with your current version of Ubuntu" I would have tried some other program instead of loosing my time trying to make this one function and I might have saved 64 euros. 

The same thing happens with the video player: when I click on "capture" it counts down from "Waiting for DV 10" to "Waiting for DV 1" and then stops the tape, displaying the message "AV/C controls enabled". 

Mariane

---

