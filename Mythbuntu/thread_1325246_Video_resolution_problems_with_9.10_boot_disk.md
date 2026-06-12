---
title: "Video resolution problems with 9.10 boot disk"
date: 2009-11-13
forum: Mythbuntu
---

### Post by Mr. Echo on 2009-11-13
During my first attempt to do a fresh install of 9.10, I ran into video problems.  As soon as 9.10 booted and X started, my Samsung TV started blinking "Mode not supported".  By pressing Ctrl-Alt-+ I was able to cycle through other resolutions that did give me video.  However, all of the other resolutions were too low and mythtv backend setup screens were too large for the TV.

I tried the safe graphics mode from the boot prompt but got the same results.  I tried it with two different nVidia cards and got the same results.

Is there way for me to specify the resolution that my TV needs at the boot prompt?  This problem didn't happen with 9.04.

---

### Post by Mr. Echo on 2009-12-05
I'll follow up my own post.  Hopefully this will help someone else.  Interestingly, the 64bit version of Mythbuntu 9.10 didn't have the problem that I described in the previous post.  When I booted it everything worked and my Samsung TV did not produce the "Mode not supported." message.  So I guess I'll switch to 64 bit.

I also learned that it's possible to install the nVidia proprietary driver once you've booted from the installation media.  You may have to use Ctrl-Alt-+ to find a temporary resolution that works but once you have video you should see a notification in the upper right corner that proprietary drivers are available.  You can download and install the nVidia driver even though you are running from the bootable media.  Once you do that, you have to find some way to restart X.  Since Ctrl-Alt-Backspace is disabled I had to find another way.  I wrote a small script that basically performs a "service gdm stop" and "service gdm start" and placed it in the /tmp directory.  Then I ran the script as root using the nohup command so that the script wouldn't die when X was shut down.  When X comes back up it should be running with the nVidia driver.  Running nvidia-settings will confirm that.

There may be a more graceful way to do this but it worked for me and will do in a pinch.

---

