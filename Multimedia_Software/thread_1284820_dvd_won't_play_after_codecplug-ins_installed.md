---
title: "dvd won't play after codec/plug-ins installed"
date: 2009-10-07
forum: Multimedia Software
---

### Post by ghostofzuul on 2009-10-07
hello. pseudo newbie here... running jaunty 9.04...

so i got a dvd rom installed and all the proper codecs and plugins installed... and dvd's still won't play... 

in both vlc and movie player what happens is the program goes to open the disc it flashes on the screen for a moment and then the program closes. same behavior with both programs. i went to check on my xorg file and it was blank...

vlc and movie player work fine for avi and xvid files... just not dvd's. 

i also tried to use xbmc and while i got it to install ok... it wouldn't open saying something about 24 bit color depth and i have no idea how to change that... 

thanks!

---

### Post by jimmers on 2009-10-07
Hi,
Have you tried installing Libdvdread4, libdvdcss2, Ubuntu-restricted extras, all available through
SPM.

Jimmers

---

### Post by ghostofzuul on 2009-10-07
> **jimmers said:**
> Hi,
Have you tried installing Libdvdread4, libdvdcss2, Ubuntu-restricted extras, all available through
SPM.

Jimmers

hi jimmers thanks for your reply...

yes... all the packages you list have been successfully installed and yet i still have the problems i detail above... quite vexing! 

not quite sure how to proceed...

---

### Post by mc4man on 2009-10-07
open vlc from the terminal with this, then try to play a dvd ( media -> open disc.

See what errors are shown in the debug output

```
vlc -vv
```
or if you'd rather read from a log file then the terminal use this, after vlc fails then look for log in home folder

```
 vlc -vv > vlc-output.log 2>&1
```

---

### Post by ghostofzuul on 2009-10-07
> **mc4man said:**
> open vlc from the terminal with this, then try to play a dvd ( media -> open disc.

See what errors are shown in the debug output

```
vlc -vv
```
or if you'd rather read from a log file then the terminal use this, after vlc fails then look for log in home folder

```
 vlc -vv > vlc-output.log 2>&1
```

this looks like the main error... although there seems to be little errors here and there. i'm not sure of the significance of those... the debug output is pretty long... i hesitate to copy/paste it here b/c of length so i'm posting what to my extreme novice eyes appears to be the problem? 

[i][????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82
[/i]

---

### Post by mc4man on 2009-10-07
Try opening vlc -> tools -> preferences and click on video icon
In the output box change in the drop down from default to X11 and click save.

Then close and reopen vlc and try playback again

You may want to see what video drivers you're using, if any, and if any options exist there ( only use nvidia cards here which for the most part work well vs. continuing issues with ati and intel

---

### Post by ghostofzuul on 2009-10-07
> **mc4man said:**
> Try opening vlc -> tools -> preferences and click on video icon
In the output box change in the drop down from default to X11 and click save.

Then close and reopen vlc and try playback again

You may want to see what video drivers you're using, if any, and if any options exist there ( only use nvidia cards here which for the most part work well vs. continuing issues with ati and intel

i have a dreaded intel driver... and found this thread about the problem:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/374258](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/374258)

however... my x11.org file doesn't look like the one in the last post in that thread so the fix they suggest won't work for me... or at least... i don't know how to do a workaround... i have a few more threads to read but it seems like i might be stuck for the moment... :(

---

### Post by ghostofzuul on 2009-10-07
> **mc4man said:**
> Try opening vlc -> tools -> preferences and click on video icon
In the output box change in the drop down from default to X11 and click save.

Then close and reopen vlc and try playback again

You may want to see what video drivers you're using, if any, and if any options exist there ( only use nvidia cards here which for the most part work well vs. continuing issues with ati and intel

interesting... when i drop down and change the output to x11 it will play the dvds but the color is totally wrong. and the video is super slow and choppy... one step closer though! :)

---

### Post by mc4man on 2009-10-07
The only thing I really know about intel is i'm glad I don't have. 

Maybe keep your eye on the karmic forums, improvements  where expected ( don't think it's happened yet)

Am curious about something and can't hurt to try.

In the vlc video dropdown see if there is a "Simple Direct Media...." option. If so select, save and give it a try.

---

### Post by ghostofzuul on 2009-10-07
> **mc4man said:**
> The only thing I really know about intel is i'm glad I don't have. 

Maybe keep your eye on the karmic forums, improvements  where expected ( don't think it's happened yet)

Am curious about something and can't hurt to try.

In the vlc video dropdown see if there is a "Simple Direct Media...." option. If so select, save and give it a try.

audio... no video w/ simple direct... 

thanks for your help!

---

