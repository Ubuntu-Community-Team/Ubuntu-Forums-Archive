---
title: "Playing wmv and flv's"
date: 2009-11-03
forum: Multimedia Software
---

### Post by n.hinton on 2009-11-03
Just Upgraded from Jaunty to Karmic and totem and vlc will no longer play wmv and flv's, made sure necessary repositories were there and correct codecs installed,  installed mplayer-nogui and smplayer which will now play everything. Totem and vlc still refuse to cooperate, totem says can't find codecs.

Ran totem &#8211;debug and got the following:

(totem:3388): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstffmpeg.so': libavutil.so.49: cannot open shared object file: No such file or directory



(totem:3388): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstx264.so': libx264.so.67: cannot open shared object file: No such file or directory



Now  '/usr/lib/gstreamer-0.10/libgstffmpeg.so' and  '/usr/lib/gstreamer-0.10/libgstx264.so' exist, but  libavutil.so.49 doesn't its libavutil.so.50 and the closest to  libx264.so.67 in the lib directory is libx264.so.76

So I strongly suspect this is the problem, but have no idea how to fix it, don't want to break mplayer-nogui as that works fine.

Any suggestions greatly appreciated.

---

### Post by mc4man on 2009-11-03
You may want ck. in synaptic for what versions of libavutil and libx264 are installed and or available. (and the ffmpeg libs in general

Did you build ffmpeg and or x264? ( and if so, before or after upgrade

Karmic only uses libx264-67 and libavutil49, the karmic vlc (vlc-nox), depends on libavutil49 as does the gstreamer ffmpeg plugin

Are you using the karmic repo mplayer-no-gui? ( which  also depends on libavutil49, libx264-67

If libavutil49, libx264-67 are installed then this may all be from doing an upgrade vs. a fresh install with certain libs and or apps installed

......................

( you can have multiple libx264-XX's installed and libavutil49 can co-exist with libavutil50, see screens

In my case have newer versions of everything, but as you'll notice the libavutil49 package is installed ( if I removed would remove gstreamer0.10-ffmpeg,

The libx264-67 is needed for the gstreamer-ugly-multiverse and would be a dep of libavcodec-extra-52 in a stock install

---

### Post by n.hinton on 2009-11-05
Hi mc4man, thanks for replying.
No I didn't build ffmpeg or 264 not that linux literate yet, must have been installed along with vlc or winff or something when back using jaunty.
libx264-67 is installed and /usr/lib/libx264.so.76 is one of its installed files, libavutil49 is not installed, just went to install it with synaptic and got this:
To be removed

devede
ffmpeg
gnomebaker
gstreamer0.10-ffmpeg
gstreamer0.10-plugins-bad-multiverse
libavcodec-extra-52
libavcodec-unstripped-52
libavfilter0
libavformat-extra-52
libavutil-extra-49
libmjpegtools-1.9
libpostproc-extra-51
libquicktime1
libswscale-extra-0
libxine1-ffmpeg
vlc
vlc-nox
vlc-plugin-pulse
winff

Consequently I did not install libavutil49 thought it best to get your advice first as I need the above.
Again thanks for your help.

PS think you must have better repos than me, you have more available packages than I do, e.g. I only have libx264-67 listed.

---

### Post by paul.gevers on 2009-11-06
> **n.hinton said:**
> libavutil49 is not installed, just went to install it with synaptic and got this:


Test if the same happens with libavutil-extra-49... They are binary compatible.

[edit]: Nevermind you already have that installed, so this does not solve your problem. For your problem libavutil49 IS installed (in the form of libavutil-extra-49)

---

### Post by mc4man on 2009-11-06
Could you post your sources.list
```
cat /etc/apt/sources.list
```

> libx264-67 is installed and /usr/lib/libx264.so.[COLOR="Red"]76[/COLOR] is one of its installed files

That is not what libx264-67 should be providing


> ....but libavutil.so.49 doesn't its libavutil.so.50

In synaptic is libavutil50 installed and if so what depends on it? (mark for removal and see

Are you using a ppa(s) now and were you using any in jaunty?

( where did you get the mplayer you're using now?

---

### Post by n.hinton on 2009-11-06
question 1 result:
kingfisher@kingfisher-desktop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted universe multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-security main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-security main restricted universe multiverse

deb [http://ppa.launchpad.net/keepassx/ppa/ubuntu](http://ppa.launchpad.net/keepassx/ppa/ubuntu) karmic main
deb [http://ppa.launchpad.net/rvm/mplayer/ubuntu](http://ppa.launchpad.net/rvm/mplayer/ubuntu) karmic main
deb [http://ppa.launchpad.net/gilir/backports/ubuntu](http://ppa.launchpad.net/gilir/backports/ubuntu) karmic main
deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) karmic main
# deb-src [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) karmic main


2nd question: In synaptic is libavutil50 installed? No Not available in my synaptic

Don't know how to answer question 3, yes I guess but don't know know what they were as after Karmic upgrade they were listed as disabled.

My first experience of Ubuntu was a few months ago when I installed jaunty, first thing I did was to enable the universe and multiverse check boxes in Software Sources. When first playing multimedia files codecs were automatically searched for and installed or just played.

Subsequently after reading that the latest versions of software existed in other ppa's and I should add those ppa's for best performance, so I did, and all worked perfectly.

Now out of my depth trying to untangle what the upgrade did - Sorry if I'm not much help here.

Many thanks for your reply

PS Don't know what is providing Mplayer but it is mplayer-nogui using smplayer as gui, this is working fine as is winff.
When smplayer is playing a wmv or flv, looking at file properties exposes a full compliment of codecs that totem and vlc can no longer detect.

PPS installed mplayer-nogui and smplayer after upgrade.

---

### Post by mc4man on 2009-11-06
Don't see any conflicts with your enabled ppa's.
Your mplayer is from the rvm ppa so it's 'self contained', meaning it's using it's own ffmpeg libs rather than the system ones.

What I'd do is completely remove some some libs and apps, re-install and see.

If inclined, then open synaptic, search vlc and mark everything from libvlc2 down for complete removal. Then search ffmpeg and do the same for ffmpeg and **all** the libs that are installed. ( some apps and plugins will also be removed

Also search libx264 and mark libx264-67 for re-installation
Click apply and then after it's done, just because - reboot

Afterwards open synaptic and mark for install starting with devede (you can do all at once, just start with devede.

devede
vlc
vlc-plugin-pulse
winff
gstreamer0.10-ffmpeg
gstreamer0.10-plugins-bad-multiverse (4th listed
libxine1-ffmpeg

Start vlc from the terminal with this, after opening you may need to go tools -> preferences -> audio and change the default output from 'default' to 'pulseaudio'
```
vlc --reset-config --reset-plugins-cache
```

---

### Post by n.hinton on 2009-11-07
Thanks again, as soon as I have time, I will implement your suggestions and post back the outcome.

Curious thing,  I assumed the smplayer may well be a 'self contained' application, as you say it is. Winff initially after Karmic upgrade, didn't work with all formats but did after the install of mplayer-no-gui/smplayer

---

### Post by n.hinton on 2009-11-08
Hi mc4man,
Have followed your instructions plus installed libavutil49 which was removed when reinstalling the previously uninstalled packages.

Sadly no change, seems exactly the same as before. I haven't got a clue what to try next.

PS Now get this:

kingfisher@kingfisher-desktop:~$ totem --debug
(totem:2935): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstpostproc.so': libavutil.so.49: cannot open shared object file: No such file or directory

(totem:2935): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstffmpegscale.so': libavutil.so.49: cannot open shared object file: No such file or directory

(totem:2935): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstffmpeg.so': libavutil.so.49: cannot open shared object file: No such file or directory

(totem:2935): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstx264.so': libx264.so.67: cannot open shared object file: No such file or directory

---

### Post by n.hinton on 2009-11-09
Noticed some version differences to yours, don't know if this would make any difference. Please see attached.

---

### Post by n.hinton on 2009-11-09
Remainder:

---

### Post by mc4man on 2009-11-09
It didn't show up in your sources.list that you posted but you are using ffmpeg  and libx264 packages from a ppa , which while they may be very nice builds are not suitable for running in karmic, 

You need to get rid of them, the source(s), and install the karmic repo ffmpeg, it's libs, and it's libx264

How it's added to your available sources I'm not sure, look in /etc/apt/sources.list.d or repost your /etc/sources.list or go 
sudo apt-get update and post the terminal output.
(till they're gone totem and the karmic repo vlc will not work correctly

Edit:
I believe your using this ppa
[https://launchpad.net/~thefirstm/+archive/karmic-testing](https://launchpad.net/~thefirstm/+archive/karmic-testing)

If you can work out how to integrate his packages with the karmic repo totem, gstreamer-plugins, and vlc, then great, otherwise remove it (the ppa) and the ffmpeg, ffmpeg libs and libx264 packages you've installed from there

( if you were to build vlc, totem and the affected gtreamer plugins off of the firstm ffmpeg -dev packages then things  may work

As a comment on his packaging, while he may have his reasons, packaging a libx264-76 as libx264-67 is not the way to do it ( the screen I posted earlier  shows how it should be done

---

### Post by n.hinton on 2009-11-09
kingfisher@kingfisher-desktop:~$ sudo apt-get update
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_GB              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release.gpg                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Translation-en_GB                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Translation-en_GB             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release.gpg                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Translation-en_GB     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Translation-en_GB   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security Release.gpg                   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/main Translation-en_GB        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/restricted Translation-en_GB  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/universe Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/multiverse Translation-en_GB  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security Release                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Packages                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Packages                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Sources                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Sources                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Sources                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Sources                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Sources               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/main Packages                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/restricted Packages           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/multiverse Packages           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/main Sources                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/restricted Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/universe Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/multiverse Sources            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_GB
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_GB
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages
Reading package lists... Done

---

### Post by n.hinton on 2009-11-09
disabled 
[http://ppa.launchpad.net/thefirstm/karmic-testing/ubuntu](http://ppa.launchpad.net/thefirstm/karmic-testing/ubuntu)
Removed the apps again, please see attached

---

### Post by n.hinton on 2009-11-09
Remainder

---

### Post by mc4man on 2009-11-09
Well it appears that you may have run the update manager while having the firstm ppa enabled.

If so, then every package on this page that you had installed would have been updated, some to incompatible versions with  standard karmic repo apps, libs, and plugins.

( a potential  mess

[https://launchpad.net/~thefirstm/+archive/karmic-testing/+packages](https://launchpad.net/~thefirstm/+archive/karmic-testing/+packages)

Your options would be to work your way thru and restore everything affected in a negative way to karmic versions.

Or re-enable the ppa and live with it.

As mentioned if you re-build the affected apps, libs, ect. then they may start working correctly.

(( that ppa can be a bit dangerous to use in a non-specific manner and certainly one that shouldn't be left enabled, particularly if the update manager is used without looking at what was to be updated

Why were you using it in the first place??

---

### Post by n.hinton on 2009-11-09
Hi mc4man, thanks for posting back.

Yes you are right I run update manager every day. Does work my way thru and restore everything affected mean forcing earlier versions?

After the Karmic upgrade could no longer play flv's or wmv's made sure I had standard karmic repos non free etc. But said files would not play in vlc or totem, installed mplayer-no-gui/smplayer which worked. Thought I must be missing a ppa so added that one (bad move) hoping to fix the issue by adding ppa's.

Don't know how to re-build the affected apps, feel like an idiot at the moment and don't think I'd trust myself.

---

### Post by mc4man on 2009-11-09
could you explain this from post 14
> Removed the apps again, please see attached
What did you remove?

I would leave some of the updates alone for the moment (alsa packages, firefox, the nvidia packages if you have a nvidia card, xserver, xulrunner

You're probably using the firstm mplayer-no gui instead of the previous rvm one, if that's ok then it can stay

You could try

open software sources and  make sure in main page first 4 boxes are checked, under the updates tab the first 2

search ffmpeg in synaptic and remove **all** installed packages seen (scroll down

search libxine1 and remove **all** packages with libxine1 in name

search libx264 and this time remove all installed

click apply

Then open a terminal and run
sudo apt-get update

Then try to install vlc, your gstreamer-plugins ect.

---

### Post by n.hinton on 2009-11-10
Hi mc4man, sorry post14 was vague, I repeated the procedures you suggested in post 7.

You are a genius, vlc totem are installed and playing wmv flv and all other formats tested so far.

Winff is reinstalled and working as is gnomebaker, reinstalled libxine1, all is working fine.

Have not reinstalled devede as it affects other packages, thought I would ask your advice on this first, please see screen-shot.

Again many thanks for your help and patience.

---

### Post by mc4man on 2009-11-10
devede wants the extra versions of the ffmpeg libs which shouldn't be an issue to install ( and may be helpful to winff

Note though that aac encoding will not be available for winff unless you build a static ffmpeg, can link to guide if needed

You may though have a problem with devede itself depending on what mencoder package is installed and if you're using devede to create dvd video

What do you want devede for?

Search mencoder in synaptic and see what version is installed


Side note on firefox

You probably have a 3.6.X version of firefox installed, (check).
 If you wish to get security updates to firefox you'll need to either return to the repo version or check the firstm ppa page ocassionally to see if there is an updated firefox package.

In that case you'd enable the ppa, **just update firefox** and then **disable the ppa immediately **

Otherwise seek advice about how to return to karmic repo firefox, I can't advise there, (maybe quite simple), if so, start  a new thread on that.

---

### Post by n.hinton on 2009-11-10
Hi mc4man,

I wanted devede for an easy way to get various formats of media file burnt to a DVD that can be played in a TV DVD player, can live without it if it will cause problems.

From 'About Mozilla FireFox':
Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.1.4) Gecko/20091028 Ubuntu/9.10 (karmic) Firefox/3.5.4

Really appreciate your help its great to have Karmic working as it should.

Thanks

PS Can I remove [http://ppa.launchpad.net/thefirstm/karmic-testing/ubuntu](http://ppa.launchpad.net/thefirstm/karmic-testing/ubuntu) ppa? Its already disabled.

---

### Post by mc4man on 2009-11-10
> PS Can I remove [http://ppa.launchpad.net/thefirstm/k...testing/ubuntu](http://ppa.launchpad.net/thefirstm/k...testing/ubuntu) ppa? Its already disabled. 

Yeah, go ahead, seems you didn't get updated there (firefox)

You can try devede, if after devede does the encoding part (mencoder) if you get an error message about 'unable to create dvd tree' then you need to use the karmic repo mencoder instead 

see related post here ( and how to revert mencoder
[http://ubuntuforums.org/showthread.php?p=8274705#post8274705](http://ubuntuforums.org/showthread.php?p=8274705#post8274705)

 In this case the Op had the rvm mplayer/mencoder versions and while mplayer worked fine, mencoder caused an issue with devede as noted above (here and in linked thread

Forcing **just mencoder** back to karmic repo version solved

Haven't had a chance to explore what the issue was/is, may have been the particular mplayer revision rvm used or that devede needs a mencoder that's built off of the system ffmpeg libs 

(in other words if karmic repo ffmpeg libs are installed then the karmic mencoder to match

It shouldn't hurt to try devede, at worst your project would fail, then follow instructions in linked post

Small note
as far as mplayer itself, the firstm package you have is fine, if desired, you could remove and install the rvm mplayer package.

( All of rvm's  ppa's  are quite safe to leave enabled

Both are far superior to the karmic repo mplayer so use one or the other

---

### Post by n.hinton on 2009-11-10
Thanks mc4man, your a star.

---

### Post by n.hinton on 2009-11-15
Hi mc4man,

Does your expertise encompass winff/ffmpeg? Used to be able to convert to gp3 format, but now seems I can't (please see screenshot). Odd, winff can play the format.

Got the following in the convert window:
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.97 (30000/1001)
Input #0, flv, from '/home/kingfisher/Videos/Charlie_the_Unicorn_3.flv':
  Duration: 00:05:57.89, start: 0.000000, bitrate: 327 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x180, 263 kb/s, 29.97 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 64 kb/s
Unknown encoder 'libfaac'

libfaac0 is installed in synaptic, would appreciate any advice you can offer if you have time, but its not essential to fix it, as I can do the conversion in windows with the winff/ffmpeg that live there. Just don't like having to rely on windows.

---

### Post by mc4man on 2009-11-15
For the most part this should be straightforward

Encoding with libfaac is no longer possible with the repo ffmpeg in karmic - it's been removed, case closed.

If you wish you can build your own ffmpeg by **following this thread carefully.**

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Some things to keep in mind.

You're only building ffmpeg itself (a static build) to replace the repo ffmpeg.
You'll be leaving your curent ffmpeg shared libs alone (libavcodec52 or libavcodec-extra-52, libavformat52, .....ect.

You'll need to also build new x264 headers as the howto shows

The only packages that will need to be removed are in step 1, leave everything else as is.

If you have a nvidia card and happen to have nvidia-185-libvdpau-dev installed, then unless there has been a recent change you'll want to add this to end of the ffmpeg configure (step 4)(also applies to 180 version

```
--disable-vdpau
```

The howto will install your new ffmpeg into /usr/local/bin, atm you'll need to adjust the path for ffmpeg and ffplay in winff's preferences menu.

FakeOutdoorsman is much more knowledgeable than me in ffmpeg, and issues can be posted into that thread and should be easily resolved.


( Well worth doing, easier than it may appear, and as noted, help is readily available

---

### Post by n.hinton on 2009-11-16
Hi mc4man,

Read through the How-To, since I have never done this before a couple of things are bugging me:

In steps 3 and 4 the code starts with a cd (change directory) with no directory specified, that wouldn't do anything (or am I missing something).

Steps 3 and 4 state respectively: 'If you are behind a firewall or unable to use git, then daily source tarballs are also available' and 'If you are behind a firewall or unable to use subversion, then nightly FFmpeg snapshots are also available' is there any way to test ability to use first? As although I have downloaded x264-snapshot-20050824-2219.tar.bz2 and ffmpeg-checkout-snapshot.tar.bz2, I wouldn't know what to do with them.

Card is ATI Rage XL

---

### Post by n.hinton on 2009-11-17
Many thanks once again mc4man, will post to FakeOutdoorsman's thread.

---

### Post by mc4man on 2009-11-17
just trust the howto, and do in order

---

### Post by n.hinton on 2009-11-17
Hi mc4man,

I now have a good ffmpeg/x264

Can't thank you enough, '**brilliant**' **!**

---

### Post by helpdeskdan on 2009-11-25
Forgive me, I don't mean to hijack the thread, but I'm also having this exact issue after upgrading.  

I've built so much from source, I can't remember; recently mplayer which works like a charm.  However, I'd like to get gstreamer and xine working again because many more apps use that as opposed to mplayer.  

Will a simply building ffmpeg from source fix this?  

GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstffmpeg.so': libavutil.so.49: cannot open shared object file: No such file or directory

---

### Post by n.hinton on 2009-11-26
Hi helpdeskdan,

I am not the expert here, mc4man is, post 18 was what finally fixed things.

I would read through the whole thread first and check out the screenshots and verify the problem you have is the same one I had.

PS
Start totem from a terminal with totem --debug
close totem and check the terminal output with the output mine had in post 1

---

### Post by Nemo_bis on 2009-11-27
Thank you, [post 18](http://ubuntuforums.org/showpost.php?p=8281817&postcount=18) worked for me too (while Medibuntu and other packages didn't help).

---

