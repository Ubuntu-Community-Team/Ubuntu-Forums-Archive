---
title: "Streaming flash plugin for Firefox broken"
date: 2011-11-08
forum: Multimedia Software
---

### Post by PhilipGanchev on 2011-11-08
When I load a Web page that has an embedded flash video in Firefox (such as on Youtube), it does not work. It loads the first 1 or 2 seconds and starts playing in the browser, but then the video stalls, because it goes back to the current point in the video and downloads again from there, and it keeps doing that. This is evident from the gray line in the progress indicator bar: the gray line first grows longer than the white line which shows what we have already watched in the video; but after 1 or 2 seconds, it shortens again to the end of the white line, and soon after that the video stops playing.

Clicking on the pause/play button does not help. Clicking to another time point in the video does not help.

This started happening right after I upgraded from Ubuntu 10.10 to 11.10 yesterday. I'm using the default setup. It has Firefox 7.0.1. Packages flashplugin-downloader and flashplugin-installer are installed, both version 11.0.1.152ubuntu1. I have some browser add-ons, but all of them are disabled.

When I download the flash file and watch it with Mplayer, it works fine.

(From the other browsers, Epiphany does not seem to have flash playback, and Chromium does not start.)

---

### Post by TBABill on 2011-11-08
Only thing I can think of is to reinstall ubuntu-restricted-extras (or just the flash plugin) and see if you get any performance improvement or to install Flash Aid plugin for Firefox and allow it to pull in the latest Flash from Adobe and install it auto-magically for you and see if that helps. It may be a newer version than what's in the repos.

---

