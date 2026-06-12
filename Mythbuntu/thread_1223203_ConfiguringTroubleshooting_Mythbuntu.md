---
title: "Configuring/Troubleshooting Mythbuntu"
date: 2009-07-25
forum: Mythbuntu
---

### Post by deamon_knight on 2009-07-25
So I took the plunge and got a new vidcard, an HVR-1600 and a new HDD and installed Mythbuntu. I'm still feeling my way through but all the hardware seems compatible. 

However, I thought there would be a desktop enviornment that the 10' GUI was running on top of, but this does not seem to be the case, I get a terminal window and the 10' GUI (and update manager, incidentally). This seems to have changed after I ran Update Manager, before it looked like there was a XFCE desktop but no panels, only menus on right click. I'm not sure what went wrong or how to fix it, update manage launches on startup and this feels like a saved sessions setting I've gotton wrong but with no desktop I don't know how to fix it.

Also, I looked to install VPUAD. Can someone confirm for me, this is NOT enabled in Mythbuntu 9.04 by default, I have remove the existing NVidia driver, add some additional repos and then install the updates, correct?

Thanks

---

### Post by crez79 on 2009-07-25
It sounds like there is an xfce is running but the panels are off the screen. Check the resolution to make sure. Try pressing alt+F2 and running "xfce4-display-settings" to see if you can sort it.

For VDPAU, check [here]("http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html"). It explains exactly what to do and is very easy. You didn't mention what video card you are using, but make [sure to verify it is VDPAU compatible]("http://www.mythtv.org/wiki/VDPAU").

---

### Post by deamon_knight on 2009-07-26
Thanks crez79, that got me thinking. I can alt+F2 and get a prompt, and I can run xfce4-panel , but I can't figure out no panels are launching on startup, or why Update Manager is loading on startup.

I've got an EVGA 9400GT vidcard, that looks like it will be enough.

---

### Post by crez79 on 2009-07-26
The Update manager popup is the new behavior in jaunty. Many find it annoying, but it can be[ fixed easily enough.]("http://maketecheasier.com/remove-the-annoying-update-manager-pop-up-in-ubuntu-jaunty/2009/06/18")

I have no idea why the panels aren't starting up. I don't like xfce much so I installed and use gnome. It is a little more of a resource hog, but I haven't seen a difference.

That video card should be fine. Applying the backports is easy and well worth it.

---

### Post by deamon_knight on 2009-07-26
Thats not the behavior I'm experiencing, I think. Update Manager is popping up on startup even when there are no updates available. Its as though I saved a session with it active and now it won't go away.

---

### Post by deamon_knight on 2009-07-26
After two reinstalls I managed to do the steps in an order that would not result in no desktop. I'm sure the problem has something to do with saving the session on shutdown, so instead of clicking restart from the popup box after the updates completed I checked all may setting and restarted mnaually.

I'm getting infrequent "Can't Start X, load Ubuntu in low graphics mode?" on startup.

I'm COMPLETELY overwhelmed by the number of options now. I added the extra repos (big thanks to the guy behind this!) I can now select VDPAU but I'm not sure if I should always be using it. There are so many rules...

I'd also like to know if its easy to transcode recorded TV to a smaller filetype and eliminate Commercials. I know its possible but what would I change an MPG to?

IMHO, Embedding the configurations on a dozen pages into the 10' GUI is very difficult to navigate.

The only digital tuner I have is now in my Mythbox. Is there any easy way to scan and view channels without configuring schedules direct? I'm trying to match their lineups to what I actually Receive, but its had to juggle all the settings.

I also need to find where the options are to shutdown/reboot the system when exiting the 10' GUI, I did it once and cannot locate that entry again.

Now I guess I need some pointers on how to configure this thing!

---

### Post by deamon_knight on 2009-07-28
Looks like I'm still having problems. The two deal breakers are the Nvidia drivers don't always load, and I'm not getting sound from analog cable. It looks like the avenard repos are loaded as VDPAU is enabled and seems to work when the nvidia drives want to load, they just don't all the time, any suggestions?

---

### Post by deamon_knight on 2009-07-28
And, I think I solved Both those problems here:

[http://ubuntuforums.org/showthread.php?p=6315676#post6315676](http://ubuntuforums.org/showthread.php?p=6315676#post6315676)

Had an HVR-1600. 

Now, I'm having an error with the nvidia control app, it won't save changes because it says it can't creat the backup xorg.conf

---

### Post by chcubsfan on 2009-07-29
Make sure you are running the nvidia control panel with sudo, you won't have write privs to /etc otherwise.

sudo nvidia-settings

from a terminal

---

