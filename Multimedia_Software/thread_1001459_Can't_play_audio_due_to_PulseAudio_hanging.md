---
title: "Can't play audio due to PulseAudio hanging"
date: 2008-12-04
forum: Multimedia Software
---

### Post by Fibonacci on 2008-12-04
Ever since upgrading to Intrepid Ibex, I've noticed that audio suddenly stops working for all apps. The cause always seems to be that /usr/bin/pulseaudio has hanged, and nothing short of killing and restarting the program will fix the problem - at least until it manifests again after PulseAudio has been running for about 2 days. However, the daemon does not respond to SIGINT or SIGTERM (kill -2 and kill -15 respectively), so I invariably have to use SIGKILL (kill -9) to terminate the program.

Following a suggestion on another thread, I decided to run pulseaudio -vv and record the output. The bzip2'ed log is attached to this message (the original file was 6.7 MiB in size). Some interesting output lines I noticed:
```

D: memblock.c: Pool full
D: memblock.c: Pool full
   (repeated 936 times)
W: protocol-native.c: Failed to push data into queue
D: memblock.c: Pool full
   (randomly printed one or the other 5000 times)
W: protocol-native.c: Failed to push data into queue
   (repeated over 42000 times)

```

Has anyone here experienced this problem? Is there anyway to prevent it that does not involve completely getting rid of PulseAudio?

Thanks in advance.

---

### Post by boxrec on 2008-12-05
bump - got the same problem

---

### Post by Fibonacci on 2008-12-06
I forgot to mention this on my first post.
If I try to open the PulseAudio volume control when PulseAudio has hanged, I get the following error message before the program automatically closes:
> 
Connection failed: Timeout

Whenever I try to play audio via MPlayer (which, by the way, works like a charm when PA is not hanged) on the same situation, I get the following error message:
> 
[AO_ALSA] alsa-lib: pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Timeout

[AO_ALSA] Playback open error: Connection refused
Could not open/initialize audio device -> no sound.


Any ideas on what could be causing this?

---

### Post by jellyfisharepretty on 2008-12-14
I am glad I am not the only one.  I have the *exact* same problem you described, Fibonacci. I tried the same stuff you did.  Finally I made a bash script that kills and restarts pulseaudio, I run it every one or two days, whenever I see my audio is not working.

You are correct in saying mplayer will refuse to start with this error.  I can also say that I will get no sound in flash in Firefox unless I restart pulseaudio, and then Firefox too, which is very annoying.

In fact all media apps will hang of refuse to start with an error relating the the sound server connection.

I would much like to know if anyone knows how to fix this problem.
Thanks!

BTW I have a creative audigy 2 pci card.  When pulseaudio has not hanged, sound works beautifully across all applications.


EDIT: I forgot to write what I see at the command line whenever pulseaudio has hanged.  I get many, many lines just saying

```
W: protocol-native.c: Failed to push data into queue
```

---

### Post by 2hot6ft2 on 2008-12-14
Here are a few options to choose from from fixing pulse to disabling it and using asla or esound.

First fixing pulse
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

Disabling pulse and using alsa
[http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a)
and another one going the same route here
[http://ubuntuforums.org/showthread.php?p=6370902#post6370902](http://ubuntuforums.org/showthread.php?p=6370902#post6370902)

Replacing pulse with esound
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

There are more but this gives you some alternatives that are being used.

---

### Post by Fibonacci on 2008-12-14
> **jellyfisharepretty said:**
> You are correct in saying mplayer will refuse to start with this error.  I can also say that I will get no sound in flash in Firefox unless I restart pulseaudio, and then Firefox too, which is very annoying.

Couldn't have said it better.

> **2hot6ft2 said:**
> First fixing pulse
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

(...)

Replacing pulse with esound
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

Why are those two links of yours the same?
Also, I had hoped I could have fixed PulseAudio instead of removing it - but I will remove it if there's no other option.

---

### Post by jellyfisharepretty on 2008-12-15
Actually, I quite like PulseAudio when it is working, so I'd also prefer to keep it.

---

### Post by markbuntu on 2008-12-15
Have you tried reinstalling pulseaudio?
also,there is a pulseaudio update today. that might fix your problem.

---

### Post by jellyfisharepretty on 2008-12-15
I think I'll try what is suggested _[here]("http://www.uluga.ubuntuforums.org/showpost.php?p=6339805&postcount=5")_ first, that is, change buffer settings of PulseAudio.

Then I'll try the update.  Do you know if the update will be through the ubuntu repositories and synaptic/apt-get or do I have to get the update directly from the PulseAudio website ?

If these steps don't work, I'll try reinstalling it.  And if that doesn't work, well I guess I just switch back to using plain old ALSA I guess.

I'll keep you posted of my findings.  Might take some days though, because I get this problem at about 1,2 or 3 days intervals.

---

### Post by kostkon on 2008-12-15
> **jellyfisharepretty said:**
> I think I'll try what is suggested _[here]("http://www.uluga.ubuntuforums.org/showpost.php?p=6339805&postcount=5")_ first, that is, change buffer settings of PulseAudio.
Also make yourself a member of the *pulse* and *pulse-rt* group, if you haven't done this already.

You can easily do it in System &#8594; Administration &#8594; Users and Groups.

---

### Post by jellyfisharepretty on 2008-12-15
Thanks Kotskon.  Upon checking, I was already a member of those groups.

---

### Post by jellyfisharepretty on 2008-12-19
Well, it's been 3 days without any incidents regarding PulseAudio.  So far so good.  I think either the PA update fixed it, or removing the buffer settings in the config file did it.  Unfortunately, I changed both those things at the same time.

If there's no more PA hanging in another 3 days, I think we can probably declare this fixed.

---

### Post by jellyfisharepretty on 2008-12-20
Sorry to post here again, but the problem has not been fixed, since PA hung again.  So we'll have to keep searching for a solution.

---

### Post by Fibonacci on 2008-12-21
Sorry to come so late, but the problem just reappeared yesterday night.
My case is slightly different from jellyfish's, since that bit about default-fragments and default-fragment-size-msec was **not** on my /etc/pulse/default.pa. I did update PA and was already a member of the mentioned user groups - according to users-admin, that is, because they don't show in the output of the groups command.

---

### Post by markbuntu on 2008-12-21
One thing that can happen with pulseaudio is that applications with poorly written alsa drivers can open and close devices at a rapid clip. When the device number reaches about 1,100 pulseaudio will crash. 

This was the problem with flash 9 and it is also a problem with some SDL apps.

You can check this in the PA Manager where you can see the sink numbers. If you see this, please file a bug report on the particular application or plugin.

default-fragments and default-fragment-size is in /etc/pulse/daemon.conf

---

### Post by chocolateboy on 2008-12-22
[Bug #288093: Can't play sound because of pulseaudio hang]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/288093")

---

### Post by Fibonacci on 2008-12-23
> **markbuntu said:**
> One thing that can happen with pulseaudio is that applications with poorly written alsa drivers can open and close devices at a rapid clip. When the device number reaches about 1,100 pulseaudio will crash. 

This was the problem with flash 9 and it is also a problem with some SDL apps.

You can check this in the PA Manager where you can see the sink numbers. If you see this, please file a bug report on the particular application or plugin.

Apparently they don't. But I'm not sure since I can't check anything after a crash.

*Edit:* I just checked, and no, the sink numbers never even exceeded 10 before PA hung again.

> **markbuntu said:**
> default-fragments and default-fragment-size is in /etc/pulse/daemon.conf

Thank you, tried that too and PA took even less time to hang.

> **chocolateboy said:**
> [Bug #288093: Can't play sound because of pulseaudio hang]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/288093")

Apparently this is exactly the same problem I'm experiencing. Good find!

---

