---
title: "[HOWTO] Install Last.FM / Scrobbler plugin in Audacious2 on Lucid Lynx"
date: 2010-04-30
forum: Multimedia Software
---

### Post by togdon on 2010-04-30
The Audacious developers have removed support for Last.FM / Scrobbler in the most recent version. See [http://boards.audacious-media-player.org/viewtopic.php?f=3&t=112&p=408](http://boards.audacious-media-player.org/viewtopic.php?f=3&t=112&p=408) for why.

I've successfully built the 2.2 plugin against 2.3 on Ubuntu Lucid (which just updated to 2.3). Here's (roughly) what I did.

```
sudo aptitude install libcurl4-dev

wget http://distfiles.atheme.org/audacious-plugins-2.2.tgz

tar -zxvf audacious-plugins-2.2.tgz

cd audacious-plugins-2.2

./configure --enable-dependency-tracking --disable-esd --disable-pulse \
--disable-coreaudio --disable-icecast --disable-dockalbumart --disable-altivec \
--disable-sse2 --disable-mp3 --disable-libmadtest --disable-rocklight \
--disable-lirc --disable-evdevplug --disable-hotkey --disable-gnomeshortcuts \
--disable-statusicon --disable-aosd --disable-aosd-xcomp --disable-adplug \
--disable-vorbis --disable-flacng --disable-libFLACtest --disable-wavpack \
--disable-aac --disable-sndfile --disable-modplug --disable-ffaudio \
--disable-jack --disable-sid --disable-oss --disable-oss4 --disable-alsa \
--disable-amidiplug --disable-amidiplug-alsa --disable-amidiplug-flsyn \
--disable-amidiplug-dummy --disable-cdaudio --disable-streambrowser \
--enable-scrobbler --enable-lastfm --disable-neon --disable-mms \
--disable-mtp_up --disable-bluetooth --disable-paranormal --disable-xspf \
--disable-xmltest --disable-cue --disable-projectm --disable-projectm-1.0 \
--disable-filewriter --disable-filewriter_mp3 --disable-filewriter_vorbis \
--disable-filewriter_flac --disable-bs2b


cd src/scrobbler/

make

sudo make install

cd ../lastfm/

make

sudo make install
```

It's definitely scrobbling, beyond that I haven't bothered figuring out what's broken or how one would play the last.fm radio (I never use it, so I don't care). I briefly looked into making a package but it's too much of a hassle, I'm assuming either someone else will or people will just move on to another player.

Hope this helps and that someone else will slog through the mess of making it into a package.

---

### Post by iuz on 2010-04-30
A prerequisite is having the audacious-dev package installed. 

After installing the scrobbler plugin is added to the General plugins tab in the Audacious preferences. I can confirm that it works just fine.

---

### Post by trpnblies7 on 2010-05-04
Would someone be able to just post the plugin for download? Or does it actually require building on my specific machine?

---

### Post by fly5 on 2010-05-07
> **trpnblies7 said:**
> Would someone be able to just post the plugin for download? Or does it actually require building on my specific machine?

i have no knowledge of that, but if you want you can try if my plugins work.
```
cd ~
wget http://fly5.kapsi.fi/misc/misc/aud2scrob/lastfm.so
wget http://fly5.kapsi.fi/misc/misc/aud2scrob/scrobbler.so
mv lastfm.so scrobbler.so ~/.local/share/audacious/Plugins/
```

this way there are no images included in settings, but i don't mind that. all i wanted was scrobbling.

---

### Post by trpnblies7 on 2010-05-08
Those work great. Thanks!

---

### Post by hamstah on 2010-05-12
Tested here too, works perfectly.
Thanks

---

### Post by breta on 2010-05-13
> **fly5 said:**
> i have no knowledge of that, but if you want you can try if my plugins work. ... 

 Hi, would you mind to post somewhere the source codes to the plugins? I am using Debian Sid (testing) and I would like to try to compile and use the plugins as well (if it is not very obvious how to compile them, please add some brief howto, thanks), because I miss the scrobbler plugin.  Best regards b.

---

### Post by breta on 2010-05-19
> **breta said:**
> Hi, would you mind to post somewhere the source codes to the plugins? I am using Debian Sid (testing) and I would like to try to compile and use the plugins as well (if it is not very obvious how to compile them, please add some brief howto, thanks), because I miss the scrobbler plugin.  Best regards b.

 Thanks fly5, I didn't understand from your post, that you present on your page compiled sources from the top post, I thought that you made your own plugins...

---

### Post by santa17 on 2010-05-27
Hi,
thanks for the code and plugins, however the plugins provided by **fly5** didn't work for me (maybe cause x86_64). Little tweeking of **togdon**'s code worked just fine:

```

sudo aptitude install libcurl4-openssl-dev 
sudo aptitude install audacious-dev

wget http://distfiles.atheme.org/audacious-plugins-2.2.tgz
tar -zxf audacious-plugins-2.2.tgz
cd audacious-plugins-2.2

# export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:/usr/lib/pkgconfig # this shouldn't be necessary

./configure --enable-dependency-tracking --disable-esd --disable-pulse \
--disable-coreaudio --disable-icecast --disable-dockalbumart --disable-altivec \
--disable-sse2 --disable-mp3 --disable-libmadtest --disable-rocklight \
--disable-lirc --disable-evdevplug --disable-hotkey --disable-gnomeshortcuts \
--disable-statusicon --disable-aosd --disable-aosd-xcomp --disable-adplug \
--disable-vorbis --disable-flacng --disable-libFLACtest --disable-wavpack \
--disable-aac --disable-sndfile --disable-modplug --disable-ffaudio \
--disable-jack --disable-sid --disable-oss --disable-oss4 --disable-alsa \
--disable-amidiplug --disable-amidiplug-alsa --disable-amidiplug-flsyn \
--disable-amidiplug-dummy --disable-cdaudio --disable-streambrowser \
--enable-scrobbler --enable-lastfm --disable-neon --disable-mms \
--disable-mtp_up --disable-bluetooth --disable-paranormal --disable-xspf \
--disable-xmltest --disable-cue --disable-projectm --disable-projectm-1.0 \
--disable-filewriter --disable-filewriter_mp3 --disable-filewriter_vorbis \
--disable-filewriter_flac --disable-bs2b


cd src/scrobbler/
make
cd ../lastfm/
make

cp lastfm.so ../scrobbler/scrobbler.so ~/.local/share/audacious/Plugins/.

```

Actuall plugins can be downloaded here:
[http://http://drop.io/audacious_scrobbler_plugin_64]("http://drop.io/audacious_scrobbler_plugin_64")

Cheers.

---

### Post by fululian on 2010-06-11
> **fly5 said:**
> i have no knowledge of that, but if you want you can try if my plugins work.
```
cd ~
wget http://fly5.kapsi.fi/misc/misc/aud2scrob/lastfm.so
wget http://fly5.kapsi.fi/misc/misc/aud2scrob/scrobbler.so
mv lastfm.so scrobbler.so ~/.local/share/audacious/Plugins/
```

this way there are no images included in settings, but i don't mind that. all i wanted was scrobbling.
Thanks a bunch dude.

---

### Post by Koala Kid on 2010-06-11
> **fly5 said:**
> i have no knowledge of that, but if you want you can try if my plugins work.
```
cd ~
wget http://fly5.kapsi.fi/misc/misc/aud2scrob/lastfm.so
wget http://fly5.kapsi.fi/misc/misc/aud2scrob/scrobbler.so
mv lastfm.so scrobbler.so ~/.local/share/audacious/Plugins/
```

this way there are no images included in settings, but i don't mind that. all i wanted was scrobbling.
Works here. Thank you very much.

---

### Post by Richard85 on 2010-06-24
I was a bit nervous about inputting all that code but in the end everything worked out fine! Works great!

---

### Post by nutellajunkie on 2010-09-10
> **togdon said:**
> I've successfully built the 2.2 plugin against 2.3 on Ubuntu Lucid (which just updated to 2.3). Here's (roughly) what I did.

Thank you very much, this is very greatly appreciated. By default, any of our linux audio players should have last.fm plug-ins.

---

### Post by Patyczak on 2010-09-10
Audacious 2.4 has scrobbler.

Just compile it from source.

---

### Post by UlrihRekkenin on 2010-10-01
> **fly5 said:**
> 

```
cd ~
wget http://fly5.kapsi.fi/misc/misc/aud2scrob/lastfm.so
wget http://fly5.kapsi.fi/misc/misc/aud2scrob/scrobbler.so
mv lastfm.so scrobbler.so ~/.local/share/audacious/Plugins/
```
Good! It works perfect!

---

### Post by UlrihRekkenin on 2010-10-01
Carramba!
Lastfm scrobbled just one song... What`s up? I didnt change anythings.

Oleg.

---

### Post by leoremons on 2010-10-09
> **santa17 said:**
> Hi,
thanks for the code and plugins, however the plugins provided by **fly5** didn't work for me (maybe cause x86_64). Little tweeking of **togdon**'s code worked just fine:

```

sudo aptitude install libcurl4-openssl-dev 
sudo aptitude install audacious-dev

wget http://distfiles.atheme.org/audacious-plugins-2.2.tgz
tar -zxf audacious-plugins-2.2.tgz
cd audacious-plugins-2.2

# export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:/usr/lib/pkgconfig # this shouldn't be necessary

./configure --enable-dependency-tracking --disable-esd --disable-pulse \
--disable-coreaudio --disable-icecast --disable-dockalbumart --disable-altivec \
--disable-sse2 --disable-mp3 --disable-libmadtest --disable-rocklight \
--disable-lirc --disable-evdevplug --disable-hotkey --disable-gnomeshortcuts \
--disable-statusicon --disable-aosd --disable-aosd-xcomp --disable-adplug \
--disable-vorbis --disable-flacng --disable-libFLACtest --disable-wavpack \
--disable-aac --disable-sndfile --disable-modplug --disable-ffaudio \
--disable-jack --disable-sid --disable-oss --disable-oss4 --disable-alsa \
--disable-amidiplug --disable-amidiplug-alsa --disable-amidiplug-flsyn \
--disable-amidiplug-dummy --disable-cdaudio --disable-streambrowser \
--enable-scrobbler --enable-lastfm --disable-neon --disable-mms \
--disable-mtp_up --disable-bluetooth --disable-paranormal --disable-xspf \
--disable-xmltest --disable-cue --disable-projectm --disable-projectm-1.0 \
--disable-filewriter --disable-filewriter_mp3 --disable-filewriter_vorbis \
--disable-filewriter_flac --disable-bs2b


cd src/scrobbler/
make
cd ../lastfm/
make

cp lastfm.so ../scrobbler/scrobbler.so ~/.local/share/audacious/Plugins/.

```

Actuall plugins can be downloaded here:
[http://http://drop.io/audacious_scrobbler_plugin_64]("http://drop.io/audacious_scrobbler_plugin_64")

Cheers.
Great 

I downloaded the files from : [http://http://drop.io/audacious_scrobbler_plugin_64](http://http://drop.io/audacious_scrobbler_plugin_64)

It worked for me like a magic... hehe he!!

Thanks santa17

---

### Post by Mr.Dunham on 2011-06-10
> **fly5 said:**
> if you want you can try if my plugins work.
```
cd ~
wget http://fly5.kapsi.fi/misc/misc/aud2scrob/lastfm.so
wget http://fly5.kapsi.fi/misc/misc/aud2scrob/scrobbler.so
mv lastfm.so scrobbler.so ~/.local/share/audacious/Plugins/
```

this way there are no images included in settings, but i don't mind that. all i wanted was scrobbling.

Sorry for digging up this old thread, but I just wanted to say thank you very much for this.

I just did a clean install of Xubuntu 10.04.2 and installed Audacious and plugins, the scrobbler plugin was supposed to be there but it wasn't; so I got those plugins and they're working fine.

I also wanted to post this reply so anyone else who's getting the same issue could fix it in such an easy way.

Once again, thank you very much.

---

