---
title: "Mpeg AAC decoder not found."
date: 2009-07-15
forum: Multimedia Software
---

### Post by cheesepenguins on 2009-07-15
Whilst trying to play certain video files on ubuntu 9.04 I can't get sound, the message I get from movie player is that "Mpeg4 AAC decoder" can't be found (whilst searching for the right codec).

This is really annoying me as the files worked fine a week or so ago, and I can't think of a reason for them to stop now.

Any packages that you think will allow audio would be great.

---

### Post by monraaf on 2009-07-15
gstreamer0.10-plugins-bad is probably what you need.

---

### Post by cheesepenguins on 2009-07-15
> **monraaf said:**
> gstreamer0.10-plugins-bad is probably what you need.

I already had that package, so I reinstalled it and still nothing, thanks for trying though. :)

---

### Post by SuperSonic4 on 2009-07-15
You may also need **faad** or **faad2** as these are the aac decoders

---

### Post by cheesepenguins on 2009-07-15
> **SuperSonic4 said:**
> You may also need **faad** or **faad2** as these are the aac decoders

faad is already on my system, this is really starting to puzzle me.

---

### Post by mc4man on 2009-07-15
I don't use gstreamer much but maybe check on your ffmpeg libs, search ffmpeg in synaptic and look to see if the un-stripped versions of libavcodec52,.ect are installed

If not then just mark them for install and apply (don't mark the current versions for uninstall, they will be replaced

For the gstreamer plug-ins, the most useful are
bad
bad-multiverse
ugly
ugly-multiverse
gstreamer-ffmpeg
pitfdll (enables use of w32codecs

They all do/enable different things

you'll see multiple listings for the bad and ugly, the 1st and 4th listed should be enabled

---

### Post by FakeOutdoorsman on 2009-07-15
> **mc4man said:**
> I don't use gstreamer much but maybe check on your ffmpeg libs, search ffmpeg in synaptic and look to see if the un-stripped versions of libavcodec52,.ect are installed

I believe the unstripped FFmpeg libraries will not provide any additional decoders, although it will provide some restricted encoders: h261, h263, h263p, libfaac, libmp3lame, libx264, libxvid, mpeg2video, mpeg4, msmpeg4, msmpeg4v1, and msmpeg4v2.  However, this is based on an Intrepid system.  Things may be different for Jaunty.

---

### Post by mc4man on 2009-07-15
> I believe the unstripped FFmpeg libraries will not provide any additional decoders

as mentioned don't use gstreamer apps, but a quick test with the default totem shows Mpeg-4 AAc is enabled with the gstreamer0.10-plugins-bad (first listed in synaptic


Edit:
while gstreamer doesn't break up the bad and ugly here's a list
[http://gstreamer.freedesktop.org/documentation/plugins.html](http://gstreamer.freedesktop.org/documentation/plugins.html)

---

### Post by cheesepenguins on 2009-07-16
Here is a screenshot of the Gstreamer plugins, ffmpeg, faad, and faac packages installed and the error from Totem as text.
```
(totem:15236): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstfaad.so': libfaad.so.0: cannot open shared object file: No such file or directory
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
** Message: don't know how to handle audio/mpeg, mpegversion=(int)4, framed=(boolean)true, codec_data=(buffer)131056e59d4800, channels=(int)2, rate=(int)48000
Segmentation fault

```

I'm really confused, I've reinstalled all the Gstreamer ones, faad, ffmpeg and faac in the past 24 hours, still nothing.

Going from the list posted above by mc4man the faad plugins required are in the bad plugin set, however I have that installed. 

(Again thanks for trying)

P.s. I'm quite new to the linux scene and nothing has really thrown me off so much as this has, it did work and then magically stopped working. I get sound through Mplayer, however I need Gstreamer to work as I would like to use Moovida media center and it runs on Gstreamer.

---

### Post by mc4man on 2009-07-16
A few things somewhat from afar (using hardy, the gstreamer plugins i have are rebuilt and installed from my local repo

There are many reported bugs in jaunty that concern totem, particularly with intel and some ati video. Your issue may lie there.

While the error reports audio why don't you see if you can or can't play a m4a (aac) audio file with a gstreamer app (totem and or rhythmbox

If you don't have an audio m4a/aac file then try this. Open up rhythmbox -> play queue and drop your mp4 video file into it. If the audio's playable rhythmbox will play it. (no video of course

While the aac audio is enabled by the plugin your showing installed and libfaad0, you're not showing the multiverse versions of bad and ugly, you should see them in synaptic, 4th listed for both. 
If not there or installed/ installable, then check your sources to make sure multiverse repo is enabled (System -> Admin, -> Software Sources, 4th listed under Ubuntu Software tab.

---

### Post by cheesepenguins on 2009-07-16
> **mc4man said:**
> A few things somewhat from afar (using hardy, the gstreamer plugins i have are rebuilt and installed from my local repo

There are many reported bugs in jaunty that concern totem, particularly with intel and some ati video. Your issue may lie there.

While the error reports audio why don't you see if you can or can't play a m4a (aac) audio file with a gstreamer app (totem and or rhythmbox

If you don't have an audio m4a/aac file then try this. Open up rhythmbox -> play queue and drop your mp4 video file into it. If the audio's playable rhythmbox will play it. (no video of course

While the aac audio is enabled by the plugin your showing installed and libfaad0, you're not showing the multiverse versions of bad and ugly, you should see them in synaptic, 4th listed for both. 
If not there or installed/ installable, then check your sources to make sure multiverse repo is enabled (System -> Admin, -> Software Sources, 4th listed under Ubuntu Software tab.

I tried to play an m4a file in Totem, it produces the same problem, so tried through Firefox using the gstreamer plugins and it gave the identical error. My Video card is Nvidia and I'm running the latest Nvidia drivers from June.

I have added the multiverse packages, still no difference. :(

List of Gstreamer packages installed.
```

sudo dpkg --get-selections | grep gstreamer
[sudo] password for m00z0r: 
gstreamer0.10-alsa				install
gstreamer0.10-esd				install
gstreamer0.10-ffmpeg				install
gstreamer0.10-fluendo-mp3			install
gstreamer0.10-gnomevfs				install
gstreamer0.10-pitfdll				install
gstreamer0.10-plugins-bad			install
gstreamer0.10-plugins-bad-multiverse		install
gstreamer0.10-plugins-base			install
gstreamer0.10-plugins-good			install
gstreamer0.10-plugins-ugly			install
gstreamer0.10-plugins-ugly-multiverse		install
gstreamer0.10-pulseaudio			install
gstreamer0.10-schroedinger			install
gstreamer0.10-sdl				install
gstreamer0.10-tools				install
gstreamer0.10-x					install
libgstreamer-plugins-base0.10-0			install
libgstreamer0.10-0				install
libgstreamer0.10-0-dbg				install
totem-gstreamer					install


```

---

### Post by monraaf on 2009-07-16
Your problem is this:

> **cheesepenguins said:**
> 
```
(totem:15236): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstfaad.so': libfaad.so.0: cannot open shared object file: No such file or directory

```


Can you give the output of this:

```

ldd /usr/lib/gstreamer-0.10/libgstfaad.so

```

and this:

```

ls -l /usr/lib/libfaad*

```

---

### Post by cheesepenguins on 2009-07-16
> **monraaf said:**
> Your problem is this:



Can you give the output of this:

```

ldd /usr/lib/gstreamer-0.10/libgstfaad.so

```

and this:

```

ls -l /usr/lib/libfaad*

```
Output of the first command:
```

<(o_O)>  ldd /usr/lib/gstreamer-0.10/libgstfaad.so
	linux-gate.so.1 =>  (0xb7f37000)
	libfaad.so.0 => not found
	libgstreamer-0.10.so.0 => /usr/lib/libgstreamer-0.10.so.0 (0xb7e59000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb7e1a000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb7d62000)
	libgstaudio-0.10.so.0 => /usr/lib/libgstaudio-0.10.so.0 (0xb7d40000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7d27000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7bc4000)
	libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0xb7bbd000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb7bb8000)
	libxml2.so.2 => /usr/lib/libxml2.so.2 (0xb7a7c000)
	librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb7a73000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7a6f000)
	libpcre.so.3 => /lib/libpcre.so.3 (0xb7a3c000)
	libgstbase-0.10.so.0 => /usr/lib/libgstbase-0.10.so.0 (0xb7a06000)
	libgstinterfaces-0.10.so.0 => /usr/lib/libgstinterfaces-0.10.so.0 (0xb79fa000)
	/lib/ld-linux.so.2 (0xb7f38000)
	libz.so.1 => /lib/libz.so.1 (0xb79e4000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb79be000)


```

And the second:
```

<(o_O)>  ls -l /usr/lib/libfaad*
-rw-r--r-- 1 root root 318198 2009-04-10 23:33 /usr/lib/libfaad.a
-rw-r--r-- 1 root root    806 2009-04-10 23:33 /usr/lib/libfaad.la
lrwxrwxrwx 1 root root     16 2009-07-16 00:22 /usr/lib/libfaad.so -> libfaad.so.2.0.0
lrwxrwxrwx 1 root root     16 2009-07-07 10:47 /usr/lib/libfaad.so.2 -> libfaad.so.2.0.0
-rw-r--r-- 1 root root 255196 2009-04-10 23:33 /usr/lib/libfaad.so.2.0.0

```

You think its a permission issue?

---

### Post by vinutux on 2009-07-16
is that files are working in vlc and other players ?

---

### Post by cheesepenguins on 2009-07-16
> **vinutux said:**
> is that files are working in vlc and other players ?

Files work fine in Mplayer, VLC crashes upon startup with the files that Totem can't play.

Moovida media center also fails to play the files and requests an Mpeg audio codec.

---

### Post by monraaf on 2009-07-16
I think it's a version issue. Maybe you got libfaad installed from some other repository?

Here's what I got:

```

/usr/lib/libfaad.so.0.0.0

```

Note this library has a different version number than yours.

I suggest removing all faad packages that you've got installed and use synaptic to install libfaad0 and select jaunty version.

---

### Post by vinutux on 2009-07-16
> **cheesepenguins said:**
> Files work fine in Mplayer, VLC crashes upon startup with the files that Totem can't play.

Moovida media center also fails to play the files and requests an Mpeg audio codec.

Are u installing  or updating anything new from other repos like mediubuntu, un-official sites, PPAs ........

---

### Post by vinutux on 2009-07-16
> **monraaf said:**
> I think it's a version issue. Maybe you got libfaad installed from some other repository?

Here's what I got:

```

/usr/lib/libfaad.so.0.0.0

```

Note this library has a different version number than yours.

I suggest removing all faad packages that you've got installed and use synaptic to install libfaad0 and select jaunty version.


That good 4 that open Synaptic select faad plugin pakage menu>force version and select jaunty version instead of current one.

---

### Post by cheesepenguins on 2009-07-16
> **monraaf said:**
> I think it's a version issue. Maybe you got libfaad installed from some other repository?

Here's what I got:

```

/usr/lib/libfaad.so.0.0.0

```

Note this library has a different version number than yours.

I suggest removing all faad packages that you've got installed and use synaptic to install libfaad0 and select jaunty version.

I removed all faad packages, which also removed some gstreamer ones, then chose libfaad0 in synaptic, here is my output, the version I chose is in the screenshot attached.

```

<(o_O)>  ldd /usr/lib/gstreamer-0.10/libgstfaad.so
	linux-gate.so.1 =>  (0xb80a9000)
	libfaad.so.0 => not found
	libgstreamer-0.10.so.0 => /usr/lib/libgstreamer-0.10.so.0 (0xb7fcc000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb7f8d000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb7ed5000)
	libgstaudio-0.10.so.0 => /usr/lib/libgstaudio-0.10.so.0 (0xb7eb3000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7e9a000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d37000)
	libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0xb7d30000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb7d2b000)
	libxml2.so.2 => /usr/lib/libxml2.so.2 (0xb7bef000)
	librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb7be6000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7be2000)
	libpcre.so.3 => /lib/libpcre.so.3 (0xb7baf000)
	libgstbase-0.10.so.0 => /usr/lib/libgstbase-0.10.so.0 (0xb7b79000)
	libgstinterfaces-0.10.so.0 => /usr/lib/libgstinterfaces-0.10.so.0 (0xb7b6d000)
	/lib/ld-linux.so.2 (0xb80aa000)
	libz.so.1 => /lib/libz.so.1 (0xb7b57000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7b31000)
<(o_O)>  ls -l /usr/lib/libfaad*
lrwxrwxrwx 1 root root     16 2009-07-16 20:19 /usr/lib/libfaad.so.2 -> libfaad.so.2.0.0
-rw-r--r-- 1 root root 255196 2009-04-10 23:33 /usr/lib/libfaad.so.2.0.0
<(o_O)>  


```

> **vinutux said:**
> Are u installing  or updating anything new from other repos like mediubuntu, un-official sites, PPAs ........
I have a few KDE packages kicking about mostly for Amarok, could this be a cause?

---

### Post by monraaf on 2009-07-16
The screenshot show's that you are using a PPA! You must select jaunty version.

---

### Post by cheesepenguins on 2009-07-16
> **monraaf said:**
> The screenshot show's that you are using a PPA! You must select jaunty version.

My mistake.

However I downgraded the one I installed in the screen shot from 2.7 to 2.6.1-3.1 and low and behold sound works again. 

Could you explain to me how I would go about selecting a Jaunty version though? For all I know I did when downgrading this. As I said earlier I'm a real nubcake at linux stuff.

Thank you so much for your help and resolving my issue. :)

---

### Post by monraaf on 2009-07-16
It seems you already did that. From menu Package -> Force Version. 

Best though is to be careful when adding extra repositories, different versions of libraries can really scr*w things up.

---

### Post by vinutux on 2009-07-16
> **monraaf said:**
> The screenshot show's that you are using a PPA! You must select jaunty version.

 yeh..its clear you are using un-official repo try this

> **vinutux said:**
> open Synaptic select faad plugin **[COLOR="Red"]pakage menu>force version and select jaunty version[/COLOR]** instead of current one.


.

---

### Post by cheesepenguins on 2009-07-16
> **monraaf said:**
> It seems you already did that. From menu Package -> Force Version. 

Best though is to be careful when adding extra repositories, different versions of libraries can really scr*w things up.
> **vinutux said:**
> yeh..its clear you are using un-official repo try this
.

Thank you both for helping me sort this out. 

And thanks for the advice.

---

### Post by anthos_hero on 2009-07-18
All I did was uninstall all totem plugins and then install mozilla-mplayer.  Then everything worked.:KS

---

### Post by vinutux on 2009-07-19
yeh..there is a vlc plugin also available in rep

```
sudo apt-get install mozilla-plugin-vlc
```

---

