---
title: "Ubuntu restricted Extras"
date: 2009-07-16
forum: Multimedia Software
---

### Post by Halcyon31415 on 2009-07-16
I would like to rip a CD to MP3 format and I just installed 9.04 and I remember I need to install Ubuntu-restricted-extras when I did this in 8.04 but now when I try to install i get the message below


This application conflicts with other installed software. To install 'ubuntu-restricted-extras' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

I'm not sure I know what that means. Is there another way to get the files i need. Maybe something like sudoaptget :) Oh my kingdom for the ability to work the terminal like a pro. 

Thx for your help in advance

Cheers

---

### Post by igorzwx on 2009-07-16
[http://ubuntuforums.org/showthread.php?t=1214052](http://ubuntuforums.org/showthread.php?t=1214052)

---

### Post by CatKiller on 2009-07-16
> **Halcyon31415 said:**
>  Switch to the 'synaptic' package manager to resolve this conflict.

I'm not sure I know what that means. 

It means instead of using the Add/Remove tool you should use System -> Administration -> Synaptic Package Manager instead. The Add/Remove tool is very simple compared to the other tools that are available and can't really do complicated dependency resolution. Synaptic is more sophisticated.

Just for information, the equivalent Terminal command would be ```
sudo apt-get install ubuntu-restricted-extras
```:)

---

### Post by bgiannes on 2009-07-16
see [https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)


i stopped using ubuntu-restricted-extras (packs like this) install with 9.04, been trying not to install stuff i don't use.

"SoundJuicer" ships with ubuntu 9.04?  ubuntu's CD ripper.

If not
sudo apt-get install soundjuicer


for DVD's and music files.....

should build ffmpeg see here
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

then for a basic gui for ffmpeg is winff, for converting media files.

sudo apt-get install winff  (you need ffmpeg installed for this)

then see
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

DVD encryption work around
sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh

i like dvdrip... so
sudo apt-get install dvdrip    (you should have ffmpeg install already)

---

### Post by Halcyon31415 on 2009-07-16
Wow,
     I feel stupid, I couldn't figure that out at all. Thx for the save everyone. I really appreciate the effort people put into helping others with Ubuntu. 

Thx again

---

