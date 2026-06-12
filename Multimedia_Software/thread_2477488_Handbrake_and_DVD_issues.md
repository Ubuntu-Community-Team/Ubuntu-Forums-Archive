---
title: "Handbrake and DVD issues"
date: 2022-07-26
forum: Multimedia Software
---

### Post by unicav on 2022-07-26
I'm running Ubuntu 22.04. Today I ran across some DVDs in storage (commercial purchased movies not home videos) and wanted to add them to my Plex library. I put the first one in the DVD drive and it blinked awhile and did nothing. Tried a few more and the system would never mount it. I went through dmesg and syslog without seeing anything related. Opened the Disks app and it shows the drive but says "No Media". I tried several suggested fixes online related to persistent storage rules, libdvd-pkg and libdvdread8 but nothing helped

Then I thought I'd just open Handbrake and see if it could access the drive, but it won't open at all. I found errors in the logs like "unable to determine mimetype" and "no such file or directory". Finally I ran it under sudo and it opened. So apparently my user account isn't allowed to run the app, but all other files in /usr/bin are owned by root and same permissions and this is the first app I haven't been able to run other than system level commands without sudo.

Would appreciate suggestions on what to do next

---

### Post by SeijiSensei on 2022-07-27
Take a look at [https://itsfoss.com/play-dvd-ubuntu-1310/](https://itsfoss.com/play-dvd-ubuntu-1310/). Did you follow the steps to compile libdvdcss2 after installing libdvd as described there?

libdvdcss2 contains the code require to decrypt the video files on standard DVDs.

---

### Post by unicav on 2022-07-27
Yes I followed that and libdvdcss and libdvdread8 are installed

---

### Post by Tadaen_Sylvermane on 2022-07-27
Try makemkv. I've rarely had success with just handbrake. Running it through makemkv to get the rip, then compressing with handbrake has been my goto solution for awhile now.

---

### Post by unicav on 2022-07-27
Interesting discovery that would help the situation. On Ubuntu 20.04 I can run Handbrake without using sudo. But on my newer system running 22.04 I can not.
On the 20.04 system the DVD drive connected via USB/SATA adapter still doesn't show up but I'm not going to fight with it at this point.
Sadly on a Windows box it just works. One of the things that aggravates me about Linux. I love Linux but why the heck, so often, is it just a PITA just to get a DVD drive to show up or be usable.

---

### Post by unicav on 2022-07-28
I wiped the system and did a full clean install. This was an upgrade from 20.04 to 22.04 and the more I messed with it there were several things that didn't jive. I'll update again when I test it

---

### Post by Yellow Pasque on 2022-07-28
You're not using a snap version of handbrake, are you?

---

### Post by unicav on 2022-07-29
I was not. Installed through apt. I think I had permissions issues with the in place upgrade. I also think my DVD drive was actually bad which is why it would never mount. Going to test it again soon with the new install and new drive

---

### Post by unicav on 2022-08-02
SOLVED
It was a bad DVD drive and permissions/install issues with the in-place upgrade from 19.04 to 22.04.
After a fresh install, replacement drive and installing the software everything is working fine. 
I can play DVD's in VLC and Handbrake opens correctly and reads the drive.

---

