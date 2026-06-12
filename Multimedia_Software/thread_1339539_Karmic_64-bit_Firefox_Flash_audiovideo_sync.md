---
title: "Karmic 64-bit Firefox Flash audio/video sync"
date: 2009-11-27
forum: Multimedia Software
---

### Post by jsimerly on 2009-11-27
Having a minor, but annoying, problem in 64-bit Karmic with Firefox 3.5 and Adobe Flash 10.0.32.18 when playing internet streaming file.

In any Flash video >10 minutes, the audio and video go badly out of sync at about the 10-minute mark.  It happens on any site with a long Flash video (Youtube, all news sites).  Downloading the video using youtube-dl command or Firefox Video Resource Downloader and playing locally fixes the sync problem.

I am currently using the manually-installed 64-bit alpha player from Adobe's website.  The problem also occurred when the 32-bit player from the repositories was installed.

I've found some great material in here on fixing very pervasive Jaunty/Karmic sound problems, but nothing recent on the audio/video being out of sync on longer files.  Any help much appreciated.

---

### Post by yellow99 on 2009-11-28
Edit: Forget about everything I wrote here! It seems like I messed up my firefox, big time. I get "Segmentation fault" after a few seconds of browsing...

> **jsimerly said:**
> I am currently using the manually-installed 64-bit alpha player from Adobe's website.  The problem also occurred when the 32-bit player from the repositories was installed.

Your issue could be related to a conflict between different versions of flash installed on your karmic 64.

I have been searching a lot today to fix issues that I have (had?) with my flashplayer. Here are my findings, strongly inspired of [http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html]("http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html") and [http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/]("http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/").

Basically, I removed everything related to flash (thanks to the script found in the first link provided above):

```

# Close firefox
sudo killall firefox

# Remove anything that is flash related
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

```

I then downloaded the prerelease version of the Adobe® Flash® Player 10 software 64-bit Linux platforms: [http://labs.adobe.com/downloads/flashplayer10_64bit.html]("http://labs.adobe.com/downloads/flashplayer10_64bit.html")

The last step was to unpack the tarball and copy the .so file to /usr/lib/mozilla/plugins/:

```

tar -xzf DOWNLOADED_FILE # mine was "libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz"
sudo cp -p libflashplayer.so /usr/lib/mozilla/plugins/

```

After I started firefox, everything is working well so far.

I am aware that the above code is not as complete as in the scripts you may use by following the links I provided above.

Good luck!

---

### Post by jsimerly on 2009-11-28
yellow99, thanks for the detailed posting and for the subsequent warning.  I had done everything in your post when I manually installed the alpha 64-bit player a few weeks ago.  Fortunately, my overall browsing experience didn't break.

I hope you're able to fix the segmentation fault.

---

### Post by yellow99 on 2009-11-28
> **jsimerly said:**
> I hope you're able to fix the segmentation fault.

I fixed the segmentation fault, but I'm back to square one. I am able to use flash, almost properly -- no interaction is possible... This means that I can watch videos on youtube, but I'm not able to remove pop-up adds nor choose a related video using the flash window. Luckily I'm not into flash games, otherwise, this would have been a pain!

I'm sure it is just a question of time before we see a proper and easy to install flash player for ubuntu 64.

Cheers!

---

