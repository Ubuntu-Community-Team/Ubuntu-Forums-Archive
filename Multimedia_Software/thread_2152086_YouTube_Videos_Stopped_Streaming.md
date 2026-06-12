---
title: "YouTube Videos Stopped Streaming"
date: 2013-06-06
forum: Multimedia Software
---

### Post by mtphr on 2013-06-06
Hi,

A couple of days ago a problem started to occur. I can't watch YouTube videos anymore. When I open a video, the animation goes on and on... untill the message "an error has occured". Very very very rarely sometimes a video loads. (Today it never happened, yesterday only once)

Like I said, a couple of days ago it was all working. I didn't do any updates. After this problem, I've installed every update, didn't solve the problem.

It is not browser specific, Google Chrome, Chromium, Firefox, Opera... All have the same problem.
It is YouTube specific, I can watch videos on facebook (not loaded through YouTube) and vimeo and more.
I have reinstalled the flashplugin, didn't solve. (Yet it is not about flash)
It is not about my network, using the same network, Windows Laptop, iPhone, Android Tablet all load v

Ubuntu 12.04 LTS 32 Bit

$ uname -a
Linux marvin 3.2.0-45-generic-pae #70-Ubuntu SMP Wed May 29 20:31:05 UTC 2013 i686 i686 i386 GNU/Linux

$ dpkg -l |grep "chrome\|firefox\|opera\|chromium\|flash"
ii  adobe-flash-properties-gtk                    11.2.202.285-0precise1                  GTK+ control panel for Adobe Flash Player plugin version 11
ii  adobe-flashplugin                             11.2.202.285-0precise1                  Adobe Flash Player plugin version 11
ii  chromium-browser                              25.0.1364.160-0ubuntu0.12.04.1          Chromium browser
ii  chromium-browser-l10n                         25.0.1364.160-0ubuntu0.12.04.1          chromium-browser language packages
ii  chromium-codecs-ffmpeg                        25.0.1364.160-0ubuntu0.12.04.1          Free ffmpeg codecs for the Chromium Browser
ii  eject                                         2.1.5+deb1+cvs20081104-9                ejects CDs and operates CD-Changers under Linux
ii  firefox                                       21.0+build2-0ubuntu0.12.04.3            Safe and easy web browser from Mozilla
ii  firefox-globalmenu                            21.0+build2-0ubuntu0.12.04.3            Safe and easy web browser from Mozilla - Unity menubar integration
ii  firefox-gnome-support                         21.0+build2-0ubuntu0.12.04.3            Safe and easy web browser from Mozilla - GNOME support
ii  firefox-locale-en                             21.0+build2-0ubuntu0.12.04.3            English language pack for Firefox
ii  google-chrome-stable                          27.0.1453.110-r202711                   The web browser from Google
ii  libcrypt-passwdmd5-perl                       1.3-10                                  interoperable MD5-based crypt() for perl
ii  opera                                         12.15.1748                              Fast and secure web browser and Internet suite
ii  xserver-xorg-video-openchrome                 1:0.2.904+svn1050-1                     X.Org X server -- VIA display driver

Any suggestions?
Sorry if it is a repost, it's hard to find this problem in the dozens of "restricted-extras not installed" problems...

---

### Post by mtphr on 2013-06-07
bump

---

### Post by nativehound on 2013-06-07
Three things i would check.

1. load a YT video and right click on it and see what version your running, (e.g. flash or html5)
    if its flash try to switch to html5 or vice versa at [http://www.youtube.com/html5](http://www.youtube.com/html5)

2. if that didn't work. try to play a YT video through a proxy.  [http://www.proxfree.com/youtube-proxy.php](http://www.proxfree.com/youtube-proxy.php) (If yes, its network related to ubuntu) 

3. if you still cant play a video try to delete the ~/.adobe in your home folder and restart your browser.

---

