---
title: "Totem, Rhythmbox, Gstreamer won't load: Error scanning registry"
date: 2009-11-18
forum: Multimedia Software
---

### Post by ttilberg on 2009-11-18
Hello, after an update a week or two ago, I started having trouble playing media files. Whenever I would execute media that would play in Rhythmbox or Totem, the mouse cursor would wait a moment, and then nothing would happen.

Upon executing totem from cli:

ttilberg@ragnarok:~$ totem --debug
Error re-scanning registry , child terminated by signal
Run 'totem --help' to see a full list of available command line options.

The same output is displayed for Rhythmbox. I have searched and found that perhaps it is a problem with gstreamer, but have not been able to fix it yet. 

Also: 
ttilberg@ragnarok:~$ gstreamer-properties 
option parsing failed: Error re-scanning registry , child terminated by signal

I have tried sudo apt-get purge gstreamer0.10-plugins-bad gstreamer0.10-x totem rhythmbox

and reinstalling, and I still rec'v this error.

I'm not sure what logs could be of use to help debug, but let me know and I'll get them.

---

### Post by lidex on 2009-11-18
/var/log/messages
dmesg

---

### Post by ttilberg on 2009-11-19
ttilberg@ragnarok:~$ totem
Error re-scanning registry , child terminated by signal
Run 'totem --help' to see a full list of available command line options.
ttilberg@ragnarok:~$ rhythmbox
Error re-scanning registry , child terminated by signal
Run 'rhythmbox --help' to see a full list of available command line options.
ttilberg@ragnarok:~$ audacious2 
LASTFM: (cleanup) Cleanup finished
ttilberg@ragnarok:~$ echo Audacious ran without problems.
Audacious ran without problems.
ttilberg@ragnarok:~$ cp /var/log/messages [/home/ttilberg/Desktop/messages]("http://ttilberg.pastebin.com/f16cfda44") 
ttilberg@ragnarok:~$ dmesg>[~/Desktop/dmesg.log]("http://ttilberg.pastebin.com/f26258fcc") 
ttilberg@ragnarok:~$ dpkg -s totem rhythmbox > [~/Desktop/packageinfo.log]("http://ttilberg.pastebin.com/f3acbb51a")
ttilberg@ragnarok:~$ uname -a
Linux ragnarok 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux


>Links to pastebin:
[http://ttilberg.pastebin.com/f16cfda44](http://ttilberg.pastebin.com/f16cfda44) : messages
[http://ttilberg.pastebin.com/f26258fcc](http://ttilberg.pastebin.com/f26258fcc) : dmesg
[http://ttilberg.pastebin.com/f3acbb51a](http://ttilberg.pastebin.com/f3acbb51a) : installed pkg info

---

### Post by mc4man on 2009-11-19
Don't use gstreamer apps too much but maybe try this.
In home folder (view -> show hidden files) there will be a folder .gstreamer-0.1.0
Inside will be a file,(registry.XXXX.bin)  delete it and then start up rhythmbox or totem and see.

---

### Post by ttilberg on 2009-11-19
ttilberg@ragnarok:~$ cd /home/ttilberg/.gstreamer-0.10/
[email]ttilberg@ragnarok:~/.gstrea[/email]mer-0.10$ ls
registry.i486.bin
[email]ttilberg@ragnarok:~/.gstrea[/email]mer-0.10$ rm registry.i486.bin 
[email]ttilberg@ragnarok:~/.gstrea[/email]mer-0.10$ ls
[email]ttilberg@ragnarok:~/.gstrea[/email]mer-0.10$ totem
Error re-scanning registry , child terminated by signal
Run 'totem --help' to see a full list of available command line options.
[email]ttilberg@ragnarok:~/.gstrea[/email]mer-0.10$ rhythmbox
Error re-scanning registry , child terminated by signal
Run 'rhythmbox --help' to see a full list of available command line options.
[email]ttilberg@ragnarok:~/.gstrea[/email]mer-0.10$

---

### Post by mc4man on 2009-11-19
Maybe search out the error and see if any of the ones found or bug reports relate to you.
For instance there are some where having frei0r-plugins installed causes a similar error ( though installing them here had no negative effect on gstreamer, ect.

---

### Post by ttilberg on 2009-11-19
Yeah, I looked around a bit, that's where I came up with reinstalling the gstreamer-plugins-bad package...
Now I'm having a new issue where when I right click properties on any media file (audio or video, but not text or others) nautilus hangs about 10 seconds, and then crashes entirely (including desktop icons).

I initially did a Jaunty upgrade into Karmic, and have been using updates-proposed for a while (since trying to get a few other issues fixed. Some guy recommended it saying he's been using it forever and never had other "problems" pop up).

The other day I read about how doing that above combination will eventually bite you, and weird things will stop working -- The bell must have rung.

I think I'm going to go the route of a fresh install instead:popcorn:. Thanks for trying though guys!

---

### Post by Radio89 on 2009-11-24
Hi!
Try ```
sudo apt-get remove frei0r-plugins
```
...it worked for me ;)

[Source: [Bug #459940]()
           "seems to appear when installing frei0r-plugins (example: for kdenlive). When removing frei0r-plugins from my karmic I've no error messages at all, and totem (and other apps) runs fine."]

---

### Post by patrickcage on 2009-11-25
I have had the same problem, Movie Player (totem) & RhythmBox not opening. Another Symptom was when I right clicked on a video file and chose 'Properties' the folder window would crash out, the rest of my Gnome desktop was ok, just the window containing the video file.

sudo apt-get remove frei0r-plugins
 cured it for me and was confirmed as the culprit when I re-installed it to check, sure enough same problem presented.

For the record I'm on Ubuntu 9.10 (kernel 2.6.31-15-generic), totem 2.28.2, rhythmbox 0.12.5

---

### Post by horseradish on 2009-12-03
> **Radio89 said:**
> Hi!
Try ```
sudo apt-get remove frei0r-plugins
```
...it worked for me ;)

[Source: [Bug #459940]()
           "seems to appear when installing frei0r-plugins (example: for kdenlive). When removing frei0r-plugins from my karmic I've no error messages at all, and totem (and other apps) runs fine."]

sorted me out too when kdenlive made my gstreamer programs crash.

---

### Post by Garibaldi3489 on 2010-01-04
Has anyone found a work around for this besides removing frei0r-plugins? I would really like to use both openshot and rhythmbox on my system but openshot depends on frei0r-plugins. I was able to run this same setup before without incident - could a downgraded version of frei0r-plugins work perhaps?

---

### Post by mc4man on 2010-01-04
> Has anyone found a work around for this besides removing frei0r-plugins?

IF you're on karmic then you should have no issue with the new, redone openshot, which uses only karmic libs to run.
The karmic frei0r-plugins should not be a problem to have installed.

The redone pa for[ karmic]("https://launchpad.net/~jonoomph/+archive/openshot-edge")

The [old one]("https://launchpad.net/~openshot.developers/+archive/ppa") is also (atm) now the same but I wouldn't use (under development


If you're using 8.04 thru 9.04 then there is only a "[build_wizard]("http://www.openshotvideo.com/2008/04/download.html")"

Taking a quick glance at the script it still  does appear there may be a chance for 'breakage' depending on the options chosen and what you're on.
( have no interest in testing

---

### Post by Garibaldi3489 on 2010-01-05
Hm... this is very odd. I have karmic installed and am using the NEW Openshot ppa. However, rhythmbox and gstreamer refuse to start as long as frei0r-plugins (version 1.1.22git20090409+repack-0ubuntu1) is installed. If I remove it, rhythmbox works like normal. Any ideas?

---

### Post by Arcadian on 2010-02-23
> **Radio89 said:**
> Hi!
Try ```
sudo apt-get remove frei0r-plugins
```
...it worked for me ;)

[Source: [Bug #459940]()
           "seems to appear when installing frei0r-plugins (example: for kdenlive). When removing frei0r-plugins from my karmic I've no error messages at all, and totem (and other apps) runs fine."]

Thanks so much!! I've been looking at this one for a few days now. I was wondering why Totem wouldn't load, neither would Banshee & Nautilus kept crashing. Kdenlive was a little flaky too. It all started when I installed Kdenlive, but I never made the connection. Thanks again. Here, have some popcorn for your troubles...

:popcorn:

---

### Post by Daxx1999 on 2011-02-08
> **Radio89 said:**
> Hi!
Try ```
sudo apt-get remove frei0r-plugins
```...it worked for me ;)

[Source: [Bug #459940]("http://Bug%20#459940")
           "seems to appear when installing frei0r-plugins (example: for kdenlive). When removing frei0r-plugins from my karmic I've no error messages at all, and totem (and other apps) runs fine."]

Thanks a lot for these valuable hint!! Despite of that it is an older post, the same problem happens on Lucid 10.04 and Songbird 1.8 after installing Openshot Video Editor. Songbird will not open any longer. 
By trying to open Songbird in a  terminal window you will  just get an error message:

[I]ERROR: Caught a segmentation fault while loading plugin file:
/usr/lib/gstreamer-0.10/libgstfrei0r.so

Please either:
- remove it and restart.
- run with --gst-disable-segtrap and debug.
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal[/I]

 Fortunately your trick by removing the frei0r-plugins solved this problem  on my Computer as well and saved my hours of fault analyses....

Thanks :D

---

