---
title: "DVD's not Playing"
date: 2008-02-23
forum: Multimedia &amp; Video
---

### Post by umphreak82 on 2008-02-23
I have been running ubuntu since Dapper on my Gateway laptop with few issues. I have no problems playing DVD's on the laptop and have reconfigured my system a number of times, always able to play encrpyted DVDs in the end.

I finally talked the wife into letting me dump windows from the Desktop and I cannot get encrypted DVDs to play.

I have installed Ubuntu-Restricted-Extras in order to enable DVD playback. The issue is that none of the players will play encrypted DVDs. 

I have two DVD drives in my system, one an LG DVD/CDR drive and the other a phillips DVDR drive. It seems that my system has labled both drives as dvd without differentiating the two. I can read files on both drives. They both play music and they still both play DVDs in Windows as I have chosen the leave the machine dual booted for the time being.

I was wondering if anyone has any ideas as to why my system will not play encrypted DVDs. 

Thinking about it now, I have not tested the drives to see if they will play burned DVDs as I do not have any on hand. 

Thanks for the assistance.

---

### Post by sanddgroper on 2008-02-23
I guess the first question is are you using Ubuntu(You would surprised  how many post here who arn't) and what version are you using.
The second question is do you have all the restricted codecs from site like medibuntu installed.If
not you may need to download and install them to get encrypted DVD's to play.
If this solves you problem please mark thread as SOLVED.

Cheers
Sandy

---

### Post by umphreak82 on 2008-02-23
> **sanddgroper said:**
> I guess the first question is are you using Ubuntu(You would surprised  how many post here who arn't) and what version are you using.
The second question is do you have all the restricted codecs from site like medibuntu installed.If
not you may need to download and install them to get encrypted DVD's to play.
If this solves you problem please mark thread as SOLVED.

Cheers
Sandy

I am running Gutsy Gibbon. As far as I know, I have all codecs installed as I installed the package ubuntu-restricted-extras. This same package enabled DVD playback on the most recent resintallation on my laptop. 

Thanks,


Dave

---

### Post by sanddgroper on 2008-02-23
Ok what video player are you using if it is totem you may need to get the gstreamer plugins
Does the DVD mount and show on your desktop.
What if any messages show when the video fails to show.Do  you  get  anything like audio
or the movie player opening but just a black screen.
If you click on the blue circle with the question mark in it on the top of the screen and scroll 
down to you find "NEW TO UBUNTU" and click on it it should tell you what version you are using.
If it is a new DVD it may have encryption that Ubuntu cant play e.g Arcoss.

Cheers
Sandy

---

### Post by umphreak82 on 2008-02-23
> **sanddgroper said:**
> Ok what video player are you using if it is totem you may need to get the gstreamer plugins
Does the DVD mount and show on your desktop.
What if any messages show when the video fails to show.Do  you  get  anything like audio
or the movie player opening but just a black screen.
If you click on the blue circle with the question mark in it on the top of the screen and scroll 
down to you find "NEW TO UBUNTU" and click on it it should tell you what version you are using.
If it is a new DVD it may have encryption that Ubuntu cant play e.g Arcoss.

Cheers
Sandy

Both the laptop (which plays said DVD's) and desktop are running 7.10 (gutsy gibbon)

When a DVD is inserted in either drive, it mounts onto the desktop. 

I have used Totem, which gives plugin is missing (ubuntu-restricted-extras and ALL gstreamer is installed).

When I use GXINE, I get an mpeg block error on the video player window followed by a second window that states "Error reading from NAV Packet"

When I use VLC, I don't get any errors, it just stops playing. It will show the title for a second down in the lower right-hand corner of the window, but that will disappear as well. Under messages, there are none.

What frustrates me most is that this ALL works on my laptop, which also has an ATI card and ALL the SAME software installed.

Thanks,


David

---

### Post by mc4man on 2008-02-23
Best bet to troubleshoot is to run vlc from the terminal and post what info is displayed

---

### Post by gandaran on 2008-02-23
to play encrypted DVDs, you need install libdvdcss2, you'll find it on the medibuntu repository, libdvdcss2 is not part of ubuntu restricted extras.
you'll also need  libdvdnav4 and libdvdread3.

if it still doesn't work, paste this on a terminal/console » sudo /usr/share/doc/libdvdread3/install-css.sh

paste this command on the multimedia tab to start gxine when you insert a dvd »   gxine -S dvd:/  (only if you want to use gxine, if you prefer the totem player leave it as it is)

---

### Post by umphreak82 on 2008-02-23
So, I finally got the DVD's to "work". The issue I kept having was that apt kept saying that libdvdcss2 was referred to by another package and that libdvdnav4 and libdvdread3 were already installed and the latest version. I found a work around and got the DVD decoders to install. 

My latest issue is that DVD's do not play normally. Depending on the player is how the DVD plays.

Totem will now play them, but only the menu before it exits without visible fault.

VLC will load the menus and then when one clicks play, it will only start playing a few chapters from the end of every movie. When I try to backup or select or different chapter/title, the player will crash and exit out. 

xgine also came up with an error, which I cannot recall right now as I am at work.

These same DVDs play on the Laptop (which I reloaded with ubuntu not more than two weeks ago).

---

### Post by mc4man on 2008-02-23
> I found a work around
may be source of problem
run vlc in terminal and post

---

### Post by umphreak82 on 2008-02-23
Here is the output from VLC in the terminal window.

> No accelerated IMDCT transform found
libdvdread: Can't seek to block 4113145
libdvdread: Invalid IFO for title 21 (VTS_21_0.IFO).
libdvdnav: ifoOpenVTSI failed - CRASHING!!!
vlc: vm.c:198: ifoOpenNewVTSI: Assertion `0' failed.
Aborted (core dumped)


---

### Post by mc4man on 2008-02-23
Actually the complete log would be more useful
the  - Assertion `0' failed - usually indicates a structure protected disk that vlc can't handle - hard to tell without full terminal output
There are workarounds for such titles but it would be better to know you can play 'normal' titles first

does the top of the terminal output show something like this
doug@doug-desktop:~$ vlc
VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
_libdvdread: Using libdvdcss version 1.2.9 for DVD access_
underlined for emphasis

---

### Post by ubuntu-freak on 2008-02-23
You may need to run the install-css.sh command, which will also downgrade libdvdcss2 and then upgrade it again (sounds weird, but works). Try part 3 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833).
 
Nathan

---

### Post by TE7 on 2008-02-25
I run gutsy and couldn't get totem to play DVDs. Tried the instructions at the following forum post. VLC played my DVDs great. Try it.

[http://ubuntuforums.org/showthread.php?t=704726&highlight=VLC+gutsy](http://ubuntuforums.org/showthread.php?t=704726&highlight=VLC+gutsy)

---

### Post by ubuntu-freak on 2008-02-25
> **TE7 said:**
> I run gutsy and couldn't get totem to play DVDs. Tried the instructions at the following forum post. VLC played my DVDs great. Try it.

[http://ubuntuforums.org/showthread.php?t=704726&highlight=VLC+gutsy](http://ubuntuforums.org/showthread.php?t=704726&highlight=VLC+gutsy)

 
That thread wouldn't be at all necessary for most users . Also, my [how-to](http://ubuntuforums.org/showthread.php?t=661833) shows you a way to make VLC launch by default when you insert a DVD or SVCD movie.
 
Nathan

---

