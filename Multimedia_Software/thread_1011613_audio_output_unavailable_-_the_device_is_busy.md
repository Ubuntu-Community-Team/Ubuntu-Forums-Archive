---
title: "audio output unavailable - the device is busy"
date: 2008-12-14
forum: Multimedia Software
---

### Post by Achilles124 on 2008-12-14
I use Amarok for music but lately something goes wrong. I get this error:

Audio output unavailable; the device is busy.
xine parameters: 

I have searched the net and I found this:
[https://answers.launchpad.net/ubuntu/+source/amarok/+question/8271]("https://answers.launchpad.net/ubuntu/+source/amarok/+question/8271")

But that solution doesn't work for me.

Other programs give similar problems.
Here are the results of the programs running in terminal:

> ecmpeek@ecmpeek-desktop:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&

> ecmpeek@ecmpeek-desktop:~$ totem
** (totem:9972): DEBUG: Init of Python module
** (totem:9972): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:9972): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:9972): DEBUG: Creating Python plugin instance
** (totem:9972): DEBUG: Init of Python module
** (totem:9972): DEBUG: Registering Python plugin instance: PythonConsolePlugin+TotemPythonPlugin
** (totem:9972): DEBUG: Creating object of type PythonConsolePlugin+TotemPythonPlugin
** (totem:9972): DEBUG: Creating Python plugin instance
** (totem:9972): DEBUG: Init of Python module
** (totem:9972): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:9972): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:9972): DEBUG: Creating Python plugin instance
** Message: Error: Failed to connect stream: Invalid argument
pulsesink.c(634): gst_pulsesink_prepare (): /GstPlayBin:play/GstBin:visbin/GstBin:abin/GstBin:audiosinkbin/GstGConfAudioSink:audio-sink/GstBin:bin6/GstAutoAudioSink:autoaudiosink1/GstPulseSink:autoaudiosink1-actual-sink-pulse

Killed

> ecmpeek@ecmpeek-desktop:~$ vlc
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "nl"
[00000001] main libvlc: Start vlc met standaard interface. Gebruik 'cvlc' om vlc zonder interface te gebruiken.
ALSA lib pcm_pulse.c:625:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

ALSA lib pcm_pulse.c:625:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

[00000460] alsa audio output error: unable to commit hardware configuration (Input/output error)
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1

Amarok, Totem and even vlc don't work as they should. What could be wrong?

Thanks beforehand.

---

### Post by chrisamiller on 2008-12-14
Try restarting pulseaudio:

In a terminal:
sudo killall pulseaudio

then hit Alt+F2, and type:
pulseaudio

---

### Post by Achilles124 on 2008-12-15
you are a miracle-doctor....it works!!!!!!!!!!!!

Thank you.

---

### Post by Plan B on 2008-12-15
^^ Excellent, worked for me too.

How come pulseaudio was broken in the first place?

---

### Post by Achilles124 on 2008-12-16
It happened to me again. I also am interested why pulseaudio breaks down.

Anyone?

---

### Post by chrisamiller on 2008-12-16
Sound on linux is a colossal mess right now, with multiple competing backends and no real agreement on what to do.  Frankly, the miracle is that Ubuntu hacked together a solution that works so well most of the time.  

Read this if you want to know some of the gory details:
[http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html](http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html)

The good news is that there's been a push for more standardization, and Ubuntu has made large leaps forward in the last few releases.  We're getting there, slowly but surely.

---

### Post by Plan B on 2008-12-17
> **Achilles124 said:**
> It happened to me again. I also am interested why pulseaudio breaks down.

Anyone?

Same same here.  Have to do the killall etc everytime I start up now to get music.

---

### Post by Plan B on 2008-12-17
^^^  I found a simple solution on this thread...

[http://ubuntuforums.org/showthread.php?p=6384998#post6384998](http://ubuntuforums.org/showthread.php?p=6384998#post6384998)

My simple solution is at the end of the thread.  Disable startup sounds.

:p

---

### Post by fareedquraishi on 2008-12-17
7 rapidshare_premium_accounts
 
[http://rapidshare.com/files/172639505/RS1__7rapidshare_premium_accounts.rar](http://rapidshare.com/files/172639505/RS1__7rapidshare_premium_accounts.rar)
 
4001 Business, Sales and Personal Letters 
 
Down Load from this link
[http://rapidshare.com/files/17305444...al.Letters.rar](http://rapidshare.com/files/17305444...al.Letters.rar)
 
Microsoft Access Bible 
 
There are three parts of this huge book, Microsoft Access From beginners to Expert Level

File: Access Bible.part1.rar
DownloadLink: [http://rapidshare.com/files/17404413...ible.part1.rar](http://rapidshare.com/files/17404413...ible.part1.rar)

File: Access Bible.part2.rar
DownloadLink: [http://rapidshare.com/files/17404965...ible.part2.rar](http://rapidshare.com/files/17404965...ible.part2.rar)

File: Access Bible.part3.rar
DownloadLink: [http://rapidshare.com/files/17405337...ible.part3.rar](http://rapidshare.com/files/17405337...ible.part3.rar)
 
Formulas and Functions With Microsoft Excel 2003 

File: Formulas and Functions With Microsoft Excel 2003.part1.rar

[http://rapidshare.com/files/17399480...2003.part1.rar](http://rapidshare.com/files/17399480...2003.part1.rar)

File: Formulas and Functions With Microsoft Excel 2003.part2.rar

DownloadLink: [http://rapidshare.com/files/17402749...2003.part2.rar](http://rapidshare.com/files/17402749...2003.part2.rar)

File: Formulas and Functions With Microsoft Excel 2003.part3.rar

DownloadLink: [http://rapidshare.com/files/17403228...2003.part3.rar](http://rapidshare.com/files/17403228...2003.part3.rar)

File: Formulas and Functions With Microsoft Excel 2003.part4.rar LAST PART

File: Formulas and Functions With Microsoft Excel 2003.part4.rar

DownloadLink: [http://rapidshare.com/files/17403388...2003.part4.rar](http://rapidshare.com/files/17403388...2003.part4.rar)

----------------------------------------------------------------------------------------------

KFC AUTHENTIC RECIPES

Mc DONALDS INCLUDES ALL THESE
Big Mac®
Arch Deluxe®
Big X-tra®
Breakfast Burrito
Cheeseburger
Chicken Fajitas
Chicken McNuggets®
Egg McMuffin®
Filet~o~Fish®
French Fries
Hamburger
McChicken®
McD.L.T.®
McRib® Sandwich
Milkshakes
Quarter Pounder®
Sweer & Sour Dipping Sauce

200 PIZZA RECIPE BOOK

VEDIC MATHEMATIC SECRET

File: Mc Donalds and KFC Recipes.rar
DownloadLink: [http://rapidshare.com/files/17403824...FC_Recipes.rar](http://rapidshare.com/files/17403824...FC_Recipes.rar)
 
--------------------------------
 
BODY LANGUAGE DICTIONARY 
 
 [http://rapidshare.com/files/17398536...Dictionary.pdf](http://rapidshare.com/files/17398536...Dictionary.pdf)  
 
-------------------------------------------------------
 
child reading
Dream Psychology
inequal justice
Homeopathy Pro v1.0.0 build 51010 w fix

All in one Link - Enjoy

File: Homeopathy.rar
DownloadLink: [http://rapidshare.com/files/173971588/Homeopathy.rar](http://rapidshare.com/files/173971588/Homeopathy.rar)
 
=====================
 
1000 hacking tutorials-The Best of 2008 
 
[http://rapidshare.com/files/17305827..._of__2008_.rar](http://rapidshare.com/files/17305827..._of__2008_.rar)
====================================
 
The Emotionally Intelligent Manager - Jossey Bass
Becoming a Strategic Leader Your Role in Your Organizations Enduring Success - Wiley
Everybody Wins The Story and Lessons Behind RE MAX
Getting An Investing Game Plan Creating It Working It Winning It -John Wiley&Sons
living the brand
Crunch Point The 21 Secrets to Succeeding When It Matters Most
Leadership Secrets of the Worlds Most Successful CEOs-Dearborn Financial 
Publishing
Customer_Once_Client_Forever
Hotel_Front_Office_Management_3rd_Edition_-_John_Wiley_and_Sons
The_Essentials_of_the_New_Workplace_A_Guide_to_the_Human_Impact_of_Modern_Working_Practices

these all books are in these two links, Lots to come

[http://rapidshare.com/files/172962944/ebooks1.rar](http://rapidshare.com/files/172962944/ebooks1.rar)
[http://rapidshare.com/files/172962945/ebooks_2.rar](http://rapidshare.com/files/172962945/ebooks_2.rar)
 
================================
 
4001 Business, Sales and Personal Letters 
 

Down Load from this link
[http://rapidshare.com/files/17305444...al.Letters.rar](http://rapidshare.com/files/17305444...al.Letters.rar)

---

### Post by Achilles124 on 2008-12-17
I have changed my loginscreen and login sound (it is now a roaring lion). Have any of you who have the same problems as me, and have you changed the login screen and music?

---

### Post by Achilles124 on 2008-12-27
I have downloaded **pulseaudio device chooser** but don't know much about it. Can someone take a look at it as well?

---

### Post by Achilles124 on 2008-12-28
Removed the login sounds and now I don't have any problems anymore.

:)

---

### Post by Aitux on 2009-02-06
Nowadays, if you want to solve this problem permanently, I found an easy solution, Menu >> Preferences >> Sessions. There, click to ADD, in the label name put anything you want, it isn't important, and in the command text box write this: "killall pulseaudio" (without quotes). With this and a restart your problem should finish.

Now, you don't need to take care of what you change on your startup sounds settings. ;)

P.D.: Sorry if my English isn't so good, I'm learning :)

---

