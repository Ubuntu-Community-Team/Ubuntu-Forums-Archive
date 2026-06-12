---
title: "Working Mythstreamtv Mythweb plugin"
date: 2008-09-17
forum: Mythbuntu
---

### Post by anonymousdog on 2008-09-17
I posted a prior version of this on the tail end of another thread, but I made a change or two and am posting a tar.gz of what I believe to be a tested, working mythstreamtv (plugin for mythweb) package for Mythbuntu 8.04.x.  (I've posted some of the original posting here to include installation instructions.)

I've been hacking on mythstreamtv on and off for a while to get it working better with 0.21. This version makes use of storage group information, includes some new bit rate options, includes a wap theme (yes, this works on mobile devices), allows (on the web server) concurrent vlc instances not owned by www-data user, corrects a handful of small errors and syntax problems, and makes a few minor additions and changes. This package is intended for Mythbuntu 8.0.4.x, but may work with other distros and MythTV 0.21 (other distro installs will have to watch out especially for the apache service account set in install.sh).

Prequisites: ffmpeg from Mediabuntu...get from Mythbuntu Control Center -- Proprietary Codecs: enable everything (but I think it just depends on Mediabuntu's ffmpeg).

Two caveats:
[LIST]
[*]No storage group can have more than one directory defined, or mythstreamtv won't be able to find the recordings files (and it won't work).  This also means that you can't just move recordings around between MythTV recordings directories (like normal); this version of mythstreamtv relies on the recording's storage group's directory in order to find the recording.
[*]The scripting assumes that the recordings files are locally accessible on the web server at the path defined for each storage group's only directory; for web servers that don't house the recordings' physical disks, you can accomplish that with remote mounts.
[/LIST]

Attached is a tgz archive  of the package.  To install it, follow the steps below:

Dl the package, open a terminal at / (root), and 'sudo tar -xzvf <path_to_package>/mythstreamtv_1.30-11-amk.tar.gz'. Now, 'cd /usr/share/mythstreamtv'. 'sudo nano ./install.sh &' to edit the options in a block beginning on line 100; the defaults are just fine in most cases. Now, 'sudo ./install.sh'. That's pretty much it. The script should run without error.

Browse to mythweb, and you'll see a new "StreamTV" option in the header (or in the list on a wap device). Select a recording on the first page and click the "Select a Recording & Continue" button. On the next page you can select some bit rate and other options. The default page has reasonable defaults for a LAN device with VGA or better screen, while the wap page's defaults are "worst quality" settings designed to work over limited bandwidth to "small" screens. Click the "Start Live Stream" button, and mythweb will take you to a streaming status page where some very obvious management functions are available. Click on the "Stop Streaming" button to free up web server resources (due to vlc's significant CPU needs) and/or stream a different recording. (I think I already fixed this issue --> )The one on the bottom is a bit broken in that it doesn't refresh the page header and leaves you on the status page, but the "Stop Streaming" button in the header stops the stream and reloads the page where you select a recording.

Stream URLs are available on the status page. You can copy them (or setup a default mms player) to play the stream with vlc, WMP, tcpmp (probably the Core), etc by opening the URL as a network stream, or, if not available, a file (e.g., WMP). WMP gives me grief playing some rescaled resolutions; so I usually use VLC on PCs and tcpmp on PDAs.

This plugin was obviously originally intended to play multiple recordings as a playlist for vlc, and, at one point, the scripting may have worked for that.  It looks like vlc dropped support for a play-and-exit option that it looks like the scripting assumed was the default.  I've changed the mythstreamtv.sh script to include mutliple recordings in a playlist that it passes to vlc with a command to have vlc exit at the end of the playlist.  So, the "Next" and "Previous" buttons now work as I expected, and, when the playlist is finished, vlc on the web server terminates -- you don't have to go back and stop the stream manually (with the Stop Streaming button).  When vlc exits, it makes some log entries that you may see in the log viewer on the web page; these are normal and not errors.

The LiveTV code is highly experimental (alpha quality or worse), and changing channels with it is likely to interfere with ongoing recordings in MythTV; so, caveat emptor.  If you have a set top box, you may want to experiment with channel changing scripts other than the included ivtv-tune.sh (which is for ivtv-driven cards that use their internal tuners).  I've included ivtv-tune.sh.for.stb as an example (that works just fine for my dish receiver).  Whatever channel change script works for MythTV should work fine for this; just make sure it's executable, named 'ivtv-tune.sh', readable by www-data (or other apache service account), and placed in /usr/share/mythstreamtv/ (by default).  Channel change scripts will likely only control one of multiple tuners; so, tuner 2 operations probably won't work, and changing channels when streaming tuner 2 will probably just attempt to change channels on tuner 1 (or whatever your channel change script actually does).  The script also assumes your tuners are /dev/video0 and /dev/video1; those are hard coded and would have to be changed manually if your tuner(s) are different devices.  I've also encountered problems with recordings that began while I was already streaming from the target tuner...not reliably, but about 20% of the time puts the tuner in an "already in use" or "locked" state such that mythbackend can't use it, and the recording ends up being empty.

fixes1: Packaging problems and installer improvements
fixes2: Implements channel changing in wap theme for experimental LiveTV support.

---

### Post by bah1976 on 2008-12-11
Hi - I've tried in the past to get this to work, with no success.  I'm back again, and I downloaded this new package, installed it, and still am having trouble.  When I start the stream with defaults I get this in the log viewer:

```
Starting Stream of  /var/lib/mythtv/recordings/1383_20080915115900.mpg
VLC media player 0.8.6e Janus
[00000292] main interface: creating httpd
libdvbpsi error (PSI decoder): TS discontinuity (received 7, expected 0) for PID 0
libdvbpsi error (PSI decoder): TS discontinuity (received 9, expected 0) for PID 80
libdvbpsi error (PSI decoder): TS discontinuity (received 10, expected 8) for PID 0
[00000309] a52 packetizer: A/52 channels:2 samplerate:48000 bitrate:128000
[00000315] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:128000
libdvbpsi error (PSI decoder): TS discontinuity (received 11, expected 10) for PID 80
```

It seems I have a libdvbpsi problem - any ideas how to fix or what it's looking for, or if it even matters - since I have partial success regardless. 

Specifically, when I stream, and get those errors, I am able to view it with WMP or VLC, if I open the stream locally as [http://192.168.10.20:8001](http://192.168.10.20:8001).  However, if I try to open it through externally through my router, ([http://domain-name:8001](http://domain-name:8001)) I don't get anything.  I don't believe this to be a streaming problem, I think it's a routing problem.  I have port 8001 forwarded to the myth server - any other ports I need open?  On a perhaps related note, I am unable to forward port 22 to SSH in either.  But, I can browse mythweb over ssl all day with port 443 allowed in.  I am reasonably sure these are router problems, which may go away after I switch to a wrt54gl with the tomato firmware in a few weeks.  In the meantime, I'd still like to stream while offsite.  Any clues?

---

### Post by bah1976 on 2008-12-11
Ok, partial edit, due to typos...  

I am able to SSH in, once i typed the name correctly.  With SSH, I'm able to create a tunnel for port 8001, and i can use WMP or VLC to view the stream by pointing to 'localhost', but that's not what I'm trying to do.  I'm still trying to grasp why I can't stream over my router. 

Kudos on the StreamTV module - it appears to work exactly as it should.  I just can't get it to work over an external connection.  All other inbound ports work, I have SSL, SSH, and a few others inbound and they're all ok.  I see possible causes in 4 places, any comments?
1) Comcast is blocking port 8001 - I don't see this as too likely...
2) My router won't let 8001 in
3) Mythstream can't find the route to let 8001 back out - I wouldn't think there's anything specific to mythstream for this...
4) Any other ports in play?

Any other thoughts?

---

### Post by kwisher on 2009-02-26
I get the error "An unknown module was specified" when starting StreamTV. Any ideas on my problem?

TIA

---

### Post by vhalros on 2009-03-17
Hey, thanks for trying to get mythstreamtv working. When I try using the package, I can get to through selecting the stream, but when I hit the "start live stream" button, I get some permission errors (and it looks like other ones too). The log is below.


```
Starting Stream of  /var/lib/mythtv/recordings/2251_20090316200000.mpg
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;[00000373] signals interface error: Caught Terminated signal, exiting...
[00000375] main http server error: object is not attached
[00000367] main playlist error: could not create /var/www/.local: Permission denied
[00000367] main playlist error: could not create /var/www/.local/share: Permission denied
[00000367] main playlist error: could not create /var/www/.local/share/vlc: Permission denied
[00000001] main libvlc error: could not create /var/www/.cache: Permission denied
[00000001] main libvlc error: could not create /var/www/.cache/vlc: Permission denied
/usr/share/mythtv/mythstreamtv/mythstreamtv.sh: line 73: unexpected EOF while looking for matching `"'
/usr/share/mythtv/mythstreamtv/mythstreamtv.sh: line 75: syntax error: unexpected end of file
 

```


Any suggestions?

---

### Post by anonymousdog on 2009-04-14
Yep, VLC in Ubuntu 8.10 seems very broken (or broken in combination with the ffmpeg in 8.10).  [This thread](http://ubuntuforums.org/showthread.php?t=952603) seems to indicate that an```
apt-get install libavcodec-unstripped-51
```fixes it.

The permission problems are not deal breakers; the plugin will work with those errors.  They can be eliminated by your creating the directory structures it's looking for and allowing write access to the apache service account (probably www-data).  VLC tries to keep a small cache there, but I note no performance difference with or without cache.

---

### Post by belbo on 2009-07-14
Hey anonymousdog

Thinking of trying out your mythstreamtv but wondering beforehand if its working in ubuntu/ mythbuntu 9.04. Also, whether it will be maintained going forward. I'm no good at scripting and programming but wondering if others may get involved to help maintain it ?

Cheers

belbo

---

### Post by anonymousdog on 2009-07-14
It has not been tested, AFAIK, in 9.04.  It's operation depends entirely upon VLC and its dependencies (and codecs).  If you can stream the desired files to another PC with VLC using http or mms protocols, you should be golden.  Issues like the "unknown module" problem above are usually failure to follow the installation instructions (like running the install script as non-root user).  Please respond with success or failure.  I may be trying this in the next couple of weeks on a new box and 9.04 (as soon as I get SPDIF sound working right).

---

### Post by belbo on 2009-07-15
Thanks mate. 

Will reply with success or failure but may take about a week to get around to it. If you get there before me please post first.

Out of interest, do you know anything about how the mythweb video streaming works (from the video directory, not the recordings directory)?

It streams well in firefox. Not sure if automatically adjusts for bandwidth, transcodes on the fly or anything, but it seems simpler than the (currently experimental) mythweb flv streaming.

Also, what sort of support do you expect you'll get for maintaining it into the future ?

Cheers

belbo

---

### Post by anonymousdog on 2009-07-16
Don't love the flv streaming either: too one-size-fits-all.

I didn't do *anything* officially with the plugin.  AFAIK, the official sourceforge project is dormant.  I just took the Mythdora rpm, unpacked it, fixed some stuff to make it work with 8.04, repackaged it, and offered it to the community FWIW.  I'm hardly a maintainer or coder (HA!) nor do I claim to have done much of any rewriting...I can figure out just enough of most languages to be really dangerous!

If someone with good PHP coding experience got motivated to do a thorough rewrite, it could be VERY cool!  Nobody would need a slingbox.

Maintaining it in the future would require a process of "keeping up" with mythweb changes.  It relies heavily on the standard tv PHP modules for listings and file lookups.  Depending upon mythweb devel, that could be very little or quite a lot.  It also depends entirely on VLC's (and its dependencies') working as intended.  Historically that hasn't been a problem, but it has become one with recent Ubuntu distros.  I'd be happy if it always worked with the most recent LTS release.

My wish list for mythstreamtv plugin:
[LIST]
Search for file location like mythbackend does: try all storage group locations first, then locations of other storage groups before failure.  I don't know how to do that in PHP...probably stupid simple.
[/LIST]
[LIST]
Better controls (on createfile.php screen) for controlling playback (e.g., skip random time forward/back like old vlc web controls).
[/LIST]
[LIST]Much improved, minimized and stripped down wap theme.
[/LIST]
[LIST]
Return some of the interactivity of the installer script that is clearly intended by some of the disabled code in it.
[/LIST]
[LIST]
Install scripted verification of prerequisites including codecs.
[/LIST]
[LIST]
Quick pick stream settings for one-click (or minimal click) stream setup.
[/LIST]
[LIST]
Auto-discover bandwidth/latency and adjust stream settings accordingly (another quick stream setup modality...like Orb does).
[/LIST]
[LIST]
Tracking/Selecting/Reuse of groups/pools of ports and other support for multiple sessions/users (e.g., first instance runs on 8001-8002, second on 8003-4, third reuses 8001-8002 because first instance finished, etc.)
[/LIST]

---

### Post by clmbngbkng on 2009-12-19
Any more recent update on all of this? I haven't tried it yet with 9.10 but I plan on giving it a go soon as I can currently stream my WinMCE over the web but would love for Mythstreamtv to work since its more flexible with all of the recordings.

---

### Post by anonymousdog on 2009-12-21
None whatsoever AFAIK.

The critical issue is whether 9.10's VLC is fixed.  If you can stream the desired files to another PC with VLC using http or mms protocols, you should be golden.  You can test that right in the VLC GUI on both PCs (server and client).

Once past that, there may be some patches required to make it work with MythTV's newest mythweb PHP modules, but the big issue is VLC's working correctly.

---

### Post by clmbngbkng on 2009-12-21
Cool, I will look into getting it to work with VLC before anything else.

Thanks for the reply! :D

---

