---
title: "Surround sound with CMI9761A"
date: 2008-04-07
forum: Multimedia &amp; Video
---

### Post by xromano on 2008-04-07
Hi peoples, 

I am just trying to use Ubuntu 7.10 instead Win. That means I am just a beginner. With my Ubuntu I have a problem with an on board sound card CMI9761A. Just fronts are playing, the rest is silent. I have already update the kernel, I have re-install ALSA. Anyway, searching the web page of C-Media for a driver, I was redirected to the ALSA web page. Unfortunately, my card is not listed in a list of supported cards. So that mean I am at the ende. Do have any suggestion, which could help me? Thanks a lot for help!!!

---

### Post by warp99 on 2008-04-08
In totem there are settings to change the sound to 5.1 surround sound and a pass-though setting to output to spdif if you have an external decoder. According to ALSA the card is supported with 6 channel surround sound.

---

### Post by xromano on 2008-04-08
Well, I tried these settings change in Totem, SMPlayer, Kaffeine and so on. Even if I start "speaker-test -t wav -D plug:surround51 -c 6" I can hear just left and right front. The rest is silent. Editing od .asoundrc with:
pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}
also did not help. In Alsamixer are center, LFE and surround always not activated. Switching them on helps not. 
Thanks for any idea!

---

### Post by warp99 on 2008-04-08
Well it could be that version 1.0.14, which is installed with Gutsy 7.10, is the cause. I did find a post at alsa-user that had a similar problem:

[http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg16175.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg16175.html)

So your not alone with the lack of support. Ubuntu is a little behind on including new Alsa releases. Support for the chipset comes the AC_97 specification:

[https://bugtrack.alsa-project.org/alsa-bug/view_all_bug_page.php](https://bugtrack.alsa-project.org/alsa-bug/view_all_bug_page.php)

Now Hardy 8.04 includes Alsa 1.0.16 which may have better support since a patch may have made it's way upstream. There is a patch available for version 1.0.14:

[https://bugtrack.alsa-project.org/alsa-bug/file_download.php?file_id=1888&type=bug](https://bugtrack.alsa-project.org/alsa-bug/file_download.php?file_id=1888&type=bug)

from this thread:

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2693](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2693)

You would have to recompile the modules with the patch applied. It's not too difficult and their are guides available on the forums and the help guides, see my signature for those.

---

### Post by xromano on 2008-04-10
Thanks for help. Unfortunately, I did not get it. I am just a beginner and it is too difficult. I will wait until the new version of Ubuntu is available and I will hope. Anyway, thank you.

---

