---
title: "Flash player in FF stops working after a while"
date: 2010-01-19
forum: Multimedia Software
---

### Post by Mihasi on 2010-01-19
It's been a while since I've posted in these forums, mainly because Ubuntu has worked so flawlessly for me up until now. Since I've installed Karmic, my flash player in Firefox stops working after a certain amount of time.

Setup:
I'm running Ubunu 9.10 64-bit, Firefox 3.5.7 and flash plugin 10.0.42.34 x64-bit.

Problem:
At first I installed the flash plugin the way I always did it up until know: download the latest Linux 64-bit tarball from the Adobe site, untar it and copy libflashplayer.so to /usr/lib/mozilla/plugins/. When I opened my browser everything worked as expected, but after a while if I opened a site with flash content on it, the place were the flash movie should be was just blank. This doesn't happen during a video, for example: if I watch a one hour youtube-movie the flash plugin will work the entire time. On the other hand, if I watch a five minute movie, close the browser or tab and try to open another (or the same) flash movie the plug-in will sometimes have stopped working. I have no way of reproducing it since the time it takes for it to stop working seems to be completely random and it doesn't seem to be related to browser sessions.

Things I've tried:
- At first I tried removing and replacing the .so file in /usr/lib/mozilla/plugins. Didn't work.
- Then I started googling around and thought my problem might be related to this one: [http://ubuntuforums.org/showthread.php?t=1249710]("http://ubuntuforums.org/showthread.php?t=1249710"). I found all the possible locations where the plugins could be in and tried replacing them all with the new plugin. To no avail.
- I tried removing all the .so-files I had manually put in and use the scripts found on [http://adammichaelroach.com/blog/110309-installing-adobe-flash-64-bit-ubuntu-910-karmic-koala]("http://adammichaelroach.com/blog/110309-installing-adobe-flash-64-bit-ubuntu-910-karmic-koala") and [http://ubuntuforums.org/showthread.php?t=1358591]("http://ubuntuforums.org/showthread.php?t=1358591"), still no go.
- The last thing I tried was installing a backport from Debian, as suggested in this post: [http://ubuntuforums.org/showpost.php?p=8629336&postcount=64]("http://ubuntuforums.org/showpost.php?p=8629336&postcount=64"). Unfortunately, still nothing.

Temporary solution:
The way I handle this now is by running the following script every time the problem occurs. 

```
#!/bin/bash
# reinstall flash plugin

# kill firefox
killall -9 firefox

# remove old instances
rm -f /usr/lib/mozilla/plugins/*flash*
rm -f ~/.mozilla/plugins/*flash*
rm -f /usr/lib/firefox/plugins/*flash*
rm -f /usr/lib/firefox-addons/plugins/*flash*

# insert new instances
cp /home/mihasi/Downloads/libflashplayer.so /home/mihasi/.mozilla/plugins/
cp /home/mihasi/Downloads/libflashplayer.so /usr/lib/firefox/plugins/
cp /home/mihasi/Downloads/libflashplayer.so /usr/lib/firefox-addons/plugins/
cp /home/mihasi/Downloads/libflashplayer.so /usr/lib/mozilla/plugins/

echo "Restart FF (again)."
```

After running that, it works again for a while. If this was session-bound I could just run the script automatically at login or when starting FF, but as it is now I have to manually run it every time the plugin stops working. I thought I could live with that, but it's starting to get really annoying now, so I was hoping you guys could help me out.

-- Edit --
Found the solution, apparently I did not erase all traces of flash on my system. After I ran the script from this post:
[http://ubuntuforums.org/showpost.php?p=8666948&postcount=72]("http://ubuntuforums.org/showpost.php?p=8666948&postcount=72") and ran my script again (without the remove lines) flash now finally works on my system.

---

### Post by noletolucas on 2010-04-14
Same problem here.

In the beggining it used to happen only in CHROME. Maybe after some updates something got broken.

That's why I keep saying: good system is old system. lol!

updates from hell... damn it!

---

