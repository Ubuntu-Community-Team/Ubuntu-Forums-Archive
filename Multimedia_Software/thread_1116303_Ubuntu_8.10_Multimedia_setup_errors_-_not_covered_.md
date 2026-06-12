---
title: "Ubuntu 8.10 Multimedia setup errors - not covered in guide"
date: 2009-04-04
forum: Multimedia Software
---

### Post by coblenis on 2009-04-04
Hello,

I tried following the comprehensive multimedia guide to setup my computer for flash/mp3/etc playback.  It did not work.  

This is what I did: 

First, I ran this command in the terminal: 

"sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list"

and then: 

"sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update"

as advised on this site: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I wasn't able to play MP3s, so I moved forward with the comprehensive guide.  

I entered: 

"sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list"

and

"wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update"

and finally, 

"sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs icedtea6-plugin libavcodec-unstripped-51 libmp3lame0 non-free-codecs openjdk-6-jre unrar"

I can't play back MP3s or video on the internet.  


I have the warning sign in the top tool bar that gives me the following: 

"An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.  The error message was: 'Error: BrokenCount> 0' This usually means that your installed packages have unmet dependencies." 

When I run the package manager, I have the option of installing libavcode51, but I get the following error when I try: 

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

I tried entering 'dpkg --configure -a' in the terminal but it says I must be a superuser and I don't know what this means.  

Any suggestions on what I can do to get media playback?

---

### Post by coblenis on 2009-04-04
... so it's been awhile since I ran ubuntu and I forgot that 'sudo' lets me run the superuser commands ... sorry for that.  everything's sorted out now.

---

