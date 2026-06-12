---
title: "Flash 10 - problems w/ Ubuntu 8.04 (Hardy)"
date: 2009-02-06
forum: Multimedia Software
---

### Post by bill-linux on 2009-02-06
I cannot get Flash 10 to work. (I've used the deb flashplugin-nonfreebeta; this replaces flashplugin-nonfree which innstalled flash 9 and worked just fine.) I cannot see Flash 10 or any flash in Firefox 3 using "about:plugins" for the URL. When I start Hulu or YouTube it doesn't say "install flash 9 or greater" it just shows a blank screen -- black for Hulu and white for YouTube. I've also tried manual installs, local installs, etc. Nothing seems to work. Any idea what's up, or how to start troubleshooting this.

---

### Post by redroad55 on 2009-02-06
read this post :[http://ubuntuforums.org/showthread.php?t=1061381]("http://ubuntuforums.org/showthread.php?t=1061381")
best to you

---

### Post by gandaran on 2009-02-06
> **bill-linux said:**
> I cannot get Flash 10 to work. (I've used the deb flashplugin-nonfreebeta; this replaces flashplugin-nonfree which innstalled flash 9 and worked just fine.) I cannot see Flash 10 or any flash in Firefox 3 using "about:plugins" for the URL. When I start Hulu or YouTube it doesn't say "install flash 9 or greater" it just shows a blank screen -- black for Hulu and white for YouTube. I've also tried manual installs, local installs, etc. Nothing seems to work. Any idea what's up, or how to start troubleshooting this. 
to see what the problem is, start firefox in terminal (just type firefox), go to youtube and try playing a video, now post all the youtube errors output here.
flash 10 does not replace flash 9, make sure you don't have any other flash package or version installed, just one, firefox only uses one.
post the output of this command **locate libflash** and also the full output of about:plugins here.

---

### Post by bill-linux on 2009-02-06
Great suggestion. I have started up firefox in a terminal and watched for errors as I try to watch a YouTube Video. It is a lengthy stream and so will excerpt it a bit here. 

The first error is 

LoadPlugin: failed to initialize shared library /usr/lib/flashplugin-nonfreebeta/libflashplayer.so [libnss3.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /usr/lib/flashplugin-nonfreebeta/libflashplayer.so [libnss3.so: cannot open shared object file: No such file or directory]

Next it appears (to me at least!) to search for plugin elsewhere, e.g.,

LoadPlugin: failed to initialize shared library /home/bill/.mozilla/plugins/libflashplayer.so [libnss3.so: cannot open shared object file: No such file or directory]

It does this again and again.


Lastly, here is the output from "locate libflash" -- it is, of course, all over the place because I've tried locate installs and manual ones etc. It SEEMS that the only on it really wants is what is in /usr/lib/flashplugin-nonfreebeta ....

locate libflash reveals:

/home/bill/.flock/plugins/libflashplayer.so
/home/bill/.mozilla/plugins/libflashplayer.so
/home/bill/.mozilla/plugins/libflashplayer.so-9
/home/bill/.mozilla/plugins/libflashplayer.so-unknown
/home/bill/temp/flash/install_flash_player_10_linux/libflashplayer.so
/usr/lib/flashplugin-nonfreebeta/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/openoffice/program/libflash680li.so

---

### Post by bill-linux on 2009-02-06
Just to update my error messages. I decided to "fix" the problem myself based on the missing "libnss3.so" ... learned from googling a bit that the 64 bit versions hows this problem and the workaround was to install libnss3-dev (the development version). I did this, but it didn't help. Flash is now missing libplds4.so ... I removed libnss3-dev thinking it would go back to the original error. It didn't: Still needs libplds4.so ... go figure. Sounds to me like Flash 10 needs some newer libraries that I'm just missing ....

---

### Post by bill-linux on 2009-02-06
SOLVED [OR really just worked around]

So, running firefox from command line I noted the errors that appeared. Flash 10 was looking for some libraries in /usr/lib. They were named differently. Specifically I had to copy three to change their names - note COPY, I left the original names

/usr/lib/libnss3.so.0d --> libnss3.so
/usr/lib/libplds4.so.0d --> libplds4.so
/usr/lib/libnspr4.so.0d --> libnspr4.so

I haven't a clue why these were renamed with the "0d" extension. I got wind of this change from googling and noting some problems folks were having with the ephiphany browser. 

A quick check indicates that flash is working fine: a) show up as ver 10 in about:plugins (note that that's about : plugins without the spaces -- this forum turns the : p into an icon!), b) Hulu and Youtube work, and c) full screen Hulu works well ... which is what I was REALLY after. Fullscreen Hulu with Flash 9 was too choppy. Thanks for hints and help. Hope I can help someone else by posting this.

Surely, my "soln" is a real hack ... and needs to be fixed in some cleaner way.

---

