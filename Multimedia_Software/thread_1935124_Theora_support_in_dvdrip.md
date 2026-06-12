---
title: "Theora support in dvd:rip"
date: 2012-03-03
forum: Multimedia Software
---

### Post by tanoloco on 2012-03-03
Hello,

I usually rip dvds using dvd::rip using ffmpeg as video codec and vorbis as audio codec.

In the drop down list of the "ffmpeg/af6 codec" I can oly choose between mpeg4 and h264.

As my ffmpeg also supports theora, I would like to know I could I add theora support in dvd::rip too.

I googled a lot without finding a way .. only this old [thread]("http://osdir.com/ml/video.dvdrip.user/2003-12/msg00041.html") indicates to change the combo box of the codec widget but without saying how ..

Is there anyone knowing this?

Alternatively as dvd::rip uses ffmpeg, is there a way to know which command it uses while you rip a dvd? In this way I would easily change the ffmpeg command to use libtheora instead.

Thanks in advance for any help

---

### Post by tanoloco on 2012-03-03
Ok.. I found that in /usr/share/perl5/Video/DVDRip/GUI/Context.pm you can change the dropdown list of the ffmpeg codecs ..

I changed
```
tc_video_af6_codec_presets => [ "mpeg4", "h264" ],
```
to
```
tc_video_af6_codec_presets => [ "mpeg4", "h264", "libtheora" ],
```

and actually the dropdown menu shows libtheora too .. but choosing it I get a long error which basically says:
```
Command exits with failure code:
Command: mkdir -m 0775 -p '/home/foo/dvdrip-data/input/tmp' && cd /home/foo/dvdrip-data/input/tmp && mkdir -p /home/foo/dvdrip-data/input/avi/001 && execflow -n 19 **transcode** -H 10 -a 0 -T 1,-1,1 -x dvd -i \/media\/mymount -w 1728,50 **-F libtheora** -b 192 --a52_drc_off -f 24,1 -Z 640x360 -R 1 -y ffmpeg,ogg -m /home/foo/dvdrip-data/input/avi/001/output.ogm -E 44100 -J resample -o /dev/null --progress_meter 2 --progress_rate 25 && echo EXECFLOW_OK

``` 

So doing that, I discover that dvd::rip doesn't use ffmpeg as I thought .. it still tries to rip the dvd using **transcode**!

So now ... as dvd::rip works like that and I don't know much about transcode would you please help me in:
1. understand if transcode support theora?
2. understand if my transcode support theora?
3. which codec string am I supposed to use as -F parameter so I can put it in the above dropdown list accordingly?

I cannot find those information by myself .. it seems from my googlings that transcode doesn't support theora at all .. and this surprise me a lot :|

On a side note can anyone explain me why if I choose ffmpeg as video codec dvd::rip still uses transcode? Isn't this confusing?

---

### Post by tanoloco on 2012-03-03
The transcode [manual]("http://transcoding.org/transcode?Building_Transcode") says that one can build transcode with theora support enabling it with --enable-theora while use ./configure .. it seems that it's disabled by default :(

So apparently transcode can support theora .. I can I know if my version
```
$ transcode -v
transcode v1.1.5 (C) 2001-2003 Thomas Oestreich, 2003-2009 Transcode Team

```
which the one in the repository of Lubuntu 11.10 Oneiric was built with such a support before trying to rebuild it? ...

I can I get a list of codecs supported by my transcode?

---

### Post by tanoloco on 2012-03-03
In the [buildlog]("https://launchpadlibrarian.net/78795710/buildlog_ubuntu-oneiric-i386.transcode_3%3A1.1.5-0ubuntu9_BUILDING.txt.gz") on launchpad it's written that the version in the repository was already built with the --enable-theora configuration option enabled ..

According to the transcode [man page]("http://manpages.ubuntu.com/manpages/lucid/man1/transcode.1.html")
> -F  codec_string
           encoder parameter strings [module dependent]. The -F parameter has
           different meanings for different export modules. Those meanings are
           documented in transcode_export(1) manual page.

while in transcode_export [man page]("http://manpages.ubuntu.com/manpages/lucid/man1/transcode_export.1.html") I cannot see theora mentioned .. so what can I do?

---

### Post by tanoloco on 2012-03-03
If a run the above transcode commad without the -F option I get a long error with the following lines in it:
```
You must chose a codec by supplying '-F <codecname>'. A list of supported codecs can be obtained with 'transcode -y ffmpeg -F list'.
```

If I type
```
$ transcode -y ffmpeg -F list
[transcode] critical: no input sources avalaible
```

I'm getting crazy here !!

Anyone can help me?
I'm one step away from giving it up :(

---

