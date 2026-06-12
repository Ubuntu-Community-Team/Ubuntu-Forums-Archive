---
title: "Adding kernel module options, where in Ubuntu??"
date: 2006-02-23
forum: Multimedia &amp; Video
---

### Post by speedsix on 2006-02-23
I need the OSS emulation module *snd-pcm-oss* to output to the digital spdif instead of the anolog.

Apparently I have to include the option;
```
options snd-pcm-oss dsp_map=2
```

Problem is I don't know where to put it. I seem to have..

/etc/modprobe.d/alsa-base
/etc/modutils/alsa-base

and also
/etc/modules

I've tried adding the option to all 3 of these but no joy, where do module options go in ubuntu and do I have to run anything after to update it?

I tried a test setting XMMS to output via OSS and it plays but no sound, which leads me to believe it's outputting via analog(cannot test for sure) and ignoring the option I added. Using 'aoss' works with some programs but not others (i.e Skype)


Many thanks

Dom

---

### Post by az on 2006-02-24
[QUOTE=speedsix]I need the OSS emulation module *snd-pcm-oss* to output to the digital spdif instead of the anolog.

Apparently I have to include the option;
```
options snd-pcm-oss dsp_map=2
```

Problem is I don't know where to put it. I seem to have..

/etc/modprobe.d/alsa-base
/etc/modutils/alsa-base

and also
/etc/modules

I've tried adding the option to all 3 of these but no joy, where do module options go in ubuntu and do I have to run anything after to update it?

I tried a test setting XMMS to output via OSS and it plays but no sound, which leads me to believe it's outputting via analog(cannot test for sure) and ignoring the option I added. Using 'aoss' works with some programs but not others (i.e Skype)


Many thanks

Dom[/QUOTE]

/etc/modprobe.d/sound 

[http://ubuntuforums.org/showpost.php?p=640288&postcount=2](http://ubuntuforums.org/showpost.php?p=640288&postcount=2)

---

### Post by speedsix on 2006-03-01
Thanks


For what it's worth, you do not need this option when using a digital connection, it seems to pick it up from your alsa config. My problem was /dev/dsp was only accessible by root.

---

