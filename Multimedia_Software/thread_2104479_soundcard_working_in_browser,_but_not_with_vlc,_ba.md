---
title: "soundcard working in browser, but not with vlc, banshee etc."
date: 2013-01-13
forum: Multimedia Software
---

### Post by Heizer on 2013-01-13
Hello,

i'm relative new to ubuntu.

my soundcard is working in any browser application (yt etc.), but not with any mp3-playback-software.

i tried a few tutorials for pulseaudio, but no success.

a few system infos:

```

lsb_release -d 
Description:    Ubuntu 11.10

uname -r
3.0.0-29-generic

grep "^audio" /etc/group | grep "$USER" | wc -l 
1

lspci -nnk | grep -iA2 audio 
00:05.0 Audio device [0403]: nVidia Corporation MCP61 High Definition Audio [10de:03f0] (rev a2)
    Subsystem: ASRock Incorporation Device [1849:0397]
    Kernel driver in use: oss_hdaudio
    Kernel modules: snd-hda-intel
00:06.0 IDE interface [0101]: nVidia Corporation MCP61 IDE [10de:03ec] (rev a2)

lsmod | grep "snd" 

cat /proc/asound/cards 
cat: /proc/asound/cards: No such file or directory


```any help i greatly appreciated!

---

### Post by Heizer on 2013-01-15
More Infos:

[http://www.alsa-project.org/db/?f=2665559be4670058cb0a9237ca37f9beabbdf458](http://www.alsa-project.org/db/?f=2665559be4670058cb0a9237ca37f9beabbdf458)

Help, Please!

---

### Post by Yellow Pasque on 2013-01-16
You installed OSS4, so you either need to set your programs to use OSS instead of pulse/ALSA (there's a howto on their site: [http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4) ), or uninstall OSS4..

---

