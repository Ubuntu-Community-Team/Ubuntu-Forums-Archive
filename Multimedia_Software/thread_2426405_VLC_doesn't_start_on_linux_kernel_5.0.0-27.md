---
title: "VLC doesn't start on linux kernel 5.0.0-27"
date: 2019-09-08
forum: Multimedia Software
---

### Post by whady on 2019-09-08
Hi all,

After upgrade the linux kernel to 5.0.0-27, VLC doesn't work anymore.
Boot kernels prior 5.0.0-27, VLC works fine.

I don't know why it's happening, but I believe this kernel version needs a fix.

Thanks.

---

### Post by mc4man on 2019-09-08
Works fine here on 18.04.3 (HWE), so likely a local issue to you 
You should provide more info, i.e, 
What release of Ubuntu
What video GPU and or driver
What version of vlc
Does vlc report  anything useful if opened from terminal
Are you dual booting with other Ubuntu install

---

### Post by crip720 on 2019-09-08
Also working with Ubuntu 19.04 with 5.0.0-28.

---

### Post by whady on 2019-09-09
> **mc4man said:**
> Works fine here on 18.04.3 (HWE), so likely a local issue to you 
You should provide more info, i.e, 
What release of Ubuntu
What video GPU and or driver
What version of vlc
Does vlc report  anything useful if opened from terminal
Are you dual booting with other Ubuntu install

My system:

Ubuntu 18.04.3 LTS
Linux xubuntu 5.0.0-27-generic #28~18.04.1-Ubuntu SMP Thu Aug 22 03:00:32 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
VLC media player 3.0.7.1 Vetinari (revision 3.0.7.1-0-gf3940db4af)

I don't understand why VLC doesn't open using kernel 5.0.0-27.
I tried to reinstall this kernel version but the problem persists.
If I boot kernels earlier version 5.0.0-27, VLC works fine.

I don't know what to do.

---

### Post by (kyT%0) on 2019-09-09
unless you have some specific requirements for which you need vlc only, like some of the bells & whistles that vlc comes with, i would suggest you try mpv.

on the latest beaver that you have, mpv works like a charm, tried & tested. if you need a no frills media player that does the job mpv is it.

---

### Post by mc4man on 2019-09-09
You didn't post any info on your GPU ..
Maybe try -
open file manager (show hidden files) > go to .config/vlc
Inside will be 2 files, delete both, then try vlc again

If still a problem then go back to that folder, in the vlcrc file  find this section, (around line 487 here)  - 
> # Hardware decoding (string)
#avcodec-hw=any

Change it to this, save file and try vlc again (i.e removing the # and changing any to none
```
# Hardware decoding (string)
avcodec-hw=none
```

---

### Post by whady on 2019-09-10
> **mc4man said:**
> You didn't post any info on your GPU ..
Maybe try -
open file manager (show hidden files) > go to .config/vlc
Inside will be 2 files, delete both, then try vlc again

If still a problem then go back to that folder, in the vlcrc file  find this section, (around line 487 here)  - 


Change it to this, save file and try vlc again (i.e removing the # and changing any to none
```
# Hardware decoding (string)
avcodec-hw=none
```

Thanks for help, but the problem persists.
Today I downloaded the latest daily Ubuntu 18.04.3 livecd ISO and made a clean install of the system, then next I installed only VLC. The problem persists.

I'm just waiting a fix for this kernel version.
Thanks for all.

---

### Post by pablosquared on 2019-09-12
VLC 3.0.8 works OK for me on that kernel (Ubuntu 19.04) when playing both live TV (DVB) and MK5/MP4/AVI files.

What happens when you launch VLC from a terminal? Do you get an error message that might help diagnose the issue?

---

### Post by whady on 2019-09-14
> **pablosquared said:**
> VLC 3.0.8 works OK for me on that kernel (Ubuntu 19.04) when playing both live TV (DVB) and MK5/MP4/AVI files.

What happens when you launch VLC from a terminal? Do you get an error message that might help diagnose the issue?

My terminal command:
> 
$ /usr/bin/vlc
VLC media player 3.0.8 Vetinari (revision 3.0.8-0-gf350b6b5a7)
$



I have a HP notebook with C200 Series Chipset and my system is xubuntu 18.04.3.
My solution is a downgrade of the kernel. VLC is working now.

I think this kernel version (5.0.0-27) has a graphic module issue that VLC doesn't start properly.
VLC is working with older kernels.

If anyone knows an Ubuntu developer, please notice this kernel issue.

Thanks for all.

---

### Post by uRock on 2019-09-14
Open System Monitor, select Processes tab, then look for VLC. I've noticed it starts in the background from time to time. I have to kill it and then it works when retrying. This didn't become a problem for me until I installed with the 18.04.3 installer. It was also a problem for me in Debian Buster.

---

### Post by uRock on 2019-09-14
> **whady said:**
> ...

If anyone knows an Ubuntu developer, please notice this kernel issue.
...
You'd have to create a bug report for the developers to notice. They do not visit the forums.

---

### Post by hk42 on 2019-09-20
> **uRock said:**
>  I've noticed it starts in the background from time to time. I have to kill it and then it works when retrying.
Hi
I seem to have the same problem of VLC staying in the background with an icon in the top bar.
I have to log out from the GUI (with a warning of VLC still playing a mysterious file)Then it works again.
Same problem with Gnome or XFCE .
I'm running 19.04 and it seems to have appeared with an update.
When trying to run VLC twice the second instance complains about not having access to the audio.

---

### Post by uRock on 2019-09-20
> **hk42 said:**
> Hi
I seem to have the same problem of VLC staying in the background with an icon in the top bar.
I have to log out from the GUI (with a warning of VLC still playing a mysterious file)Then it works again.
Same problem with Gnome or XFCE .
I'm running 19.04 and it seems to have appeared with an update.
When trying to run VLC twice the second instance complains about not having access to the audio.

I am using Xubuntu, but have Gnome System Monitor installed. I am sure Xubuntu's Task Manager can be used as well. I keep system monitor open all the time, so when this happens, I just go to processes, find VLC, then right click and select Kill. Afterwards, I am able to open the video. Not sure what is causing this issue. I didn't see the problem on my previous install of 18.04.2, though the problem started after doing a fresh install of 18.04.3. It was also a problem when running Debian 10.

---

### Post by hk42 on 2019-09-22
Thanks for the tip but in my case it seems that gnome system monitor doesn't work anymore.
htop does the job anyway
I noticed that Kaffeine suffers the same problem:
On first launch it works OK but when closed an icon stays on the top bar and I cannot launch it again.

---

