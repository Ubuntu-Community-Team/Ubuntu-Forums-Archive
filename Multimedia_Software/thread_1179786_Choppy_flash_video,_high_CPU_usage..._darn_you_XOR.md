---
title: "Choppy flash video, high CPU usage... darn you XORG!!!"
date: 2009-06-06
forum: Multimedia Software
---

### Post by dfehrer on 2009-06-06
I just installed Ubuntu Jaunty on what was previously an XP computer and I have been having major problems viewing Flash videos in Firefox.  The Flash videos are really choppy, and whenever I try to view one, my CPU usage goes through the roof!  Even when I am NOT viewing a flash video, the CPU usage usually hovers around 40-50%.  Xorg seems to be the guilty party, but I am not sure what to do about it.

I tried installing the GNASH and swfdec packages, but those don't even work, so I had to go with the newest Adobe flash player.  I also tried the UXA fix ([https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance#Problem:%20%20UXA%20gives%20better%20performance%20than%20EXA%20-%20why%20not%20move%20to%20UXA?](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance#Problem:%20%20UXA%20gives%20better%20performance%20than%20EXA%20-%20why%20not%20move%20to%20UXA?))  (I don't know if that was relevant because I do not have an Intel Video Card, but it did not fix my problem.)

This is my videocard: 01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05).

Pretty much everything else on my computer is Intel.

I feel like my problem is the same as many Intel video card users are having, but there is even less support because I am have a Savage card.  Can anyone think of a fix for this?

Thanks a lot everyone!

---

### Post by lovinglinux on 2009-06-06
Welcome to the "choppy flash club".

> **dfehrer said:**
> I tried installing the GNASH and swfdec packages, but those don't even work, so I had to go with the newest Adobe flash player.  I also tried the UXA fix ([https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance#Problem:%20%20UXA%20gives%20better%20performance%20than%20EXA%20-%20why%20not%20move%20to%20UXA?](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance#Problem:%20%20UXA%20gives%20better%20performance%20than%20EXA%20-%20why%20not%20move%20to%20UXA?))  (I don't know if that was relevant because I do not have an Intel Video Card, but it did not fix my problem.)

No, it's not relevant. It's an Intel technology.

Check [this](http://ubuntuforums.org/showthread.php?t=1146943), [this](http://ubuntuforums.org/showthread.php?t=1152095), and [this](http://ubuntuforums.org/showthread.php?t=1178961).

---

### Post by dfehrer on 2009-06-07
Thanks for the reply LovingLinux.

I've tried EVERYTHING on the posts you sent.  Modifying xorg (one of these changes made me unable to display ANY graphics), tweaking the flash plugin, changing the ondemand file, testing in Opera.. Nothing seemed to work.

This is my first install of Ubuntu, so I only have Python 2.6 installed, and it uses hardly any CPU, so I don't think that is the problem.

I am curious if NVIDIA drivers could be causing this.  As I mentioned earlier, I have a S3Graphics Savage video card, and it looks like I already have drivers installed for that.  Can I uninstall everything NVIDIA?  Maybe this would help...  If I can't figure this out I guess I am just switching back to XP, unfortunately.

Thanks!

---

### Post by sandydoull on 2009-06-17
This seems to be linux-wide issue that has existed in as far back as version 9 of adobe flash player. Symptoms are choppy video playback especially when viewing fullscreen videos from sites such as youtube, BBCiplayer, hulu.com etc.

It might help if everyone who is having this issue goes to adobe's support site and votes for the bug to be worked on: [http://bugs.adobe.com/jira/browse/FP-1692](http://bugs.adobe.com/jira/browse/FP-1692)

Has anyone found a workaround for this issue, if so you might want to let them know over at adobe :lol:

---

### Post by gyre007 on 2010-11-15
The real question here is why is flah killing Xorg ?? it makes no sense...
once I close firefox or any other browser I donnt want to be disrupted by slowered performance of Xorg which is the case even after the browser using the flash is closed...
I though the restart of Xorg will help but the only thing that helps is restart of the whole system which is totally ridiculous..WE ARE NOT USING WINDOWS!!!
anyway...just my thoughts...as I've spent quite some time investigating this problem but I've given up decided to live without a flash...

---

### Post by Yellow Pasque on 2010-11-15
Thank you for necromancing this thread to post a rant. It's really useful....

---

