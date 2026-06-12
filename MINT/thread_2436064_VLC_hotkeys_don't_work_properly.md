---
title: "VLC hotkeys don't work properly"
date: 2020-01-30
forum: MINT
---

### Post by Kevin McCready on 2020-01-30
I have 3.0.8 Vetinari VLC but the hotkeys don't work properly, specifically Left and right to move forward or backward in a video. I also want to change the jump from 5 seconds to 1 second. When I assigned "very short jump" to the left key, it jumps back to the beginning of the video.

My system is
```
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=19.3
DISTRIB_CODENAME=tricia
DISTRIB_DESCRIPTION="Linux Mint 19.3 Tricia"
NAME="Linux Mint"
VERSION="19.3 (Tricia)"
ID=linuxmint
ID_LIKE=ubuntu
PRETTY_NAME="Linux Mint 19.3"
VERSION_ID="19.3"
HOME_URL="https://www.linuxmint.com/"
SUPPORT_URL="https://forums.ubuntu.com/"
BUG_REPORT_URL="http://linuxmint-troubleshooting-guide.readthedocs.io/en/latest/"
PRIVACY_POLICY_URL="https://www.linuxmint.com/"
VERSION_CODENAME=tricia
UBUNTU_CODENAME=bionic
```

---

### Post by howefield on 2020-01-31
Another thread moved to the "*MINT*" forum.



> Forum: Ubuntu Official Flavours Support

Choose the most appropriate category for your questions regarding Ubuntu, Kubuntu, Xubuntu, Edubuntu, Lubuntu, UbuntuGnome, Ubuntu Studio, Mythbuntu, Ubuntu Mate, Ubuntu Budgie and Ubuntu Kylin.

> Forum: MINT

For all your Linux Mint questions.

---

### Post by ajgreeny on 2020-01-31
Many, if not all, of VLC's hotkey settings are included towards the bottom of the configuration file ***~/.config/vlc/vlcrc*** which is a plain text file you can edit as you wish or delete to allow it to be created as new.

However, can I check whether you're using the snap version of VLC. Show us the output of ***snap list*** in terminal; if you see VLC in the list from that I suspect the vlcrc file I mentioned will be left over from a previously installed version of VLC, but my knowledge of snaps is very limited so don't accept that as fact.

---

### Post by Kevin McCready on 2020-02-03
Thanks. the vlcrc file was useful.



Re not posting to a MINT forum, whenever I try to start a thread it doesn't give me that option.

---

### Post by wildmanne39 on 2020-02-03
You can find the Mint forum here:

[https://ubuntuforums.org/forumdisplay.php?f=446](https://ubuntuforums.org/forumdisplay.php?f=446)

---

