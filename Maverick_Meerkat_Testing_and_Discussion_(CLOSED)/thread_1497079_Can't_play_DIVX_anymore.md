---
title: "Can't play DIVX anymore"
date: 2010-05-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by yelo3 on 2010-05-30
With a recent update I figured out that I couldn't play any DIVX file with either totem and vlc.

---

### Post by taavikko on 2010-05-30
```
/usr/lib/libavformat.so.52: symbol av_destruct_packet, version LIBAVCODEC_52 not defined in file libavcodec.so.52 with link time reference
```

---

### Post by taavikko on 2010-05-30
Looks like the libavcodec doesn't install shared objects...
```
dpkg -L libavcodec-extra-52 
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libavcodec-extra-52
/usr/share/doc/libavcodec-extra-52/copyright
/usr/share/doc/libavcodec-extra-52/changelog.gz
/usr/share/doc/libavcodec-extra-52/CREDITS
/usr/share/doc/libavcodec-extra-52/TODO
/usr/share/doc/libavcodec-extra-52/codecs.txt.gz
/usr/share/doc/libavcodec-extra-52/MAINTAINERS.gz
/usr/share/doc/libavcodec-extra-52/README.Debian.gz
/usr/share/doc/libavcodec-extra-52/changelog.Debian.gz
```

---

### Post by Reiger on 2010-05-30
Yep there's definitely something weird going on with the ffmpeg libraries; witness the mess that mplayer dependencies are now.

I guess it's waiting until ffmpeg/VLC/mplayer/gstreamer/phonon get rebuilt?

---

### Post by MacUntu on 2010-05-30
I need gstreamer right now - how dare they to mess around with my productive system? :D

---

### Post by vikrant82 on 2010-05-30
> **taavikko said:**
> Looks like the libavcodec doesn't install shared objects...

Right, [http://ubuntuforums.org//showpost.php?p=9378022&postcount=5](http://ubuntuforums.org//showpost.php?p=9378022&postcount=5)

---

### Post by taavikko on 2010-05-30
> **vikrant82 said:**
> Right, [http://ubuntuforums.org//showpost.php?p=9378022&postcount=5](http://ubuntuforums.org//showpost.php?p=9378022&postcount=5)

Yes.
However, "ffplay <file>" works, 
even when *-extra-* fmpeg files are replaced by the normal versions.

Just that mplayer/vlc/totem fails to correctly play it.
So they need to be patched...?

---

### Post by zika on 2010-05-30
> **taavikko said:**
> Yes.
However, "ffplay <file>" works, 
even when *-extra-* fmpeg files are replaced by the normal versions.

Just that mplayer/vlc/totem fails to correctly play it.
So they need to be patched...?/tmp$ ffplay ttt.wmv
ffplay: error while loading shared libraries: libavformat.so.52: cannot open shared object file: No such file or directory

Fixed it: installed: libavcodec52 libavutil49 libavformat52 (all without "extra"). Thank You!

---

### Post by taavikko on 2010-05-31
[https://bugs.edge.launchpad.net/ubuntu/+source/ffmpeg-extra/+bug/587424](https://bugs.edge.launchpad.net/ubuntu/+source/ffmpeg-extra/+bug/587424)

---

### Post by zika on 2010-05-31
While we are on the subject of "extra"... What is the real difference between "plain" and "extra" packages. I tried to get that picture from descriptions, but...

---

### Post by taavikko on 2010-05-31
> **zika said:**
> While we are on the subject of "extra"... What is the real difference between "plain" and "extra" packages. I tried to get that picture from descriptions, but...

Restricted version...
Supports more formats...

there ends my knotwledge, even if the previous was even accurate?

---

### Post by mc4man on 2010-05-31
> What is the real difference between "plain" and "extra" packages

The 'extra' versions allow for encoding with 'restricted' formats, should not be needed for decoding.

aac encoding has been removed from both, can only be enabled thru building your own ffmpeg or medibuntu offers their own 'extra' versions where it (aac), has been enabled.

Many times when a new ffmpeg (shared) is introduced, players that use those libs need to be rebuilt off of the new ffmpeg headers either to take advantage of new stuff or to run at all.

Ex. 
the new ffmpeg in maverick has native support for wmap and wmas. For vlc to decode it will need to be rebuilt, wmap support will be automatically added, for wmas vlc (1.0.X) will need a small patch.
ect. ect

---

### Post by eris23 on 2010-06-01
> **zika said:**
> /tmp$ ffplay ttt.wmv
ffplay: error while loading shared libraries: libavformat.so.52: cannot open shared object file: No such file or directory

Fixed it: installed: libavcodec52 libavutil49 libavformat52 (all without "extra"). Thank You!

I had to install libpostproc51 and libswscale0 as well (replacing the -extra libraries)

---

### Post by zika on 2010-06-01
> **eris23 said:**
> I had to install libpostproc51 and libswscale0 as well (replacing the -extra libraries)I've had those two already installed...

---

### Post by donniezazen on 2010-06-03
Is there any solution to it? Not having to play movies is frustrating. I am getting following errors.

In VLC
> No suitable decoder module:
VLC does not support the audio or video format "XVID". Unfortunately there is no way for you to fix this.

In Terminal
> [0x9b9c0b8] main decoder error: no suitable decoder module for fourcc `XVID'.
VLC probably does not support this sound or video format.

Thanks.

---

### Post by donniezazen on 2010-06-03
> **zika said:**
> 
Installed: libavcodec52 libavutil49 libavformat52 (all without "extra"). Thank You!

Thanks it worked.

---

### Post by taavikko on 2010-06-03
Newest mplayer and ffmpeg-extra is currently building by builders.
Maybe some time today they're shoved upon us :)

ffmpeg-extra fixes the missing .so files

Now, waiting for the gstreamer-bad to be fixed so totem plays nicely...

---

### Post by zika on 2010-06-05
I still can not play (almost) anything with Totem (it searches for plugin aand...)... Any news? My system is totally up-to-date... (Maverick). Yes, thanks to You guys I can use ffplay...

---

### Post by taavikko on 2010-06-05
> **zika said:**
> I still can not play (almost) anything with Totem (it searches for plugin aand...)... Any news? My system is totally up-to-date... (Maverick). Yes, thanks to You guys I can use ffplay...

totem requires gstreamer0.10-plugin-bad to work...
which at the moment can't be installed due to dependancy errors.

VLC should work out of the box

mplayer works without the lib*-extra-* from ffmpeg

---

### Post by VMC on 2010-06-05
> **taavikko said:**
> t...

mplayer works without the lib*-extra-* from ffmpeg

How do you get mplayer to play video folder VIDEO_TS to play like a DVD video player would. Change titles, menu options, etc. I can't figure it out. Tried most options , ready man pages.

---

### Post by taavikko on 2010-06-05
> **VMC said:**
> How do you get mplayer to play video folder VIDEO_TS to play like a DVD video player would. Change titles, menu options, etc. I can't figure it out. Tried most options , ready man pages.

Haven't used mplayer to play DVD's
/* only mlayer-nogui installed */
So can't answer to the part concerning menu's and such, sorry.

altough mplayer plays the VIDEO_TS folder nicely.
```
mplayer /path/to/VIDEO_TS/ dvd://1
```

there's options like "-alang DE" to use specified subs/language


edit:// excuse me and apologies, housewarming party going on...

---

### Post by mc4man on 2010-06-05
> How do you get mplayer to play video folder VIDEO_TS to play like a DVD video player would. Change titles, menu options, etc.

Well dvdnav is a bit of a pita in mplayer and can be affected by the build.

Not exactly sure what the keypad controls for the version used in maverick are - seeing as it's 15+ months old have no intention of ever using. (yet another crappy mplayer build in ubuntu

You may have better luck getting smplayer set up and using that to try dvdnav.

EDIT; went ahead and tried the mplayer build in maverick - no dvdnav available

Generally speaking for a VIDEO_TS and cli dvdnav you'd go..

mplayer  -dvd-device /path/to/VIDEO_TS -dvdangle [COLOR="Blue"]1[/COLOR] -nocache dvdnav://

As far as controls - using a recent build they are working here from keypad


> KP8 dvdnav 1            # DVDNav UP
KP2 dvdnav 2            # DVDNav DOWN
KP4 dvdnav 3            # DVDNav LEFT
KP6 dvdnav 4            # DVDNav RIGHT
KP5 dvdnav 5            # DVDNav MENU
KP_ENTER dvdnav 6       # DVDNav SELECT (ok)
KP7 dvdnav 7            # DVDNav PREVIOUS menu (in the order chapter->title->root)


On a laptop here there is no 'KP - Enter' so needed to re-map in ~.mplayer/input.conf like this
> ESC pt_step 1 1
ENTER dvdnav 6

Also note there are continuing issues with 5.1 streams, (at least from cli), you need to go -channels 6 and then cycle thru the audio stream once movie has started to get true 5.1 output, if one has 5.1 sound system

======================================
The latest ffmpeg-extras were built awile ago - not sure that they've made it into multiverse repo yet
[https://launchpad.net/ubuntu/+source/ffmpeg-extra/4:0.6~svn20100505-1ubuntu5](https://launchpad.net/ubuntu/+source/ffmpeg-extra/4:0.6~svn20100505-1ubuntu5)

Edit:
As far as gstreamer - 
the only thing missing are the 'bad plugins'..
The bad provides dvd_video playback (no big loss), aac decoding, mms/mmsh streams and a few other things - 

Otherwise all audio streams should decode fine and video that doesn't contain an aac stream or mpeg2 in dvd_video format.

---

### Post by zika on 2010-06-06
> **taavikko said:**
> totem requires gstreamer0.10-plugin-bad to work...
which at the moment can't be installed due to dependancy errors.

VLC should work out of the box

mplayer works without the lib*-extra-* from ffmpeggst came throgh, bad and good, but Totem still asks for h.264 (or sometnihg like that) ...

---

### Post by taavikko on 2010-06-06
> **zika said:**
> gst came throgh, bad and good, but Totem still asks for h.264 (or sometnihg like that) ...

Hmmm...
```
@vaio:~$ totem Desktop/Boys_hockey_game.mp4 
(gst-plugin-scanner:8170): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstpostproc.so': libavutil.so.49: cannot open shared object file: No such file or directory

(gst-plugin-scanner:8170): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstffmpeg.so': libavutil.so.49: cannot open shared object file: No such file or directory

(gst-plugin-scanner:8170): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstffmpegscale.so': libavutil.so.49: cannot open shared object file: No such file or directory
** Message: Missing plugin: gstreamer|0.10|totem|MPEG-4 Video decoder|decoder-video/mpeg, mpegversion=(int)4, parsed=(boolean)true, systemstream=(boolean)false (MPEG-4 Video decoder)
** Message: Missing plugin: gstreamer|0.10|totem|MPEG-4 Video decoder|decoder-video/mpeg, mpegversion=(int)4, parsed=(boolean)true, systemstream=(boolean)false (MPEG-4 Video decoder)
```

---

### Post by taavikko on 2010-06-06
> **taavikko said:**
> Hmmm...
```
@vaio:~$ totem Desktop/Boys_hockey_game.mp4 
(gst-plugin-scanner:8170): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstpostproc.so': libavutil.so.49: cannot open shared object file: No such file or directory

(gst-plugin-scanner:8170): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstffmpeg.so': libavutil.so.49: cannot open shared object file: No such file or directory

(gst-plugin-scanner:8170): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstffmpegscale.so': libavutil.so.49: cannot open shared object file: No such file or directory
** Message: Missing plugin: gstreamer|0.10|totem|MPEG-4 Video decoder|decoder-video/mpeg, mpegversion=(int)4, parsed=(boolean)true, systemstream=(boolean)false (MPEG-4 Video decoder)
** Message: Missing plugin: gstreamer|0.10|totem|MPEG-4 Video decoder|decoder-video/mpeg, mpegversion=(int)4, parsed=(boolean)true, systemstream=(boolean)false (MPEG-4 Video decoder)
```

Yes,
by removing contents of ~/.gstreamer-0.10/
and installing libavutil49 mpeg4 videos work.
/* replacing the libavutil-extra-49 */

libavutil-extra-49 is still missing the shared objects.
And not all apps are not patched to use libavutil-extra-50

---

### Post by zika on 2010-06-06
> **taavikko said:**
> Yes,
by removing contents of ~/.gstreamer-0.10/
and installing libavutil49 mpeg4 videos work.
/* replacing the libavutil-extra-49 */

libavutil-extra-49 is still missing the shared objects.
And not all apps are not patched to use libavutil-extra-50Now I'm really confused: should I have libav* installed or libav*-extra-*... ?
I'm talking about:
libavcodec{52, -extra-52}
libavdevice{52, -extra-52}
libavfilter{1, -extra-1}(is the other needed?: {0, -extra-0})
libavutil{{49,52}, -extra-{49,52}}
libavformat{52, -extra-52}
libpostproc{51, -extra-51}
libswscale{0, -extra-0}

Bingo! With "ordinary" installed and with refreshed registry it works, finally. Thank You!...

---

### Post by taavikko on 2010-06-06
> **zika said:**
> Now I'm really confused: should I have libav* installed or libav*-extra-*... ?
I'm talking about:
libavcodec{52, -extra-52}
libavdevice{52, -extra-52}
libavfilter{1, -extra-1}(is the other needed?: {0, -extra-0})
libavutil{{49,52}, -extra-{49,52}}
libavformat{52, -extra-52}
libpostproc{51, -extra-51}
libswscale{0, -extra-0}

Bingo! With "ordinary" installed and with refreshed registry it works, finally. Thank You!...

What I have installed...

```
dpkg -l libavcodec* libavutil* libavdevice* libavfilter* libavformat* libswscale* libpostproc* | grep ^ii
ii  libavcodec-extra-52                    4:0.6~svn20100505-1ubuntu5                      ffmpeg codec library
ii  libavdevice52                          4:0.6~svn20100505-1ubuntu2                      ffmpeg device handling library
ii  libavfilter1                           4:0.6~svn20100505-1ubuntu2                      ffmpeg video filtering library
ii  libavformat-extra-52                   4:0.6~svn20100505-1ubuntu5                      ffmpeg file format library
ii  libavutil-extra-50                     4:0.6~svn20100505-1ubuntu5                      ffmpeg utility library
ii  libavutil49                            4:0.5.1-1ubuntu1                                ffmpeg utility library
ii  libpostproc51                          4:0.6~svn20100505-1ubuntu2                      ffmpeg video postprocessing library
ii  libswscale-extra-0                     4:0.6~svn20100505-1ubuntu5                      ffmpeg video scaling library

```

---

### Post by zika on 2010-06-06
> **taavikko said:**
> What I have installed...

```
dpkg -l libavcodec* libavutil* libavdevice* libavfilter* libavformat* libswscale* libpostproc* | grep ^ii
ii  libavcodec-extra-52                    4:0.6~svn20100505-1ubuntu5                      ffmpeg codec library
ii  libavdevice52                          4:0.6~svn20100505-1ubuntu2                      ffmpeg device handling library
ii  libavfilter1                           4:0.6~svn20100505-1ubuntu2                      ffmpeg video filtering library
ii  libavformat-extra-52                   4:0.6~svn20100505-1ubuntu5                      ffmpeg file format library
ii  libavutil-extra-50                     4:0.6~svn20100505-1ubuntu5                      ffmpeg utility library
ii  libavutil49                            4:0.5.1-1ubuntu1                                ffmpeg utility library
ii  libpostproc51                          4:0.6~svn20100505-1ubuntu2                      ffmpeg video postprocessing library
ii  libswscale-extra-0                     4:0.6~svn20100505-1ubuntu5                      ffmpeg video scaling library

```

```
:~$ dpkg -l libavcodec* libavutil* libavdevice* libavfilter* libavformat* libswscale* libpostproc* | grep ^ii
ii  libavcodec52                                      4:0.6~svn20100505-1ubuntu2                                          ffmpeg codec library
ii  libavdevice52                                     4:0.6~svn20100505-1ubuntu2                                          ffmpeg device handling library
ii  libavfilter1                                      4:0.6~svn20100505-1ubuntu2                                          ffmpeg video filtering library
ii  libavformat52                                     4:0.6~svn20100505-1ubuntu2                                          ffmpeg file format library
ii  libavutil49                                       4:0.5.1-1ubuntu1                                                    ffmpeg utility library
ii  libavutil50                                       4:0.6~svn20100505-1ubuntu2                                          ffmpeg utility library
ii  libpostproc51                                     4:0.6~svn20100505-1ubuntu2                                          ffmpeg video postprocessing library
ii  libswscale0
```
I see that You have a mix of "ordinary" and "extra". How do You pick?

---

### Post by taavikko on 2010-06-06
> **zika said:**
> 
I see that You have a mix of "ordinary" and "extra". How do You pick?

I don't pick :)

libavcodec-extra is installed by hand only...
I don't install restricted-extras meta-package, only few things I need from it.
The other ones are brought by some other packages.
The above is a little mixed cause trying to get the libraries to work :)

---

### Post by zika on 2010-06-06
> **taavikko said:**
> I don't install restricted-extras meta-packageDitto. Mainly because of 64-bit Flash plugin and (before it became official) 64-bit Java plugin...

---

### Post by mc4man on 2010-06-06
You are making this more complicated than needed

The ffmpeg extra libs only add encoding support, not decoding.
The same for the gstreamer multiverse plugins

So as it stands now gstreamer works fine **with everything as far as decoding **now that the bad plugin has been redone.

If you wish to use the extra ffmpeg libs than anything less than these vesrsions may be borked in some manner

> libavcodec-extra-52_0.6~svn20100505-1ubuntu5_i386.deb
libavformat-extra-52_0.6~svn20100505-1ubuntu5_i386.deb
libavutil-extra-50_0.6~svn20100505-1ubuntu5_i386.deb
libpostproc-extra-51_0.6~svn20100505-1ubuntu5_i386.deb
libswscale-extra-0_0.6~svn20100505-1ubuntu5_i386.deb



---

### Post by taavikko on 2010-06-06
> **mc4man said:**
> You are making this more complicated than needed

The ffmpeg extra libs only add encoding support, not decoding.
The same for the gstreamer multiverse plugins


Yup, I do need them for converting my son's hockey games (avchd) material to more convenient format, via openshot (very nice app)

So some of the responses are getting mixed up :)

---

### Post by mc4man on 2010-06-06
> So some of the responses are getting mixed up

Same here - I just noticed the ...ubuntu5 versions are now in the repo for the extras - weren't last night at least here.

So it looks like gstreamer is pretty good now, some 3rd party players will benefit from a rebuild and or upgrade like vlc, mplayer remains a disappointment, particularly if on a 64 bit system.

(I'm going to file a bug on mplayer though the odds are the  response will not be positive

---

### Post by VMC on 2010-06-06
Thanks taavikko & mc4man for your responses regarding mplayer. I couldn't get it to work like I wanted. I found vlc to work perfectly. I just "drop" any *VIDEO_TS* folder into vlc and then I can watch any title on the copied dvd.

I could get mplayer to work by "dropping" indivual *VTS_01_0.IFO* files, but I wanted to be able to select any title by itself.

---

### Post by mc4man on 2010-06-06
> I found vlc to work perfectly. 

vlc is much better at dvd nav. than mplayer and at this point any other available player.

The only thing close was totem-xine which was discontinued (though I've keep it alive for karmic and  lucid, am going to try a maverick build just to see if possible.

---

### Post by yelo3 on 2010-06-06
I still can't play DivX MPEG-4 version 5 in totem, and it finds no decoder in the codec search. What about you?

---

### Post by zika on 2010-06-06
> **mc4man said:**
> You are making this more complicated than needed

The ffmpeg extra libs only add encoding support, not decoding.
The same for the gstreamer multiverse plugins

So as it stands now gstreamer works fine **with everything as far as decoding **now that the bad plugin has been redone.

If you wish to use the extra ffmpeg libs than anything less than these vesrsions may be borked in some mannerThanks!
No, I do not want to use "extra" more than anything else, I, just, wanted movies to work. Now I'm OK...

---

### Post by mc4man on 2010-06-06
> still can't play DivX MPEG-4 version 5 in totem

No issue here with that or any supported audio/video.

Make sure these plugins are installed

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

Then maybe open up home folder -> .gstreamer-0.10 and just delete the registry.bin file(s) inside, then try totem again.

or run command as posted here 
[http://ubuntuforums.org/showthread.php?t=1495980&page=3](http://ubuntuforums.org/showthread.php?t=1495980&page=3) #29

---

### Post by yelo3 on 2010-06-06
thanks!

---

### Post by moviemaniac on 2010-06-06
After figuring out a mess with different versions of avutil I got it working again too. However I am still lacking creation of new video thumbnails in Gnome. Can anyone confirm this?

---

### Post by pferraro on 2010-06-06
> **moviemaniac said:**
> After figuring out a mess with different versions of avutil I got it working again too. However I am still lacking creation of new video thumbnails in Gnome. Can anyone confirm this?

Aha!  That was my problem too.  libmoon was pulling in an older version of avutil - so I removed it for now, until it gets rebuilt against the new version.

---

### Post by VMC on 2010-06-06
> **yelo3 said:**
> With a recent update I figured out that I couldn't play any DIVX file with either totem and vlc.

After re-discovering VLC, I just tried a sample Divx avi file and it played great. I'm amazed at all the codecs that VLC brings with it. All my music mp3 files, dvd movie files , and now Divx files play perfectly.

---

### Post by dinamic1 on 2010-06-06
[IMG]http://img697.imageshack.us/img697/4523/screenshotpg.jpg[/IMG]

---

### Post by bahubindu on 2010-06-07
Installing correct versions of libavcodec does the trick. More info here: [http://www.khattam.info/2010/06/07/solved-media-playing-issues-in-ubuntu-10-10-maverick-meerkat/](http://www.khattam.info/2010/06/07/solved-media-playing-issues-in-ubuntu-10-10-maverick-meerkat/)

---

