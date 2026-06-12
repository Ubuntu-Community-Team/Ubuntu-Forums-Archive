---
title: "Problems with alsa in ubutnu 10.10"
date: 2011-09-22
forum: Multimedia Software
---

### Post by shini-kire on 2011-09-22
I had the alsa version 1.0.23, now I have version 1.0.24 but I have no sound.

I Am user Ubuntu 10.10 (32 bits)

My Target of sound is:

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

need help please, Iam Upgrade this:

I download this alsa-driver, alsa-lib, alsa-utils from [http://www.alsa-project.org/](http://www.alsa-project.org/) compile this form

```
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2

cd alsa-driver*
sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)
sudo make
sudo make install

cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install

cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install
```

In case you get this error:

```
checking for new_panel in -lpanelw... no configure: error: panelw library not found 
```

you can try to fix it adding this symbolic links:

```
sudo ln -s libpanelw.so.5 /usr/lib/libpanelw.so
sudo ln -s libformw.so.5 /usr/lib/libformw.so
sudo ln -s libmenuw.so.5 /usr/lib/libmenuw.so
sudo ln -s libncursesw.so.5 /lib/libncursesw.so
```

and Reboot

in  run dmesg and look for the string "snd_" this:

```
[   15.522657] snd: Unknown symbol unregister_sound_special (err 0)
[   15.522986] snd: Unknown symbol register_sound_special_device (err 0)
[   15.596475] Linux agpgart interface v0.103
[   15.599371] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   15.599825] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   15.690528] snd_timer: Unknown symbol snd_info_register (err 0)
[   15.690615] snd_timer: Unknown symbol snd_info_create_module_entry (err 0)
[   15.690747] snd_timer: Unknown symbol snd_info_free_entry (err 0)
[   15.690942] snd_timer: Unknown symbol __snd_printk (err 0)
[   15.691026] snd_timer: Unknown symbol snd_iprintf (err 0)
[   15.691149] snd_timer: Unknown symbol snd_ecards_limit (err 0)
[   15.691276] snd_timer: Unknown symbol snd_oss_info_register (err 0)
[   15.691360] snd_timer: Unknown symbol snd_unregister_device (err 0)
[   15.691478] snd_timer: Unknown symbol snd_device_new (err 0)
[   15.691687] snd_timer: Unknown symbol snd_register_device_for_dev (err 0)

```

this error at run "alsamixer" 

```
hikaru@Hikaru-x01:~$ alsamixer
can not open the mixer: No such file or directory
```

help please and thnks!

---

### Post by .... on 2011-09-22
I would suggest undoing what you did by cd'ing to the source directories and running (sudo) make uninstall. Then, try this script: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

---

### Post by shini-kire on 2011-09-22
> **.... said:**
> I would suggest undoing what you did by cd'ing to the source directories and running (sudo) make uninstall. Then, try this script: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

v -f .deps/pcm_a52.Tpo .deps/pcm_a52.Plo
/bin/bash ../libtool --tag=CC   --mode=link gcc -Wall -g -I/usr/include/alsa   -I/usr/local/include -DAVCODEC_HEADER="<libavcodec/avcodec.h>" -g -O2 -module -avoid-version -export-dynamic -no-undefined   -o libasound_module_pcm_a52.la -rpath /usr/lib/alsa-lib pcm_a52.lo -lasound   -pthread -L/usr/local/lib -lavcodec -ldl -lva -ljack -lasound -lSDL -lbz2 -lz -lavutil -lm   -lasound 
gcc -shared  .libs/pcm_a52.o  -L/usr/local/lib -lavcodec -ldl /usr/local/lib/libva.so -ljack -lSDL -lbz2 -lz -lavutil -lm /usr/lib/libasound.so  -pthread -Wl,-soname -Wl,libasound_module_pcm_a52.so -o .libs/libasound_module_pcm_a52.so
/usr/bin/ld: cannot find -lSDL
collect2: ld returned 1 exit status
make[2]: *** [libasound_module_pcm_a52.la] Error 1
make[2]: se sale del directorio «/opt/Alsa-1.0.24/alsa-plugins-1.0.24/a52»
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio «/opt/Alsa-1.0.24/alsa-plugins-1.0.24»
make: *** [all] Error 2

***************************************************************************
*  alsa-plugins-1.0.24 make failed
***************************************************************************

---

### Post by .... on 2011-09-22
Rerun the script with -d option.** Make sure that no other package managers are open or you will not get the needed packages.** The package you're missing is libsdl1.2-dev

Hmm: This package is not in the alsaupgrade script. I wonder why no one complained of this error before :?

---

### Post by shini-kire on 2011-09-22
> **.... said:**
> Rerun the script with -d option.** Make sure that no other package managers are open or you will not get the needed packages.** The package you're missing is libsdl1.2-dev

Hmm: This package is not in the alsaupgrade script. I wonder why no one complained of this error before :?
 thnks!  =) 

I Install this:

```
sudo apt-get install libsdl1.2-dev
```

thnks!

---

### Post by .... on 2011-09-22
[http://decatf.wordpress.com/2010/11/04/gstreamer-delta-audio-sharpening-plugin/](http://decatf.wordpress.com/2010/11/04/gstreamer-delta-audio-sharpening-plugin/)

EDIT: Wrong thread

---

