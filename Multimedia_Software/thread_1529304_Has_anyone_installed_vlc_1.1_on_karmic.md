---
title: "Has anyone installed vlc 1.1 on karmic?"
date: 2010-07-12
forum: Multimedia Software
---

### Post by Bakon Jarser on 2010-07-12
I can't seem to find a .deb or ppa to get vlc 1.1 on karmic.  the korn ppa only works for lynx and maverick.  Am I finally gonna have to break down and install this from source?

---

### Post by Bakon Jarser on 2010-07-12
Anybody?

---

### Post by Bakon Jarser on 2010-07-12
No one?  Compiling this from source is harder than I thought.  Maybe I'll just upgrade to maverick.

---

### Post by ron999 on 2010-07-12
I'm using VLC v1.0.5 with Karmic.
What is the advantage with v1.1 ? What's new?

---

### Post by sidzen on 2010-07-12
> **Bakon Jarser said:**
> No one?  Compiling this from source is harder than I thought.  Maybe I'll just upgrade to maverick.

It's not easy using apt-get! 
Enable medibuntu repository
[PHP]sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update[/PHP] The above is from the site [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu).  I found Brasero interfering, so I purged it [PHP]sudo apt-get purge brasero[/PHP]. Update[PHP] sudo apt-get update[/PHP] Then I build dependencies around that which I want    [PHP]sudo apt-get build-dep dvdcss && sudo apt-get -f install dvdcss[/PHP]  NOTE: one may have to use "dvdcss2" in place of the simple dvdcss.  Then, install vlc [PHP]sudo apt-get build-dep vlc && sudo apt-get -f install vlc[/PHP]In addition, I find aptitude more to my liking for doing upgrades, so if you cannot, apter first updating, do this [PHP]sudo aptitude safe-upgrade[/PHP], then get it with the apt-get install command.

Hope this proves useful to you.

---

### Post by Bakon Jarser on 2010-07-12
> **ron999 said:**
> I'm using VLC v1.0.5 with Karmic.
What is the advantage with v1.1 ? What's new?

The major feature that I need is gpu decoding for HD video.  I'm using smplayer til I can get this installed.

---

### Post by Bakon Jarser on 2010-07-12
> **sidzen said:**
> It's not easy using apt-get! 

Hope this proves useful to you.

Thanks for trying but medibuntu doesn't have the latest vlc (or any vlc).  That just installed vlc 1.0.2 which is the default version for karmic.

Edit:  list of packages in medibuntu karmic repository

[http://packages.medibuntu.org/karmic/index.html](http://packages.medibuntu.org/karmic/index.html)

---

### Post by mc4man on 2010-07-12
It's actually not that hard to build once you've done, actually just finished a 1.1.1 build to test a patch to correct vp8 decoding.

I could point you to a how-to, but you'd need to make some adjustments in the method and/or use as a basis. 

Are you on a 32 or 64 bit install? (makes a bit of diff.

====================================================================

Otherwise - there is a ppa with a vaapi enabled  vlc 1.1 but it's a little old - 3/24, though it may work for you.

Keep in mind that it will install new ffmpeg shared libs, some karmic apps will break though he does provide some replacements.

[https://launchpad.net/~nvidia-vdpau/+archive/cutting-edge-multimedia](https://launchpad.net/~nvidia-vdpau/+archive/cutting-edge-multimedia)

(if using, and gtreamer apps matter I'd first enable this ppa and update the gstreamer libs and plugins, then use the above ppa (and don't use his gstreamer ffmpeg plugin

[https://launchpad.net/~gstreamer-developers/+archive/ppa/+packages](https://launchpad.net/~gstreamer-developers/+archive/ppa/+packages)


As far as maverick - the vlc 1.1.0 build does not have vaapi enabled, you'll have to build or ppa's will certainly have once maverick releases 

small note - ymmv - I find vaapi to be **nowhere** as good as vdpau in mplayer though that certainly could be different depending on hardware one has

---

### Post by andrew.46 on 2010-07-13
Hi ron,

> **ron999 said:**
> I'm using VLC v1.0.5 with Karmic.
What is the advantage with v1.1 ? What's new?

Looks like some pretty impressive changes:

[http://www.videolan.org/developers/vlc/NEWS](http://www.videolan.org/developers/vlc/NEWS)

Andrew

---

### Post by mc4man on 2010-07-13
Taking a closer look at Andrew's guide I see he's updated the ffmpeg source inb. with the newer amd_64 patch so you could use that guide as is for 1.1.1 or 1.1.0 (almost..
You'd want to substitute the source from the 1.2 git to 1.1.0 or 1.1.1, install libva libs and headers, and for taglib (libtag - 3 packages) the 1.6.3 source should work - available in lucid-proposed or default in maverick. (or can be statically built and linked as like ffmpeg

[http://nightlies.videolan.org/build/source/?C=M;O=D](http://nightlies.videolan.org/build/source/?C=M;O=D)
Look at 'latest', if latest is 1.2 then look at first listed 'branch' for 1.1.1,  
1.1.0 is on [main vlc page]("http://www.videolan.org/vlc/") under "You can also directly get the.."
=============================================================

If a newer than 4/28 ffmpeg source is desired for 32 bit just use it instead of source in guide, for 64 bit the current patch should still work


Patch for amd_64 - first one listed - applt to ffmpeg source before compiling
[http://connie.slackware.com/~alien/slackbuilds/vlc/build/](http://connie.slackware.com/~alien/slackbuilds/vlc/build/)

(--enable-libfaad needs to be removed from ffmpeg configure for recent ffmpeg sources)

The guide 
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

---

### Post by sidzen on 2010-07-13
> **Bakon Jarser said:**
> Thanks for trying but medibuntu doesn't have the latest vlc (or any vlc).  That just installed vlc 1.0.2 which is the default version for karmic.

Edit:  list of packages in medibuntu karmic repository

[http://packages.medibuntu.org/karmic/index.html](http://packages.medibuntu.org/karmic/index.html)

[PHP]sudo apt-get install ubuntu-restricted-extras vlc compizconfig-settings-manager catfish audacious wine startupmanager firestarter thunderbird localepurge emerald rar unrar-free flashplugin-nonfree virtualbox-ose gparted xchat[/PHP]

Are you just trying to be difficult?

---

### Post by mc4man on 2010-07-13
> **sidzen said:**
> [PHP]sudo apt-get install ubuntu-restricted-extras vlc compizconfig-settings-manager catfish audacious wine startupmanager firestarter thunderbird localepurge emerald rar unrar-free flashplugin-nonfree virtualbox-ose gparted xchat[/PHP]

Are you just trying to be difficult?

Is there a point to your post relevant to this thread?

---

### Post by Yellow Pasque on 2010-07-13
LOL. This is why I like rolling-release distros. With old Ubuntu versions, you can build stuff from source, but then you find you need an updated version of this dependency and that dependency. Before you know it, it would have been quicker/easier just to upgrade to the latest version...

---

### Post by ron999 on 2010-07-18
Hi
The Windows version of VLC 1.1.0 runs with Wine in Ubuntu Karmic. :D

---

