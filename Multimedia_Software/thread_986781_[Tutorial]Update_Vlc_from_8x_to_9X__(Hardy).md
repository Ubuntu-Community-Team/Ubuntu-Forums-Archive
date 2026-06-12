---
title: "[Tutorial]Update Vlc from 8x to 9X  (Hardy)"
date: 2008-11-18
forum: Multimedia Software
---

### Post by nakama85 on 2008-11-18
*_Note: Ubuntu 8.04 does not officially support Vlc 9x however since vlc no longer supports 8x I think this may be useful/necessary for some of you. Furthermore this build is somewhat experimentel, you may run into stability issues. As of now I have not run into any however that does not mean you will not_*

**How To Update Vlc from 8x to 9X in Ubuntu 8.04 (32bit)**_(special Thanks To **"mc4man"**)_

If you want to try a 0.9.x version you can add the *korn ppa* sources to your sources list and install 0.9.3.

Before trying to install go into synaptic, search vlc and remove vlc, vlc-nox, libvlc0, and any vlc plugins.

copy and paste the 2 lines below one at a time into System -> Administration -> Software sources -> Third-party Sources -> add.       (these are the _korn ppa_ sources)
```
deb http://ppa.launchpad.net/c-korn/ubuntu hardy main

deb-src http://ppa.launchpad.net/c-korn/ubuntu hardy main
```

Now Go to Terminal and enter the following.
```
 sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
```

[B]Congrats. You now have VLC 9.3
[/B]

If you try 0.9.3 from (*korn ppa*) and want 0.9.5 with 'embedded' video enabled and for the bug fixes follow the directions below.
_***Note: embedded video is considered broken by Vlc. If you would still like 9.5 without embedded it can be done.***_
(this line disables the embedded video)

> #if 0 /* this is totally broken */
add_submodule ()
set_capability( "vout window", 50 )
set_callbacks( WindowOpen, WindowClose )

_***Note: This Is Only For Ubuntu 8.04 Hardy***_
**You must still have the *korn ppa* sources (listed above) enabled as a software source for this to work.**

All the needed .debs are in a *.7z* file, archive manager can extract as long as *p7zip* is installed. If you don't already have *p7zip* you can install it by entering the following code in terminal.
```
sudo apt-get install p7zip
```

From here download the *install.7z* file

[http://www.mediafire.com/download.php?mwymzmzgvyj](http://www.mediafire.com/download.php?mwymzmzgvyj)    
*Note: this download was provided to us from "mc4man" himself (thanks again "mc4man")*

Extract it to your *"Home"* folder (It will create a file called *"install"*). Once you have done this we can install it by entering the following code in Terminal

```
cd install && sudo dpkg -i *.deb
```  

Thats it You are done. Again, many thanks to **"mc4man"** without his help this would not have been possible!!!!!!!!!!!

*_A Side Note From "mc4man"_*
> **mc4man said:**
> 

Hardy uses libdvdnav4-0.1.10 which is perfectly fine. There are though some titles that won't playback due to a udf structure protection. In *many* but not *all* cases using a patched libdvdnav4 would resolve.
There are now some newer versions of libdvdnav4 available which have already been patched.

Version 4.1.2-3 is fully compatible with hardy and vlc. 
I'd be careful of Version 4.1.3-1 which is only needed for the dvdnav enabled mplayer.

Can be gotten here 
[http://packages.ubuntu.com/intrepid/libdvdnav4](http://packages.ubuntu.com/intrepid/libdvdnav4)
[B]
Do not[/B] uninstall current version of libdvdnav4, just download and let GDebi handle the install if the need to use this version arises (in region 1 limited to some New line releases, more widespread in regions 2, 4


_*Some Known Issues from "mc4man"*_:

> **mc4man said:**
> there are some things that don't work or work right in vlc 0.9.x

I'm continuing to have no issues though with the 'embedded'.

As far as 'other' issues, I think that comes down to one's use. 

For me it's accessing a video_ts dir. from vlc is broken, though opening vlc from the video_ts dir. works.

The other minor issue for me is the equalizer only stays enabled for one track.

side note: just built the latest 1.0 unstable with 'embedded' enabled, again no issues.
Whether it's ubuntu, my hardware or combo of the two don't know, post back if vlc shows problems or crashes at random.

---

### Post by notanerd on 2008-11-23
I have an amd64 and get this error when i put in 

cd install && sudo dpkg -i *.deb

dpkg: error processing libvlc0_0.9.5+x264snapshot20080928+faad2.6.1-1~ppa1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing mozilla-plugin-vlc_0.9.5+x264snapshot20080928+faad2.6.1-1~ppa1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing vlc_0.9.5+x264snapshot20080928+faad2.6.1-1~ppa1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing vlc-nox_0.9.5+x264snapshot20080928+faad2.6.1-1~ppa1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package vlc-plugin-alsa.
(Reading database ... 140224 files and directories currently installed.)
Unpacking vlc-plugin-alsa (from vlc-plugin-alsa_0.9.5+x264snapshot20080928+faad2.6.1-1~ppa1_all.deb) ...
dpkg: error processing vlc-plugin-pulse_0.9.5+x264snapshot20080928+faad2.6.1-1~ppa1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: dependency problems prevent configuration of vlc-plugin-alsa:
 vlc-plugin-alsa depends on vlc; however:
  Package vlc is not installed.
dpkg: error processing vlc-plugin-alsa (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libvlc0_0.9.5+x264snapshot20080928+faad2.6.1-1~ppa1_i386.deb
 mozilla-plugin-vlc_0.9.5+x264snapshot20080928+faad2.6.1-1~ppa1_i386.deb
 vlc_0.9.5+x264snapshot20080928+faad2.6.1-1~ppa1_i386.deb
 vlc-nox_0.9.5+x264snapshot20080928+faad2.6.1-1~ppa1_i386.deb
 vlc-plugin-pulse_0.9.5+x264snapshot20080928+faad2.6.1-1~ppa1_i386.deb
 vlc-plugin-alsa
evan@durruti:~/install$

---

### Post by mc4man on 2008-11-24
I don't see it mentioned in the thread but this is for 32 bit ubuntu only.

Also I'd like to repeat this from orig. thread (Regarding using 'embedded' video

Videolan does consider it broken, as seen in the latest source, notice the comment (this line disables the embedded video

> #if 0 /* this is totally broken */
add_submodule ()
set_capability( "vout window", 50 )
set_callbacks( WindowOpen, WindowClose ) 

I've had no issues using the embedded video, even with the latest 1.0 unstable and nether have several other hardy users.

That doesn't mean vlc will 'behave' in all cases, though it seems to be fairly stable in ubuntu.

---

### Post by nakama85 on 2008-11-24
> **mc4man said:**
> I don't see it mentioned in the thread but this is for 32 bit ubuntu only.

Also I'd like to repeat this from orig. thread (Regarding using 'embedded' video

Videolan does consider it broken, as seen in the latest source, notice the comment (this line disables the embedded video



I've had no issues using the embedded video, even with the latest 1.0 unstable and nether have several other hardy users.

That doesn't mean vlc will 'behave' in all cases, though it seems to be fairly stable in ubuntu.

Sorry about that. I fixed the thread. If there is anything else you think I should add let me know.

---

