---
title: "Issue using TV-Only with NVIDIA in Feisty"
date: 2007-06-17
forum: Multimedia &amp; Video
---

### Post by rahmza on 2007-06-17
Hey everyone,

I'm having a heck of a time trying to figure out how the heck to get TV Out working properly with Feisty Fawn. Here's my setup and what's happening. Any thoughts or suggestions on what to do would be great.

Basically, I'm trying to setup my Television as the only display to use so I can set it up as a MythTV Setup. I'm using a GeForce4 Ti4600 graphics card. I plugged in the TV using an S-Video Cable with a small S-Video to Composite Adapter and setup my Xorg.conf. The strange thing is, it will actually work properly as long as I have another monitor plugged in to the VGA port (I imagine this is the case for DVI too). It actually will turn off the CRT, and show things only on the TV. I can then disconnect the other monitor as if nothing happened.

The problem comes though when another monitor isn't connected. The system will hang when trying to startup Xorg and I can't get out of it to a console or anything. I can't figure out what the heck the problem is. I'm running Feisty Fawn with all the latest updates. I haven't tried using the NVIDIA drivers from their website, but I'm willing to try if y'all think it will help.

I've also attached my xorg.conf, a log of Xorg where it starts up properly (not .old), and one where it hangs (old). In the logs, it looks like it hangs on the last line, where it just continues during the log with the CRT attached.

Thanks and again, any suggestions would be appreciated. I want to use a MythTV setup but I don't want to have to keep this monitor with it at all times!

Attached are:
Xorg.0.log.1.txt (First portion of log with CRT attached. File was to large by itself)
Xorg.0.log.2.txt (Second portion of log with CRT attached)
Xorg.0.log.old.txt (Log with no CRT attached where it hangs)
Xorg.conf (My Xorg config file)

---

