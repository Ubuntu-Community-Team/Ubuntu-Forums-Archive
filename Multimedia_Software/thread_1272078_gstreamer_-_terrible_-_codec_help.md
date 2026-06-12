---
title: "gstreamer - terrible - codec help?"
date: 2009-09-21
forum: Multimedia Software
---

### Post by aidevelopment on 2009-09-21
Hey All,

I'm a long time Red Hat / Fedora user. I've resisted Ubuntu (Debian) for the longest time,but need to use it for work. I have my system set up the way I want, except for one thing. 

I can't get codecs to work very well for the life of me. Perhaps I just need the right package?

Flash, and Java are installed great. I installed gstreamer, which works, but sound and video are very choppy/laggy. 

Any suggestions on how to get smooth / proper sound and video running?

Gstreamer:
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse

Kernel:
2.6.28-15-generic #49-Ubuntu SMP i686 GNU/Linux

aidevelopment[at]gmail[dot]com

Thanks!

---

### Post by cor2y on 2009-09-21
You didnt say which codecs, so what you can do if you are tied to using gstreamer with totem and not totem-xine, smplayer or vlc is install these gstreamer plugins (make sure to enable all your ubuntu repos first)

gstreamer0.10-ffmpeg
gstreamer0.10-fluendo-mp3
gstreamer0.10-fluendo-mpegdemux
gstreamer0.10-fluendo-mpegmux
gstreamer0.10-pitfdll (for use with the w32codecs found in medibuntu)
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly

All these plugins should be automatically available for installation if gnome-app-install and gnome-codec-install are installed once totem or rhythmbox comes up files they cant play it should notify you about what gstreamer plugins you need and ask you if to install them.

Video Choppiness could be due to your video drivers, are you using nvidia drivers with compiz?
If yes what is the nvidia video card type and what version of drivers.
If you are not using a nvidia based card then what are your cpu specs?
Could be its because you are trying to play hidef video and your system cant handle it , in that case if you do have a nvidia card then vdpau could be used to fix that or you will have to ditch gstreamer and use mplayer/smplayer custom compiled with the Core AVC codec or dual or greater cpu support.

---

### Post by aidevelopment on 2009-09-21
Thanks cor2y. I'll give that a shot tomorrow, and update. Sorry for the lack of description, I'm really not an A/V guy :)

I've only tested m4a, and mpeg, both with the same choppiness/lagginess. I would have assumed the two packages I had would have contained the codecs. I'll search for the others, although I'm sure they didn't come up for me before. Maybe I need to find another repo.

Everything plays, just poorly. Even a youtube video for example, is not a smooth watch (which required m4a support). 

It is an nvidia card, only using compiz if it's installed by default. I'm sure it's not a matter of system performance though, as the windows virtual machine can handle it okay! 

Cheers

---

### Post by cor2y on 2009-09-21
That is peculiar, are you using the default open source drivers that come installed by default with kubuntu or the closed source nvidia binary drivers?
Since its nvidia and if you are using the closed source binary driver then you may need to edit compiz to get rid of the video tearing/choppiness.

Open Compiz Config Settings Manager (System->Preferences->Compiz Config Settings Manager) go to General Options->DIsplay Settings, uncheck Dectect Refresh Rate and manually set your refresh rate to TWICE what your monitor's refresh rate is example if its 60 set it to 120 also check Sync To VBlank in there.
In The Nvida X Server Settings App make sure Sync To VBlank is also checked under XServer XVideo Settings. Under OpenGl Settings make sure Sync To VBlank is NOT CHECKED.

That should take care of any choppiness with use of the closed binaries.
For video stuttering/slow down if thats a problem (mainly with hidef video playback depending on your cpu type) you will need to install a media player with vdpau support for hidef playback like smplayer/mplayer or totem-xine 
[http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625) [https://launchpad.net/~nvidia-vdpau/+archive/ppa]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa")

---

### Post by aidevelopment on 2009-09-22
Compiz is not in use, so I skipped that configuration part, nvidia xserver was set correctly though.

nvidia-glx-180 package (driver) on

$ lspci | grep nV
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 135M (rev a1)

The fluendo package, and the gstreamer bad packages are conflicting, so I went with gstreamer bad, given I had no audio at all on fluendo.

The other packages seemed to help out a bit, but I'm still hitting spikes. 
I looked in to the CPU, as you suggested, while doing a Youtube test.

cat /proc/cpuinfo | grep "model name"
model name      : Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz

Windows VM on the same box, shows the page with ~30% CPU utilization (1 core), whereas Kubuntu base uses 50-80% cpu utilization (both cores). I've confirmed that when the CPU pegs, is when playback gets choppy.

So, it looks like there's a bug/very poorly written package here.

Any further suggestions?

---

### Post by cor2y on 2009-09-22
OK you didnt say it was in conjunction with fluendo's full codec pack.
That could be the problem, yes it clashes with gstreamer-bad.
Fluendo shouldn't be giving you a lack of audio (unless its some esoteric audio codec in use), update your fluendo gstreamer package deb to 7.0 it now fully supports all its listed codecs (wmv,mpeg4 divx,h.264,wma pro, mp3 aac etc) If it was bought via the ubuntu store then you have the update free not to sure about the fluendo shop/site.

So lets see, i assume that you are doing flash based playback as you listed youtube as an example, even with fluendo installed and all the gstreamer plugins except bad, gstreamer cant handle some flash based media and most of the time doesnt do the rest very well.
I dont believe there is a flash based totem-gstreamer plugin so my guess is you problem with choppiness as relates to flash is with the flash plugin.
You will have to ditch the opensource implementations and only use the adobe based flash plugin which means removing these packages if you have them installed.

flashplugin-installer
flashplugin-nonfree-extrasound
gnash
swfdec-gnome
swfdec-mozilla
mozilla-plugin-gnash
libswfdec (any versions)

Once those are removed next install the 
adobe-flashplugin, remember to enable your multiverse, restricted and universe repos to see the package.

This is the only flash support you should have in use.

Now back to stand alone videos, you can try removing totem-gstreamer (this includes the gstreamer-mozilla plugin you should replace this with the mplayer-mozilla plugin really) completely and replace it with totem-xine and the xine plugins (excluding the xine-mozilla plugin) see how video playback is then with totem-xine as the default player.
xine plugins are
libxine1-ffmpeg
libxine1-gnome
libxine1-misc-plugins

Dont install xine-plugin which is the mozilla plugin.

---

### Post by aidevelopment on 2009-09-24
Hi cor2y,

Thanks again for your help so far. Just as an FYI, this is on hold a bit, as I've switched to a different laptop. 

Cheers!
Steve

---

