---
title: "Anyone get FUPPES / Image transcoding working?"
date: 2009-06-01
forum: Multimedia Software
---

### Post by arc2v on 2009-06-01
Hi all,
I got FUPPES working over the weekend.  It streams video and audio both transcoded and plain to my Xbox.

I can view photos on the Xbox, just fine in jpg format.  However they are very large and take a few seconds to update.  At the least, I would like to resize them down to the projector native format, maybe even smaller to speed things up.  That alone should make the images 1/3 the original size.

Anyway, the ImageMagick or Magick-Wand doesn't appear to work.  When I enable it, the images show up as a rectangle with an X.  The debug log says it's transcoding, and it shows the transcoding plugin as being enabled, meaning it found the object library on startup.

I tried running as root and regular user, in case it was a directory permissions issue.  No luck.

I'm running Jaunty Ubuntu, fairly clean install -- nothing major updated except for the fuppes dependencies.

I submitted this as a bug to the official FUPPES site, but haven't heard anything back.

Please respond if you have gotten this to work with any distro of FUPPES/Ubuntu.  Maybe we can compare library locations and config files to see what's awry.

Thanks in advance,
Anthony

---

### Post by mibu on 2009-06-14
Hi, Anthony,

I run 8.04 and fuppes is already streaming to my Phillips 8404 TV.

That was done with the standard setup including a directory with some jpeg and inserting the correct interface to the fuppes.cfg.

After that it became weird. I tried to transcode flv-files to mp4 or mpg, but ffmpeg produces no output. (invoking ffmpeg manually produces mpg or avi-files, which can be streamed) 

As you do I would like to convert jpg-files to smaller jpg-files, but if I put convert=true there is no file to get anymore from my tv - converting does not work.

Checking the installation and reading a lot of threads and postings I did run outoreconf and configure with a lot of options, after I installed a lot ( >25 ? ) of libs: 
[FONT=monospace]
[/FONT]autoreconf -vfi
 ./configure --prefix=/usr --enable-gpl --enable-pp --enable-pthreads --enable-liba52 --enable-libdc1394 --enable-libfaac --enable-libfaad --enable-libgsm --enable-libtwolame --enable-libmp3lame --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-shared --enable-pp --enable-pthreads --enable-video-transcoding --enable-transcoding --enable-lame --enable-twolame --enable-faad --enable-mad --enable-exiv2 --enable-dnla --enable-flac --enable-taglib --enable-magickwand --enable-vorbis --enable-tremor --enable-musepack --enable-mp4v2

Nearly everythin is recognized, except of exiv2::

  SUMMARY

  audio transcoding plugins
    encoder:
      lame       : yes
      twolame    : yes
      pcm/wav    : yes
    decoder:
      vorbis     : yes (libvorbisfile)
      mpc        : yes
      flac       : yes
      faad       : yes (aac/mp4/m4a)
      mad        : yes (mpeg Layer I, II & III)

  video transcoding plugins
    ffmpeg     : enabled

  image conversion/rescaling plugins
    ImageMagick: enabled  (Wand C-API)

  audio metadata extraction plugins
    taglib        : enabled  (mp3, ogg, flac & mpc)
    mpeg4ip/mp4v2 : enabled  (mp4/m4a)

  image metadata extraction plugins
    Exiv2         : disabled
    ImageMagick   : enabled  (Wand C-API)
    simage        : enabled  (jpeg, png, gif, tiff, rgb, pic, tga, eps)

  video metadata extraction plugins
    libavformat   : enabled

  miscellaneous
    iconv      : enabled (charset conversion)
    uuid       : enabled
    inotify    : enabled

Thanks for using fuppes
please report bugs

But if I start fuppes (as root) and type i I don't understand the result:

general information:
  version     : 0.636
  hostname    : media
  OS          : Linux 2.6.24-16-generic
  build at    : Jun 14 2009 17:20:49
  build with  : 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
  address     : 192.168.0.7
  sqlite      : 
  log-level   : 1 (normal)
  webinterface: [http://192.168.0.7:1234/](http://192.168.0.7:1234/)

configuration file:
  /root/.fuppes/fuppes.cfg

faad: disabled
flac: disabled
iconv: enabled
ImageMagick++: disabled
ImageMagick Wand: disabled
inotify: enabled
lame: disabled
libavformat: enabled
libnotify: disabled
mad: disabled
mp4ff: disabled
mpeg4ip: disabled
musepack: disabled
simage: disabled
inotify: enabled
taglib: disabled
tremor: disabled
twolame: disabled
uuid: enabled
vorbis: disabled

With this info I understand that transcoding is not working, even if I do the cfg-file right. But why are all these codexs disabled even if in configure they are recognized?
What to do? 

regards
michael

---

