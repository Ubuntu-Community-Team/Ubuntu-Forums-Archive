---
title: "Natty + Gnome 3 : screensaver when watching a video"
date: 2011-05-04
forum: Multimedia Software
---

### Post by Romu on 2011-05-04
Hi all,
I thought this bug was fixed few years ago :(

I made a fresh Natty installation + Gnome3. Everything seems fine except some screensaver or energy saver starts even while watching a video.

Any idea to fix this?

Thanks.

---

### Post by hkbruvold on 2011-05-04
I have exactly the same problem.

EDIT: Removing gnome-screensaver didn't help.

SECOND EDIT:
Removing and killing the already running gnome-power-manager might be a way around to problem. But that is not a good solution.

---

### Post by Romu on 2011-05-05
Hi,
I've tried to disable the "Dim screen after X mns" in the system settings, but that doesn't change the issue.

I've just tried to create a bug report on Launchpad, my attempt as failed because of the OpenPGP signature. What a difficult process, just to create a bug report!! Personnaly I give up, if someone want to create this bug report, feel free.

---

### Post by hkbruvold on 2011-05-05
Yeah. All the removing thing did not wark. It din't dim slowly, it just got black after a couple of minutes. And I couldn't change the time it take before it get back.

EDIT:
After running
```
gsettings set org.gnome.desktop.screensaver idle-activation-enabled false
```
the screensaver (or at least the dimming) went away. But after 1 min 40 sek the screen turns off. 
And if I set the brightness setting to two minutes the screen turns off after about 3 minutes. There must be another setting in the screensaver application that did not got changed.


SECOND EDIT:
OK, so I did some more research and figured out something that (by now) seems to work.

This is what I did:
First turn off the gnome screensaver:
```
gsettings set org.gnome.desktop.screensaver idle-activation-enabled false
```
Then turn off DPMS:
```
xset -dpms
```
And then I had to make it do that every time I log in.
Add "xset -dpms" into gnome-session-properties

I've tested it for about 10 minutes, and so far it works.


To restore the changes:
```
gsettings set org.gnome.desktop.screensaver idle-activation-enabled true
```
```
xset +dpms
```
And remove the entry from gnome-session-properties.

---

### Post by Romu on 2011-05-06
Thanks for this tricky fix, maybe too much tricky for me, but that's the only one I have.

I've tried caffeine and this doesn't fix the issue.

---

### Post by el_bandido on 2011-08-09
is it just me, or is gnome 3 utterly terrible? I have just about got used to the interface, but I can't change the screen saver, can't disable it while VLC is running, can't swap the DEL key to be the move to wastepaper bin shortcut (despite trying the gconf-editor tick box setting), have to press ALT to shut the ******* thing down (though fixed with extension) and can't even add a shortcut to my sodding pictures folder on the dash.

RAGE.

---

### Post by m10 on 2011-09-04
i'm using oneiric now and it is an issue there too :(

---

### Post by edbova on 2011-09-27
All you have to do is open ubuntu software center search gnome screen saver then click more info and add power manager for xfce desktop with that you will be able to set the screen to always stay on or any settings you want

---

