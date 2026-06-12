---
title: "Converting FLAC's to AAC"
date: 2015-01-01
forum: Multimedia Software
---

### Post by warren3 on 2015-01-01
Hi.

I'm trying to find out how to convert my FLAC library to AAC.  Unfortuntaley being a bit of a Linux newb I cannot follow the guides that are already on here as they just go over my head.

So I need to get something called ffmpeg?  I think I may already have it but I am not sure.  How would I go about checking?

When I get ffmpeg etc. how do I go about converting files?

Thanks.

---

### Post by slickymaster on 2015-01-01
If you're somewhat uncomfortable using the terminal to achieve it, there's [SoundConverter]("http://soundconverter.org/"), a Gnome HIG compliant interface.

---

### Post by ajgreeny on 2015-01-01
I prefer winff to the gnome sound-converter, but it's your choice, and unless you jump through a few hoops for ffmpeg, you may find that avconv is easier to use.

The avconv command would be something like ```
avconv -i infile.flac -codec:a libvo_aacenc -ab 128k outfile.aac
```where you can vary the audio-bitrate of the output file as you want; I show it as **-ab 128k**, but there is no point giving it more than the original file.
Just to show what the command means I will split it here into constituent parts:-
[LIST=1]
[*]**avconv** is the command line application in use.
[*]**-i infile.flac** is the file you want to convert.
[*]**-codec:a libvo_aacenc** is the codec to use for encoding the new file, ie libvo_aacenc.
[*]**-ab 128k** is the audio-bitrate you want for the output file.
[*]**outfile.aac** is the name of the output file.
[/LIST]
Similar command syntax can be used for other output file types by using different codecs, eg libmp3lame for mp3 files.

---

### Post by warren3 on 2015-01-01
> **slickymaster said:**
> If you're somewhat uncomfortable using the terminal to achieve it, there's [SoundConverter]("http://soundconverter.org/"), a Gnome HIG compliant interface.

Oh my that is one sweet program!  Many thanks!

I have just downloaded it now and ripped a FLAC album and its worked fine.  Does that mean I have everything needed installed to use the program like GStreamer etc.?  When I looked in Ubuntu Software Centre three GStreamer plugins are installed - 'extra...' 'mms...' and 'aac...', but the 'Gstreamer ffmpeg video plugin' comes up with a Not Found page.  Do I need this?

---

### Post by warren3 on 2015-01-01
> **ajgreeny said:**
> I prefer winff to the gnome sound-converter, but it's your choice, and unless you jump through a few hoops for ffmpeg, you may find that avconv is easier to use.

The avconv command would be something like ```
avconv -i infile.flac -codec:a libvo_aacenc -ab 128k outfile.aac
```where you can vary the audio-bitrate of the output file as you want; I show it as **-ab 128k**, but there is no point giving it more than the original file.
Just to show what the command means I will split it here into constituent parts:-
[LIST=1]
[*]**avconv** is the command line application in use. 
[*]**-i infile.flac** is the file you want to convert. 
[*]**-codec:a libvo_aacenc** is the codec to use for encoding the new file, ie libvo_aacenc. 
[*]**-ab 128k** is the audio-bitrate you want for the output file. 
[*]**outfile.aac** is the name of the output file. 
[/LIST]
Similar command syntax can be used for other output file types by using different codecs, eg libmp3lame for mp3 files.

Thanks.  So avconv is built into Ubuntu and I just need to use the terminal with the above code to convert my files?

---

### Post by ajgreeny on 2015-01-01
> **warren3 said:**
> Thanks.  So avconv is built into Ubuntu and I just need to use the terminal with the above code to convert my files?Yes, more or less.

Use terminal to change to the flac folder
```
cd /path/to/folder
```
then use that command, changing the input file and output file names to suit.

I am sure it is possible to use a script using variables to put all the files into that command and rename them accordingly, but that takes a bit more explaining, and I have never needed to use it, so I am not sure how to do it.

---

### Post by mc4man on 2015-01-01
> **warren3 said:**
> Thanks.  So avconv is built into Ubuntu and I just need to use the terminal with the above code to convert my files?
No you need to install the  **libav-tools** package.
Also you need to install libavcodec-extra-XX to enable aac encoding thru avconv (XX would be dependent on which Release of Ubuntu you have, ie. 14.04 (trusty) or 14.10 (utopic) which you haven't posted.

additionally if you want tags on your flac > aac files then don't output to .aac as in above posted command, use .m4a instead

As far as the gstreamer0.10-ffmpeg, you don't need it for sound-converter for your present use. It would only add the ability to convert a couple of other formats like some .wma, ect.

(- if you did need the gstreamer0.10-ffmpeg plugin then I moved packages from a heavily populated ppa to a standalone - 
[https://launchpad.net/~mc3man/+archive/ubuntu/gstffmpeg-keep](https://launchpad.net/~mc3man/+archive/ubuntu/gstffmpeg-keep)

---

### Post by slickymaster on 2015-01-01
> **warren3 said:**
> Oh my that is one sweet program!  Many thanks!

I have just downloaded it now and ripped a FLAC album and its worked fine.  Does that mean I have everything needed installed to use the program like GStreamer etc.?  When I looked in Ubuntu Software Centre three GStreamer plugins are installed - 'extra...' 'mms...' and 'aac...', but the 'Gstreamer ffmpeg video plugin' comes up with a Not Found page.  Do I need this?

The FFmpeg plugin for GStreamer 0.10 is not available in the official Ubuntu 14.04 repositories. See this [bug]("https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-ffmpeg/+bug/1275556").

A possible workaround is to install it by using a PPA:```
sudo add-apt-repository ppa:mc3man/trusty-media
sudo apt-get update
sudo apt-get install gstreamer0.10-ffmpeg
```

---

### Post by warren3 on 2015-01-01
Thank you everyone.  Now I know what I need and don't need.

Sound Converter vs avconv - are there any sound quality differences between the two for FLAC to aac conversion?

Just another little question.  When you see code like this for the terminal:
```

sudo add-apt-repository ppa:mc3man/trusty-media
sudo apt-get update
sudo apt-get install gstreamer0.10-ffmpeg
```

or 
```

sudo add-apt-repository ppa:mc3man/trusty-media
sudo apt-get update
sudo apt-get install gstreamer0.10-ffmpeg
```

Does that mean you can copy and paste it all and run it or do you need to run it line by line?  Its something I have always wanted to ask.

P.S. I just love Ubuntu.  Next week I am going full time Ubuntu.  I was going to buy another Windows 7 OEM licence but I now think Ubuntu covers everything I need to do on a computer so no need for dual boot anymore!  No more Micro$oft for me.  Plus my Windows install on the dual boot refuses to load now so maybe its a sign.

---

### Post by mc4man on 2015-01-01
> **warren3 said:**
> Thank you everyone.  Now I know what I need and don't need.

Sound Converter vs avconv - are there any sound quality differences between the two for FLAC to aac conversion?

Just another little question.  When you see code like this for the terminal:

sudo add-apt-repository ppa:mc3man/trusty-media
sudo apt-get update
sudo apt-get install gstreamer0.10-ffmpeg

or 

sudo add-apt-repository ppa:mc3man/trusty-media
sudo apt-get update
sudo apt-get install gstreamer0.10-ffmpeg

Does that mean you can copy and paste it all and run it or do you need to run it line by line?  Its something I have always wanted to ask.

P.S. I just love Ubuntu.  Next week I am going full time Ubuntu.  I was going to buy another Windows 7 OEM licence but I now think Ubuntu covers everything I need to do on a computer so no need for dual boot anymore!  No more Micro$oft for me.  Plus my Windows install on the dual boot refuses to load now so maybe its a sign.
Warren3 - 
I think you should use the ppa I linked to get the gstreamer plugin. As far as the media ppa it's quite extensive & if you do decide to use it please go to the [ppa page first]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media") & read thru *before* deciding to use.
Thanks

---

### Post by andrew.46 on 2015-01-03
This needs a little bit of script work (at least to preserve the meta-tags) but something like [the following]("http://wiki.hydrogenaud.io/index.php?title=Fraunhofer_FDK_AAC#Examples") will give the best sound quality:

```

flac -s -d -c test.flac | \
     fdkaac --ignorelength --profile 2 --bitrate-mode 5 \
     -o test.m4a -

```

Now if some kind person would add in some meta-tag stripping + re-adding, wrap it in some find syntax this would be the easiest and most straightforward way, as well as giving superior sound  :).

---

### Post by Bucky Ball on 2015-01-03
You copy and paste each line one at a time, hitting enter after each and letting it do its thing.

Yes, Sound Converter rocks. ;)

---

