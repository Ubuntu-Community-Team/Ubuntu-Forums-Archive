---
title: "Ringtail: Black line at top of screen on fullscreen playback"
date: 2013-04-27
forum: Multimedia Software
---

### Post by sdgiffin on 2013-04-27
On 13.04 Ringtail, during fullscreen video playback, I'm seeing a black line at the very top of the screen where the Menu bar is normally (see screen shot). It's happening on Totem, GnomePlayer, Xine, and even VLC, and it's a little annoying. Anybody know how to fix this? And before you ask, yes, that's Torchwood: Miracle Day. I chose it  specifically because the white title screen showed off the line most  prominently.

[IMG]http://i114.photobucket.com/albums/n256/evilsupahfly/Screenshotfrom2013-04-27124908_zps6d2ec13f.png[/IMG]

---

### Post by P4N0 on 2013-04-27
> **sdgiffin said:**
> On 13.04 Ringtail, during fullscreen video playback, I'm seeing a black line at the very top of the screen where the Menu bar is normally (see screen shot).


Hello,

Here is same. It's really-really annoying.
Any solutions? This is a bad bug.. I'm so nervous :@

The cursor and navigation is disappear after switching to full screen but this disgusting line not.

---

### Post by P4N0 on 2013-04-27
[CENTER][B] 
_I found the solution!_[/B]
[/CENTER]
 
[CENTER]**Try to enable workspaces in the system settings - >appearance -> behavior .**
[/CENTER]
 
It's work for me now.

---

### Post by jimmy321 on 2013-04-28
enabling workspaces had no effect on mine but for vlc if you drag the video to the top where it maximizes and go full screen the black line is gone :)

the black line also disappears when you drag the video to the side, where it half-maximizes, and then go fullscreen

for online videos playback the line is gone so thanks for the enable workspace tip however they should fix this bug cause some of us don't really use workspaces and for me personally i don't like having an icon in the launcher about something that i don't use just for a workaround to a bug

---

### Post by sdgiffin on 2013-04-29
The solution is to enable Workspaces?

....

:(

---

### Post by Thee on 2013-04-29
I got the same issue.

---

### Post by KiDQUiCK on 2013-05-01
I had this issue as well. 

Surprisingly the "enable workspaces" solution worked for me... mostly. Double-clicking in VLC does indeed fullscreen the video without the black line. But when I move the mouse the black bar re-appears... then disappears again when the VLC navigation controls and mouse cursor disappear after 2-3 seconds of no mouse movement. Strange...

FWIW, this is my graphics hardware:
```
$ lspci | grep "VGA"
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
```

---

### Post by terriblechild on 2013-05-03
I have the same issue. I haven't tried the workspaces workaround, but even if it works, they still need to fix the bug, as many people (like me) don't use multiple workspaces.

---

### Post by brainwash on 2013-05-03
Bug report: [https://launchpad.net/bugs/1170958](https://launchpad.net/bugs/1170958)

---

