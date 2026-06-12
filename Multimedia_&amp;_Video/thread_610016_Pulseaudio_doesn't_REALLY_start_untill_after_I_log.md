---
title: "Pulseaudio doesn't REALLY start untill after I log on"
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by 4KvRMU7Nnv on 2007-11-11
Ok so I have pulseaudio workign for all of my applications but when I log in, it takes a LONG time to get working.  After I log in, approximately 25 seconds later, the gnome volume mixer appears in the panel.  In addition to this, if i go to system>preferences>sound it takes a long time to open as well.  I believe this is because the actual daemon is not starting until after I log in.  Also, none of the comptuer noises work, liek the login noise or the logoff noise or the login is ready noise.  I was wondering whether the pulseaudio should be started in a lowerlevel part of startup like when the usplash screen is up, it shoudl be starting then and remaining on throughout my computer on time.  Other than this, pulseaudio is amazing, and i even feel like I have surround sound with only two speakers! hope someone can help.

:::EDIT:::
Found the problem.  If you add 

pcm.!default {
    type pulse
}

ctl.!default {
    type pulse
} 

to your /etc/asound.conf file, it will autostart as the default.  It is so beutiful...sniff :)

---

