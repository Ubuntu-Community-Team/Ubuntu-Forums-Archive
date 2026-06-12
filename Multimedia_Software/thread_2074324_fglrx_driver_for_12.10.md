---
title: "fglrx driver for 12.10"
date: 2012-10-21
forum: Multimedia Software
---

### Post by weseven on 2012-10-21
Hi all, I have a ATI HD 6870 video card and I was using the official fglrx driver from the repos in Ubuntu 12.04.

Since I upgraded to 12.10, though, the fglrx driver still installs correctly but it's not active, and a compatibility driver is used (in system details says VESA:BARTS).

I tried removing and purging and reinstalling the fglrx or the fglrx-updates driver, re-doing aticonfig --initial but still with no success.

(the catalyst control center actually works and displays all the correct infos).

Can anyone help getting the fglrx driver working?

---

### Post by cor2y on 2012-10-21
Actually its working however the video playback is having tearing issues, in 12.04 it listed VESA-BARTS as well on my machine but fglrx was working . I know its working because Unity 3D and my 3D based games all run as normal with no slow downs or graphical issues. Its just video playback thats terrible regardless of which video player is in use. This didnt happen on 12.04 at all so its either a kernel issue or something with this new driver when it interacts with Unity. I'll have to install gnome-shell and boot into it to see if thats the case.

---

### Post by weseven on 2012-10-21
> **cor2y said:**
> Actually its working however the video playback is having tearing issues, in 12.04 it listed VESA-BARTS as well on my machine but fglrx was working . I know its working because Unity 3D and my 3D based games all run as normal with no slow downs or graphical issues. Its just video playback thats terrible regardless of which video player is in use. This didnt happen on 12.04 at all so its either a kernel issue or something with this new driver when it interacts with Unity. I'll have to install gnome-shell and boot into it to see if thats the case.

I don't think it's working as intended, in 12.04 it was listed right (don't remember if fglrx or other, surely not vesa)and running a test like fglrx_glxgears dealt >16k fps... now it's around 200/300.

I did not try with something more stressful, like a game, though.

---

### Post by cor2y on 2012-10-21
It looks like its a Unity/Compiz issue, in  Gnome Shell video playback is tearless and video adapter is listed as fglrx (at least on my system)

---

### Post by weseven on 2012-10-21
that's interesting, I'll try installing another de to see if the problem's still here.

---

### Post by novafluxx on 2012-10-21
> **weseven said:**
> that's interesting, I'll try installing another de to see if the problem's still here.

Please check out this thread and let me know if that helps you

[http://ubuntuforums.org/showthread.php?p=12309529#post12309529](http://ubuntuforums.org/showthread.php?p=12309529#post12309529)

---

### Post by weseven on 2012-10-21
> **novafluxx said:**
> Please check out this thread and let me know if that helps you

[http://ubuntuforums.org/showthread.php?p=12309529#post12309529](http://ubuntuforums.org/showthread.php?p=12309529#post12309529)

thank you, it really made sense, but I still have the same situation as before on my system.
I made sure to remove and purge fglrx-updates, reverted xorg.conf to an almost blank one, rebooted, made sure there was no fglrx module loaded (there was none in the system), reinstalled linux-headers-generic (which was still installed), reinstalled fglrx-updates, redone aticonfig --initial, rebooted but still using that VESA:BARTS :(

this is my xorg.conf, if it's of any help: [http://pastebin.com/By1603ux](http://pastebin.com/By1603ux)

I still have no clue what is wrong, since fglrx was working pretty much out of the box in 12.04...

---

### Post by crushkittykitty on 2012-10-22
here is how i fixed mine same card mine was for running hdmi just you tube search it 
"ubuntu 12.10 installing ati drivers for hdmi"

---

### Post by weseven on 2012-10-22
> **crushkittykitty said:**
> here is how i fixed mine same card mine was for running hdmi just you tube search it 
"ubuntu 12.10 installing ati drivers for hdmi"
what you are suggesting isn't reasonable: I don't have any nvidia hardware on the system, I don't need any nvidia driver.
It worked for you because installing the nvidia driver removes fglrx, which then you reinstall after a reboot (but at this point with linux-headers-generic in your system). 
This however does not work in my case :/

---

### Post by cor2y on 2012-10-23
An update . its being recommended that those having issues with 12.10 and the fglrx driver go back to 12.04 or stay there if you havent yet upgraded, apparently theres a whole mess of issues involving unity and compiz as relates to the 12.10 fglrx driver and because 12.10 uses a special/old version of xorg grabbing the latest beta driver directly from AMD will not work. The other option if you dont want to reinstall 12.04 is to leave unity desktop behind and go with plain gnome 2.0 or gnome shell which will  alleviate some of the issues but not all. Finally this problem isnt only limited to AMD cards , nvidia card users are also reporting problems and slow downs if the phoronix forums are to be believed.

---

