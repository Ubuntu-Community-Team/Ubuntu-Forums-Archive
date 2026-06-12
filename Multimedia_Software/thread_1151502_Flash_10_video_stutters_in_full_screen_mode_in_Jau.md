---
title: "Flash 10 video stutters in full screen mode in Jaunty 9.04"
date: 2009-05-07
forum: Multimedia Software
---

### Post by pyutaros on 2009-05-07
**RESOLVED:  I finally tried the suggestion given in [#4]("http://ubuntuforums.org/showpost.php?p=7236965&postcount=4").  Actually, I read [this post]("http://ubuntuforums.org/showpost.php?p=7535876&postcount=70") and it reminded me of #4.  Anyhow, creating the flash config file and overriding the GPU validation has done the trick.  Don't bother with these downgrade instructions.**

I have been working on this issue since I upgraded to Jaunty a week or so ago, so I wanted to share my experience as to how I finally fixed my problem.  Basically, when viewing flash videos in full screen (such as videos from Youtube or Hulu), the audio plays fine, but the video stutters and skips.  I had performed many tests to make sure it was not a video card, browser, or bandwidth problem.  The same flash videos played fine in VLC.  I tried Opera, Firefox, and a few others.  Besides which this was not a problem for me in Hardy.

After reading a few posts on the web, it seemed that the issue was directly related to the Adobe Flash v10 that is included in the Jaunty Medibuntu repositories.  [A simple search reveals many people reporting the same issue.]("http://www.google.com/search?hl=en&safe=off&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=xxF&q=ubuntu+9.04+flash+player+10+stuttering&btnG=Search")  [I believe the bug has been reported,]("http://forums.adobe.com/thread/199736") but am not certain.

Anyhow, none of the fixes for the Flash 10 video problem seemed to work for me, so I decided to see if downgrading would fix the issue.  It did (I downgraded to v9 r159), but v9 of Flash had no sound.  It turned out that this was due to (I believe) compatibility issues with Flash 9 and Pulse Audio.  I ended up having to compile a special libflashsupport.so and finally I had both working flash video AND sound in Jaunty.  This is obviously not a SOLUTION, but at least can give us all a workaround, while we wait for Flash v10 to get the bugs worked out.  Here's the step by step.  While these instructions are specific to Firefox, they should be able to be adapted for any browser.

**Uninstalling Flash**
Run the following in a terminal (don't worry if your system doesn't have all of them installed):
```
sudo apt-get remove --purge adobe-flashplugin flashplugin-installer flashplugin-nonfree 
```
Open Firefox to "about:plugins".
There should be no version number listed for Shockwave Flash.

**Installing Flash v9**
[Go to the archive page for older Flash versions and download the zip file for version 9 (non development).]("http://www.adobe.com/cfusion/knowledgebase/index.cfm?id=tn_14266")
Extract the contents of the zip file.
Browse the extracted filed to */fp9_archive/9r159/ .
Extract the contents of flashplayer9r159_linux.tar.gz and browse install_flash_player_9_linux.
Copy libflashplayer.so to ~/username/.mozilla/plugins/ .
Open Firefox to "about:plugins".
Your version should read: 'Shockwave Flash 9.0 r159'.

**Getting sound working in Flash v9**
These last directions I took straight from [here.]("http://motls.blogspot.com/2007/01/adobe-flash-9-for-linux-sound.html")
See the original post for complete detail.

> Go to the page of [flashsupport]("http://labs.adobe.com/wiki/index.php/Flash_Player:Additional_Interface_Support_for_Linux"). At the bottom, you will find the flashsupport.c source. Save it on your disk in the directory with libflashplayer.so and compile it. In the ideal case, the following three commands are enough (please join the first three lines into a single command with many arguments):

```
cc -shared -O2 -Wall -Werror -licuuc -lssl flashsupport.c -o libflashsupport.so
ldd libflashsupport.so
sudo cp libflashsupport.so /usr/lib
```

Needless to say, the first command may give you about 35 errors, just like in my case. It's because you don't have a working openssl either. ;-) So you open the flashsupport.c source, find the #define OPENSSL line, and comment it out by "//" just like the following lines. The first "cc" command will still return you an error message and create no "so" output. Don't panic and simplify the first command to something like:

```
cc -shared -O2 -Wall -Werror flashsupport.c -o libflashsupport.so
```

Then you follow the other two commands above, or copy the resulting libflashsupport.c file wherever you need, to the directory with the other "so" plugins. In my case, the audio in Flash started to work after I restarted Firefox.

You should now have a working Flash version with sound and no video stutter.

EDIT: Here is the link to the Flash Bug Report - [http://bugs.adobe.com/jira/browse/FP-169]("http://bugs.adobe.com/jira/browse/FP-1692")2

---

### Post by pyutaros on 2009-05-07
If anyone comes across the link for the actual bug report, please post it.  I can't seem to find it, but that may be because it hasn't been reported.

---

### Post by lovinglinux on 2009-05-08
Thanks for sharing. I followed the tutorial and it worked, but then I had audio/video sync issues.

BTW, I couldn't find the plugins directory, so I used the installation script provided by the flash package without using sudo, so it created the plugin directory under ~/.mozilla.

---

### Post by psyke83 on 2009-05-08
Using the libflashsupport library will allow Flash 9 to play sound in PulseAudio, but it will also cause *serious instability* in Firefox. The bug is within Flash itself and cannot be fixed. For anyone that's reading, take a look at the bug report below before using this library.

See [bug #192888]("https://bugs.launchpad.net/bugs/192888").

Most users noticed reduced CPU usage with Flash 10, so your issue is somewhat surprising. I recommend you remove libflashsupport and Flash 9, simply because the instability is not worth bearing.

Try to force hardware acceleration in the Flash plugin. See: [http://blogs.adobe.com/penguin.swf/2008/08/secrets_of_the_mmscfg_file_1.html](http://blogs.adobe.com/penguin.swf/2008/08/secrets_of_the_mmscfg_file_1.html) (you need to set OverrideGPUValidation=1 in your configuration file).

Also, it may be possible (though not likely) that you're experiencing a bug with your audio card which is fixed in kernel 2.6.28-12-generic. You can get this kernel by enabling the "proposed" Jaunty repository and upgrading.

---

### Post by pyutaros on 2009-05-10
Thanks both for your replies.  Like I mentioned previously, this is just intended to be a workaround until the issues with Flash 10 are addressed.  I can't speak to most people, but posts like [this]("http://ubuntuforums.org/showthread.php?p=7202906") convince me that it's a big enough issue to downgrade temporarily.
Admittedly, the video is still not perfect with the above solution, but it is FAR better than what I was experiencing after the upgrade to Flash 10.  I took a look at the solution offered involving mms.cfg, but I couldn't find a sample file to work with.  Seeing as how the solution above is working "well enough" for now, I'll probably wait until someone else has tried it out and posts a copy of a mms.cfg file.  (The default flash installation does not create this file.)
Thanks again for your replies.

---

