---
title: "Should Mythbuntu switch to LXDE to avoid long-standing HDMI bug in XFCE?"
date: 2016-08-26
forum: Mythbuntu
---

### Post by gottabefoss on 2016-08-26
There's a long-standing unfixed HDMI bug in XFCE that has been posted to launchpad (with suggested user patches) for at least 2 years. What happens is that if your computer uses HDMI and you switch off the TV (or receiver if hooked up through the stereo) the output resets to NULL and will not come back when you turn the TV back on, or alternately, the screen will return, but the sound disconnects. It can be reset by ssh'ing into the computer, and doing some xrandr magic. Which then will turn blank again next time the user turns the TV off.

The XFCE maintainers have not released a fix upstream, so Mythbuntu is fairly unfriendly to new users who attach their PC to their TV and/or receiver using HDMI.

The problem is specifically in the [COLOR=#000000]xfsettingsd[/COLOR] daemon, so is easily bypassed by either using a different desktop manager or for users that use kodi, by running kodi in stand-alone mode (i.e., without a desktop manager).

See:

[LIST]
[*][https://bugs.launchpad.net/ubuntu/+source/xfce4-settings/+bug/1575123](https://bugs.launchpad.net/ubuntu/+source/xfce4-settings/+bug/1575123)
[*][https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1308105](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1308105)
[*][https://ubuntuforums.org/showthread.php?t=2276556](https://ubuntuforums.org/showthread.php?t=2276556)
[/LIST]

Considering LXDE is lightweight much like XFCE is and completely avoids this issue, should Mythbuntu consider replacing XFCE with LXDE by default?

Switching default desktop managers to one that avoids this HDMI-killing bug would certainly make mythbuntu significantly friendlier to new users.

---

### Post by uteck on 2016-08-26
Or use LXQT, which is LXDE but using QT and not GTK. It is not quite ready for prime-time, but should be soon.

---

### Post by Bucky Ball on 2016-08-26
I have a Raspberry Pi and doesn't matter what DE I use on that; if you switch the TV off goes back to null. I've used LXDE and XFCE4 on it. No different.

---

### Post by tgm4883 on 2016-08-27
> **gottabefoss said:**
> There's a long-standing unfixed HDMI bug in XFCE that has been posted to launchpad (with suggested user patches) for at least 2 years. What happens is that if your computer uses HDMI and you switch off the TV (or receiver if hooked up through the stereo) the output resets to NULL and will not come back when you turn the TV back on, or alternately, the screen will return, but the sound disconnects. It can be reset by ssh'ing into the computer, and doing some xrandr magic. Which then will turn blank again next time the user turns the TV off.

The XFCE maintainers have not released a fix upstream, so Mythbuntu is fairly unfriendly to new users who attach their PC to their TV and/or receiver using HDMI.

The problem is specifically in the [COLOR=#000000]xfsettingsd[/COLOR] daemon, so is easily bypassed by either using a different desktop manager or for users that use kodi, by running kodi in stand-alone mode (i.e., without a desktop manager).

See:

[LIST]
[*][https://bugs.launchpad.net/ubuntu/+source/xfce4-settings/+bug/1575123](https://bugs.launchpad.net/ubuntu/+source/xfce4-settings/+bug/1575123)
[*][https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1308105](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1308105)
[*][https://ubuntuforums.org/showthread.php?t=2276556](https://ubuntuforums.org/showthread.php?t=2276556)
[/LIST]

Considering LXDE is lightweight much like XFCE is and completely avoids this issue, should Mythbuntu consider replacing XFCE with LXDE by default?

Switching default desktop managers to one that avoids this HDMI-killing bug would certainly make mythbuntu significantly friendlier to new users.

You can use Mythbuntu-control-centre to install/configure mythtv on any DE. Mythbuntu isn't releasing any more ISOs, so there isn't really a default DE to worry about.

---

