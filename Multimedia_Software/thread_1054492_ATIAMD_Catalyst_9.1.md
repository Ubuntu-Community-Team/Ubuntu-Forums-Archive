---
title: "ATI/AMD Catalyst 9.1"
date: 2009-01-29
forum: Multimedia Software
---

### Post by PoopyTheJ on 2009-01-29
I can't believe no ones posted this yet or I can't find it but ATI released the Catalyst 9.1 drivers finally offering support for Quad core and fixing the flickering video when compiz is enabled. I'm sure there are more fixes, performance is very nice either way. If you've got a newer ATI card do yourself a favor and go grab em!

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

---

### Post by tehk on 2009-01-29
gonna wait for a few more, OK's before installing them as I've had problems installing ATI drivers from the shell on multiple distros in the past and usually rely on the package manager to do it for me....

---

### Post by frashman on 2009-01-30
I'm wondering, if ubuntu updates restricted drivers?
Or must I do it manually?

Greetings

---

### Post by mozychan on 2009-01-30
Just installed and it is working pretty good, other then a few minor glitches.  Keep it coming AMD!

-moose

---

### Post by binbash on 2009-01-30
It works great and fixes some of my problems!...

---

### Post by tom-ubuntu on 2009-01-30
> **frashman said:**
> I'm wondering, if ubuntu updates restricted drivers?
Or must I do it manually?

Greetings

I doubt, they will update them that shortly.

Will give it a try this weekend. Sounds pretty promising from what I read so far. Hopefully we ATI users will get a smooth Compiz experience finally  :)

Any experience from other users are very welcome.

---

### Post by centos on 2009-01-30
Is it necessary to deactivate proprietary driver first? I have tried to manually install drivers once and it didn't work very well so I'm rather asking..

---

### Post by dopira on 2009-01-30
I didn't uninstall the previous drivers, just ran the script from their website. Everything went fine (I have a 4850 and 64-bit 8.10)

Finally no flickering for my movies!

---

### Post by PoopyTheJ on 2009-01-30
usually I just let the automatic install do the work for me on 8.04, sudo sh ati-driver* and it uninstalls the old driver and installs the new driver. Well since about 8.09 or so anyways, I'm very happy with these drivers good job AMD!

---

### Post by frogotronic on 2009-01-30
> **centos said:**
> Is it necessary to deactivate proprietary driver first? I have tried to manually install drivers once and it didn't work very well so I'm rather asking..

Follow this guide...[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

-CH   :popcorn:

---

### Post by centos on 2009-01-30
Didn't work for me, I installed it and after restart last thing I saw was a few lines of text with Checking battery state as the last one, then screen went black and that was it. 
At least I have two graphic cards in my laptop, so hopefully I will able to unistall it because the other one works. But still gl output at videos is broken. Just great.

edit: thanks, aticonfig --initial -f helped.
this card (mobility radeon hd2600) has same gl problem as x1250.. wonder if it is driver problem or anything else's
and can't set any compiz effects, but this doesn't bother me, don't see point of using it

---

### Post by centos on 2009-01-30
Turned out that Totem (and other gstreamer based apps like Gnome Subtitles) flickers. I tried to reinstall gstreamer plugins and change output, no change. Just me? :/

---

### Post by mozychan on 2009-01-30
One major problem is that the videos don't align within the windows of players correctly.  There is always a black bar at the top.  Viewing the video full screen will centre it like it should, which is good.

Still some other minor, but irritating, glitches.

-moose

---

### Post by mozychan on 2009-01-30
> **mozychan said:**
> One major problem is that the videos don't align within the windows of players correctly.  There is always a black bar at the top.  Viewing the video full screen will centre it like it should, which is good.

Still some other minor, but irritating, glitches.

-moose

Ok I figured it out.  When I installed 9.1 I changed the video output drivers back to the default xv so that I could verify that they were no longer choppy.  They are no longer choppy, but the video is not aligning properly in the windows and hides the player controls sometimes.  Now if I go back to the x11 driver I had set before, there is no longer any problem.

-moose

---

### Post by theApokalypsis on 2009-01-31
lol, duplicated thread. but this one has the action, better title too :)

[http://ubuntuforums.org/showthread.php?t=1054581]("http://ubuntuforums.org/showthread.php?t=1054581")

Mplayer seems to be best. At random times watching in Totem my x crashes and restarts. and some decorating issues...

but all in all working.


however still no luck with Jaunty and new xserver support. but progress is being made :D

using a (HD 3300/HD 4870)

---

### Post by centos on 2009-01-31
So yesterday everything but gstreamer went fine, today I turned it on and after boot screen it didn't se anything, just heard cpu fan because of high cpu usage. I had to reboot and change graphic card, with that other it showed command line at least, so I copied xorg.conf backup to make it work.
I'm just curious if I'm stupid, my laptop is or ATI is. Definitely one of the three, maybe all.

---

### Post by kgotth on 2009-02-01
> **cement_head said:**
> Follow this guide...[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

-CH   :popcorn:

Still no luck, I followed manual install [http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide) last night 3 times, no errors but after restart low graphic mode and fglrxinfo saying mesa drivers, so I switched to older version 8.543, anyone similar expirience?   
I have ati radeon mobility x1600 on ubuntu 8.10 with compiz fusion

---

### Post by frogotronic on 2009-02-01
> **kgotth said:**
> Still no luck, I followed manual install [http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide) last night 3 times, no errors but after restart low graphic mode and fglrxinfo saying mesa drivers, so I switched to older version 8.543, anyone similar expirience?   
I have ati radeon mobility x1600 on ubuntu 8.10 with compiz fusion

Hi,

I've had this problem - you have to uninstall the mesa drivers...

```
Removing Mesa drivers

If fglrxinfo reports that Indirect rendering by Mesa is in place, even though you have installed ATI driver, check:

    * Remove the package xserver-xgl. 

    sudo apt-get remove xserver-xgl

    Explanation: If you installed this previously in order to make compiz work, it will not allow direct rendering on your display. You can check out if this is what it causing the problem by running 

    DISPLAY=:0 glxinfo | grep render

    If it returns an ATI renderer, it means that xgl is being displayed indirectly on the display 1. (Taken from [1]) 

    Warning: This might make your compiz stop working as it is configured to use XGL. A solution might be to run the Envy script in order to configure compiz. Or, if Compiz stopped working due to "Composite" problem, check that the following is set in the /etc/X11/xorg.conf 

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

then reboot, you should now have ati fglrx rendering

- CH

---

### Post by theApokalypsis on 2009-02-01
> **centos said:**
> So yesterday everything but gstreamer went fine, today I turned it on and after boot screen it didn't se anything, just heard cpu fan because of high cpu usage. I had to reboot and change graphic card, with that other it showed command line at least, so I copied xorg.conf backup to make it work.
I'm just curious if I'm stupid, my laptop is or ATI is. Definitely one of the three, maybe all.

Check out this post i made about reconfiguring. it may help :)

[http://ubuntuforums.org/showpost.php?p=6646754&postcount=9]("http://ubuntuforums.org/showpost.php?p=6646754&postcount=9")

---

### Post by kgotth on 2009-02-01
Thanks guys, now new ATI driver is in place!!!strange thing... after reboot it starts out of range resolution (1200x1600) and should be 1400x900 (set in Catalyst CC). relevant sections of xorg:
Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

does it matter that in System/Administration/Hardware Drivers ATI/AMD fglrx graphic driver is NOT active? I'm afraid to change anything, don't want to loose the driver!!!

---

### Post by centos on 2009-02-01
> **theApokalypsis said:**
> Check out this post i made about reconfiguring. it may help :)

[http://ubuntuforums.org/showpost.php?p=6646754&postcount=9]("http://ubuntuforums.org/showpost.php?p=6646754&postcount=9")

thx will check it out

kgotth: mine is inactive too but new drivers are working

---

### Post by frogotronic on 2009-02-01
> **kgotth said:**
> Thanks guys, now new ATI driver is in place!!!strange thing... after reboot it starts out of range resolution (1200x1600) and should be 1400x900 (set in Catalyst CC). relevant sections of xorg:
Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

does it matter that in System/Administration/Hardware Drivers ATI/AMD fglrx graphic driver is NOT active? I'm afraid to change anything, don't want to loose the driver!!!

It should be green, but not checked.  Have you tried the [wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")?

You can try adding the following to your xorg.conf file 

```
Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1400x900" "1024x768" "800x600"
	EndSubSection
EndSection
```

- CH

---

### Post by zim2dive on 2009-02-01
what verasion of ccc comes with this?  I have 2.3, but think I have seen references to something newer (but 2.3 is all I got? with my 9.1 install).

So what I don't see with 2.3 is how to adjust overscan on HDMI?  The Vista version comes with CCC 3.x, and it has overscan adjustment.. but I can't find it under my 2.3 version in Ubuntu.

I installed 9.1 by hand via the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

thanks!
Mike

---

### Post by theApokalypsis on 2009-02-02
the linux CCC is very different than the Vista CCC including features. the one that comes with the 9.1 is the lastest so far for Linux. 

I believe... correct me if I am wrong people!

---

### Post by zim2dive on 2009-02-02
> **theApokalypsis said:**
> the linux CCC is very different than the Vista CCC including features. the one that comes with the 9.1 is the lastest so far for Linux. 

I believe... correct me if I am wrong people!

What do you get for > /usr/bin/amdcccle -version

I get 2.3.

Shocked that it doesn't include the basic functions for overscan, screen position (since ATI doesn't seem smart enough to pick good defaults on a digital video output)

---

### Post by theApokalypsis on 2009-02-02
confirmed 2.3.

---

### Post by zim2dive on 2009-02-02
> **theApokalypsis said:**
> confirmed 2.3.

thanks.. guess I have to stick with the command line to override the nutty defaults they pick for overscan (10% overscan on an LCD?!?!)... any way to push > sudo aticonfig --set-dispattrib=tmds2,sizeX:1920
sudo aticonfig --set-dispattrib=tmds2,sizeY:1080
sudo aticonfig --set-dispattrib=tmds2,positionX:+0
sudo aticonfig --set-dispattrib=tmds2,positionY:+0 into my xorg.conf?  I don't want to have to run these commands every time I log in.

---

### Post by theApokalypsis on 2009-02-02
unfortunatly I have not found a way to persist it to the DB. 

I do the same thing on startup with setting my ATI fan speed.

---

### Post by zim2dive on 2009-02-02
> **theApokalypsis said:**
> unfortunatly I have not found a way to persist it to the DB. 

I do the same thing on startup with setting my ATI fan speed.

Is there a good way to automate this? (I could put in my .profile, but aticonfig requires root privs... something like /etc/rc.local?)

---

### Post by theApokalypsis on 2009-02-02
see i ran this command at startup, but with no sudo and it worked.

aticonfig --pplib-cmd "set fanspeed 0 45"

but i believe you are right. and im not sure about that one :s

---

### Post by zim2dive on 2009-02-02
On my 1st reboot after the config I 

- see the text boot stuff
- see the Ubuntu splash, progress bar
- get a black screen after that

I can ssh in.

This is a new one... how do I recover?

---

### Post by theApokalypsis on 2009-02-02
you can use 

sudo editor /filepath

to use a terminal based editor to revert your changes.

---

### Post by zim2dive on 2009-02-02
> **theApokalypsis said:**
> you can use 

sudo editor /filepath

to use a terminal based editor to revert your changes.

I never made any file changes...I only issued those commands from the command line..

---

### Post by zim2dive on 2009-02-02
So I "recovered" by> sudo apt-get remove --purge xorg-driver-fglrx
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv 

so what are my driver alternatives?? :)

EDIT: or not.. reboot gets me: "No servers were identified in the configuration file and XDMCP was disabled.  This can only be a configuration error.  GDM has started a single server for you.  You should log in and fix the configuration.  Note that automatic and timed logins are disabled now".  Happy happy joy joy

EDIT2: this link worked to fix the black screen... [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Black_Screen_when_supposed_to_see_login_screen](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Black_Screen_when_supposed_to_see_login_screen)

---

### Post by motang on 2009-02-02
> **PoopyTheJ said:**
> I can't believe no ones posted this yet or I can't find it but ATI released the Catalyst 9.1 drivers finally offering support for Quad core and fixing the flickering video when compiz is enabled. I'm sure there are more fixes, performance is very nice either way. If you've got a newer ATI card do yourself a favor and go grab em!

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)
Well let me tell you, I saw this posted on [Softpedia]("http://news.softpedia.com/news/Latest-ATI-Linux-Video-Driver-Introduces-Full-OpenGL-3-0-Support-103262.shtml") and quickly downloaed it and installed it on my system.  After that was done, my system is so much smoother, and I am loving it.  Compiz-fusion is smooth, and much faster.  I am really liking this and finally we Ubuntu/Linux users are getting some really high qaulity products from big companies like Flash 10 and Flash 10 64bit, now this.  Things are really looking up!

---

### Post by theApokalypsis on 2009-02-02
> **zim2dive said:**
> So I "recovered" by

so what are my driver alternatives?? :)

EDIT: or not.. reboot gets me: "No servers were identified in the configuration file and XDMCP was disabled.  This can only be a configuration error.  GDM has started a single server for you.  You should log in and fix the configuration.  Note that automatic and timed logins are disabled now".  Happy happy joy joy

EDIT2: this link worked to fix the black screen... [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Black_Screen_when_supposed_to_see_login_screen](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Black_Screen_when_supposed_to_see_login_screen)


try in the command line...


sudo dpkg-reconfigure -phigh xserver-xorg
sudo aticonfig --initial -f


then try and reboot that should set everything back to a genric config

---

### Post by zim2dive on 2009-02-02
> **theApokalypsis said:**
> try in the command line...


sudo dpkg-reconfigure -phigh xserver-xorg
sudo aticonfig --initial -f


then try and reboot that should set everything back to a genric config


I'll file that away (thanks), but I _think_ I'm back to where I was before I "fixed" my resolution issue (before the black screen reboot).  I suppose I can try the aticonfig commands again, and keep the PCI line in my xorg.  I probably ended up backrevving my ATI driver in the recovery process.

Given that I couldn't get flash audio with the new driver either, I think I'll focus on that (started a thread), and then worry about getting the newest driver later.

thanks!

---

### Post by theApokalypsis on 2009-02-02
good luck!

ive had my share of headaches with Linux and drivers etc.

but wheres the fun in having everything working and perfect :) lol

---

### Post by zim2dive on 2009-02-02
> **theApokalypsis said:**
> good luck!

ive had my share of headaches with Linux and drivers etc.

but wheres the fun in having everything working and perfect :) lol

Gee, I dunno.. I'd like to have the chance to find out :)

---

### Post by soderman on 2009-02-04
> **zim2dive said:**
> Gee, I dunno.. I'd like to have the chance to find out :)

I know how you feel. =/

I also have problem when rebooting. Only black

I have to "sudo cp /etc/ati/amdpcsdb.default /etc/ati/amdpcsdb"
And then again change vsync and that stuff in CCCP.

And the HDTVunderscan,0 doenst work it seems...so I guess something is ****** up with ATI...again..

/Söder

---

### Post by jimmal on 2009-02-04
under/overscan makes my pc crush too. the only workout is as mentioned above set amdpcsdb defaults.

BE2400 - 4850 - intrepid 8.10/x_64

---

### Post by ErsinG on 2009-02-04
well i'm downloading too.. gonna check it and feedback here.. :) ty for sharing the link

---

### Post by theApokalypsis on 2009-02-04
Anyone checked out the 9.2 Beta?

Just installed, seems like nothing changed. but then again the beta was leaked before 9.1 was even released so.......

---

### Post by zika on 2009-02-04
> **theApokalypsis said:**
> Anyone checked out the 9.2 Beta? Just installed, seems like nothing changed. but then again the beta was leaked before 9.1 was even released so.......
I do not see much differences.

if I switch to xv I do no get movie shifted 1/2 window down (as I do get with 9.1) but no video at all, sound is OK.

a little bit even slower than 9.1 but with, I think, sharper picture.

interesting. (uneventful installation though)

---

### Post by kgotth on 2009-02-04
Hello, still can't get it right!!!driver is in place,but resolution is now like 1024x768  
fglrxinfo gives me:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series     
OpenGL version string: 2.1.8395 Release

my xorg:

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "on"
	Option	    "TexturedVideo" "on"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1400x900" "1024x768" "800x600"
	EndSubSection
EndSection

video card: ati x1650 pro, x64 on Ibex
any help or idea much appreciated

---

### Post by nimbus9 on 2009-02-05
I noticed the ATI Radeon HD 4650 was not listed. Does software for this card usually come later or am I just out of luck?

---

### Post by theApokalypsis on 2009-02-05
the newests AMD/ATI drivers support 2D/3D for newer cards. the 4000 series is based on the R700 so i dont see any reason why it should not work.

---

### Post by Pitboss on 2009-02-07
I installed the new drivers, but I have some problems. Although at first I was happy to see that the video doesn't flash any more, now other problems occur. If I open a video file with vlc or totem the video player windows looks "damaged". When I use mplayer it doesn't seem to have this problem, but I noticed that every 15 ~ 20 minutes the video stops playing for a second or two and then continues normally again. It's pretty irritating and I'll appreciate some advice.

---

### Post by theApokalypsis on 2009-02-07
Im having the same issues. there are still some bugs.

ps

watch out when using totem on ocasion the xserver crashes when going to full screen.


hopefully it gets better with the next release. hopefully that will be soon.

---

### Post by theApokalypsis on 2009-02-08
and resizing with VLC and Totem player seems to crash everything as well :).


now Im forced to deal with Mplayer and i hate it. anyone know any better media players?

EDIT:

just an edit. tried out Totem Player with the Xine backend and not gstreamer. seems to be less crash prone so far.

---

### Post by frogotronic on 2009-02-08
> **theApokalypsis said:**
> and resizing with VLC and Totem player seems to crash everything as well :).


now Im forced to deal with Mplayer and i hate it. anyone know any better media players?

EDIT:

just an edit. tried out Totem Player with the Xine backend and not gstreamer. seems to be less crash prone so far.

I use XINE...

---

### Post by zim2dive on 2009-02-09
> **theApokalypsis said:**
> and resizing with VLC and Totem player seems to crash everything as well :).


now Im forced to deal with Mplayer and i hate it. anyone know any better media players?

EDIT:

just an edit. tried out Totem Player with the Xine backend and not gstreamer. seems to be less crash prone so far.

I was always a VLC fan.. someone pointed me to SMplayer.. It didn't seem that bad :)  (mplayer does handle WMVs better)

---

### Post by jml75 on 2009-02-09
For me, I'va seen a major improuvement in desktop smoothness with this release.

Way to go AMD!

This is a much better driver than the 8.12 one.

---

### Post by PoopyTheJ on 2009-02-11
I have noticed increased flakiness with these and movie playback. I noticed that killing the pulseaudio process before opening any video does wonders for stability with video playback. I don't crash when I kill pulseaudio and playback videos. With pulseaudio running and Xine it's almost a guaranteed crash.

---

### Post by projectbronco on 2009-02-11
I just installed this. So far what I've noticed is:
Crisper display, no blackouts so far(I have the syncmaster 204B), and now I have the Catalyst tools. I'm pretty happy!
I haven't tried to play any movies yet, but I may even keep my x800 pro now. I was planning on upgrading because of the blackouts. 

I didn't actually uninstall the proprietary driver, I just disabled it. I figured if this didn't work, I could go back. I found it interesting though, that when scanning for drivers, 9.1 didn't come up...Oh well, it is obviously working so who cares?!:guitar:


Vlc hesitates like everyone has been saying. Also, still blackouts. 
I'LL GET YOU BLACKOUTS!!!

---

### Post by theApokalypsis on 2009-02-11
yeah. ubuntus restricted drivers are a bit behind but supported and tested for the distro.

i believe Jaunty is sporting the newests 9.1 in the repos...

---

### Post by Pitboss on 2009-02-14
Does anyone have trouble with gnome-screensaver? My computer crashes sometimes if I try to change my screensaver from System > Preferences > Screensaver. The whole system just freezes and I have to reboot manually. Also every preview of the screensaver in window or fullscreen flashes like movies flashed with the last driver. I installed xserverscreensaver but it seems that there are problems too. I have this strange feeling that this has something to do with the driver :D, but I haven't noticed anyone else complaining for that.

So, anyone? :)

---

### Post by frogotronic on 2009-02-14
> **Pitboss said:**
> Does anyone have trouble with gnome-screensaver? My computer crashes sometimes if I try to change my screensaver from System > Preferences > Screensaver. The whole system just freezes and I have to reboot manually. Also every preview of the screensaver in window or fullscreen flashes like movies flashed with the last driver. I installed xserverscreensaver but it seems that there are problems too. I have this strange feeling that this has something to do with the driver :D, but I haven't noticed anyone else complaining for that.

So, anyone? :)

I think so...I had hard lockups with GLMatrix.  I switched to Cosmos (bitmap; not OpenGL screencaver) and been okay for four days.  I'm trying GLMatrix again and will let you know.

- CH  :rolleyes:

---

### Post by Pitboss on 2009-02-17
It's nothing relevant, my mistake.

---

### Post by markofealing on 2009-02-22
Avoid the 9.2 drivers if you have a Radeon 9600. I've just installed on Kubuntu 8.10 (fresh install with latest Kubuntu patches) and have got the White Screen of Death.

Thank you ATI having spent months trying to dual screen so I can move to Linux from Windows I give up!

In fact I'm so fed up with KDE4 and Kubuntu's exceptionally poor support for dual display that I've just tried Ubuntu 8.10 Live CD. Dual Desktop works perfectly with open source drivers, so guess what I'm installing.

---

### Post by theApokalypsis on 2009-02-23
Im running the 9.2 on 8.10 Gnome with Big Desktop. working great. better improvement and bug fixes from 9.1 (albeit not that much). (Radeon HD 4870)

---

### Post by screaminj3sus on 2009-02-23
run as good as the others on my mobility 2600. compiz is decently smooth but vsync STILL doesn't work and STILL get black screen on resume with compiz enabled.

> **cement_head said:**
> Follow this guide...[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

-CH   :popcorn:

that guide worked very poorly for me. Generating the ubuntu packages and installing the way the guide told me to made me drop into the cmd next boot, but from there I just decided to do it the friggin easy way and just did sh ./[drivername] and bam worked perfectly. I think that guide has a lot of unecessary steps.

---

### Post by zika on 2009-02-23
> **screaminj3sus said:**
> that guide worked very poorly for me. Generating the ubuntu packages and installing the way the guide told me to made me drop into the cmd next boot, but from there i just decided to do it the friggin easy way and just did sh ./[drivername] and bam worked perfectly. I think that guide has a lot of unecessary steps.
+1

---

### Post by Reeman on 2009-02-23
Dcop bull again no doubt...try to chown the .kde to the desktop user as root. If I am not mistaken the ati driver needs to write to it in pure KDE and for some strange reason non KDE apps cannot access the user hidden .kde where the desktop configuration files are stored. Same crap happens with audio software I have had to change ownership of the .kde file for years to get everything to work right with realtime audio. It might just do the same crap with the ATI driver.

---

### Post by dyrer on 2009-02-23
How can accelerate my desktop with newest drivers from ATI?

---

### Post by screaminj3sus on 2009-02-23
> **dyrer said:**
> How can accelerate my desktop with newest drivers from ATI?

What do you mean? Did you install the drivers and desktop effects aren't working?

---

### Post by leffty on 2010-03-11
Hey i have a problem im trying to play wow on ubuntu 9.10 and i found one forum that says that i need to set a proprietary drive but when i got o set up a proprietary drive it says theres nothing there and when i look at my catalyst thing it says there are no drivers installed or there not working properly and when i try to install the drivers using terminal and also stuff that i found in the software center and i tried to install the drivers with wine using the setup file for the drivers for windows vista (seemed like a good idea at the time) but nothing is working if anyone knows anything that i can try or were i could find a version of the ubuntu drivers for an ati radeon x1200 (i think it was 1200) your help would be much appreciated

---

### Post by frogotronic on 2010-03-11
> **leffty said:**
> Hey i have a problem im trying to play wow on ubuntu 9.10 and i found one forum that says that i need to set a proprietary drive but when i got o set up a proprietary drive it says theres nothing there and when i look at my catalyst thing it says there are no drivers installed or there not working properly and when i try to install the drivers using terminal and also stuff that i found in the software center and i tried to install the drivers with wine using the setup file for the drivers for windows vista (seemed like a good idea at the time) but nothing is working if anyone knows anything that i can try or were i could find a version of the ubuntu drivers for an ati radeon x1200 (i think it was 1200) your help would be much appreciated


Hello,

  You cannot use the FGLRX (proprietary) ATI drivers in 9.10 with your card.  Its too old.  You cannot install hardware drivers with WINE.  Only software applications (like WOW or Microsoft Office).

  You can either try running WOW in WINE ( [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) ) or buy a newer video card and use the FGLRX drivers.

- CH

---

### Post by leffty on 2010-03-11
> **cement_head said:**
> Hello,

  You cannot use the FGLRX (proprietary) ATI drivers in 9.10 with your card.  Its too old.  You cannot install hardware drivers with WINE.  Only software applications (like WOW or Microsoft Office).

  You can either try running WOW in WINE ( [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) ) or buy a newer video card and use the FGLRX drivers.

- CH

ok TY i've tried running WoW in wine and every time it crashes could it be because i was trying to run it off of an external harddrive? and would it be possible if i tried using an older version of ubuntu?

---

### Post by frogotronic on 2010-03-12
> **leffty said:**
> ok TY i've tried running WoW in wine and every time it crashes could it be because i was trying to run it off of an external harddrive? and would it be possible if i tried using an older version of ubuntu?

You have to "patch" WOW as per the wiki link in the above post.  In order to use FGLRX drivers in Ubuntu (without any hardware changes) you would have to install Ubuntu 8.10 Intrepid Ibex.  Might be better to dual boot with windowsXP for WOW.

Quick question -> what type and model of computer do you have?

- CH

---

