---
title: "Best music playback software."
date: 2014-12-20
forum: Multimedia Software
---

### Post by warren3 on 2014-12-20
Hi.

I am looking for a nice music program to play FLAC's on.  Any recommendations?

Thanks.

---

### Post by sudodus on 2014-12-20
There are many alternatives in linux - try them and select the one you like the best. You can start with what comes with your flavour of Ubuntu, and then install some of the other alternatives. You can use audio-only programs as well as programs that can play video too, for example vlc.

```
sudo apt-get install vlc
```

Edit: You may wish to install the restricted extras to get more codecs and other tools for music and multimedia (including flashplayer - flashplugin-installer)

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Yellow Pasque on 2014-12-20
I like audacious with crystalizer plugin. Of course, if you prefer something with more "library" focus, there is clementine.

---

### Post by shantiq on 2014-12-22
as library player Clementine is now EXCELLENT!   with **delta plugin**

```
sudo apt-get install clementine
```

```
sudo add-apt-repository ppa:decatf/testy 

``` ```
sudo apt-get update && sudo apt-get install delta
``` 
   
need to go down to "raring" in software-properties-gtk/other software for the delta add-on
then do

```
gconftool –type string –set /system/gstreamer/0.10/default/musicaudiosink “delta gain=100 ! autoaudiosink”

```

and in clementine go to tools/preferences and pick GSettings audio sink
   




**As ad hoc player XMMS or Audacious **[COLOR=#000000][B]with crystalizer plugin
[/B] 


[Xmms]("http://ubuntuforums.org/showthread.php?t=1525072&highlight=xmms+shantiq") install on 14.04   [no longer maintained but still best sound ever]
=============


[/COLOR]

```
sudo add-apt-repository ppa:ibid-ag/oldgtk1 
sudo apt-get update

```



run


```
 software-properties-gtk



```

then

change both ibid lines to lucid
and also while there add:


```
deb http://www.pvv.ntnu.no/~knuta/xmms/karmic ./



``````
deb-src http://www.pvv.ntnu.no/~knuta/xmms/karmic ./



```

and tick all of these new ones in software center and close ; it will reload and therefore update
=====

then

```
sudo apt-get build-dep libglib1.2-dev



```happy with enough dependencies by then it should be ....

and then for xmms and plugins from ibidem

```
sudo apt-get install xmms   xmms-cueinfo xmms-mp4plugin   xmms-wavpack



```

if you want to play flac 

```
sudo apt-get install flac
``` ; then install [flac deb]("http://ubuntuforums.org/attachment.php?attachmentid=205283&d=1319398314")  64-bit

you may need to move libxmms-flac.so manually from


```
sudo cp /usr/lib64/xmms/Input/libxmms-flac.so  /usr/lib/xmms/Input

```[COLOR=#000000]


[/COLOR]

---

### Post by Rob Sayer on 2014-12-22
I second the Clementine recommendaton but I have no intention of installing the delta plugin.  A quick look gave me ...

[https://github.com/clementine-player/Clementine/issues/4586](https://github.com/clementine-player/Clementine/issues/4586)

... which doesn't sound promising.  I'm not going to install a 3rd party ppa ... which can lead to breakage during an update in case the OP didn't know this ... for a program available in the repos anyway.  Forget it.

Besides I don't want to use gstreamer plugins or any software that require them anymore.  I don't feel the quality is great and it's particularly obtuse even by Linux audio standards.  I used to run Kubuntu and it used it as a default backend.  I could never get the audio quality the way I wanted it.  SOmething in there I could never find was resampling to 48K probably.  ANd gstreamer isn't all that well documented.

Linux audio is convoluted enough already.  It's the only thing about linux I find just isn't straightforward enough.  I just use alsa or pulseaudio, depending on the app.  I've found audio software tends to work better with one or the other.  In Kubuntu 12.04 I found the alsa module worked best.  In Cinnamon (which is gtk) it prefers pulse.  In fact I'm gettng better sound now from clementine out of the box than I could *ever* get in KDE.

One thing that surprised me when I finally installed linux a few years ago is just how dang many music playng programs there are for linux.  I think some guy writes one every week.  So I 

Clementine is still the one I mostly use because it has the playlist features I need.  You can get very good playback quality too.

VLC is actually an excellent audio player too, and has very good playlist design too.  But I don't use it much for music in linux.  In windows ... which I no longer use ... it's my favorite.

I also use Audacious because it's so fast to load and you can set it up to give you good quality easily.  If I just want to play a track file or an album folder I'll open them in audacity from file manager rather than load clementine.  But audacity doesn't have the playlist capability.  Neither does anything else I've found except vlc.

There's a ridiculous number of linux music players, which surprised me.  It could be confusing for sure.  I don't see the need to install anything that's not in the repos.

If you're looking for flac playback you probably want max audio quality.  In absolute terms that means no processing plugins if you want to take a purist approach.  I never use them.  I don't even use any software volume controls for music.  Definitely no eq.  And resampling to 44.1K to 48K is the default in linux just like windoze.  A PITA, and there's no Wasapi driver equivalent for linux.  I just edit the alsa config to set the dmix default to 44100.  Pulse already default to 44.1.  I don't care if I lose audio quality in videos.

---

### Post by Yellow Pasque on 2014-12-22
First off, Audacious and Audacity are different programs. ;)

The link you give is talking about a different "delta." If you really don't trust PPA's, you can build the delta plugin yourself and either put it in /usr/local or use checkinstall to make your own .deb. Then, if you try it out and decide you don't like it, it's easy to remove/uninstall.

> In fact I'm gettng better sound now from clementine out of the box than I could ever get in KDE.
KDE is a desktop environment. There's no difference between running Clementine in KDE and running it in Unity/Gnome (it's still a gstreamer program).

> no processing plugins if you want to take a purist approach. I never use them.
I've found that most DSP plugins are really glorified ways to induce clipping and/or overdrive the speakers. The delta plugin (called "crystalizer" in Audacious or "Noise sharpening" in foobar2000) is an exception.

> And resampling to 44.1K to 48K is the default in linux just like windoze
Most distros are using pulse nowadays, which I think defaults to 44.1k (as you've noted). Pulse's resampling can be minimized if you enable the alternate sample rate in /etc/pulse/daemon.conf. If you start playing 44.1k audio and then play a 48k video at the same time, it will still resample the video, but if you just play things one at a time, it will not resample if you uncomment the lines:
```
 default-sample-rate = 44100
alternate-sample-rate = 48000
```

---

