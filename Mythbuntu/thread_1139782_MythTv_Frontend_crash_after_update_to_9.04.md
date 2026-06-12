---
title: "MythTv Frontend crash after update to 9.04"
date: 2009-04-27
forum: Mythbuntu
---

### Post by junglecat on 2009-04-27
Hi,

I just updated my Mythbuntu 8.10 to 9.04 via the system update service. So far everything runs very well EXCEPT the MythTV frontend. 

The frontend crashed (switches to the desktop) after a recording is stopped and I try to return to the recordings page. When the Video is gone I will find myself again on the desktop not in the frontend anymore - oh and the frontend has died by then. 

ANYBODY has a solution / hint for me? I would be very thankful.:popcorn:

I use the 64 bit version on an AMD dualcore. (X2)

---

### Post by superm1 on 2009-04-27
Are you using fglrx?  I believe there is a bug in the AMD closed source graphics driver.  Unfortunately, there is a worse bug in the open source one causing mythtv to not show *any* text...

---

### Post by junglecat on 2009-04-27
I use an NVIDIA Chipset and the integrated graphics (430a).

Regards,

Jan.

---

### Post by superm1 on 2009-04-27
> **junglecat said:**
> I use an NVIDIA Chipset and the integrated graphics (430a).

Regards,

Jan.
OK, well are you on the closed source driver for nvidia?

---

### Post by alexyz on 2009-04-27
Same problem here, crash when you stop playing back recording and return to menu.  After jaunty upgrade.

Running frontend verbose doesn't show anything, but there's a segfault in my syslog that looks like this

> [ 4667.647233] mythfrontend.re[7117]: segfault at 2f2ce534 ip 2f2ce534 sp a721d35c error 4

* The internal player is crashing.  I have my frontend set up to use VLC as player for videos, and that works fine, exits back to menu.  So one fix would be to switch to VLC instead of the internal player for recordings.  Pretty sure that's possible but I haven't looked into it yet.  

I have an nvidia card and have tried various drivers:  proprietary hardware drivers (180.53?), directly from nvidia (180.51), as well as the latest beta from nvidia (185.18.04).  Have not tried downgrading to an earlier driver.  


Here's another (dead) thread with the same problem

[http://ubuntuforums.org/showthread.php?t=819605](http://ubuntuforums.org/showthread.php?t=819605)

---

### Post by superm1 on 2009-04-27
> **alexyz said:**
> Same problem here, crash when you stop playing back recording and return to menu.  After jaunty upgrade.

Running frontend verbose doesn't show anything, but there's a segfault in my syslog that looks like this


* The internal player is crashing.  I have my frontend set up to use VLC as player for videos, and that works fine, exits back to menu.  So one fix would be to switch to VLC instead of the internal player for recordings.  Pretty sure that's possible but I haven't looked into it yet.  

I have an nvidia card and have tried various drivers:  proprietary hardware drivers (180.53?), directly from nvidia (180.51), as well as the latest beta from nvidia (185.18.04).  Have not tried downgrading to an earlier driver.  


Here's another (dead) thread with the same problem

[http://ubuntuforums.org/showthread.php?t=819605](http://ubuntuforums.org/showthread.php?t=819605)
If you can, try to turn on apport (/etc/default/apport needs to be modified and then run the init script).  If you can get it to catch one of these crashes, Launchpad can work out a backtrace using debug symbols.

---

### Post by alexyz on 2009-04-27
> **superm1 said:**
> If you can, try to turn on apport (/etc/default/apport needs to be modified and then run the init script).  If you can get it to catch one of these crashes, Launchpad can work out a backtrace using debug symbols.

Got a report but have never done this before - could you point me to a howto?  I can figure it out but a quick look didn't turn up anything.  I do have a launchpad account.

* NEVER MIND I just RTFManpage...

---

### Post by alexyz on 2009-04-27
In case anyone is curious about apport - it's very easy.  If you have apport-gtk installed it pops up a wizard-like window to do the crash report.  There's also a command-line version, apport-cli ...

[https://wiki.kubuntu.org/Apport](https://wiki.kubuntu.org/Apport)

except it just failed with a network timed out error :-|

am trying again with the cli...

---

### Post by alexyz on 2009-04-27
apport is uploading the crash report OK but hangs when it goes to enter a bug in launchpad.  I'll try again later and will post the bug report here.

---

### Post by junglecat on 2009-04-28
@Alexyz: How exactly did you exchange the internal player with VLC? I could only manage that for "Videos" but not for "Recordings". Could you please point me in the right direction?

Thanks.

I will also try to completely deinstall the frontend and then reinstall it using the paket manager. I will loose all settings (or won't I?), but it's worth a try...

---

> **alexyz said:**
> Same problem here, crash when you stop playing back recording and return to menu.  After jaunty upgrade.

Running frontend verbose doesn't show anything, but there's a segfault in my syslog that looks like this


* The internal player is crashing.  I have my frontend set up to use VLC as player for videos, and that works fine, exits back to menu.  So one fix would be to switch to VLC instead of the internal player for recordings.  Pretty sure that's possible but I haven't looked into it yet.  

I have an nvidia card and have tried various drivers:  proprietary hardware drivers (180.53?), directly from nvidia (180.51), as well as the latest beta from nvidia (185.18.04).  Have not tried downgrading to an earlier driver.  


Here's another (dead) thread with the same problem

[http://ubuntuforums.org/showthread.php?t=819605](http://ubuntuforums.org/showthread.php?t=819605)

---

### Post by alexyz on 2009-04-28
> **junglecat said:**
> @Alexyz: How exactly did you exchange the internal player with VLC? I could only manage that for "Videos" but not for 
---

I don't think you can plug it in in place of the internal player, but you can do a hackish workaround, to make your recordings appear under videos.

- First set up VLC as your player for "videos"
- Symlink to your "recordings" directory from your "videos" directory
- Set videos file association for mpg to use "default" player instead of "internal"

BIG problem:  you see the recordings filenames, which are timestamps.  I've heard of a script that changes the file names to the program title, but I haven't looked into that yet.  Somewhere the distro includes a bunch of utility scripts.

Obviously you also lose integration with other functions, like deleting programs.

If you need more detailed instructions let me know, I'm too busy right now.

About reinstalling:  I doubt that will fix it.  But most settings are in the database so you won't lose them unless you blow away the database.

---

### Post by alexyz on 2009-04-28
To make the VLC workaround more user-friendly, the script to rename recordings files is here:

/usr/share/doc/mythtv-backend/contrib/mythrename.pl.gz

documentation here:

[http://www.mythtv.org/wiki/Mythrename.pl](http://www.mythtv.org/wiki/Mythrename.pl)

n.b. the --link option - looks like this is the best way to use it, create a set of symlinks in another directory rather than actually renaming the files.  I'll try this if we don't come up with a fix in the next couple days.

---

### Post by gtp_tj on 2009-04-29
> **junglecat said:**
> Hi,
The frontend crashed (switches to the desktop) after a recording is stopped and I try to return to the recordings page. When the Video is gone I will find myself again on the desktop not in the frontend anymore - oh and the frontend has died by then. 

ANYBODY has a solution / hint for me? I would be very thankful.:popcorn:


I had the exact same problem.  Also saw a similar crash in vlc when exiting video.

I uninstalled pulseaudio, and the problem went away.  Re-installed pulse, and it was back.  But in an apport dump I filed, the automated tracer said my libavutil and libavcodec weren't up to the right level.  Seems I had the unstripped versions of those libraries installed.  After installing those 2 (which forced removal on the unstripped versions)... the problem went away, even with pulseaudio running.

You might check those libraries first, and if that doesn't do it, then try uninstalling pulseaudio (if you are running it).

---

### Post by alexyz on 2009-04-29
thanks gtp_tj \\:D/

It appears to be related to pulseaudio.  I went through a slightly different procedure as follows:

> installed libavcodec52, libavutil49
> removed libavcodec-unstripped-52, libavutil-unstripped-49

still broken

> removed pulseaudio
> removed ubuntu-desktop

fixed

> reinstalled pulseaudio
* > along with:  libpulse-browse0, pulseaudio-module-hal, pulseaudio-module-x11, pulseaudio-utils

still works


* OBVIOUS QUESTION: if those are pulseaudio dependencies why weren't they installed before?  ...actually they appear to be suggests and recommends ... so I'm not sure why they were installed (using synaptic) - since when does that happen?

---

### Post by alexyz on 2009-04-29
Bad news is ... looks like live TV crashes in the same manner, and that is not fixed.

CORRECTION:  seems to be working.  It was broken along the way somewhere.

once again thanks gtp_tj - how do you officially thank someone anyhow?  I guess that feature has gone away.

---

### Post by junglecat on 2009-04-29
Ok, here is the part where I have to out me a a n00b ;-)

Alexyz: How did you install / uninstall those components?
If I open Synaptic and check those components for installation it automatically checks certain other components for DEinstallation (like VLC / MythBackend / ...). Is there a way of just replacing those files (like you did) without deinstalling all other applications that are connected with it?
Or is that the "safe" way and it is ok to do so?

Pls. help - I just don't want to trash my MythTV installation - it runs too well for that...

Thanks a LOT.

Regards,

JC.

> **alexyz said:**
> thanks gtp_tj \\:D/

It appears to be related to pulseaudio.  I went through a slightly different procedure as follows:

> installed libavcodec52, libavutil49
> removed libavcodec-unstripped-52, libavutil-unstripped-49

still broken

> removed pulseaudio
> removed ubuntu-desktop

fixed

> reinstalled pulseaudio
* > along with:  libpulse-browse0, pulseaudio-module-hal, pulseaudio-module-x11, pulseaudio-utils

still works


* OBVIOUS QUESTION: if those are pulseaudio dependencies why weren't they installed before?  ...actually they appear to be suggests and recommends ... so I'm not sure why they were installed (using synaptic) - since when does that happen?

---

### Post by alexyz on 2009-04-29
> **junglecat said:**
> 
If I open Synaptic and check those components for installation it automatically checks certain other components for DEinstallation (like VLC / MythBackend / ...). 

That didn't happen for me.  Are you doing it all at once?  Here's what I did, using synaptic.  

- Selected these two packages for installation:  libavcodec52, libavutil49

- This flagged two packages for removal:  libavcodec-unstripped-52, libavutil-unstripped-49

That's all.  Then I ran the update.  You probably have to do this as ONE operation - install the first two and remove the second two at the same time.  After than I removed and reinstalled pulseaudio.  Sounds like gtp_tj did it the other way around, uninstalled pulseaudio first.

Usually you can figure out what's going on by looking at dependencies.  In symantic, right click on the package and then select Dependencies.  That shows which other packages must be installed to use the one you're looking at.  Also if you're experimenting, File->History gives you a chronological list of updates, so you can see exactly what you've done.  If this doesn't work, post a list of exactly what it wants to uninstall.

---

### Post by junglecat on 2009-04-29
I tried to do this in one step but synaptic wants to remove the following:

libavcodec-unstripped-52
.. more unstripped stuff .. think THAT is ok

MythArchive
MythTV-Backend
MythTV-Backend-master
mythvideo
transcode
vlc
xine-ui
....

---

### Post by alexyz on 2009-04-29
Could be some difference in repositories.  In settings > repositories, do you "multiverse" selected?  That's the one that says "Software restricted by..."  My version of myth is coming from that repository.

I'm going to be offline for a while.  Sorry about that, maybe someone else can check their settings?  I actually noticed something wrong with my repositories (I have mediabuntu hardy enabled) but that probably is not causing any problems.  I can't do any testing at the moment.

---

### Post by gtp_tj on 2009-04-29
> **junglecat said:**
> I tried to do this in one step but synaptic wants to remove the following:

libavcodec-unstripped-52
.. more unstripped stuff .. think THAT is ok

MythArchive
MythTV-Backend
MythTV-Backend-master
mythvideo
transcode
vlc
xine-ui
....

junglecat, instead of marking the -unstripped- versions for removal... just mark libavcodec52 and libavutil49 for installation.  Marking those for installation should automagically mark the -unstripped- versions for removal and not cause mythv/vlc/etc to be removed too.

---

### Post by alexyz on 2009-04-30
junglecat, what gtp_tj said.  I didn't think of that.

---

### Post by junglecat on 2009-04-30
Hi GTP_TJ: Yes they do BUT also marking MythTV Backend, VLC and most other video apps for deinstallation.

But I solved the problem yesterday night: Using the Mythbuntu Command center I deactivated the Medibuntu codecs - by using the checkbox. That did work. The MythTV frontend now behaves well. 

Everybody thanks for their help!!

---

