---
title: "What happened to Aqualung?"
date: 2014-11-06
forum: Multimedia Software
---

### Post by oldrocker99 on 2014-11-06
Aqualung has been my go-to music player. It is truly gapless, and lightweight. It has unaccountably disappeared from the 14.10 repos.

I have downloaded a Lucid package, but it has unresolvable dependencies. I downloaded the source code, and after some dependency searching, produced a makefile. Then the compiler output ended with this:
```
/usr/bin/ld: volume.o: undefined reference to symbol 'sqrtf@@GLIBC_2.0'
/lib/i386-linux-gnu/libm.so.6: error adding symbols: DSO missing from command line
collect2: error: ld returned 1 exit status
Makefile:285: recipe for target 'aqualung' failed
make[3]: *** [aqualung] Error 1
make[3]: Leaving directory '/home/oldrocker99/Downloads/aqualung-0.9beta11/src'
Makefile:356: recipe for target 'all-recursive' failed
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory '/home/oldrocker99/Downloads/aqualung-0.9beta11/src'
Makefile:231: recipe for target 'all-recursive' failed
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/oldrocker99/Downloads/aqualung-0.9beta11'
Makefile:170: recipe for target 'all' failed
make: *** [all] Error 2
```


This is ***extremely*** frustrating. Is there any reason that this (for me) essential program has been dumped from the repos? Do I have to use 14.04? Or Manjaro?

---

### Post by mc4man on 2014-11-06
For various reasons it's been removed, sounds like a reasonable action
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=748560](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=748560)

---

### Post by mc4man on 2014-11-06
But that doesn't mean you can't use on 14.10 
Seeing as you been using then apparently LAVC (libav, ffmpeg) support doesn't matter ( and won't work anyway.

You can give this build a quick test, if ok keep it & the .deb, and or download the source to have to build for yourself.
*removed*

Note will only be there for a few days, then I'll remove.

If you wanted it appears monkey audio is available if you have libmac-dev  installed (available in various places.

---

### Post by oldrocker99 on 2014-11-06
Thankyou thankyou thankyou! It is installed and I can do my college radio show with it; MIXXX is too slow on my 8 year old laptop.

---

### Post by oldrocker99 on 2014-11-06
Thankyou thankyou thankyou! It is installed and I can do my college radio show with it; MIXXX is too slow on my 8 year old laptop.

---

### Post by mc4man on 2014-11-06
I didn't notice when building but aqualung.desktop is slightly lacking.
If you want aqualung to show in the context menu then - 
```

sudo -H gedit  /usr/share/applications/aqualung.desktop
```

Change the Exec=aqualung to this (add a space & %U
```
Exec=aqualung %U
```

(- Opens it on the file, though doesn't auto start..

---

### Post by mc4man on 2014-11-07
Actually rather than above post, seems one could set up some  custom context options, Ex's

gedit ~/.local/share/applications/aqualung1.desktop

```
[Desktop Entry]
Name=Play in Aqualung
Comment=Plays single track
Exec=aqualung -N 0 -L %U
Icon=aqualung.xpm
Categories=GTK;AudioVideo;Audio;Player;
Terminal=false
Type=Application
```

gedit ~/.local/share/applications/aqualung2.desktop

```
[Desktop Entry]
Name=Enqueue in Aqualung
Comment=Enqueues tracks, same instance
Exec=aqualung -N 0 -E %U
Icon=aqualung.xpm
Categories=GTK;AudioVideo;Audio;Player;
Terminal=false
Type=Application
```

ect., ect.

---

### Post by a-you on 2014-11-07
I saw this thread because I too have been using aqualung and though it was working fine up to some time not long ago (I don't remember exactly when) it stopped outputting sound. That is, it runs, seems to play, but no sound. I do believe that it was working with ubuntu studio 14.4 earlier on, though to be honest I'm not 100% certain.

Anyway aqualung seems to be the only sound file player that's broken on my system.

Any thoughts would be appreciated. I've tried alsamixer, pulseaudio volume control and various other simple things but still don't know what's up.

Ubuntu Studio 14.4 64 bit

(Perhaps this should be a separate thread??)

[editing]

Huh, I see that it's not really maintained anymore and I guess incompatible with the current state of libav. Was this another casualty in the ffmpeg-libav fight?

---

### Post by mc4man on 2014-11-07
> **a-you said:**
> I

(Perhaps this should be a separate thread??)

[editing]

Huh, I see that it's not really maintained anymore and I guess incompatible with the current state of libav. Was this another casualty in the ffmpeg-libav fight?
Sounds like a local or Ubuntu Studio issue, another thread may be better. (what does it report when opening from terminal?

As far as "casualty", not at all. The aqualung project isn't being developed so libav & ffmpeg support would have been broken some time ago

---

### Post by Rob Sayer on 2014-11-07
It's not really earth shaking if a package all of a sudden isn't in the repos when you do a release-upgrade to a new release.  I've found it pretty common.

They tend to reappear eventually but I had a look at that debian bug link above.  Frankly it doesn't look good.

Fortunately there are a ton of linux music players.  That surprised me when I first installed ubuntu.  It seems one comes out every week.  It's one area where linux beats Windoze to hell and back for selection.

---

### Post by andrew.46 on 2014-11-07
> **mc4man said:**
>  The aqualung project isn't being developed so libav & ffmpeg support would have been broken some time ago

There seems to be an RC release this year (version 1.0-rc1 2014-06-03 16:32) and some fairly recent activity on svn:

```

andrew@ilium~$ **[COLOR="#FF0000"]svn log svn://svn.code.sf.net/p/aqualung/code/trunk -l 2[/COLOR]**
------------------------------------------------------------------------
r1309 | tszilagyi | 2014-09-02 05:24:59 +1000 (Tue, 02 Sep 2014) | 2 lines

Add updated German translation from Wolfgang Stoeggl

------------------------------------------------------------------------
r1308 | tszilagyi | 2014-08-26 01:29:39 +1000 (Tue, 26 Aug 2014) | 12 lines

Support XDG Basedir specification

Implement feature request #192
http://aqualung.factorial.hu/mantis/bug_view_page.php?bug_id=0000192

Having all configuation in one subdirectory makes backups much easier
and declutters the home directory. The implementation auto-migrates
~/.aqualung (if it exists) to $XDG_CONFIG_HOME/aqualung (most likely
~/.config/aqualung) and uses the new location going forward.
Compatibility with the legacy location is thus ensured.


------------------------------------------------------------------------
andrew@ilium~$ 

```

No world shaking changes but activity nonetheless...

**Edit:** Mind you I built aqalung and had a look at it, I feel that the world has moved along a little since this application was being fully developed :)

---

### Post by mc4man on 2014-11-07
> **andrew.46 said:**
> There seems to be an RC release this year (version 1.0-rc1 2014-06-03 16:32) and some fairly recent activity on svn:

Will have to check out.., thanks

Did a quick test here with the last source Debian/Ubuntu have provided/used. It can use ffmpeg/libav but has to be old, similar to audacity mess before it was fixed by FFmpeg dev. Doesn't like the latest libmac2  (4.11+) though..


Never have used before but has some interesting elements once dug into - 
[http://aqualung.factorial.hu/manual/aqualung-doc.html](http://aqualung.factorial.hu/manual/aqualung-doc.html)

Edit: wow, don't know why Debian claimed 'not maintained' unless they only 'count' releases?

---

### Post by mc4man on 2014-11-07
Did a quick build off of ffmpeg-2.4.3 & aqualung works fine, so they could of kept it..

---

### Post by andrew.46 on 2014-11-07
> **mc4man said:**
> Did a quick build off of ffmpeg-2.4.3 & aqualung works fine, so they could of kept it..

Hmmm.... interesting, I am having a few issues compiling the *newest* aqalung with my 'other' distro so I shall perservere...

**Edit:** A truly embarrassing error on my part which I shall never admit to :). Running RC1 and I am gradually warming to it. Debian guys are a bit funny, perhaps they do in fact need the tag **[COLOR="#FF0000"]'Released'[/COLOR]** and RC 1 did not cut it.

---

### Post by andrew.46 on 2014-11-07
Interestingly enough Aqualung did well on my 'Lucky Night' lossless torture test only failing on WMA lossless. Did this fail on your system as well mc4man?

---

### Post by mc4man on 2014-11-07
> **andrew.46 said:**
> Interestingly enough Aqualung did well on my 'Lucky Night' lossless torture test only failing on WMA lossless. Did this fail on your system as well mc4man?
Yep - it appears that while a recent FFmpeg is ok only wma2 will work 
(if you were to run from a terminal the errors are shown

---

### Post by andrew.46 on 2014-11-07
I confess I have not investigated too deeply but I have made the following:

[http://aqualung.factorial.hu/mantis/bug_view_page.php?bug_id=0000193](http://aqualung.factorial.hu/mantis/bug_view_page.php?bug_id=0000193)

and perhaps this will be productive, mind you I forgot to add FFmpeg version :(.

**Edit: **Added.... Mantis seems fairly usable!

---

### Post by mc4man on 2014-11-07
> **andrew.46 said:**
> I confess I have not investigated too deeply but I have made the following:

[http://aqualung.factorial.hu/mantis/bug_view_page.php?bug_id=0000193](http://aqualung.factorial.hu/mantis/bug_view_page.php?bug_id=0000193)

and perhaps this will be productive, mind you I forgot to add FFmpeg version :(.

**Edit: **Added.... Mantis seems fairly usable!
At least here wmap is also an issue

(- unsupported - 
.opus
wmal
wmap
.ape (- though may work with libmac-3.99
.shn
Otherwise pretty good

---

### Post by shantiq on 2014-11-08
Aqualung was always one of the corkers.  Excellent player.   Would it be ok to store your deb here Mc   or do you have reasons to delete it?  Since it is small it can be zipped and kept here on the thread page.   


Personally I often use*** [XMMS]("http://ubuntuforums.org/showthread.php?t=1525072")*** which has been "gone" a long time as it still has the best sound of them all to my ears

Although these days ***Clementine*** with the [Delta Plugin]("https://decatf.wordpress.com/2010/11/04/gstreamer-delta-audio-sharpening-plugin/")

Install

```
sudo add-apt-repository ppa:decatf/testy ;
sudo apt-get update && sudo apt-get install delta
```


then do


```
gconftool &#8211;type string &#8211;set /system/gstreamer/0.10/default/musicaudiosink &#8220;delta gain=100 ! autoaudiosink&#8221;

```

and in clementine go to tools/preferences and pick GSettings audio sink


or ***Audacious ***with the Crystalizer plugin are almost as good and maybe as good  Preferences/Plugins/Effects


Always sad to see good software fade away :]

---

### Post by mc4man on 2014-11-08
I do see a small issue with the 1.0rc1
Aqualung doesn't seem to have any way to default config an audio out unless one specifies on cli or by adding to the .desktop. ( -o <whatever>
So it probes each time it opens, starting with jack.

The issue then is what version of libjack a user has, libjack0 or libjack-jack2-0 ( you almost wish there was only one or the other...

Ex.'s
 Both 0.9.x & 1.0rc1 w/ libjack0, aqua opens fast
> $ aqualung 
No output driver specified, probing for a usable driver.
Probing JACK driver... JACK server not found
Probing PulseAudio driver... OK


0.9 with libjack-jack2-0 - opens pretty fast

> $ aqualung 
No output driver specified, probing for a usable driver.
jack_client_new: deprecated
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Probing JACK driver... JACK server not found
Probing PulseAudio driver... OK

1.0rc w/ libjack-jack2-0, opens very slow, could cause users to open a couple of instances if opening from an icon

>  $ aqualung 
No output driver specified, probing for a usable driver.
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
exec of JACK server (command = "/usr/bin/jackd") failed: No such file or directory
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Probing JACK driver... JACK server not found
Probing PulseAudio driver... OK

Too bad aqualung doesn't have a config item to set an audio out... & the whole dual libjack thing is a pita.

---

### Post by andrew.46 on 2014-11-08
Looks like the audio out is set in the config file *$HOME/.config/aqualung/config.xm*l:

```
  <default_param>-o alsa</default_param>
```

but can more easily be set in the settings from:

Settings --> General --> Miscellaneous --> Implicit comandline

I have only used alsa and not experimented with more exotic commandlines :)

---

### Post by mc4man on 2014-11-08
The issue with libjack version aside maybe tonight will put up some test packages to see
(- there also may be some ways to improve the .desktop for unity

So it would be something like this - 

> $ aqualung -v
Aqualung -- Music player for GNU/Linux
Build version: R-1309
(C) 2004-2014 Tom Szilagyi <tszilagyi@users.sourceforge.net>
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details.

This Aqualung binary is compiled with:

  Optional features:
    [+] LADSPA plugin support
    [+] CDDA (Audio CD) support
    [+] CDDB support
    [+] Sample Rate Converter support
    [+] iRiver iFP driver support
    [+] JACK port management support
    [+] Loop playback support
    [+] Systray support
    [+] Podcast support
    [+] Lua extension support

  Decoding support:
    [+] sndfile (WAV, AIFF, etc.)
    [+] Free Lossless Audio Codec (FLAC)
    [+] Ogg Vorbis
    [+] Ogg Speex
    [+] MPEG Audio (MPEG 1-2.5 Layer I-III)
    [+] MOD Audio (MOD, S3M, XM, IT, etc.)
    [+] Musepack
    [+] Monkey's Audio Codec
    [+] WavPack
    [+] LAVC (AC3, AAC, WavPack, WMA, etc.)

  Encoding support:
    [+] sndfile (WAV)
    [+] Free Lossless Audio Codec (FLAC)
    [+] Ogg Vorbis
    [+] LAME (MP3)

  Output driver support:
    [ ] sndio Audio
    [+] OSS Audio
    [+] ALSA Audio
    [+] JACK Audio Server
    [+] PulseAudio
    [ ] Win32 Sound API

(with the current configure.ac/configure it doesn't find lua5.2 (dev), can modify to find, have to look at, something with the extended lua detect routines..

---

### Post by mc4man on 2014-11-08
> **andrew.46 said:**
> Looks like the audio out is set in the config file *$HOME/.config/aqualung/config.xm*l:

```
  <default_param>-o alsa</default_param>
```

but can more easily be set in the settings from:

Settings --> General --> Miscellaneous --> Implicit comandline

I have only used alsa and not experimented with more exotic commandlines :)
Thank you, the things I miss...

---

### Post by andrew.46 on 2014-11-08
> **mc4man said:**
> Doesn't like the latest libmac2  (4.11+) though.

You have solved the ape / libmac issue?

---

### Post by mc4man on 2014-11-08
> **andrew.46 said:**
> You have solved the ape / libmac issue?

Well you did really..
A recent commit to svn enabled/fixed for 4.11, tested with luckynight 
As far as lua, 5.2 is recommended but at least here will not be detected. Solved by making the very last lua entry in configure.ac 5.2 & the 2nd to last 5.1 (flip-floped them
 Then caused a reconfig (./autogen.sh for self builds
Though lua has no value without scripts..

---

### Post by andrew.46 on 2014-11-08
> **mc4man said:**
> Well you did really..
A recent commit to svn enabled/fixed for 4.11, tested with luckynight .

I see the problem now, I am running the older version of libmac :). I found it here:

[http://etree.org/shnutils/shntool/support/formats/ape/unix/3.99-u4-b5/](http://etree.org/shnutils/shntool/support/formats/ape/unix/3.99-u4-b5/)

but I could not find the source for this newer version except at the base of a Debian multimedia page. Do you have an address for the most recent source? I gather more recent versions are put together by enthusiasts...

**Edit**: I used the source from Debian Multimedia, odd that there is no dedicated page or site for the source.

---

### Post by mc4man on 2014-11-08
> **andrew.46 said:**
> 
**Edit**: I used the source from Debian Multimedia, odd that there is no dedicated page or site for the source.

see you got, alt.
```
wget -c http://opensourceliving.googlecode.com/files/mac-4.11-u4-b5-s7.tar.gz
```

edit - just the same as from deb multi, not sure where orig is, if anywhere now??

---

### Post by andrew.46 on 2014-11-08
Thank you :)

---

### Post by mc4man on 2014-11-08
For the few that desire a test build of latest svn (1309),  for the most part fully enabled.
Has 14.04 & 14.10 packages, 14.04 will eventually get a new one in multimedia ppa with more useful .desktop in a unity session
(-  ape support added thru supplied libmac2
14.04 works fine here, 14.10 I don't have & won't...
[https://launchpad.net/~mc3man/+archive/ubuntu/aqua-tests](https://launchpad.net/~mc3man/+archive/ubuntu/aqua-tests)

---

### Post by oldrocker99 on 2014-11-10
> **mc4man said:**
> For the few that desire a test build of latest svn (1309),  for the most part fully enabled.
Has 14.04 & 14.10 packages, 14.04 will eventually get a new one in multimedia ppa with more useful .desktop in a unity session
(-  ape support added thru supplied libmac2
14.04 works fine here, 14.10 I don't have & won't...
[https://launchpad.net/~mc3man/+archive/ubuntu/aqua-tests](https://launchpad.net/~mc3man/+archive/ubuntu/aqua-tests)

Wonderful! And, it's on a PPA!

You are a hero.

---

### Post by a-you on 2014-11-11
> **mc4man said:**
> Sounds like a local or Ubuntu Studio issue, another thread may be better. (what does it report when opening from terminal?

As far as "casualty", not at all. The aqualung project isn't being developed so libav & ffmpeg support would have been broken some time ago

Sorry for the delay. Starting it from terminal:

```
No output driver specified, probing for a usable driver.
jack_client_new: deprecated
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Probing JACK driver... JACK server not found
Probing PulseAudio driver... OK
no more csLADSPA plugins
```

But even when I specifally start it with one of:

```
--output pulse|alsa
```

The symptoms are the same: it behaves as if it's playing but no sound comes out.

As others have mentioned there are planty of alternatives, so it's not a major issue. Too bad in a way though, I thought it was a nice audio player.

[edited] Sorry, I just replied as soon as I read mc4man's comment asking me what happens when started from terminal, but see now that there are a lot of comments in this thread since; I'll go read those now. Might have answers for me too.

---

### Post by oldrocker99 on 2015-06-16
As the person who started this thread: Interestingly enough, running 14.04, I just got an update of Aqualung from 0.9 to 1.0. It apparently **is** still under development!;)

Halloo, hallay, it's a wonderful day!

---

### Post by mc4man on 2015-06-16
> **oldrocker99 said:**
> As the person who started this thread: Interestingly enough, running 14.04, I just got an update of Aqualung from 0.9 to 1.0. It apparently **is** still under development!;)

Halloo, hallay, it's a wonderful day!If you got an update it was from a ppa, no longer in Ubuntu after 14.04 (0.9~beta11-2
And likely isn't being developed, just the last source..

---

### Post by oldrocker99 on 2015-06-16
I was so excited about the upgrade that I neglected to add this.

There **is** a ppa:[https://launchpad.net/~mc3man/+archive/ubuntu/aqua-tests](https://launchpad.net/~mc3man/+archive/ubuntu/aqua-tests), which updated the version from 0.9 to 1.0, and that would indicate that *someone* is working on it.

Note that Aqualung builds are for Trusty (14.04) and Utopic (14.10) but there's nothing listed for Vivid (15.04).

I also tried the tar.gz [http://aqualung.factorial.hu/download.html](http://aqualung.factorial.hu/download.html) as well as the Git repository:
```
git clone git://github.com/jeremyevans/aqualung.git
```

Neither would compile on my 32-bit laptop. Your mileage may vary; if it were available for 15.04, I'd certainly upgrade.

---

### Post by mc4man on 2015-06-16
> **oldrocker99 said:**
>  if it were available for 15.04, I'd certainly upgrade.
Well 15.04 is only a 9 month release but I guess no harm in providing. Give it a try & see if there is any lavc support, should be up in a few min. or so..

---

### Post by oldrocker99 on 2015-06-17
By the way: Aqualung got updated again in the last 12 hours or so, and there's a Vivid version now!

The biggest change in 1.0, for me, is support for AAC files; I had had to convert AAC to Ogg, which sort of worked.

The PPA's advice to edit ~/.config/aqualung/config.xml to include

```
<default_param>-o pulse</default_param>
```

worked fine for me. It doesn't load quite as quickly as 0.9 did, but I can certainly live with that; it's still faster than other music players load.

---

### Post by oldrocker99 on 2016-04-09
The PPA doesn't have a Xenial build yet, so I (finally) managed to compile v1.0, using the listed dependencies here[http://aqualung.jeremyevans.net/compiling/](http://aqualung.jeremyevans.net/compiling/). All the -dev files I neded were in the repos.

---

### Post by mc4man on 2016-04-10
aqualung still seems viable though it's development has basically ceased. ubuntu session users won't get a systray unless they re-enable the systray in unity.
So all in all it would be ok for 16.04, barely.

---

