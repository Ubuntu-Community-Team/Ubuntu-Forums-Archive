---
title: "Easy MP3 Gain..."
date: 2009-05-24
forum: Multimedia Software
---

### Post by Baldrick_NZ on 2009-05-24
Hi all,

Hoping somebody will be able to give me the APT line for this software, or could possibly walk this newbie through activating the MP3 Gain program which Synaptic informs me I currently have installed on 9.04, yet doesn't show up anywhere under Applications...

Easy MP3Gain works well natively in opensuse KDE 4.2, but doesn't appear to be an option here.

Any help would be greatly appreciated.

---

### Post by valxp on 2009-05-27
mp3gain is command line utility. If you want to normalize your mp3 use it in terminal
$mp3gain <filename>
or for all files in your ubuntu:
$find . -type f -iname '*.mp3' -print0 | xargs -0 mp3gain -r -k

Also look here: [http://ubuntuforums.org/showthread.php?t=1032650&highlight=mp3gain](http://ubuntuforums.org/showthread.php?t=1032650&highlight=mp3gain)

---

### Post by kpkeerthi on 2009-05-27
> **Baldrick_NZ said:**
> Hi all,

Hoping somebody will be able to give me the APT line for this software, or could possibly walk this newbie through activating the MP3 Gain program which Synaptic informs me I currently have installed on 9.04, yet doesn't show up anywhere under Applications...

Easy MP3Gain works well natively in opensuse KDE 4.2, but doesn't appear to be an option here.

Any help would be greatly appreciated.

Download the [easymp3gain-gtk2_0.4.2_i386.deb]("http://sourceforge.net/project/showfiles.php?group_id=207001&package_id=247705&release_id=640832") file to your desktop. Then double-click on it to launch the installation.

---

