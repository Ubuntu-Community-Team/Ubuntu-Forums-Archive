---
title: "Ubuntu 10.10 cannot play dvds with Totem."
date: 2011-01-23
forum: Multimedia Software
---

### Post by The WHAM Burglar on 2011-01-23
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256

Ubuntu was advertised as having software that can to play DVDs. While
running the ‘system testing’ program I discovered that any DVD I tried
to play could not be accessed. Please advise the most appropriate means of
diagnosing and solving this problem.


[http://www.youtube.com/watch?v=5tXBYy6l0GU](http://www.youtube.com/watch?v=5tXBYy6l0GU)

-----BEGIN PGP SIGNATURE-----
Version: (N/A)
Charset: utf-8

wlcDBQFNPTM+MiSrPaXCPwQRCPxtAPwOXKukOH1qxWjHViO4LoUa5UlDeXIao8Om
3H9N2axRuQD+L7qC2b4+V0eHyHBnsOblHG34xu7ewCj0TkL62Q5dxGA=
=CGHp
-----END PGP SIGNATURE-----

---

### Post by johntaylor1887 on 2011-01-23
```
sudo apt-get install libdvdread4
```
then
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
Rebooting may be necessary.

---

### Post by ivanovnegro on 2011-01-23
Have you installed all the codecs you need for?
There is a repository with the name 'Restricted Extras' also to enable some problematic codecs with right issues such as DVD codecs or to be able to play MP3 tracks/WMA etc.
Go the the Software Center and enable the restricted repositories in the Software sources list or go to the Synaptic Package Manager and there to the software sources list to add it.

---

### Post by hsoulen on 2011-01-24
> **The WHAM Burglar said:**
> -----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256

Ubuntu was advertised as having software that can to play DVDs. While
running the ‘system testing’ program I discovered that any DVD I tried
to play could not be accessed. Please advise the most appropriate means of
diagnosing and solving this problem.


[http://www.youtube.com/watch?v=5tXBYy6l0GU](http://www.youtube.com/watch?v=5tXBYy6l0GU)

-----BEGIN PGP SIGNATURE-----
Version: (N/A)
Charset: utf-8

wlcDBQFNPTM+MiSrPaXCPwQRCPxtAPwOXKukOH1qxWjHViO4LoUa5UlDeXIao8Om
3H9N2axRuQD+L7qC2b4+V0eHyHBnsOblHG34xu7ewCj0TkL62Q5dxGA=
=CGHp
-----END PGP SIGNATURE-----

Relax there fella! :D

Ubuntu does not include all of the necessary components to play DVDs in the default install for a reason (see the link below). With that said, it is a simple procedure to enable this support. Please check this link: [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

Why Ubuntu does not include all the software for DVD playback by default: [http://en.wikipedia.org/wiki/Ubuntu-restricted-extras]("http://en.wikipedia.org/wiki/Ubuntu-restricted-extras")

Enjoy the DVD playback.

Hank

---

### Post by Yellow Pasque on 2011-01-24
Next time, try Google before making a youtube video. Much more efficient use of time/bandwidth...

---

### Post by The WHAM Burglar on 2011-01-25
> **johntaylor1887 said:**
> ```
sudo apt-get install libdvdread4
```then
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```Rebooting may be necessary.

 Thank you, unfortunately that sort of fixes the problem. Video playback from the DVD occurs but is extremely choppy. In addition, no audio playback occurs.

[http://www.youtube.com/watch?v=Yo6ugkx_PaY](http://www.youtube.com/watch?v=Yo6ugkx_PaY)

 Update: This seems to have broken Pulse Audio! Log follows:
```

ubuntu python: io/hpmud/pp.c 627: unable to read device-id ret=-1
ubuntu pulseaudio[13594]: alsa-util.c: snd_pcm_avail() returned a value that is exceptionally large: 70560 bytes (400 ms).
ubuntu pulseaudio[13594]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_ens1371'. Please report this issue to the ALSA developers.
ubuntu pulseaudio[13594]: alsa-util.c: snd_pcm_dump():
ubuntu pulseaudio[13594]: alsa-util.c: Hardware PCM card 0 'Ensoniq AudioPCI' device 0 subdevice 0
ubuntu pulseaudio[13594]: alsa-util.c: Its setup is:
ubuntu pulseaudio[13594]: alsa-util.c:   stream       : PLAYBACK
ubuntu pulseaudio[13594]: alsa-util.c:   access       : MMAP_INTERLEAVED
ubuntu pulseaudio[13594]: alsa-util.c:   format       : S16_LE
ubuntu pulseaudio[13594]: alsa-util.c:   subformat    : STD
ubuntu pulseaudio[13594]: alsa-util.c:   channels     : 2
ubuntu pulseaudio[13594]: alsa-util.c:   rate         : 44100
ubuntu pulseaudio[13594]: alsa-util.c:   exact rate   : 44101 (1445100000/32768)
ubuntu pulseaudio[13594]: alsa-util.c:   msbits       : 16
ubuntu pulseaudio[13594]: alsa-util.c:   buffer_size  : 3528
ubuntu pulseaudio[13594]: alsa-util.c:   period_size  : 441
ubuntu pulseaudio[13594]: alsa-util.c:   period_time  : 9999
ubuntu pulseaudio[13594]: alsa-util.c:   tstamp_mode  : ENABLE
ubuntu pulseaudio[13594]: alsa-util.c:   period_step  : 1
ubuntu pulseaudio[13594]: alsa-util.c:   avail_min    : 441
ubuntu pulseaudio[13594]: alsa-util.c:   period_event : 1
ubuntu pulseaudio[13594]: alsa-util.c:   start_threshold  : -1
ubuntu pulseaudio[13594]: alsa-util.c:   stop_threshold   : 1849688064
ubuntu pulseaudio[13594]: alsa-util.c:   silence_threshold: 0
ubuntu pulseaudio[13594]: alsa-util.c:   silence_size : 0
ubuntu pulseaudio[13594]: alsa-util.c:   boundary     : 1849688064
ubuntu pulseaudio[13594]: alsa-util.c:   appl_ptr     : 250929
ubuntu pulseaudio[13594]: alsa-util.c:   hw_ptr       : 265041
ubuntu pulseaudio[13594]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
ubuntu pulseaudio[13594]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_ens1371'. Please report this issue to the ALSA developers.
ubuntu pulseaudio[13594]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
ubuntu python: io/hpmud/pp.c 627: unable to read device-id ret=-1
ubuntu python: io/hpmud/pp.c 627: unable to read device-id ret=-1
ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
50mounted-tests: debug: /dev/sda2 type not recognised; skipping
ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
ubuntu 50mounted-tests: debug: /dev/sda5 is a swap partition; skipping
ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
ubuntu 50mounted-tests: debug: /dev/sda2 type not recognised; skipping
ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
ubuntu 50mounted-tests: debug: /dev/sda5 is a swap partition; skipping
ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
ubuntu python: io/hpmud/pp.c 627: unable to read device-id ret=-1
ubuntu python: io/hpmud/pp.c 627: unable to read device-id ret=-1
ubuntu python: io/hpmud/pp.c 627: unable to read device-id ret=-1
ubuntu python: io/hpmud/pp.c 627: unable to read device-id ret=-1
ubuntu python: io/hpmud/pp.c 627: unable to read device-id ret=-1
ubuntu pulseaudio[1846]: pid.c: Daemon already running.
ubuntu pulseaudio[1833]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
ubuntu pulseaudio[1833]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_ens1371'. Please report this issue to the ALSA developers.
ubuntu pulseaudio[1833]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
```

I am unsure on how to fix such an error.

---

### Post by johntaylor1887 on 2011-01-25
> **The WHAM Burglar said:**
> Thank you, unfortunately that sort of fixes the problem. Video playback from the DVD occurs but is extremely choppy. In addition, no audio playback occurs. Perhaps I have missed something?
  
[http://www.youtube.com/watch?v=Yo6ugkx_PaY](http://www.youtube.com/watch?v=Yo6ugkx_PaY)

What video card do you have?

---

### Post by The WHAM Burglar on 2011-01-25
I have a NVIDIA GeForce 9500 GT GPU.

---

### Post by johntaylor1887 on 2011-01-26
Did you install the nvidia driver?

---

### Post by The WHAM Burglar on 2011-01-27
Yes the NVIDIA binary X.Org driver has been installed. This includes the modaliases for the driver as well.

In addition, the DVD does not seem to be detected be is somehow detected.
[http://i1013.photobucket.com/albums/af255/TheWHAMBurglar/Ubuntu-2011-01-27-17-04-33.png](http://i1013.photobucket.com/albums/af255/TheWHAMBurglar/Ubuntu-2011-01-27-17-04-33.png)

Also crashes.
[http://i1013.photobucket.com/albums/af255/TheWHAMBurglar/crash.png]("http://i1013.photobucket.com/albums/af255/TheWHAMBurglar/crash.png?t=1296165629")

---

### Post by victorhugo289 on 2011-01-30
Guys, guys, guys, don't change the subject of conversation here, he's taking about playing DVD on Totem.
I have the exact same problem, and I know it has nothing to do with video card drivers because I watched like 10 DVd movies on Ubuntu 10.04 before I moved to 10.10.
I get the exact same video problem that the OP says, it has nothing to do with VIDEO DRIVERS!! pls...
I installed Medibuntu, then I added the restricted extras, then I installed the libdvd4 and whatnot. Still the video is all choppy and it even slows down the computer when Totem is open trying, it says "Stopped".
Does anybody know how to deal with this?

---

### Post by BicyclerBoy on 2011-01-30
AFAIK
Totem is now using Xine in 10.10.
Totem in 10.04 used gstreamer.

It is possible that Totem (xine) does not dlopen libdvdcss.

Just use VLC or a better media player.

---

### Post by NightwishFan on 2011-01-30
Totem uses gstreamer, and can play DVDs, perhaps your DVDs are region locked. Also, try running this command:
```
sudo sh /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by BicyclerBoy on 2011-01-30
AFAIK & IIRC

10.10 Totem is not gstreamer based, it is xine based.

---

### Post by NightwishFan on 2011-01-30
[LIST]
[*]Totem does not even officially support Xine any more.
[*]It has "AFAIK" always used Gstreamer in Ubuntu by default, it has since I used it in 7.10
[*]There is no room on the default CD for Gstreamer and Xine
[*]Rhythmbox uses Gstreamer, and it is default.
[*]The package for totem-xine is marked as deprecated and links to the gstreamer version of Totem in Ubuntu 10.10 [http://packages.ubuntu.com/maverick/totem-xine](http://packages.ubuntu.com/maverick/totem-xine)
[*]I have not modified my Maverick install and I have the gstreamer totem
[*]Totem Gstreamer in 10.10 is much better at playing DVDs than the one in 10.04, it supports libdvdread4, which in turn uses libdvdcss.
[*]This is not really on topic, and doesn't really matter, but no Totem does not use Xine by default. If at all in Ubuntu 10.10.
[*]Afaik :lolflag:
[/LIST]

---

### Post by BicyclerBoy on 2011-01-30
Thank you for clarifying.
I think the facts about Totem in 10.10 fairly on topic..

I know Totem did not use xine in 10.04.
I have just un-installed it in the past, but it works okay in 10.04 netbook.

So why did Ubuntu make a totem-xine package ?
Was gstreamer more closely aligned to KDE than Gnome ?

Will note that there are a few people, in the forums lately, having DVD playback issues with 10.10.

---

### Post by NightwishFan on 2011-01-31
KDE uses Phonon with the Xine backend, however that is only relevant for KDE applications such as Amarok, the KDE sound system and Dragon player. (I believe Kubuntu is moving over to pulseaudio and gstreamer with phonon)

---

### Post by mc4man on 2011-01-31
> but no Totem does not use Xine by default. If at all in Ubuntu 10.10.
Totem-xine was discontinued back in karmic. It's still viable though and for some local files is superior to totem (gstreamer), and in particular  DVD_VIDEO movies.
It uses a different dvdnav and allows picking/switching streams, ie. subs and audio.
(still have it alive here in natty and maverick

Totem (gstreamer) has gotten much better in 10.10 and 11.04 though in some hardware could have issues w/ 5.1 analog output. (switched to 5.1 digital here so haven't keep up on that.

---

### Post by ranjix on 2011-01-31
You need to install additional plugin to play DVD video. Toten will search for plug-in when you try to play DVD video. Try VLC, it comes with necessary plug-ins.

---

### Post by Yellow Pasque on 2011-01-31
Updating to latest stable gstreamer might help Totem playback: [https://launchpad.net/~gstreamer-developers/+archive/ppa?field.series_filter=maverick](https://launchpad.net/~gstreamer-developers/+archive/ppa?field.series_filter=maverick)

If you want to try something with a xine backend, try gxine (or kaffiene). Of cource, there are other players too (mplayer, vlc, etc.)

---

### Post by victorhugo289 on 2011-01-31
> **Temüjin said:**
> Updating to latest stable gstreamer might help Totem playback: [https://launchpad.net/~gstreamer-developers/+archive/ppa?field.series_filter=maverick]("https://launchpad.net/%7Egstreamer-developers/+archive/ppa?field.series_filter=maverick")


I hope I'm not speaking too soon, but doing the above appears to have solved the problem, I can finally watch DVD in totem! With menus and everything. 
I went to the link above and added the PPA following the intructions in there. After that I went to "Update Manager" and there were like 2 errors or so but Synaptic Package Manager apparently fixed them.
I rebooted --it didn't ask to-- and I can play DVD.

----UPDATE: Yep, that solved my problem. Thank you!

---

