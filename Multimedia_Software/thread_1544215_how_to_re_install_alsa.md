---
title: "how to re install alsa?"
date: 2010-08-02
forum: Multimedia Software
---

### Post by raymondvillain on 2010-08-02
Ubuntu 10.04, 64 bit.  Sound was working well, thought I would run some scripts ([http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137))
to install the latest version of alsa, but now I have no sound at all.

The command aplay -l gives:

aplay: device_list:223: no soundcards found...

and the command 

cat /proc/asound/version
produces:

cat: /proc/asound/version: No such file or directory

So I no longer have a directory /proc/asound.

If I open the window system>preferences>sound

there are no entries under hardware or output.

I have tried to re-install alsa with this command:
sudo apt-get install --reinstall alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base alsamixergui

but still no sound.

Any suggestions would be greatly appreciated.

---

### Post by zerek on 2010-11-04
bump on this one. Got same problem.
Was trying to install a realtek driverpackage by following the installguide. 

[http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)


mkdir temp
cd temp 
tar xfv LinuxPkg_5.15rc19.tar.bz2
cd realtek-linux-audiopackage-5.15
sudo ./install```

cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1

```


tar xfvj alsa-driver-1.0.23-5.15rc19.tar.bz2
cd alsa-driver-1.0.23
sudo ./configure  --with-cards=hda-intel
sudo make
```

e.c:489: error: implicit declaration of function ‘pm_qos_remove_requirement’
/home/phatz/temp/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore/pcm_native.c:492: error: implicit declaration of function ‘pm_qos_add_requirement’
make[3]: *** [/home/phatz/temp/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore/pcm_native.o] Error 1
make[2]: *** [/home/phatz/temp/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore] Error 2
make[1]: *** [_module_/home/phatz/temp/realtek-linux-audiopack-5.15/alsa-driver-1.0.23] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [compile] Error 2
```


sudo make install

```
mkdir -p /lib/modules/2.6.35-22-generic/kernel/sound/acore
cp snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-timer.ko snd.ko /lib/modules/2.6.35-22-generic/kernel/sound/acore
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/phatz/temp/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore'
make: *** [install-modules] Error 1
```


alsamixer does not work, and
cat: /proc/asound/version: No such file or directory
Anyone got a idea what I'm doing wrong here?

---

