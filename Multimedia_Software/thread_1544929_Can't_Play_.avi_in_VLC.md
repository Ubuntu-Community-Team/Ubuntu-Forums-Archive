---
title: "Can't Play .avi in VLC"
date: 2010-08-03
forum: Multimedia Software
---

### Post by shinigami13 on 2010-08-03
Tried playing a .avi movie using vlc and i keep getting the "mp4v" error. I have the sound of the movie but no video.

---

### Post by jerenept on 2010-08-03
have you installed the "ubuntu-restricted-extras" package?

open a Terminal and type ```
sudo apt-get install ubuntu-restricted-extras
```

then enter your password.
This should fix your problem.

---

### Post by shinigami13 on 2010-08-03
> **jerenept said:**
> have you installed the "ubuntu-restricted-extras" package?

open a Terminal and type ```
sudo apt-get install ubuntu-restricted-extras
```then enter your password.
This should fix your problem.

Run the code and the problem didn't get fix

it still display

 p, li { white-space: pre-wrap; }  [COLOR=#FF0000]No suitable decoder module:[/COLOR]
 [COLOR=#000000]VLC does not support the audio or video format "mp4v". Unfortunately there is no way for you to fix this.[/COLOR]
 [COLOR=#000000][/COLOR]

still no video but have sound

---

### Post by ron999 on 2010-08-03
> **shinigami13 said:**
> 

still no video but have sound

Use **mediainfo** to find out what's instide that avi file.
It's probably using some video codec that VLC can't handle.

---

### Post by shinigami13 on 2010-08-03
> **ron999 said:**
> Use **mediainfo** to find out what's instide that avi file.
It's probably using some video codec that VLC can't handle.

Run the file with mediainfo and heres what  i've got

General
Complete name                    : /media/Data/A.Nightmare.on.Elm.Street.2010.Super.Custon.XviD.UNDEAD.NoRar.[www.crazy-torrent.com/A.Nightmare.on.Elm.Street.2010.Super.Custon.XviD.UNDEAD.NoRar.www.crazy-torrent.com.avi]("http://www.crazy-torrent.com/A.Nightmare.on.Elm.Street.2010.Super.Custon.XviD.UNDEAD.NoRar.www.crazy-torrent.com.avi")
Format                           : AVI
Format/Info                      : Audio Video Interleave
File size                        : 700 MiB
Duration                         : 1h 30mn
Overall bit rate                 : 1 084 Kbps
Movie name                       : DEN_ANIGHTMAREONELMSTREET.Title1.DVDRip
Writing application              : Lavf52.33.0
Original source form/Name        : DEN_ANIGHTMAREONELMSTREET

Video
ID                               : 0
Format                           : MPEG-4 Visual
Format profile                   : Simple@L3
Format settings, BVOP            : No
Format settings, QPel            : No
Format settings, GMC             : No warppoints
Format settings, Matrix          : Default (H.263)
Codec ID                         : XVID
Codec ID/Hint                    : XviD
Duration                         : 1h 30mn
Bit rate                         : 880 Kbps
Width                            : 656 pixels
Height                           : 282 pixels
Display aspect ratio             : 2.35:1
Frame rate                       : 29.970 fps
Resolution                       : 8 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.159
Stream size                      : 568 MiB (81%)
Writing library                  : XviD 1.2.1 (UTC 2008-12-04)

Audio
ID                               : 1
Format                           : AC-3
Format/Info                      : Audio Coding 3
Codec ID                         : 2000
Duration                         : 1h 30mn
Bit rate mode                    : Constant
Bit rate                         : 192 Kbps
Channel(s)                       : 2 channels
Channel positions                : Front: L R
Sampling rate                    : 48.0 KHz
Stream size                      : 124 MiB (18%)
Alignment                        : Aligned on interleaves
Interleave, duration             : 32 ms (0.96 video frame)

---

### Post by ron999 on 2010-08-03
Hi
I can't see anything wrong with that printout.
It's just a regular XviD codec used.
Try to play the file using a different player such as mPlayer or Xine.

---

### Post by shinigami13 on 2010-08-03
Tried mplayer, xine, gxine and vlc.. all with the same result.. no video but have sound..

Tried playing the file in a Windows XP OS, in case maybe the file itself was corrupted.. but i played with video under the xp OS..

Kinda getting frustrated..in trying to make this file work

---

### Post by ron999 on 2010-08-03
Hi
Try adding the Medibuntu repository.
Read the page and do the part that says '**Adding the Repository**'.
Here:-[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by shinigami13 on 2010-08-03
> **ron999 said:**
> Hi
Try adding the Medibuntu repository.
Read the page and do the part that says '**Adding the Repository**'.
Here:-[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Have added the Medibuntu repository and added the win32 codecs
yet still same result. I'm thinking maybe there's a conflict in the codecs or something that prevents the player to play the video... or i'm just missing something..

---

### Post by mc4man on 2010-08-04
You might wish to try this - 
Open synaptic, search ffmpeg, and remove all installed ffmpeg libraires, starting with libavcodec* down to libswscale*

You'll lose some players and a plugin or 2, no matter, they can be reinstalled. (in synaptic, file -> history will show you

Then install some players and libxine1-ffmpeg and see.

For vlc - start the first time from terminal with
```

vlc --reset-plugins-cache --reset-config
```

Or go into home folder -> view, show hidden files, and in the .cache and .config folders delete the vlc folder

---

### Post by shinigami13 on 2010-08-04
> **mc4man said:**
> You might wish to try this - 
Open synaptic, search ffmpeg, and remove all installed ffmpeg libraires, starting with libavcodec* down to libswscale*

You'll lose some players and a plugin or 2, no matter, they can be reinstalled. (in synaptic, file -> history will show you

Then install some players and libxine1-ffmpeg and see.

For vlc - start the first time from terminal with
```

vlc --reset-plugins-cache --reset-config
```Or go into home folder -> view, show hidden files, and in the .cache and .config folders delete the vlc folder



Still no dice sir.. :(...

---

### Post by shinigami13 on 2010-08-04
mplayer-gui won't open

---

### Post by sarang on 2010-08-10
Yes, no video for me either after upgrade today. I will try and do some troubleshooting for a few days but I we may have to file a bug report.

---

### Post by no2498 on 2010-08-10
type smplayer in a terminal it tells you how to install it

down load the video open the folder right click the video open with smplayer

hope that helps you

---

### Post by Cavsfan on 2010-08-10
If you did the update with the partial upgrade it removed [COLOR=Red]ffmpeg[/COLOR].

[B]sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade[/B]
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
[COLOR=Red]The following packages will be REMOVED:
  ffmpeg[/COLOR]
The following NEW packages will be installed:
  libavutil50 libva1
The following packages have been kept back:
  libavdevice52
The following packages will be upgraded:
  libpostproc51 libswscale0
2 upgraded, 2 newly installed, 1 to remove and 1 not upgraded.
Need to get 362kB of archives.
After this operation, 569kB disk space will be freed.
Do you want to continue [Y/n]? 

```

---

### Post by sarang on 2010-08-10
I just solved my vlc video problems. It appears that the culprit was the getdeb repository that I had recently added. I commented out that repo and downgraded several packages - libavcodec-extra-52, libavdevice-extra-52 etc. The most important one seems to be libva1.

In case anyone needs detailed version information for some packages, I will be happy to post.

My repositories in /etc/apt/sources.list:

```


deb http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-updates main restricted multiverse universe

deb http://archive.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu lucid-proposed main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu lucid-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

# SARANG: Luna Renko has updated DigiKam packages:
deb http://ppa.launchpad.net/lure/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/lure/ppa/ubuntu lucid main

# SARANG: Photo panorama and HDR software 'hugin':
deb http://ppa.launchpad.net/hugin/hugin-builds/ubuntu lucid main
deb-src http://ppa.launchpad.net/hugin/hugin-builds/ubuntu lucid main

# SARANG: ppa for Redshift which adjusts display colour temperature based on time.
deb http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu lucid main

# SARANG: Empathy / telepathy ppa for using Google Talk voice?
deb http://ppa.launchpad.net/telepathy/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/telepathy/ppa/ubuntu lucid main

# SARANG: Medibuntu:
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ lucid free non-free
# deb-src http://packages.medibuntu.org/ lucid free non-free

# SARANG: VirtualBox:
deb http://download.virtualbox.org/virtualbox/debian lucid non-free

# SARANG: For KDE 4.3:
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu lucid main
deb http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu lucid main

# SARANG: TuxOnIce hibernation:
deb http://ppa.launchpad.net/tuxonice/ppa/ubuntu lucid main

# SARANG: Wine PPA:
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu lucid main

# SARANG: VDPAU nVidia video acceleration and new drivers
deb http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu lucid main

# SARANG: PPA for Pidgin IM
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu lucid main

# SARANG: PPA for cutting edge builds of vlc / ffmpeg / mplayer etc.
deb http://ppa.launchpad.net/nvidia-vdpau/cutting-edge-multimedia/ubuntu lucid main
deb-src http://ppa.launchpad.net/nvidia-vdpau/cutting-edge-multimedia/ubuntu lucid main

# SARANG: Repo for TOR. karmic repo officially works for lucid.
deb http://deb.torproject.org/torproject.org karmic main






###################################################################################

# SARANG: PPA for VLC
# deb http://ppa.launchpad.net/c-korn/vlc/ubuntu lucid main
# deb-src http://ppa.launchpad.net/c-korn/vlc/ubuntu lucid main


# SARANG: Google Chrome web browser:
#deb http://dl.google.com/linux/deb/ stable main

# SARANG: GetDeb repo for newer, less tested builds
# deb http://archive.getdeb.net/ubuntu lucid-getdeb apps

# SARANG: PPA for Invisible mode for Pidgin. Also has other unwanted unstable crap
#deb http://ppa.launchpad.net/frasten/ppa/ubuntu lucid main
#deb-src http://ppa.launchpad.net/frasten/ppa/ubuntu lucid main

# SARANG: Some guy's PPA for mplayer updated builds 
#deb http://ppa.launchpad.net/rvm/mplayer/ubuntu lucid main
#deb-src http://ppa.launchpad.net/rvm/mplayer/ubuntu lucid main

# SARANG: PPA for songbird daily builds:
#deb http://ppa.launchpad.net/songbird-daily/ppa/ubuntu lucid main
#deb-src http://ppa.launchpad.net/songbird-daily/ppa/ubuntu lucid main


# deb http://ubuntu.media.mit.edu/ubuntu/ karmic universe
# deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic multiverse universe

# SARANG: Firefox smooth scaling ppa:
# deb http://ppa.launchpad.net/firefox-smooth-scaling/ppa/ubuntu karmic main

# SARANG: ppa for getdeb repository:
# deb http://archive.getdeb.net/ubuntu karmic-getdeb apps

# SARANG: ppa for amarok 1.4:
# deb http://ppa.launchpad.net/bogdanb/ppa/ubuntu karmic mainuniverse
# deb-src http://ppa.launchpad.net/bogdanb/ppa/ubuntu karmic main

# SARANG: ppa for moblock-deb:
# deb http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu karmic main

# deb http://ppa.launchpad.net/whoopie79/ppa/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/whoopie79/ppa/ubuntu jaunty main
# deb http://ppa.launchpad.net/daniel-elstner/ppa/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/daniel-elstner/ppa/ubuntu jaunty main

# PPA for andersk for nvidia new stuff:
# deb http://ppa.launchpad.net/anders-kaseorg/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/anders-kaseorg/ppa/ubuntu karmic main

# SARANG: PPA for DropBox:
# deb http://linux.getdropbox.com/ubuntu karmic main
# deb-src http://linux.getdropbox.com/ubuntu karmic main

# SARANG: PPA for Synapse IM client:
# deb http://ppa.launchpad.net/firerabbit/ppa/ubuntu karmic main

# SARANG: PPA for Samsung printer / scanner drivers:
# deb http://www-personal.umich.edu/~tjwatt/suldr/ debian extra

# SARANG: PPA for gscan2pdf:
# deb http://ppa.launchpad.net/jeffreyratcliffe/ubuntu karmic main
# deb-src http://ppa.launchpad.net/jeffreyratcliffe/ubuntu karmic main

# SARANG: For PyQwt, which is broken in official repo.
# SARANG: Do not enable, has potential to break many python apps
# deb http://ppa.launchpad.net/treparel/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/treparel/ppa/ubuntu karmic main

# SARANG: For Mozilla daily:
# deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main

# SARANG: Amarok nightly, for amarok-2.2 that doesn't interfere with amarok 1.4
# deb http://ppa.launchpad.net/project-neon/ppa/ubuntu jaunty main

# SARANG: PPA for vlc:
# deb http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main
# deb-src http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main

# SARANG: PPA for gnome-do:
# deb http://ppa.launchpad.net/do-core/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/do-core/ppa/ubuntu karmic main

# SARANG: PPA for Twinkle IP phone and other SIP goodies:
# deb http://ppa.launchpad.net/gnutelephony/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/gnutelephony/ppa/ubuntu karmic main

############################################################################################





```

---

### Post by Cavsfan on 2010-08-10
Glad you got it working! :D 
I don't even have VLC installed, 
I just use Movie Player (Totem) and I can play anything.

---

