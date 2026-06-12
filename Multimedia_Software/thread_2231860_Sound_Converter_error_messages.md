---
title: "Sound Converter error messages"
date: 2014-06-28
forum: Multimedia Software
---

### Post by J Tinsby on 2014-06-28
Using Synaptic I installed the Sound Convertor program. When I try to convert a file I get 2 messages on screen;

1/ Required plug-in could not be found ( see screen shot )

2/ Failed to install plug-ins                 ( see screen shot )

I thought I got all the necessary codecs with the install but obviously not, what do I need to make the program work?

Thanks!

J T

---

### Post by Yellow Pasque on 2014-06-28
Soundconverter is still using the old gstreamer (0.10). For full functionality, you can install gstreamer0.10-plugins-ugly package as well as getting the old gstreamer0.10-ffmpeg package from a PPA, such as :  [https://launchpad.net/~mc3man/+archive/trusty-media](https://launchpad.net/~mc3man/+archive/trusty-media)

---

### Post by J Tinsby on 2014-06-29
> **Temüjin said:**
> Soundconverter is still using the old gstreamer (0.10). For full functionality, you can install gstreamer0.10-plugins-ugly package as well as getting the old gstreamer0.10-ffmpeg package from a PPA, such as :  [https://launchpad.net/~mc3man/+archive/trusty-media](https://launchpad.net/~mc3man/+archive/trusty-media)

I already have the gstreamer0.10-plugins-ugly package installed. But the second one gives me an error message as below. I'm sure I am doing something wrong but dunno what it is. Never having used a PPA before this, may be part of the problem. Good chance I tried to install the wrong one :/

Got to the terminal where I get this description:

fred@fred-CAUS:~$ sudo add-apt-repository ppa:mc3man/trusty-media 
[sudo] password for fred: 
 Upgraded, advanced or not normally available multimedia packages for Trusty

A few notes:
gstreamer0.10-ffmpeg - needed for some apps that still use gstreamer-0.10 & also provides h.264 in html5 decoding for firefox < 30.
Note that Firefox 30 will support h.264 in html5 thru gstreamer1.0-libav & should be available soon

Totem+grilo - it's quite possible this & RB+grilo will show in 14.04 by first point release, if so will probably remove. Also note some plugins work well, some don't at all, bit of a mess

rhythmbox+grilo - needs to be enabled in rhythmbox > tools > plugins
Plus install grilo-plugins if not already

mpv - described here, add. info links
[https://launchpad.net/~mc3man/+archive/mpv-tests](https://launchpad.net/~mc3man/+archive/mpv-tests)
The mpv build in this ppa uses quvi0.9, the above linked ppa quvi0.4

*Note* - Osc config options now go into ~/.mpv/lua-settings/osc.config
refer to manpage or pdf in /usr/share/doc/mpv

mplayer - described here, note mencoder is not inc. & likely will not be, you may be able to use repo mencoder..
[https://launchpad.net/~mc3man/+archive/mplayer-test](https://launchpad.net/~mc3man/+archive/mplayer-test)

fdkaac (fdkaac-encoder) - described here
[https://launchpad.net/~mc3man/+archive/fdkaac-encoder](https://launchpad.net/~mc3man/+archive/fdkaac-encoder)

x264 - for use with ffmpeg from here, supports both 8 & 10 bit encoding

ffmpeg -
a static build for use of the binaries, installed to /opt/ffmpeg
binaries are symlinked in /usr/bin (ffmpeg, ffplay, ffprobe

For info on using libfdk_aac see here -
[http://trac.ffmpeg.org/wiki/Encode/AAC](http://trac.ffmpeg.org/wiki/Encode/AAC)

Can be used for both 8 & 10 bit x264 encoding with this ppa's libx264, default is 8
For 10 bit preload the 10 bit .so first in terminal, eg.,
export LD_PRELOAD=/usr/lib/x86_64-linux-gnu/x264-10bit/libx264.so.142
or
export LD_PRELOAD=/usr/lib/i386-linux-gnu/x264-10bit/libx264.so.142

You can use the install for building against if source accepts statically linking
To try - install build deps of ffmpeg in addition to source being builtgstreamer0.10-ffmpeg
At terminal build prompt set env paths, usually just this will suffice
 export PKG_CONFIG_PATH=/opt/ffmpeg/lib/pkgconfig
 export LIBRARY_PATH=/opt/ffmpeg/lib

libav - has fdkaac encoding enabled

yasm -
 has been patched to improve compiling x265

I also recommend for gstreamer & vlc  users checking out this ppa for h265 support in gst & a vlc plugin (vlc-libde265
[https://launchpad.net/~strukturag/+archive/libde265](https://launchpad.net/~strukturag/+archive/libde265)

For rhythmbox users a wide range of plugins can be found here -
[https://launchpad.net/~fossfreedom/+archive/rhythmbox-plugins](https://launchpad.net/~fossfreedom/+archive/rhythmbox-plugins)
fred@fred-CAUS:~$ sudo add-apt-repository ppa:mc3man/trusty-media 
[sudo] password for fred: 
 Upgraded, advanced or not normally available multimedia packages for Trusty

A few notes:
gstreamer0.10-ffmpeg - needed for some apps that still use gstreamer-0.10 & also provides h.264 in html5 decoding for firefox < 30.
Note that Firefox 30 will support h.264 in html5 thru gstreamer1.0-libav & should be available soon

Totem+grilo - it's quite possible this & RB+grilo will show in 14.04 by first point release, if so will probably remove. Also note some plugins work well, some don't at all, bit of a mess

rhythmbox+grilo - needs to be enabled in rhythmbox > tools > plugins
Plus install grilo-plugins if not already

mpv - described here, add. info links
[https://launchpad.net/~mc3man/+archive/mpv-tests](https://launchpad.net/~mc3man/+archive/mpv-tests)
The mpv build in this ppa uses quvi0.9, the above linked ppa quvi0.4

*Note* - Osc config options now go into ~/.mpv/lua-settings/osc.config
refer to manpage or pdf in /usr/share/doc/mpv

mplayer - described here, note mencoder is not inc. & likely will not be, you may be able to use repo mencoder..
[https://launchpad.net/~mc3man/+archive/mplayer-test](https://launchpad.net/~mc3man/+archive/mplayer-test)

fdkaac (fdkaac-encoder) - described here
[https://launchpad.net/~mc3man/+archive/fdkaac-encoder](https://launchpad.net/~mc3man/+archive/fdkaac-encoder)

x264 - for use with ffmpeg from here, supports both 8 & 10 bit encoding

ffmpeg -
a static build for use of the binaries, installed to /opt/ffmpeg
binaries are symlinked in /usr/bin (ffmpeg, ffplay, ffprobe

For info on using libfdk_aac see here -
[http://trac.ffmpeg.org/wiki/Encode/AAC](http://trac.ffmpeg.org/wiki/Encode/AAC)

Can be used for both 8 & 10 bit x264 encoding with this ppa's libx264, default is 8
For 10 bit preload the 10 bit .so first in terminal, eg.,
export LD_PRELOAD=/usr/lib/x86_64-linux-gnu/x264-10bit/libx264.so.142
or
export LD_PRELOAD=/usr/lib/i386-linux-gnu/x264-10bit/libx264.so.142

You can use the install for building against if source accepts statically linking
To try - install build deps of ffmpeg in addition to source being built
At terminal build prompt set env paths, usually just this will suffice
 export PKG_CONFIG_PATH=/opt/ffmpeg/lib/pkgconfig
 export LIBRARY_PATH=/opt/ffmpeg/lib

libav - has fdkaac encoding enabled

yasm -
 has been patched to improve compiling x265

I also recommend for gstreamer & vlc  users checking out this ppa for h265 support in gst & a vlc plugin (vlc-libde265
[https://launchpad.net/~strukturag/+archive/libde265](https://launchpad.net/~strukturag/+archive/libde265)

For rhythmbox users a wide range of plugins can be found here -
[https://launchpad.net/~fossfreedom/+archive/rhythmbox-plugins](https://launchpad.net/~fossfreedom/+archive/rhythmbox-plugins)

An excellent  audio recorder is available here -
[https://launchpad.net/~osmoma/+archive/audio-recorder](https://launchpad.net/~osmoma/+archive/audio-recorder)
 More info: [https://launchpad.net/~mc3man/+archive/trusty-media](https://launchpad.net/~mc3man/+archive/trusty-media)
Press [ENTER] to continue or ctrl-c to cancel adding it


An excellent  audio recorder is available here -
[https://launchpad.net/~osmoma/+archive/audio-recorder](https://launchpad.net/~osmoma/+archive/audio-recorder)
 More info: [https://launchpad.net/~mc3man/+archive/trusty-media](https://launchpad.net/~mc3man/+archive/trusty-media)
Press [ENTER] to continue or ctrl-c to cancel adding it

I am NOT sure if I hit ENTER do I get all the items listed, including the gstreamer0.10-ffmpeg listed near the very top of it all? Right now I am choosing ctrl-c to be safe!
Or do I have to use a sudo apt-get install gstreamer0.10-ffmpeg to just get that file or package? 

Apologies for using so much real estate with that capture from the terminal, I didn't know how else to do it.



J T

---

### Post by Yellow Pasque on 2014-06-29
Is there a reason you're trying to install the -dbg package? Did you add the PPA to your sources or are you trying to download/install the package individually?
What is output of:
```
sudo apt-get install gstreamer0.10-ffmpeg
```

---

### Post by J Tinsby on 2014-06-29
No reason except ignorance of what to do.

fred@fred-CAUS:~$ sudo apt-get install gstreamer0.10-ffmpeg
[sudo] password for fred: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gstreamer0.10-ffmpeg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gstreamer0.10-ffmpeg' has no installation candidate
fred@fred-CAUS:~$

I did get another file 

[LIST]
[*]       [gstreamer0.10-ffmpeg_0.10.13-5ubuntu1~trusty2.debian.tar.gz]("https://launchpad.net/%7Emc3man/+archive/trusty-media/+files/gstreamer0.10-ffmpeg_0.10.13-5ubuntu1%7Etrusty2.debian.tar.gz")          (11.4 KiB)and have it on the desktop, if i extract it will it go to the right place or must I tell it what path to use?
[/LIST]

---

### Post by J Tinsby on 2014-06-29
fred@fred-CAUS:~$ sudo apt-get install gstreamer0.10-ffmpeg
[sudo] password for fred: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gstreamer0.10-ffmpeg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gstreamer0.10-ffmpeg' has no installation candidate
fred@fred-CAUS:~$

---

### Post by Yellow Pasque on 2014-06-29
Did you run 'sudo apt-get update' after adding the PPA?

Note: debian.tar.gz only has the packaging information. It's probably not what you want...

---

### Post by J Tinsby on 2014-06-29
> **Temüjin said:**
> Did you run 'sudo apt-get update' after adding the PPA?

Note: debian.tar.gz only has the packaging information. It's probably not what you want...

Update:

On the next boot, it installed the file I needed and is working OK now! Stands to reason that it would, after sitting here typing away trying to explain what was going on! lol

 Makes me wonder about these PPA's and how safe they are, if they are made by individuals....

Thanks temujin!

J T

---

### Post by mc4man on 2014-06-29
> **J Tinsby said:**
> 
 Makes me wonder about these PPA's and how safe they are, if they are made by individuals....
J T

On ppa's in general & specific to that one.

For any ppa, particularly those with multiple sources, app packages,  I would not use a cli upgrade (sudo apt-get upgrade
Better to go to ppa page, see what's there, read any info, ect. ( on a ppa page if you click on "Show package details" you can then expand any package listing to see current changelogs for add. info 

Synaptic is usually the best way to deal with ppa's that have diverse sources - 
Status > Installed (upgradeable) will show packages you currently have that could be upgraded
Origin > there will be 2 listings for a ppa, the 1st. one shows what is installed from that ppa, the 2nd shows all available packages 

With any ppa always pay attention if installing or upgrading requires removing existing packages other than what's being upgraded. Sometimes it's necessary & of no issue, sometimes may cause issues.

In regards to that ppa, it's mine & I assure you all packages have been pre-tested by me to whatever extent & time possible.
You are not 'required' to upgrade all that's in there, you can pick & choose.
If the 0.10 gstreamer plugin is all you wanted then after installing go ahead & disable/remove the ppa,  there is little likelihood I'll be updating that package.
If you do use anything else & experience issue then use launchpad email (requires launchpad account) & I'll see what's up & adjust if possible/as needed

---

