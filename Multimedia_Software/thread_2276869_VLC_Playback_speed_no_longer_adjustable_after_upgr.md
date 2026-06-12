---
title: "VLC Playback speed no longer adjustable after upgrade to 15.04"
date: 2015-05-05
forum: Multimedia Software
---

### Post by terrypearson on 2015-05-05
Hello,

I recently upgraded from 14.10 to 15.04. The only issue I had after upgrade was that I cannot adjust the playback speed in VLC anymore.

I try to adjust speed by going to Playback->Speed. Unfortunately, the speed is grayed out. (I also tried the shortcut keys, but still no luck).

Since this only started after upgrade, I thought I would start fresh. I did a `sudo apt-get purge vlc*` and then reinstalled vlc. I restarted the computer, and then tried again. Still, the speed menu is grayed out (Actually, title, chapter, program, custom bookmarks, and speed are all grayed out under the Playback menu, but I never use the other options, so I am not sure if that is normal). 

Has anyone else ran into this?

---

### Post by ajgreeny on 2015-05-05
Speed changes seem to work on my system which is running in VBox, but VLC is dreadfully unstable as far as I can see; whenever I make a change to anything in the preferences it seems to crash.

I also do not have any way of making VLC always start with the volume level set to 100%, as that option is also greyed out, like your speed controls.

I have used VLC as my default video player for a long time now, but if that is the way it's going to work from now on I shall quickly find another application; VLC at the moment in 15.04 is just too flaky to use as the default.  I hope it improves to become what I want very quickly.

As you upgraded it may be worth removing to trash the **~/.config/vlc** folder in your home to see if that helps.

---

### Post by mc4man on 2015-05-05
If you were to force menus back into vlc then they all would work. To see just start vlc from a terminal as such - 
```
export QT_X11_NO_NATIVE_MENUBAR=1 && vlc
```

To do that when opening vlc normally or from the context menu then you'd need to edit the Exec= line in vlc.desktop. currently in 15.04 it's - 
Exec=/usr/bin/vlc --started-from-file %U
change to -
```
Exec=env QT_X11_NO_NATIVE_MENUBAR=1 /usr/bin/vlc --started-from-file %U

```
It's possible this is a theming issue, clearly broken in ubuntu default light-themes in 15.04

---

### Post by terrypearson on 2015-05-06
Thank you to both of you for your ideas. I tried them both and I still have the speed bar missing. It is interesting that your VLC works and allows speed adjustments.

So I followed up by purging vlc and then removing the videolan ppa (hadn't realized I had this PPA active). I once again deleted the config files for vlc. Then reinstalled.

So now I am using Ubuntu's original release. The funny thing is that I still cannot update the speed. Everything is grayed out. 

Is there something else I might need to do to completely remove vlc and start fresh?

Thanks!

---

### Post by mc4man on 2015-05-07
As far as speed control via the menu - setting as described fixes here.
As far as "speed bar", that works by default > View > enable Status Bar to expose

---

### Post by andrew.46 on 2015-05-07
I can confirm mc4man's fix on Vivid (using vlc-git)...

---

### Post by mc4man on 2015-05-09
bug causing this - 
[https://bugs.launchpad.net/ubuntu/+source/lyx/+bug/1430059](https://bugs.launchpad.net/ubuntu/+source/lyx/+bug/1430059)

---

