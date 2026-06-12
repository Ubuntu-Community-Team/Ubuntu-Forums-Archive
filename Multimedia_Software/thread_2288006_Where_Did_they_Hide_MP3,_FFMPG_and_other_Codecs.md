---
title: "Where Did they Hide MP3, FFMPG and other Codecs?"
date: 2015-07-23
forum: Multimedia Software
---

### Post by Rick St. George on 2015-07-23
Just intalled Xubuntu on my wifes laptop. Can't play any video or listen to music. 
Even though I selected upon new install to include 3rd party codec for MP3.

Seen old posts which are invalid. 


Attempting ```
 sudo apt-get install ubuntu-restricted-extras
``` gives - "unable to locate package". 

Where & How can we get the codecs?

Thanks!
Rick

---

### Post by qamelian on 2015-07-23
The command you used should work if you are using a currently supported release of Xubuntu. You can also try:
```
sudo apt-get install xubuntu-restricted-extras
```

---

### Post by Rick St. George on 2015-07-23
"unable to locate package" is the return. Apparently ... they are no longer available starting with v14.04. 
Funny, I have them installed on my UbuntuStudio.

This is recent decision by somebody, and I am sure everyone is gonna wanta know - WHY?

What Codecs do we need, and where can we get them for MP3, other audio and video ? ? ?

I cannot believe, they refused to include these "important to the community" codes necessary to simply play audio and video.

HMMMMmmmm  ... Nah - Couldn't be a C O N SPIRACY ?!?!?!  

Rick

---

### Post by Rick St. George on 2015-07-23
Found this ....

"gstreamer0.10-ffmpeg is not supported on 14.04 at this time. See [this page]("http://www.webupd8.org/2014/03/get-firefox-and-phonon-gstreamer-to.html") for details and workarounds."
[http://www.webupd8.org/2014/03/get-firefox-and-phonon-gstreamer-to.html](http://www.webupd8.org/2014/03/get-firefox-and-phonon-gstreamer-to.html)

---

### Post by v3.xx on 2015-07-23
<snip>

---

### Post by mc4man on 2015-07-23
On a new install - 
sudo apt-get update

---

### Post by mystics on 2015-07-23
The Ubuntu Software Center has Ubuntu restricted extras, so you could open up the software center and just search for it.

Also, the Xubuntu documentation has some information on getting music and video to play in both their [Quick Guide to Default Applications]("http://docs.xubuntu.org/1404/guide-default-apps.html#default-media") and [Media Applications]("http://docs.xubuntu.org/1404/media-apps.html") chapters. These include some specific packages you can install, including more Xubuntu-specific packages. Just know that some of them are specific to the default applications on Xubuntu and aren't necessary if you're using something else, but these should be easy to spot just on the names.

Edit: Oh yeah, and be sure to run:

```
sudo apt-get update
```

That may fix all the problems with using the terminal.

---

### Post by SeijiSensei on 2015-07-23
I recommend using Doug McMahon's excellent [repository]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media") for these types of software.  Follow the instructions on that page to add his PPA to your repository list.  

I also recommend using **mpv** as your default media player.  If you install smplayer as the front end, it now supports mpv as well as mplayer.

---

### Post by Rick St. George on 2015-07-23
> **mc4man said:**
> On a new install - 
sudo apt-get update

Did that, then

```

sudo apt-get install xubuntu-restricted-extras

```

I got;

"E: unable to locate package xubuntu-restricted-extras"

Why is it looking on the E drive ? ? ?  According to Software Updater it should retrieve from MAIN SERVER ... 
and Canonical Partners right.  

Stumped ! ! !

---

### Post by Rick St. George on 2015-07-23
[QUOTE=Mystics]
The Ubuntu Software Center has Ubuntu restricted extras, so you could open up the software center and just search for it.

Also, the Xubuntu documentation has some information on getting music and video to play in both their [Quick Guide to Default Applications]("http://docs.xubuntu.org/1404/guide-default-apps.html#default-media") and [Media Applications]("http://docs.xubuntu.org/1404/media-apps.html") [/QUOTE]


You must have missed Post #4 above. It is no longer supported in v14.04.

Even Ubuntu Software Center shows - "There isn't a software package called gestreamer0.10-ffmpeg in your current software sources". 
And this after allowing UNIVERSE as source.

---

### Post by mc4man on 2015-07-23
E: means error , not drive
Maybe post this - 
```
cat /etc/apt/sources.list
```
If it looks good then post the results of a sudo apt-get update

---

### Post by efflandt on 2015-07-23
ubuntu-restricted-extras or xubuntu-restricted-extras are still in the (multiverse) repositories for 14.04. Do you have an Internet connection and does Software Updater automatically notify you when there are updates you should do? **Ubuntu Software Center** should be able to find them by simply entering the word **restricted** in its search bar.

---

### Post by Rick St. George on 2015-07-23
> **SeijiSensei said:**
> I recommend using Doug McMahon's excellent [repository]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media") for these types of software.  Follow the instructions on that page to add his PPA to your repository list.  

I also recommend using **mpv** as your default media player.  If you install smplayer as the front end, it now supports mpv as well as mplayer.


The following is what shows when attempting to add his Repo;  Looks dangerous and complicated ???

```

 Upgraded, advanced or not normally available multimedia packages for Trusty

*Please note that if using this ppa I would *not* try upgrading to 14.10/15.04, ect. Do a fresh install instead. The intent here is just for users wishing to stay on 14.04*

If upgrading releases anyway use ppa-purge *First* -
sudo ppa-purge  ppa:mc3man/trusty-media

Also note that using this ppa then disabling may cause issue for installing i386 packages like used by wine. So once enabled leave enabled or purge before removing.

Additionally if using apt-get * sudo  apt-get dist-upgrade will be needed* at times.(pay attention).  Otherwise package managers may be ok.

So typically -
sudo add-apt-repository ppa:mc3man/trusty-media
sudo apt-get update
sudo apt-get dist-upgrade

A few notes:
gstreamer0.10-ffmpeg - needed for some apps that still use gstreamer-0.10 & also provides h.264 in html5 decoding for firefox < 30.
Note that Firefox 30 will support h.264 in html5 thru gstreamer1.0-libav & should be available soon

A standalone ppa is here for gstreamer0.10-ffmpeg  -
https://launchpad.net/~mc3man/+archive/ubuntu/gstffmpeg-keep

Added: gstreamer-vaapi, now works ok...

Totem+grilo - it's quite possible this & RB+grilo will show in 14.04 by first point release, if so will probably remove. Also note some plugins work well, some don't at all, bit of a mess

rhythmbox+grilo - needs to be enabled in rhythmbox > tools > plugins
Plus install grilo-plugins if not already

mpv - described here, add. info links
https://launchpad.net/~mc3man/+archive/mpv-tests
The mpv build in this ppa uses quvi0.9, the above linked ppa quvi0.4
For vaapi I'd use -
--vo=opengl-hq --hwdec=vaapi ( or --vo=opengl for some?
As --vo=vaapi can cause tearing in fullscreen

*Note* - Osc config options now go into ~/.mpv/lua-settings/osc.config
refer to manpage or pdf in /usr/share/doc/mpv
If this is a new install of mpv setting are in ~/.config/mpv

mplayer - described here, note mencoder is not inc. & likely will not be, you may be able to use repo mencoder..
https://launchpad.net/~mc3man/+archive/mplayer-test

fdkaac (fdkaac-encoder) - described here
https://launchpad.net/~mc3man/+archive/fdkaac-encoder

x264 - for use with ffmpeg from here, supports both 8 & 10 bit encoding

ffmpeg -
a static build for use of the binaries, installed to /opt/ffmpeg
binaries are symlinked in /usr/bin (ffmpeg, ffplay, ffprobe

For info on using libfdk_aac see here -
http://trac.ffmpeg.org/wiki/Encode/AAC

Can be used for both 8 & 10 bit x264 encoding with this ppa's libx264, default is 8
For 10 bit preload the 10 bit .so first in terminal, eg.,
export LD_PRELOAD=/usr/lib/x86_64-linux-gnu/x264-10bit/libx264.so.142
or
export LD_PRELOAD=/usr/lib/i386-linux-gnu/x264-10bit/libx264.so.142

libav - has fdkaac encoding enabled

yasm -
 has been patched to improve compiling x265

devede -
 can use either avconv or ffmpeg from here
 1st choice for previewer is mplayer (version here is best

K9copy -
Mainly for ripping, as far as encoding there are better apps. If inclined to use for encoding then use mencoder as ffmpeg support is quite limited

For rhythmbox users a wide range of plugins can be found here -
https://launchpad.net/~fossfreedom/+archive/rhythmbox-plugins

Abcde -
ck. Suggested in synaptic for add. useful packages
A guide to config is here -
http://www.andrews-corner.org/abcde.html

An excellent  audio recorder is available here -
https://launchpad.net/~osmoma/+archive/audio-recorder

A good blender ppa is here -
 https://launchpad.net/~irie/+archive/blender

To further extend this ppa to libav11 check here -
https://launchpad.net/~mc3man/+archive/ubuntu/testing6

To repeat -
*Please note that if using this ppa I would *not* try upgrading to 14.10/15.04, ect. Do a fresh install instead. The intent here is just for users wishing to stay on 14.04*
If upgrading anyway use ppa-purge first -
sudo ppa-purge  ppa:mc3man/trusty-media

Also note that with apt-get a sudo apt-get dist-upgrade is needed for initial setup & with some package upgrades
 More info: https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media
Press [ENTER] to continue or ctrl-c to cancel adding it


```

---

### Post by Rick St. George on 2015-07-23
> **mc4man said:**
> E: means error , not drive
Maybe post this - 
```
cat /etc/apt/sources.list
```
If it looks good then post the results of a sudo apt-get update


----- RESULTS -------- 

```

# deb cdrom:[Xubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu trusty main restricted
deb-src http://archive.ubuntu.com/ubuntu trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu trusty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://archive.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu trusty-security main restricted

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu trusty main
# deb-src http://extras.ubuntu.com/ubuntu trusty main


```

END

---

### Post by mc4man on 2015-07-23
Open up Software & Updates, on first tab make sure the top 4 are enabled as in screen 1
On the Updates tab make sure top 2 are enabled as in screen 2
reload source & try again.

---

### Post by mystics on 2015-07-23
> **Rick St. George said:**
> You must have missed Post #4 above. It is no longer supported in v14.04.

Even Ubuntu Software Center shows - "There isn't a software package called gestreamer0.10-ffmpeg in your current software sources". 
And this after allowing UNIVERSE as source.

Sorry, I must have been in the middle of writing my own response when you posted that you were having that problem.

---

### Post by Rick St. George on 2015-07-23
WOW - running update in terminal must have helped fix the problem - for some reason.

After apt-get update; Opened Software Center, searched for Restricted, and found "Xubuntu Restricted Extras". Installed and the laptop played MP3 songs and even a .WMV video.

Just a couple hours of patience! But what a waste of time for anyone who is going to attempt an install of 14.04 or later of any flavor of Ubuntu.

TAKE NOTE - EVERYONE IN THE FUTURE WHO HAPPENS UPON THIS THREAD.

You must install Codecs via the flavor of your choice - as X / Myth / K / etc., as in;

xubuntu-restricted-extras

As for why?  Well, that can by YOUR Homework ! ! ! 

This Case Closed.

Thanks Guys!
Rick

---

### Post by mc4man on 2015-07-23
On a *new install* you need to first update your sources before you can install anything from apt-get...
software-center would do this on opening so it would take care of the above.

---

### Post by Rolandl on 2015-07-24
How about converting mp4 to mp3. (hope this is right place to ask). 
I've installed 'selene media encoder' with terminal and don't know how to run it. 
Does it work good in ubuntu 15.04? Thank you.

---

### Post by SeijiSensei on 2015-07-24
[MP4]("https://en.wikipedia.org/wiki/MPEG-4_Part_14") is a video container; [MP3]("https://en.wikipedia.org/wiki/MP3") is an audio codec.  Converting from MP4 to MP3 will drop the video stream.

---

### Post by Rolandl on 2015-07-24
Yes I know the diff between mp4 and 3. What I'm mainly concerned about right now is getting a converter software that works well for ubuntu 15.04 to convert mp4 videos to mp3 audio.

Thank you.

---

### Post by mc4man on 2015-07-24
> **Rolandl said:**
> Yes I know the diff between mp4 and 3. What I'm mainly concerned about right now is getting a converter software that works well for ubuntu 15.04 to convert mp4 videos to mp3 audio.

Thank you.
that selena seems too simplistic, for a gui try either winff or this one ( free fom link, $3 from software-center
[http://dmsimpleapps.blogspot.ro/2014/04/dmmediaconverter.html](http://dmsimpleapps.blogspot.ro/2014/04/dmmediaconverter.html)

---

### Post by Yellow Pasque on 2015-07-25
> **Rolandl said:**
> to convert mp4 videos to mp3 audio.

Do you need mp3, or would AAC work? No reason to convert the AAC to mp3 if you can avoid it (or you will needlessly lose audio quality).

---

### Post by Rolandl on 2015-07-25
I've just tried Selene and seems to be working well for me so far, and quick conversion. 
Will give it a good trial.  Thanks y'all.

---

