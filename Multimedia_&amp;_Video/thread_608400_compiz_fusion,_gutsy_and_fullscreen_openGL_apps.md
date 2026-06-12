---
title: "compiz fusion, gutsy and fullscreen openGL apps"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by karlhm76 on 2007-11-10
Hi all, I have an annoying problem that is probably caused by a combination of compiz fusion and the nvidia driver, but its been happening for quite some time on pretty much every version of Ubuntu I've run compiz fusion on, and its really beginning to bug me.

If I play a fullscreen openGL game such as SDLmame and I have compiz fusion activated, after a certain time, which is random as far as I can tell, the fullscreen app will suddenly become windowed and my mouse and keyboard stop working. Most of the time the app continues to play with no input, but a couple of times the system appeared to totally freeze up.

The solution is to perform a reset, turn off compiz in the appearance options, and restart playing.

It only happens in fullscreen openGL apps. If I play a video fullscreen it is fine, and if I play a windowed openGL app it is also fine. That's why I think it could be because of the nvidia driver.

Anyone have any more information on this, perhaps a fix or a bug report?

---

### Post by karlhm76 on 2007-11-11
anyone? surely someone having the same problems?

---

### Post by warjowuch on 2007-11-11
yeah same here, when I open gl-app or dosbox fullscreen, avery now and then it becomes windowed, but after 10 seconds, it comes back to fullscreen.
But, since gutsy, it i salso with gnome.
THe weird thing is, at first it was with the appearance of new windows, but now no new windows appear. I think it might have something to do with 'check new mail' or the wheather applet of gnome, whih updates every 5 minutes. I have to try these. THen a bugreport may be filed.

---

### Post by warjowuch on 2007-11-13
Ok, with thunderbird off and my wheather-applet not updating... no success.
I don't understand, it must be something which does something every 5 minutes or so.

I did mention an improvement after I set the fullscreen-starting app to windowed-mode, and then put it back to normal. Soon another small test...

---

### Post by warjowuch on 2007-11-16
But even this test failed... So, I am searching for a launchpad entry, and will otherwise file a bugreport!
Still, I'd like to know if other people have this issue.

---

### Post by Toffeeapple on 2007-11-16
not sure if this will help...

but!

I was getting similar problems while playing Neverwinter Nights... I turned off the screen saver and disabled the monitor power saving and the problem went away.. not sure which of the two sorted it.

try that.

---

### Post by Seine on 2007-11-17
Yes I have this too and its quite annoying. It happens for me in MAME, PadMan & ET:QW. As you say, all full screen OpenGL apps.

Has a launchpad question or defect been raised?

BTW, no need to reboot. Hold CTRL+ALT+F6 for a terminal (login and) then use kill to remove the stalled app. CTRL+ALT+F7 to get back to your desktop.

---

### Post by warjowuch on 2007-11-19
launchpad: see

[https://bugs.launchpad.net/ubuntu/+source/trigger/+bug/163865](https://bugs.launchpad.net/ubuntu/+source/trigger/+bug/163865)

I Will relate to this thread from there as well...

Disabling powersave and screensaver... Yeahm it is plausibvle this has something to do with it. Every 5 minutes it happens here, and my screensaver activates after 5 minutes... Wow, i'd like to try

---

### Post by OneGravenKiss on 2007-11-21
I have a Radeon 9600 pro and I found this info very helpful. [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)   It got rid of XGL whic disables your 3d rendering when you use compiz and replaces it with a driver that ATI can use that keeps the 3d rendering enabled. I do not know what you guys can do with Nvidia but you can follow some of what this says.

---

### Post by warjowuch on 2007-11-22
Thanks for your reaction here :)
But I don't think it applies to our problem. 

THe problem is not that we have no 3d accelleration, but it is when fullscreen applications are opened up, the screensaver seems to steal focus when the mouse is untouched. It does not really display the screensaver, but the trigger wehen it should've gone into screensaver-mode, is enough to loose fullscreen-focus.

But, then again, maybe I don't understand your explanation... So if you please, maybe I've got it wrong...

---

