---
title: "Problem streaming mp3 music from Windows Vista shared folder"
date: 2013-05-14
forum: Multimedia Software
---

### Post by nictu on 2013-05-14
Hi Folks,

UBUNTU 12.04 ASUS EeePC 1000HG

I have connected to a shared folder on a Windows Vista PC and am trying to play the mp3 music files contais there using RhythmBox music player. I can see the files and Rhthmbox loads them and 'plays' them but you can't hear the music (volume is turned up by the way !).

Any help and advice is much appreciated.
nictu.

---

### Post by ipeters61 on 2013-05-14
Do you have the MP3 codecs installed?  Go into the Software Center and install the GStreamer plugins (I think GStreamer ugly), then you should be able to play MP3s.

---

### Post by nictu on 2013-05-15
Thanks ipeters61,

I will give that a try.

nictu.

---

### Post by nictu on 2013-05-15
Hi,

I have just checked and it appear I already have GStreamer plug ins installed.
Any more advice is usper appreciated,
nictu.

---

### Post by CraigPid on 2013-05-16
I think I've had a simliar situation. I don't really know what I'm talking about but I think it has something to do with the player having a samba backend. Have you tried different players? Possibly VLC. What would work also is if you mount that share in a local folder. Preferably a folder in your home folder so you don't have permission problems. Find out the ip address of your xp machine.(in the xp command prompt type "ipconfig".) To mount the share type " mount -t cifs //192.168.100.101/LORE /home/craig/Lore " of course using your proper information. If you get an error you may have to install cifs-utils. Also you could mount the share at boot by editing fstab. The command has a few more options but if you googe automount shares ubuntu I'm sure you could find it.
   Craig

---

### Post by nictu on 2013-05-18
Thanks Craig,

I will give your suggestions a try.

Many thanks for you rknowledge and help,
nictu.

---

