---
title: "Why Doesn't cdrdao Have MP3 Support?"
date: 2010-08-08
forum: Multimedia Software
---

### Post by clevertomato on 2010-08-08
People say Brasero and Gnomebaker will burn CDs using cue sheets, but they fail for me saying, "cdrdao was compiled without mp3 support." I've searched all over the forums and elsewhere. Others have had the same problem but no good solution seems to exist that I've found. I'm not going to spend a whole day hacking just to get CD recording software to do what it should already do. Man it's frustrating to hit brick walls like this. I assume (but don't know for sure) that NeroLinux would work, but it's not open source and that's one reason I switched to Ubuntu from Windows. If I'm going to have to buy proprietary software for something as common as CD recording, I may as well go back to Windows. (I won't, but it's still frustrating!)

I don't know about K3B but I don't want any KDE apps on my Gnome.

Anybody know any solution to this problem?

---

### Post by krishnandu.sarkar on 2010-08-08
Brasero is good nor nothing. Try K3B. Though I'm not sure K3B is capable. But as like you I've also found CD/DVD Burning a daunting task in Linux. I burnt a couple of ISO's with both Brasero and K3B, but unluckily none of them worked. All were bootable. I need to again buy CD's and burn them from Windows.

Now I'm really afraid of burning CD/DVD's in Linux, may be they won't work and I've to buy CD/DVD's again.

---

### Post by Linuxforall on 2010-08-08
Brasero and k3b all work fine here, no issues at all, with regular, mp3 or bootable CDs.

---

### Post by clevertomato on 2010-08-08
People say Brasero works fine for them, but for what tasks? Brasero has worked fine for me for buring CDs from Ubuntu ISO images and making plain data CDs. But when I try to record an audio CD using a CUE file and MP3, it fails miserably, along with every other gnome solution I've tried.

I finally installed K3B and it burned an audio CD using a CUE file and MP3 just fine! But I really don't want to have to run a KDE app on Gnome and there MUST be a way to do it in Gnome if K3B can do it.

Doesn't anyone know?

---

### Post by MartyBuntu on 2010-08-08
Brasero is pitiful.

Just take K3B and the extra libs and be done with it.

---

### Post by clevertomato on 2010-08-08
It looks like that what I'm going to have to do, but dog gone it, it amazes me that K3B is the only solution for this on Linux. I really can't believe there is no command-line utility that will do it.

I guess I should be thankful that K3B is out there, but I'll keep this thread unsolved for a while hoping someone may surprise me with a GTK / Gnome / CLI solution.

---

### Post by qamelian on 2010-08-08
I'm not sure where the problem is, but I just used Brasero to burn an audio CD from 7 MP3 tracks from a friend's band. They converted to raw audio and the CD burned without a problem. Just tested it in my stereo and the disc plays fine too.

---

### Post by clevertomato on 2010-08-09
qamelian: I've used Brasero for basic things, too. What I cannot get it to do is burn a tradition audio CD (usable in any CD player) using a CUE sheet file that contains information for how to split one big MP3 file into the appropriate CD tracks. K3B does it fine for me, and Nero does it fine on Windows, but Brasero, Gnomebaker, and NeroLinux 4 all fail to do this one particular thing... at least for me.

If I could figure out a command line equivalent of what K3B is doing to accomplish it, I'd be content for now (although of course I wish there were a Gnome app as capable and reliable as K3B someday). But even the command line attempts elude me (I've tried doing it with wodim).

---

