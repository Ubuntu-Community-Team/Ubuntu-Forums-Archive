---
title: "A great Library Music Player: Cantata with mpd"
date: 2015-07-20
forum: Multimedia Software
---

### Post by shantiq on 2015-07-20
[[IMG]http://s20.postimg.org/n8jfpzjq1/image.png[/IMG]]("http://postimg.org/image/n8jfpzjq1/")    click on the I icon and all this shows up     [[IMG]http://s20.postimg.org/erjxf2f15/image.png[/IMG]]("http://postimg.org/image/erjxf2f15/")



I am running this on 14.04 with LXDE desktop environment [0.18.7 in repo][available MPD 0.19.10 released
June 21, 2015]

To get most recent versions >>

```
sudo add-apt-repository ppa:jean-francois-dockes/mpd
sudo apt-get update ; sudo apt-get install mpd
```
```
sudo add-apt-repository ppa:ubuntuhandbook1/cantata
sudo apt-get update ; sudo apt-get install cantata
```

where mpd is the music player and cantata the client

info:
[http://www.musicpd.org/doc/user/config.html](http://www.musicpd.org/doc/user/config.html)
[https://wiki.archlinux.org/index.php/Music_Player_Daemon#Setup](https://wiki.archlinux.org/index.php/Music_Player_Daemon#Setup)

To make sure mpd starts everytime you start up



Copy and Place the following in   ~/.config/autostart/

save as >>  ~/.config/autostart/**mpd.desktop**

```
[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=Music Player Daemon
Comment=Server for playing audio files
Exec=mpd
StartupNotify=false
Terminal=false
Hidden=false
X-GNOME-Autostart-enabled=false
```




Playback Formats available !! **  includes cue zips [and actually works] **etc plays ALL formats it seems ...

```
Music Player Daemon 0.19.9

Copyright (C) 2003-2007 Warren Dukes <warren.dukes@gmail.com>
Copyright (C) 2008-2014 Max Kellermann <max@duempel.org>
This is free software; see the source for copying conditions.  There is NO
warranty; not even MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


Database plugins:
 simple proxy upnp

Storage plugins:
 local smbclient nfs

Neighbor plugins:
 smbclient upnp

Decoders plugins:
 [mad] mp3 mp2
 [mpg123] mp3
 [vorbis] ogg oga
 [oggflac] ogg oga
 [flac] flac
 [opus] opus ogg oga
 [sndfile] wav aiff aif au snd paf iff svx sf voc w64 pvf xi htk caf sd2
 [dsdiff] dff
 [dsf] dsf
 [faad] aac
 [mpcdec] mpc
 [wavpack] wv
 [modplug] 669 amf ams dbm dfm dsm far it med mdl mod mtm mt2 okt s3m stm ult umx xm
 [mikmod] amf dsm far gdm imf it med mod mtm s3m stm stx ult uni xm
 [sidplay] sid mus str prg P00
 [wildmidi] mid
 [fluidsynth] mid
 [adplug] amd d00 hsc laa rad raw sa2
 [ffmpeg] 16sv 3g2 3gp 4xm 8svx aa3 aac ac3 afc aif aifc aiff al alaw 
amr anim apc ape asf atrac au aud avi avm2 avs bap bfi c93 cak cin cmv
 cpk daud dct divx dts dv dvd dxa eac3 film flac flc fli fll flx flv g726 gsm 
gxf iss m1v m2v m2t m2ts m4a m4b m4v mad mj2 mjpeg mjpg mka mkv 
mlp mm mmf mov mp+ mp1 mp2 mp3 mp4 mpc mpeg mpg mpga mpp mpu 
mve mvi mxf nc nsv nut nuv oga ogm ogv ogx oma ogg omg opus psp pva qcp 
qt r3d ra ram rl2 rm rmvb roq rpl rvc shn smk snd sol son spx str swf tgi tgq 
tgv thp ts tsp tta xa xvid uv uv2 vb vid vob voc vp6 vmd wav webm wma wmv wsaud wsvga wv wve
 [gme] ay gbs gym hes kss nsf nsfe sap spc vgm vgz
 [pcm]

Output plugins:
 shout null fifo pipe alsa roar ao oss openal pulse jack httpd recorder

Encoder plugins:
 null vorbis opus lame wave flac

Archive plugins:
 [bz2] bz2
 [zzip] zip
 [iso] iso

Input plugins:
 file alsa archive curl ffmpeg smbclient nfs mms cdio_paranoia


```


**and the shortcuts/hotkeys really work too...**

---

### Post by bapoumba on 2015-07-20
Soft Machine :)

---

### Post by shantiq on 2015-07-20
yea bapoumba I am that old :] and still in love ...

---

### Post by bapoumba on 2015-07-20
Well, that makes two of us :)
And there is at least another one here I know of.
/me stops the off topic ;)

---

### Post by shantiq on 2015-07-20
yes    ...     Cantata a nice player here for guys seeking a library-type itunes-like piece of kit  ...    [aTunes]("http://ubuntuforums.org/showthread.php?t=2285566&p=13321381#post13321381") is quite good too but a tad buggy ..    of course Clementine is the modern one but hey the more the merrier ...

---

### Post by arias2 on 2015-08-13
Interesting and thanks for the repo info. Are there any capabilities that you see available that makes you prefer it to clementine?

---

### Post by shantiq on 2015-08-13
Well arias found this new toy a month ago or so and not used anything else since

Remembers where your last track stopped and picks up from there FAULTLESSLY

just really stable way more than Clementine which i also love    BUT the sound on Cantata is MPD so REALLY excellent whereas on Clem it is theirs and frankly a tad muddy at times;    so this listener here stays with Cantata for now

PS also ace if you want to make a radio playlist

my advice to anyone who is using Clementine would be try this see what you think
[more info]("https://www.maketecheasier.com/cantata-new-music-player-for-linux/")

[[IMG]http://s4.postimg.org/4npy79v6h/image.jpg[/IMG]]("http://postimg.org/image/4npy79v6h/")

---

