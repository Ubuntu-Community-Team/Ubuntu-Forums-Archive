---
title: "Mythweb streaming issues"
date: 2008-09-23
forum: Mythbuntu
---

### Post by bah1976 on 2008-09-23
I have mythweb setup with a self-signed ssl certificate so most traffic is over port 443.  I have it configured to force streams over port 9009.  On the apache2 side of things, I have two virtual hosts setup, on 443 & 9009, and I also have basic authentication configured.  I have two problems:

1) I can't for the life of me get WMP to work.  It redirects to something that isn't valid and quits.  I get what seems to be a common but unsolved "the server has redirected you to an invalid location" error.  VLC seems to be working fairly well, but when I go to my non-linux friend's houses (I have a few) I won't be able to show off my streaming if they only have WMP.  However, that won't be a big problem if I can't fix #2:
2) Internally, everything works beautifully.  I can browse to [https://192.168.10.20/mythweb](https://192.168.10.20/mythweb), pick a recording, download the .asx and run with VLC.  It's nice...  However, if I go through my router by browsing [https://dnsname/mythweb](https://dnsname/mythweb), I can't stream.  Everything else works - all setup, listing, scheduling functions - but .asx streaming results in about 2 seconds of video before it stalls.  I have ports 443 & 9009 both open into my server, and if it were a port problem I'd expect it to not work at all.  I even tried making it the default dmz server to let everything through, but that didn't work either.

Any ideas on either problem?

---

### Post by anonymousdog on 2008-09-23
You'd have to have some mega bandwidth on both ends to do asx streaming over the internet; that's an uncompressed stream of the mpeg recording and requires LAN-strength bandwidth.

Try mythstreamtv mythweb plugin.  It uses vlc on the server to transcode recordings on the fly and stream them over tcp 8001 (with a tcp 8002 control port) -- none of it over ssl (though an ssl tunnel might work...haven't tried).  Overall, it's a bit more "fiddly" to operate than the single-click asx stream, but it's flexible enough to work in most screen/bandwidth/OS combinations from full-size LAN PCs to PDAs using Edge. 

Take a look at my most recent [tarball](http://ubuntuforums.org/showthread.php?t=922937) for Mythbuntu 8.4.x.  I've made some improvements to the official release (and over the Mythdora rpm).

---

### Post by bah1976 on 2008-09-24
that looks very promising - and cool.  But it's not working... :)

When I start up a stream I get this:
```

Starting Stream of  myth://192.168.10.20:6543/1091_20080924090642.mpg
VLC media player 0.8.6e Janus
[00000291] main interface: creating httpd
[00000295] main input error: no suitable access module for `myth://192.168.10.20:6543/1091_20080924090642.mpg'
[00000310] dummy demuxer: command `quit'
[00000287] main playlist: stopping playback
[00000001] main private error: could not create /var/www/.vlc (Permission denied)
[00000001] main private error: could not create /var/www/.vlc/cache (No such file or directory)


```

I'm thinking it may be because I wasn't sure what VLC path to use in the install script, so I used /usr/bin/vlc

Any hints?

---

### Post by anonymousdog on 2008-09-24
No, that looks like a problem with the install script.  I'll check it after work...this evening...and get back.

---

### Post by anonymousdog on 2008-09-24
Very sorry...major packaging problem.  I've posted a fixed tarball.  You can just unpack this and run the install script (as root) at /usr/share/mythstreamtv/install.sh.

---

### Post by bah1976 on 2008-09-24
Closer!  I have video, but no audio.  The log says this:
```

Starting Stream of  /var/lib/mythtv/recordings/1321_20080923200000.mpg
VLC media player 0.8.6e Janus
[00000292] main interface: creating httpd
libdvbpsi error (PSI decoder): TS discontinuity (received 7, expected 0) for PID 0
libdvbpsi error (PSI decoder): TS discontinuity (received 1, expected 0) for PID 48
libdvbpsi error (PSI decoder): TS discontinuity (received 9, expected 8) for PID 0
[00000309] a52 packetizer: A/52 channels:6 samplerate:48000 bitrate:448000
[00000314] ffmpeg encoder error: cannot find encoder MPEG Audio layer 1/2/3
[00000298] stream_out_transcode private error: cannot find encoder ((null))
[00000298] stream_out_transcode private error: cannot create audio chain
[00000309] main packetizer error: cannot create packetizer output (a52 )

```

I looked in the readme and tried to configure vlc & ffmpeg, but I can't get the commands to run - but I don't know where to run them from.  I tried to download ffmpeg from the place that  ffmpeg.sourceforge.net  sent me to, but that didn't even download right.  

ffmpeg seems to be a binary in /usr/bin - is there somewhere else I can run the ./configure from?
Other thoughts?

---

### Post by anonymousdog on 2008-09-24
Do you have Mediabuntu proprietary codecs enabled in the MCC (and ffmpeg)?  What's the output from 'vlc -list | grep encoder'?  How about 'ffmpeg -version'?  If it works with MPGA audio codec, I think there's a problem with mp3 support in your ffmpeg.

---

### Post by bah1976 on 2008-09-25
> Do you have Mediabuntu proprietary codecs enabled in the MCC (and ffmpeg)? 
I do now...
> What's the output from 'vlc -list | grep encoder'? 
```
VLC media player 0.8.6e Janus
  theora                Theora video encoder
  x264                  H.264/MPEG4 AVC encoder (using x264 library)
  araw                  Raw audio encoder
  flacdec               Flac audio encoder
  vorbis                Vorbis audio encoder
  speex                 Speex audio encoder
  ffmpeg                FFmpeg audio/video decoder/encoder ((MS)MPEG4,SVQ1,H263,WMV,WMA)
  ffmpeg                FFmpeg audio/video encoder
  dvbsub                DVB subtitles encoder
  dummy                 Dummy encoder function
```

> How about 'ffmpeg -version'? 
```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:37:31, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
ffmpeg      SVN-rUNKNOWN
libavutil   3212032
libavcodec  3352064
libavformat 3344896
```

> If it works with MPGA audio codec, I think there's a problem with mp3 support in your ffmpeg.
It does not work with MPGA codec.

I find it interesting that ffmpeg doesn't know what version it is, I'm going to work on that.  If you have any other thoughts, I'd love to hear them...

---

### Post by anonymousdog on 2008-09-25
I have these additional configuration flags on ffmpeg: --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb.  That's on a clean build from 8.4 32 bit CD and no fancy recompiling of ffmpeg, just updates and changes to packages via the GUI tools.

'dpkg-query -p ffmpeg | grep Version' should yield 'Version: 3:0.cvs20070307-5ubuntu7.1+medibuntu1'.

Try using vlc at the desktop to open one of those files and network stream it out (via whatever port) via the desires audio codecs.  I curious as to what the interactive feedback might be.

---

### Post by habajaba on 2008-11-04
Hello,
You may or may not choose to have mercy on me, but I'm having no luck elsewhere. I'm a lowly MythDora user, trying to get MythStreamTV to work. I installed it per the MythDora guys' instructions ([http://www.mythdora.com/?q=node/3325](http://www.mythdora.com/?q=node/3325)), didn't seem to have any issues there. However, when I try to hit play, I'm getting a "no suitable access module" error. I tried running vlc from the command line and I get the same error -

```
/usr/bin/vlc -I http --http-host=:8002 --sout-tr
anscode-fps=25 --sout-transcode-deinterlace myth://192.168.1.15:6543/1300_200811
03193001.mpg ":sout=#transcode{vcodec=DIV3,acodec=MPGA,vb=500,ab=128,scale=100%}
:std{access=mmsh,mux=asfh,url=:8001}"
VLC media player 0.8.6e Janus
[00000308] main interface: creating httpd
[00000313] main input error: no suitable access module for `myth://192.168.1.15:
6543/1300_20081103193001.mpg'
[00000302] main playlist: nothing to play
```

Initially I also received this error -
```
libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: Permission denied

```
But that went away after I ran VLC from the command line.

Can I get any love from the MythBuntu crowd?

Thanks in advance for any help!

---

### Post by anonymousdog on 2008-11-04
> **habajaba said:**
> Hello,
You may or may not choose to have mercy on me, but I'm having no luck elsewhere. I'm a lowly MythDora user, trying to get MythStreamTV to work. I installed it per the MythDora guys' instructions ([http://www.mythdora.com/?q=node/3325](http://www.mythdora.com/?q=node/3325)), didn't seem to have any issues there. However, when I try to hit play, I'm getting a "no suitable access module" error. I tried running vlc from the command line and I get the same error -

```
/usr/bin/vlc -I http --http-host=:8002 --sout-tr
anscode-fps=25 --sout-transcode-deinterlace myth://192.168.1.15:6543/1300_200811
03193001.mpg ":sout=#transcode{vcodec=DIV3,acodec=MPGA,vb=500,ab=128,scale=100%}
:std{access=mmsh,mux=asfh,url=:8001}"
VLC media player 0.8.6e Janus
[00000308] main interface: creating httpd
[00000313] main input error: no suitable access module for `myth://192.168.1.15:
6543/1300_20081103193001.mpg'
[00000302] main playlist: nothing to play
```

Initially I also received this error -
```
libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: Permission denied

```
But that went away after I ran VLC from the command line.

Can I get any love from the MythBuntu crowd?

Thanks in advance for any help!

That's the rpm/package from which I began with my rewrite; so, with some mods to the install script, you should be able to use my package instead.

The core issue, "no suitable access module for myth:\\", is an unresolved issue since MythTV 0.21 or 0.20; you can hack the underlying scripts to replace the "myth://192.168.1.15:6543" bits of the vlc command with a single path to all your mythtv recordings, or you can go with my rewrite that relies on storage group information to find the recordings (please see caveats in linked post).

Just remove your rpm version, follow the instructions at [this post](http://ubuntuforums.org/showthread.php?t=922937), and make sure to check/modify the options, especially your apache service account (and, to a lesser extent, your mythtvbackend service/user group), in the install.sh script before running it.  I think the other defaults will be ok for your distro.  You should check before installation whether your vlc and ffmpeg were compiled with the necessary codecs (see above).  The README file is from the original author, and the VERSIONS file isn't totally up to date.

---

