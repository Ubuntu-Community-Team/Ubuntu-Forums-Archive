---
title: "Problem when full screen in youtube by firefox"
date: 2015-05-03
forum: Multimedia Software
---

### Post by sw.ng on 2015-05-03
My system is ubuntu 12.04 with latest firefox.

I had a problem when see the movie in youtube by firefox when using full screen mode.

After I click the "full screen button", the browser do go to full screen but the dimension of the movie window had not changed.

You can see that the full screen mode had not filled by the movie content. The movie content is as same as the size of normal display. 
[IMG]http://www.4freeimagehost.com/resized/726ab7b08fa5.png[/IMG]

This problem only happen in youtube, and found no problem when visit dailymotion. Dailymotion can show the real full screen for the movie.

I had perform the following but still no luck.
- delete the user profile and try to resume the default status (sudo  rm -r ~/.mozilla)
- clear all the cookies of youtube,
- clear the permissions data of youtube(access by about: permissions)
- clear all the cookies of the browser
- reinstall firefox
- reinstall the flash player at [https://get.adobe.com/flashplayer/](https://get.adobe.com/flashplayer/), current install **Version 11.2.202.457**

I can tell that under the flash install of the ubuntu with firefox, this problem would not occurs. I don't aware what have I done for this, it is because I would not check "full screen" for every move.

Please advice any hints for this problem.

---

### Post by bapoumba on 2015-05-03
Could you please give a link to the video you are viewing ? Tried a few and full screen behaves as expected here. What is your FF version ?

---

### Post by sw.ng on 2015-05-03
Thanks for the quick reply. 

All the video of youtube also encounter the same problem. 

Here is the FF version:
sudo apt-cache policy firefox
firefox:
  Installed: 37.0.2+build1-0ubuntu0.12.04.1
  Candidate: 37.0.2+build1-0ubuntu0.12.04.1
  Version table:
 *** 37.0.2+build1-0ubuntu0.12.04.1 0
        500 [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) precise-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main amd64 Packages
        100 /var/lib/dpkg/status
     11.0+build1-0ubuntu4 0
        500 [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) precise/main amd64 Packages

Additional information (by about: plugins)
--------------------------------
**Shockwave Flash**

File: libflashplayer.so
Path: /usr/lib/adobe-flashplugin/libflashplayer.so
Version: 11.2.202.457
State: Enabled
Shockwave Flash 11.2 r202

[TABLE="class: contenttable"]
[TR]
[TH="class: type"]MIME Type
[/TH]
[TH="class: desc"]Description[/TH]
[TH="class: suff"]Suffixes[/TH]
[/TR]
[TR]
[TD]application/x-shockwave-flash[/TD]
[TD]Shockwave Flash[/TD]
[TD]swf[/TD]
[/TR]
[TR]
[TD]application/futuresplash[/TD]
[TD]FutureSplash Player[/TD]
[TD]spl[/TD]
[/TR]
[/TABLE]

---

### Post by bapoumba on 2015-05-03
OK thanks. I have the same FF version and Flash plugin (on 15.04 though).

may be try this ? 
[https://support.mozilla.org/en-US/kb/flash-videos-wont-play-full-screen](https://support.mozilla.org/en-US/kb/flash-videos-wont-play-full-screen)

---

### Post by sw.ng on 2015-05-03
The 4 methods in [https://support.mozilla.org/en-US/kb...ay-full-screen]("https://support.mozilla.org/en-US/kb/flash-videos-wont-play-full-screen"), I had been done but still no luck.

For the method 1 - preload the libGL.so.1 library, I would like to share some additional information.
Since I cannot found the request file /usr/lib/libGL.so.1, i try to search within the /usr/lib/ (by $ find . -name "libGL*").

Here is the result:
   /usr/lib/x86_64-linux-gnu/libGLU.so.1.3.08004 
/usr/lib/x86_64-linux-gnu/libGLU.so.1 
/usr/lib/x86_64-linux-gnu/libGLEW.so.1.6 
/usr/lib/x86_64-linux-gnu/libGLEW.so.1.6.0 
/usr/lib/x86_64-linux-gnu/libGLEWmx.so.1.6.0 
/usr/lib/x86_64-linux-gnu/mesa/libGL.so.1.2.0 
/usr/lib/x86_64-linux-gnu/mesa/libGL.so.1 
/usr/lib/x86_64-linux-gnu/libGLEWmx.so.1.6 

Therefore, I test with both version by edit file /usr/share/applications/firefox.deskop, but still no luck 
Exec=env LD_PRELOAD=/usr/lib/x86_64-linux-gnu/mesa/libGL.so.1.2.0 firefox %u
Exec=env LD_PRELOAD=/usr/lib/x86_64-linux-gnu/mesa/libGL.so.1 firefox %u

---

### Post by bapoumba on 2015-05-03
Hmm, I had not checked and I indeed have the file at the same location.

Other than a video driver problem (which I'm afraid I wont be of much help with), I'm not sure what to suggest. Do you have a single monitor ?

---

### Post by sw.ng on 2015-05-03
Oh ! I get the solution.

By your reply related to single monitor, I just go to "system settings" -> "display" -> "detect displays" without any meaning (just click the button spontaneously).
 
But after "detects displays", I go to youtube and find the normal FULL SCREEN resume !

In my analysis, I was focusing in the profile setting and package reinstall. At the end, the problem is solved only by refresh the display!

Thank bapoumba advice !!!

---

### Post by bapoumba on 2015-05-03
Nice :)
Thanks to you sw.ng for marking your thread as solved !

---

