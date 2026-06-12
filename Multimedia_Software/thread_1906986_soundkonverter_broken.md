---
title: "soundkonverter broken"
date: 2012-01-10
forum: Multimedia Software
---

### Post by Aisteru on 2012-01-10
I interrupted soundkonverter during an operation, & now it won't start. 

When I try to start it from the terminal I get this:

```


soundkonverter(26208)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/soundkonverter_codec_lame.so" does not offer a qt_plugin_instance function.
soundkonverter(26208)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/soundkonverter_codec_flac.so" does not offer a qt_plugin_instance function.
soundkonverter(26208)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/soundkonverter_codec_timidity.so" does not offer a qt_plugin_instance function.
soundkonverter(26208)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/soundkonverter_codec_musepack.so" does not offer a qt_plugin_instance function.
soundkonverter(26208)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/soundkonverter_codec_neroaac.so" does not offer a qt_plugin_instance function.
soundkonverter(26208)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/soundkonverter_codec_twolame.so" does not offer a qt_plugin_instance function.
soundkonverter(26208)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/soundkonverter_codec_shorten.so" does not offer a qt_plugin_instance function.
soundkonverter(26208)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/soundkonverter_codec_faac.so" does not offer a qt_plugin_instance function.
soundkonverter(26208)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/soundkonverter_codec_mac.so" does not offer a qt_plugin_instance function.
soundkonverter(26208)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/soundkonverter_codec_ffmpeg.so" does not offer a qt_plugin_instance function.
soundkonverter(26208)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/soundkonverter_codec_wavpack.so" does not offer a qt_plugin_instance function.
soundkonverter(26208)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/soundkonverter_codec_flake.so" does not offer a qt_plugin_instance function.
soundkonverter(26208)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/soundkonverter_codec_vorbistools.so" does not offer a qt_plugin_instance function.
soundkonverter(26208)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/soundkonverter_codec_mplayer.so" does not offer a qt_plugin_instance function.
soundkonverter(26208)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/soundkonverter_replaygain_musepackgain.so" does not offer a qt_plugin_instance function.
soundkonverter(26208)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/soundkonverter_replaygain_aacgain.so" does not offer a qt_plugin_instance function.
soundkonverter(26208)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/soundkonverter_replaygain_vorbisgain.so" does not offer a qt_plugin_instance function.
soundkonverter(26208)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/soundkonverter_replaygain_mp3gain.so" does not offer a qt_plugin_instance function.
soundkonverter(26208)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/soundkonverter_replaygain_wvgain.so" does not offer a qt_plugin_instance function.
soundkonverter(26208)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/soundkonverter_replaygain_metaflac.so" does not offer a qt_plugin_instance function.
soundkonverter(26208)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/soundkonverter_ripper_cdparanoia.so" does not offer a qt_plugin_instance function.
ICE default IO error handler doing an exit(), pid = 26208, errno = 32
unnamed app(26207): Communication problem with  "soundkonverter" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" " 


```I've tried purging & re-installing, but to no avail.
I am using xubuntu 11.10

Any ideas? Thanks in advance.

---

### Post by Aisteru on 2012-02-25
Bump.

---

### Post by winh8r on 2012-02-25
Probably easiest to do 

```
sudo apt-get remove soundkonverter --purge
```


then run 

```
sudo apt-get install soundkonverter
```

Just be sure to check what else will be affected by removing it though before you run the remove --purge command.

hope this helps.

---

### Post by Aisteru on 2012-02-25
Thanks for the reply.

I've tried purging & re-installing, but to no avail.

I guess using the --purge option must not have removed the right thing.

---

### Post by winh8r on 2012-02-25
you could open a terminal and try:

```
locate soundkonverter
```


this will show everything connected with soundkonverter installed on your system and you can manually remove them if the remove /purge option is not working as it should.

---

### Post by Aisteru on 2012-02-25
Thank you, that seems to have done it. Although the locate command still  reported things there after I had deleted them. Anyway, it is working  now. Thanks again. :-)

---

### Post by winh8r on 2012-02-26
No problem.

Glad you got it working again.

Good luck

---

