---
title: "Let XScreenSaver play videos using MPlayer"
date: 2012-08-16
forum: Multimedia Software
---

### Post by Marric on 2012-08-16
Let XScreenSaver play videos using MPlayer, in **3 easy steps**:

Using Ubuntu 12.04 OS with Gnome 3, the Gnome-Screensaver is not working as it used to anymore.
> Screensavers were actually removed back in Ubuntu 11.10. Ubuntu  uses  gnome-screensaver and inherited the change from upstream GNOME.  The  GNOME developers think a black screen that puts your monitor into   lower-power mode is optimal. [http://www.howtogeek.com/114027/how-to-add-screensavers-to-ubuntu-12.04/](http://www.howtogeek.com/114027/how-to-add-screensavers-to-ubuntu-12.04/)
So I removed Gnome-Screensaver and **install**ed** XScreenSaver**
```
sudo apt-get purge gnome-screensaver

sudo apt-get install xscreensaver xscreensaver-gl-extra xscreensaver-data-extra
```Details: [http://www.distrogeeks.com/how-to-install-xscreensaver-in-ubuntu-12-04/](http://www.distrogeeks.com/how-to-install-xscreensaver-in-ubuntu-12-04/)

Then I **install**ed** MPlayer**
```
sudo apt-get install mplayer
```The next thing was to **edit the XScreenSaver Preferences File**
```
sudo gedit ~/**.**xscreensaver
```Under 
programs:          \ 
I added
```
"My Movies" mplayer -shuffle -nosound -really-quiet \
-nolirc -nostop-xscreensaver -wid \
$XSCREENSAVER_WINDOW -fs -loop 0 \
$HOME/Path/to/my/movies/* \n\
```[U]Here I used *~/movies/****** to play all the files in the *~/movies/* directory.
[/U]e.g. Use *~/movies/******.avi to play all avi files    or     *~/movies/**mymovie*.mp4 to loop one file.

The MPlayer option _-shuffle_ _plays the files in random order_.
I also used -nosound for it to be a silent screensaver.

Source: [http://www.jwz.org/xscreensaver/faq.html#mpeg](http://www.jwz.org/xscreensaver/faq.html#mpeg)
For further information check the manual links at the bottom of this post.


The XScreenSaver Preferences File then looks like this
```
# XScreenSaver Preferences File
# Written by xscreensaver-demo 5.15 for marric on Sat Aug 11 08:28:35 2012.
# http://www.jwz.org/xscreensaver/

timeout:    0:01:00
cycle:        0:10:00
lock:        False
lockTimeout:    0:00:00
passwdTimeout:    0:00:30
visualID:    default
installColormap:    True
verbose:    False
timestamp:    True
splash:        True
splashDuration:    0:00:05
demoCommand:    xscreensaver-demo
prefsCommand:    xscreensaver-demo -prefs
nice:        10
memoryLimit:    0
fade:        True
unfade:        False
fadeSeconds:    0:00:03
fadeTicks:    20
captureStderr:    True
ignoreUninstalledPrograms:False
font:        *-medium-r-*-140-*-m-*
dpmsEnabled:    False
dpmsQuickOff:    False
dpmsStandby:    2:00:00
dpmsSuspend:    2:00:00
dpmsOff:    4:00:00
grabDesktopImages:  False
grabVideoFrames:    False
chooseRandomImages: False
imageDirectory:    

mode:        one
selected:    0

textMode:    url
textLiteral:    XScreenSaver
textFile:    
textProgram:    fortune
textURL:    http://fridge.ubuntu.com/node/feed

programs: \
[B]        "My Movies" mplayer -shuffle -nosound -really-quiet \
        -nolirc -nostop-xscreensaver -wid \
        $XSCREENSAVER_WINDOW -fs -loop 0 \
        $HOME/Path/to/my/movies/* \n\[/B]
         maze -root \n\
         superquadrics -root \n\
         attraction -root \n\

*# Here might be a long list of programs*
                  
         blitspin -root \n\
         greynetic -root \n\
         helix -root \n\


pointerPollTime:    0:00:05
pointerHysteresis:  10
windowCreationTimeout:0:00:30
initialDelay:    0:00:00
GetViewPortIsFullOfLies:False
procInterrupts:    True
xinputExtensionDev: False
overlayStderr:    True

```Start XScreenSaver
```
xscreensaver-demo
```Now I can choose the new program *My Movies* in the scrolling menu.
The display mode can be changed by clicking 'Settings...' and then 'Advanced >>'.


Links:

XScreenSaver
[https://en.wikipedia.org/wiki/Xscreensaver](https://en.wikipedia.org/wiki/Xscreensaver)
[http://packages.ubuntu.com/precise/xscreensaver]("https://en.wikipedia.org/wiki/Xscreensaver")
[http://www.jwz.org/xscreensaver/man1.html](http://www.jwz.org/xscreensaver/man1.html) Manual

MPlayer
[https://en.wikipedia.org/wiki/Mplayer](https://en.wikipedia.org/wiki/Mplayer)
[http://packages.ubuntu.com/precise/mplayer](http://packages.ubuntu.com/precise/mplayer)
[http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html](http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html) Manual

---

