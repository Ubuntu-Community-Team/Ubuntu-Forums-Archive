---
title: "HOWTO: Play Videos as Screensaver"
date: 2009-12-30
forum: Multimedia Software
---

### Post by kazza on 2009-12-30
Recently I wanted to play a video as my screensaver. Thinking this would be a simple job, I set about searching. After a little time I could not find anything about using gnome-screensaver to play videos. But this has been done with xscreensaver, so I set about lifting the solution to gnome-screensaver.

What follows was adapted from the electric sheep project to use MPlayer to render the screensaver. Two files need to be created, one .desktop that is used by the gnome-screensaver and the other is a script to select a video launch MPlayer.

Step 1)
```
sudo apt-get install mplayer
```

Its a good idea to test mplayer on a video file, 
```
mplayer yourvideo.file
```
just to make sure it can render well enough. If there are problems it could be the case that a different video driver is required, specified with the -vo command line argument. See MPlayer doc for more info.

Step 2)
Create a new file in /usr/share/applications/screensavers/ called movie.desktop,
```
sudo touch /usr/share/applications/screensavers/movie.desktop
```

Then as root enter into movie.desktop 
```

[Desktop Entry]
Encoding=UTF-8
Name=Movie
Comment=Plays Videos
TryExec=movie.sh
Exec=movie.sh
StartupNotify=false
Terminal=false
Type=Application
Categories=Screensaver;
OnlyShowIn=GNOME;
```

This will be used by gnome-screensaver and specifies that the script movie.sh should be run when the screensaver is launched.

Step 3) - movie.sh
There are a few choice that can be made, the script I now present has a list of video files and randomly chooses one, plays it then randomly selects another and continues. It should be fairly simple to modify to suit your own purposes.

Create the script,
```
sudo touch /usr/lib/gnome-screensaver/gnome-screensaver/movie.sh
```
make it executable
```
sudo chmod 755 /usr/lib/gnome-screensaver/gnome-screensaver/movie.sh
```
enter the following 
**NOTE: See bootch's comment below for a better way of writing this script.**
```
#! /bin/bash

## setup MPlayer aruments, remove -nosound if you want the video
## to play sound. If you have to specify the video driver to use
## then add that to the list
MPLAYERARGS="-nosound -nolirc -wid $XSCREENSAVER_WINDOW -nostop-xscreensaver -fs -really-quiet"

## add videos to this list, one will be chosen and played, note
## that wild cards can be used here
VIDEOS=( "/path/to/vid.avi" 
        /path/with/wildcard/*avi)

## child pid, no need to modify
CPID=0

## we handle SIGTERM and SIGINT here to kill the child
## if active then quit.
function ex {
    if [ $CPID -gt 0 ] 
    then
	kill -s 9 $CPID
    fi
    exit 0
}
trap ex SIGINT SIGTERM

## loop while video list is not empty
while [ ${#VIDEOS[*]} -gt 0 ] 
do
    ## pick a random video
    VIDEO=${VIDEOS["$RANDOM % ${#VIDEOS[*]}"]}

    ## play video
    mplayer $MPLAYERARGS "$VIDEO" &
    CPID=$!
    ## wait for video to finish
    wait $CPID
    ## if things went wrong then exit
    if [ $? -ne 0 ]
    then
	exit 1
    fi
    CPID=0
done
```

Please be careful when copying the code that "#! /bin/bash" is at the beginning of the file (no white space).

This script might look complicated, but most of the code is taken up with killing mplayer when the script is killed. This could have been simplified by the use of exec but then to get a different video the screensaver has to be restarted. In a great simplification of the above script would have only one video, which would loop. See
```

#! /bin/bash

## setup MPlayer aruments, remove -nosound if you want the video
## to play sound. If you have to specify the video driver to use
## then add that to the list
MPLAYERARGS="-nosound -nolirc -wid $XSCREENSAVER_WINDOW -nostop-xscreensaver -fs -really-quiet"

## path to video
VIDEO=/path/to/vid

exec mplayer $MPLAYERARGS -loop 0 "$VIDEO"
```

Step 4)
Configure the script by entering videos into the list VIDEOS, to understand the syntax of the list see bash arrays ([http://tldp.org/LDP/abs/html/arrays.html](http://tldp.org/LDP/abs/html/arrays.html)). Make sure that quotes are not used around paths with wild cards as this stops shell expansion.

Finally go System -> Preferences -> Screensaver and select Movie from the list. Your movie should start playing in the preview window, if not make sure the above steps were followed.

All Done.


To test the script remove "-wid $XSCREENSAVER_WINDOW" and "-really-quiet" from the arguments, and run the script from a terminal to see error messages.

---

### Post by ssuuddoo on 2009-12-30
hi, thnx finally for posting this information.

I made all the steps, (had a little problem, because somehow
I didnt correctly copy-paste the whole text to the *.desktop file. ;)

thank You very much


ssuuddoo
Slovakia

---

### Post by SSVegito888 on 2010-02-03
I'm having a hard time with

MPLAYERARGS="-nosound -nolirc -wid $XSCREENSAVER_WINDOW -nostop-xscreensaver -fs -really-quiet"




The part that is giving me errors is:

-wid $XSCREENSAVER_WINDOW


the "$XSCREENSAVER_WINDOW" is doing it.

I am using CentOS 5 and would have posted in the CentOS forums, but I used to use ubuntu so I decided to post here, since you created the script, I figured you'd know the script better than anyone else.


So, how exactly do I define the variable $XSCREENSAVER_WINDOW


Thanks,

SSVegito888

---

### Post by bootch on 2010-03-10
Thanks a lot for this HOWTO.

Also to make the script a lot shorter but still have a random list of videos you can use the playlist function of MPlayer :

The script :
```
#! /bin/bash

## setup MPlayer aruments, remove -nosound if you want the video
## to play sound. If you have to specify the video driver to use
## then add that to the list
MPLAYERARGS="-nosound -nolirc -wid $XSCREENSAVER_WINDOW -nostop-xscreensaver -fs -really-quiet"

exec mplayer $MPLAYERARGS -loop 0 -shuffle -playlist /path/to/playlist
```The playlist can be a simple text file with the path to a video file on each line.

---

### Post by hydrozen on 2010-03-10
Hey there,

thanks for the script. Been trying to find a SaveHollywood equivalent for linux. I have a problem with your solution though.... it works well when I just preview the screensaver from the gnome-screensaver gui utility.... but when the screensaver actually starts when the computer is idle, it does not seem to work.... the screen fades to black and then it goes back to desktop and the screensaver never tries to kick in again.

any ideas on how I might solve this or troubleshoot the issue?

thanks

---

### Post by kazza on 2010-03-12
> **SSVegito888 said:**
> I'm having a hard time with

MPLAYERARGS="-nosound -nolirc -wid $XSCREENSAVER_WINDOW -nostop-xscreensaver -fs -really-quiet"




The part that is giving me errors is:

-wid $XSCREENSAVER_WINDOW


the "$XSCREENSAVER_WINDOW" is doing it.

I am using CentOS 5 and would have posted in the CentOS forums, but I used to use ubuntu so I decided to post here, since you created the script, I figured you'd know the script better than anyone else.


So, how exactly do I define the variable $XSCREENSAVER_WINDOW


Thanks,

SSVegito888

Hi SSVegito888,

Firstly, I would have replied sooner if this was a new message as I get emailed not an edited old message that said you had solved the problem.

The $XSCREENSAVER_WINDOW variable is defined by xscreensaver, also gnome-screensaver defines it for compatibility. Its purpose is to provide a window ID that the screen saver can draw onto.

At a guess, the problem you are having appears to be that $XSCREENSAVER_WINDOW is not defined, so is reduced to nothing. An actual error message would be helpful.

To test this I ran gnome-screensaver-preferances from the terminal and selected the script from the list, this way any output from the script was dumped to the terminal. At this point all that is required is a simple script that echos $XSCREENSAVER_WINDOW, if it is not defined then please look up for you system how the screen saver finds the correct window to draw onto.

Best
Kazza

---

### Post by kazza on 2010-03-12
> **bootch said:**
> 
Also to make the script a lot shorter but still have a random list of videos you can use the playlist function of MPlayer

...

The playlist can be a simple text file with the path to a video file on each line.

A nice elegant solution, Ive added a note above for people to use this version instead.

Also as a side issue, from a security perspective this is better as the playlist could be in the users home directory, thus they dont need root access to change the video list and each user can have there own playlist :).

---

### Post by kazza on 2010-03-12
> **hydrozen said:**
> 
any ideas on how I might solve this or troubleshoot the issue?


Hi Hydrozen,

Does it work in full screen from the gnome-screensaver-preferences dialog? If not then this would be a good place to start.

To test, as mentioned above run gnome-screensaver-preferences from the terminal and look at the outputs.  


Also, there could be some issue with video drivers, does MPlayer work in full screen normally?

Best,
Kazza

---

### Post by khaye on 2010-03-12
Have to try this but it looks complicated to me. Pardon for my ignorance. I just had my net installed. I'll try to do it. But expect me to keep asking questions everytime.
Thanks for the tip, anyway.

---

### Post by PerfectReign on 2010-05-04
Yes!!

I've been searching for a little while for GNOME video screensaver. Should have looked here first. I noticed that my wife's Vista computer - in the same home office as my Ubuntu laptop and desktop - plays videos on her standard photo screen saver, for those video files in our Photos directory.

Now I can too!

Thanks!!


I used the second script and created a text file containing the videos in a folder.  Works perfectly.

---

### Post by theonlytruth on 2010-05-17
Hey,
I tried your HowTo, but the new Screensaver doesn't appear in the screensaver menu. 

I tested the movie.sh script like you told and this runs.

Do you know my problem?

OS: Ubuntu 10.04

I think I found my mistake: Now I entered the whole path and now its listed. (I also added some other lines So now it lokks so:

```
[Desktop Entry]
Encoding=UTF-8
Name=Movie
Comment=Plays Videos
TryExec=movie.sh
Exec=/usr/lib/gnome-screensaver/gnome-screensaver/movie.sh
StartupNotify=false
Terminal=false
Type=Application
Categories=GNOME;Screensaver;
OnlyShowIn=GNOME;
X-Ubuntu-Gettext-Domain=gnome-screensaver

```

---

### Post by davitodd on 2010-06-08
I wrote out the scripts, and it didn't let my load the video. Mplayer keeps saying that it could not open the video out device. I already tried to change it, to things in the /dev/ folder that looked like it would be for the video. I am running on Ubuntu 9.10, and I also have an ATI graphics card. If you could point me in the right direction, and show me what I'm doing wrong, any help would be greatly appreciated.

---

### Post by brendanpiater on 2010-08-10
Thanks for a great post, this is really useful. Just a small point, the list of screensavers is not updated automatically when you open screensaver prefs. it only updates apparently when running "dpkg" in 10.04 (not sure on previous). 

I just ran a pending update and the list was refreshed to include the new screensaver. I guess installing something from the repos if you don't have an update pending would do the same.

Hope that helps someone.

Cheers
B

---

### Post by M4he on 2010-08-12
Many many thanks for this brilliant HowTo!
I'm just pointing the script to a special directory in my Videos folder and it plays everything I throw in there as screensaver. It works like a charm.

> **brendanpiater said:**
> [...] the list of screensavers is not updated  automatically when you open screensaver prefs. it only updates  apparently when running "dpkg" in 10.04

Hmm strange... I'm also running 10.04 but the screensaver was in the list soon after I added the .desktop file into the according directory.

Thanks a bunch for this awesome tutorial!

---

### Post by MattBlack on 2010-10-28
Hi

Using 10.10 - I have tried the above and all works fine except....

The videos reset after 10mins.

Can anyone shine some light on why this is so.

Many thanks.
Me

---

### Post by MattBlack on 2010-10-28
> **MattBlack said:**
> Hi

Using 10.10 - I have tried the above and all works fine except....

The videos reset after 10mins.

Can anyone shine some light on why this is so.

Many thanks.
Me

Hi

This can be aleviated by changing the value of cycle_delay. (gconf-editor -> apps-> gnome-screensaver ) By default this is 10 (mins) changing to 3600 seems to have the desired effect. Setting this to 0 actually sets cycle to 1 min.

Therefore it seems that even though mode is single it still cycles according to cycle delay.

Hope this helps other people experiencing this.

Matt

---

### Post by CyberCod on 2010-12-09
Great thread!  Much thanks!  Will be using this for a video box at work for company vids. Figured I'd share my modifications in case they help someone else down the line.

This is how I ended up doing it:

```

#! /bin/bash

## delete previous playlist
rm -f /home/tv/playlist.pls

## setup MPlayer aruments, remove -nosound if you want the video
## to play sound. If you have to specify the video driver to use
## then add that to the list
MPLAYERARGS="-nolirc -wid $XSCREENSAVER_WINDOW -nostop-xscreensaver -fs"


## find all files in the chosen directory add to playlist 
find /Storage/Media/Videos/PlayAsScreensaver/* > /home/tv/playlist.pls

## child pid, no need to modify
CPID=0

#play freshly generated playlist
exec mplayer $MPLAYERARGS -loop 0 -shuffle -playlist /home/tv/playlist.pls

```

---

### Post by CyberCod on 2010-12-18
> **MattBlack said:**
> Hi

This can be aleviated by changing the value of cycle_delay. (gconf-editor -> apps-> gnome-screensaver ) By default this is 10 (mins) changing to 3600 seems to have the desired effect. Setting this to 0 actually sets cycle to 1 min.

Therefore it seems that even though mode is single it still cycles according to cycle delay.

Hope this helps other people experiencing this.

Matt

Actually, I'm still having this problem.  Ubuntu 10.04.  Any Help?  I already set the cycle delay to 3600.

---

### Post by Toost Inc. on 2010-12-30
> **SSVegito888 said:**
> I'm having a hard time with

MPLAYERARGS="-nosound -nolirc -wid $XSCREENSAVER_WINDOW -nostop-xscreensaver -fs -really-quiet"




The part that is giving me errors is:

-wid $XSCREENSAVER_WINDOW


the "$XSCREENSAVER_WINDOW" is doing it.

I am using CentOS 5 and would have posted in the CentOS forums, but I used to use ubuntu so I decided to post here, since you created the script, I figured you'd know the script better than anyone else.


So, how exactly do I define the variable $XSCREENSAVER_WINDOW


Thanks,

SSVegito888


I'm running Ubuntu 10.04  and I seem to be having the same problem.
The error message I keep getting when running gnome-screensaver-preferences is:
"Terminal type `unknown' is not defined."

And indeed when I put $XSCREENSAVER_WINDOW in quotes, it doesn't give me this error anymore, but also just a black screen to look at. If I completely remove the -wid argument however the same error is back. 

Has anyone had any progress with this?

Thanks,
Toost Inc.

---

### Post by clauguia on 2011-04-12
Thank you Kazza and bootch!

Works like charm in ubuntu 10.10

---

### Post by draldo on 2011-04-27
Hey all, 


Nice piece of work there =D Much appreciated. I also ran into a couple of the same problems others have had here but managed to sort them. The first was the Screensaver menu entry which was sorted thanks to theonlytruth and brendanpiater. The second was that, like others, fullscreen preview didn't show nor did it kick in when it should have and only "seemed" to go back to desktop after first showing a black screen.

This last issue was fixed by adding a specific output option in the code, I chose xv and that works like a charm : 

```
#! /bin/bash

## setup MPlayer aruments, remove -nosound if you want the video
## to play sound. If you have to specify the video driver to use
## then add that to the list
MPLAYERARGS="-nosound -nolirc -vo xv -wid $XSCREENSAVER_WINDOW -nostop-xscreensaver -fs -really-quiet"

## path to video
VIDEO=/path/to/video

exec mplayer $MPLAYERARGS -loop 0 "$VIDEO"
```

You can of course choose whichever output you wish whether it be xv, x11, gl, gl2 etc

Thanks again.

---

### Post by SSVegito888 on 2011-05-07
Long time no see everyone. I've been using Debian Squeeze as my primary distro for a good while now. I really like it. I switched from CentOS about 6 months to a year ago. Does anyone know how to modify this screensaver setup to work in other desktop environments such as KDE4 and LXDE. I'd also like to know how to get it working on xscreensaver also.



Thanks,

SSVegito888

EDIT: By the way I like the playlist idea.

I modified the scripts a tiny bit and combined several of the parameters that I wanted into a slightly new one.


Here's the code for the script.

```

#! /bin/bash

## delete previous playlist
rm -f ~/.Screensavers/playlist.pls

## setup MPlayer aruments, remove -nosound if you want the video
## to play sound. If you have to specify the video driver to use
## then add that to the list
MPLAYERARGS="-nolirc -vo xv -wid $XSCREENSAVER_WINDOW -nostop-xscreensaver -fs -really-quiet"


## find all files in the chosen directory add to playlist
find ~/.Screensaver/.Videos/* > ~/.Screensaver/playlist.pls

## child pid, no need to modify
CPID=0

#play freshly generated playlist
exec mplayer $MPLAYERARGS -loop 0 -shuffle -playlist ~/.Screensaver/playlist.pls
```

---

### Post by SSVegito888 on 2011-05-13
Seriously, anyone know how to get it working in kde4?

---

### Post by Scot_Bernard on 2011-08-15
Hello, trying to make it work with two monitors in twin view with no luck. the preview works but when the screensaver starts i get a blank screen in my two monitors. Some idea how to fix it?

---

### Post by SSVegito888 on 2011-08-29
Sorry it took me so long to reply back. I've been without an internet connection for a long time now. I got it working. My problem was, xscreensaver wasn't set up properly. But, fixed it.



Also, for those of you who want to run xscreensaver on two monitors, my guess would be either looking around the man pages for xscreensaver and/or mplayer for display flags.

eg. man mplayer lists an option for "-display". Try modding the mplayer script to say:

```
-display :0 --display :1
```


That may work. But, i'm not sure.


-SSVegito888

---

### Post by baltisalty on 2011-11-14
Does anybody have this working for 11.10 with gnome 3?

---

### Post by johnsky on 2011-12-17
We can't be serious...

...?


A screensaver is supposed to be one of the most absolute basic parts of a GUI OS these days. And you need to go through lines of code JUST TO PUT A VIDEO AS YOUR SCREENSAVER?! (sorry for the caps, but I'm a little flustered here)

This simply must be addressed. Not in a how to with points of "copy this folder", "type this code", "enter this in terminal"...

Imagine how fast a first time ex-windows user will drop Ubuntu when THIS is the best answer we can give them regarding making a simple video as their screensaver!


The reason I wound up here : 
I've created a rather nice animation for a studio to use as their screensaver. They love it. And so far, all I can use it on is their winblows machines because they're not willing to copy lines of code on each machine just to have the screensaver on the hundreds of Ubuntu machines they have.

They want a simple solution. Set this as screensaver, done.


This is really an issue?

---

### Post by ba0bab on 2012-07-29
> **draldo said:**
> Hey all, 


Nice piece of work there =D Much appreciated. I also ran into a couple of the same problems others have had here but managed to sort them. The first was the Screensaver menu entry which was sorted thanks to theonlytruth and brendanpiater. The second was that, like others, fullscreen preview didn't show nor did it kick in when it should have and only "seemed" to go back to desktop after first showing a black screen.

This last issue was fixed by adding a specific output option in the code, I chose xv and that works like a charm : 

```
#! /bin/bash

## setup MPlayer aruments, remove -nosound if you want the video
## to play sound. If you have to specify the video driver to use
## then add that to the list
MPLAYERARGS="-nosound -nolirc -vo xv -wid $XSCREENSAVER_WINDOW -nostop-xscreensaver -fs -really-quiet"

## path to video
VIDEO=/path/to/video

exec mplayer $MPLAYERARGS -loop 0 "$VIDEO"
```

You can of course choose whichever output you wish whether it be xv, x11, gl, gl2 etc

Thanks again.


THANKS! That goes out to both TheOnlyTruth and Draldo. I just got a blanck screen, but the -vo x11 helped solve the problem. Thank you for stating that you could use not only xv but also x11, a very thorough explanation that solved my problem. -vo xv didn't do it, but -vo x11 did the trick. Perfect! Thanks alot, this is great.

---

### Post by Marric on 2012-08-11
Let XScreenSaver play videos using MPlayer, in **3 easy steps**:

Using Ubuntu 12.04 OS with Gnome 3, the Gnome-Screensaver is not working as it used to anymore.
> Screensavers were actually removed back in Ubuntu 11.10. Ubuntu uses  gnome-screensaver and inherited the change from upstream GNOME. The  GNOME developers think a black screen that puts your monitor into  lower-power mode is optimal. [http://www.howtogeek.com/114027/how-to-add-screensavers-to-ubuntu-12.04/](http://www.howtogeek.com/114027/how-to-add-screensavers-to-ubuntu-12.04/)So I removed Gnome-Screensaver and **install**ed** XScreenSaver**
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

### Post by astembridge on 2013-05-06
Anyone successfully made this work with VLC instead of MPlayer?

---

