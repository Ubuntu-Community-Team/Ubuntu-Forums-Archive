---
title: "INSTALL xmms on 14.04"
date: 2015-03-02
forum: Multimedia Software
---

### Post by shantiq on 2015-03-02
This is an update as earlier [threads]("http://ubuntuforums.org/showthread.php?t=1525072") are now out of date; and some still like the old Swedish beast known as xmms ...    so here an easy way to get it fired up on the latest versions of U


[[IMG]http://s20.postimg.org/f9g9uw5g9/Xmms_coverviewer.jpg[/IMG]]("http://postimg.org/image/f9g9uw5g9/")




**1.**  go to >> software-properties-gtk and add >>

> deb [http://www.pvv.ntnu.no/~knuta/xmms/ubuntu](http://www.pvv.ntnu.no/~knuta/xmms/ubuntu) karmic main
deb-src [http://www.pvv.ntnu.no/~knuta/xmms/ubuntu](http://www.pvv.ntnu.no/~knuta/xmms/ubuntu) karmic main
deb [http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu](http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu](http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu) lucid main


and reload

**2. **find online and install   [sometimes needed but not always]

[ x11proto-core-dev_7.0.17-1_all.deb]("http://launchpadlibrarian.net/51704257/x11proto-core-dev_7.0.17-1_all.deb")
[x-dev_7.0.11-1_all.deb]("ftp://ftp.gnome.org/mirror/temp/ubuntu-test/pool/main/x/x11proto-core/x-dev_7.0.11-1_all.deb")


**3.** then enter


```
sudo apt-get install xmms  xmms-cueinfo xmms-mp4plugin   xmms-wavpack

```

**4.** to add flac >> [add]("http://ubuntuforums.org/attachment.php?attachmentid=205283&d=1319398314") 
**5.** to add shorten >>  the [codec]("http://ubuntuforums.org/attachment.php?attachmentid=162586&d=1278411609")   and  the xmms [plugin]("http://ubuntuforums.org/attachment.php?attachmentid=205281&d=1319398134")


=========


you may need to move libshn.so  libxmms-flac.so  to cd /usr/lib/xmms/Input/   [FONT=comic sans ms]otherwise plugins will not be seen[/FONT]


see below >>>


> shantiq@shantiq-00000000000000000000000:/usr/lib64/xmms/Input$ ls
libshn.so  libxmms-flac.so
shantiq@shantiq-00000000000000000000000:/usr/lib64/xmms/Input$ sudo mv * /usr/lib/xmms/Input/
shantiq@shantiq-00000000000000000000000:/usr/lib64/xmms/Input$ ls
shantiq@shantiq-00000000000000000000000:/usr/lib64/xmms/Input$ cd
shantiq@shantiq-00000000000000000000000:~$ cd /usr/lib/xmms/Input/
shantiq@shantiq-00000000000000000000000:/usr/lib/xmms/Input$ ls
libcdaudio.la  libmikmod.la  libmp4.la  libmpg123.la  libshn.so      libtonegen.so  libvorbis.so  libwavpack.la  libwav.so
libcdaudio.so  libmikmod.so  libmp4.so  libmpg123.so  libtonegen.la  libvorbis.la   libwav.la     libwavpack.so  libxmms-flac.so






**refer** to earlier closed thread here [for more info]("http://ubuntuforums.org/showthread.php?t=1525072")


**PS    ** to make sure all your accents cyrillic and other diacritics are seen properly do [this]("http://ubuntuforums.org/showthread.php?t=1525072&p=11848773#post11848773") [only font to do** all** european languages]
[[IMG]http://img651.imageshack.us/img651/7481/screenshotat20120416181.th.png[/IMG]]("http://img651.imageshack.us/img651/7481/screenshotat20120416181.png")

**PS 2** install should be fine on 14.10 and maybe 15.04 too but have not personally tested;   comment if you do please

---

