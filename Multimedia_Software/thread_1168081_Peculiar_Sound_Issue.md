---
title: "Peculiar Sound Issue"
date: 2009-05-23
forum: Multimedia Software
---

### Post by azaraelishanti on 2009-05-23
Hello, I'm fairly new to Ubuntu, but I've been poking around since Gutsy Gibbon and have recently started hosting servers using Ubuntu, which works really well. However, until now, I've never had to set up a sound card...and it's giving me major issues. I'll be as thorough as I can.

aplay -l 
```
aplay: device_list:217: no soundcards found...
```lspci -v
```
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 8095
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
    I/O ports at e000 [SIZE=1]
    I/O ports at ef00 [/SIZE] [SIZE=1]
    Memory at fe600000 (32-bit, non-prefetchable)
    Capabilities: <access denied>
    Kernel modules: snd-intel8x0[/SIZE]
```[SIZE=1]

Now I'm simply assuming the above is what we're looking for. The odd thing is, Controler is misspelled (which has led to Google not being happy a few times...). I assume the "snd-intel8x0" is what I'm looking for.

[http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0 ]("http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0")
seems to be the correct ALSA thingmummy, yes? So it's supported, yes? (If I'm reading this correctly)

I use the "Quick Installation" instructions and can't get past the first box:
```
cp: cannot stat `/downloads/alsa-*': No such file or directory
```[/SIZE][SIZE=1]

/usr/src/alsa$ sudo modprobe snd-intel8x0

results in:
```
WARNING: Could not open '/lib/modules/2.6.28-11-generic/kernel/sound/core/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.28-11-generic/kernel/sound/core/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.28-11-generic/kernel/sound/core/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.28-11-generic/kernel/sound/core/snd-pcm.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.28-11-generic/kernel/sound/ac97_bus.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.28-11-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.28-11-generic/kernel/sound/pci/snd-intel8x0.ko': No such file or directory
```[/SIZE][SIZE=1]

I can't find the particular command at the moment, but I submitted something to ALSA and they generated a website from my terminal results. On the site, no sound cards were listed, and the "ALSA Version" was blank. No version #s at all...which of course was not mentioned in the "Troubleshooting" I was reading :)

I even
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

alsamixer
```
alsamixer: function snd_ctl_open failed for default: No such device
```And still the problem isn't fixed. Help :)

-Az[/SIZE]

---

### Post by xzero1 on 2009-05-23
Just a hunch. You might check if you have older kernel headers lying around. If so remove the older one(s) then try again.

---

### Post by azaraelishanti on 2009-05-24
This is a fairly fresh (2 days old...not much changed except installing software and monkeying around with the sound card) format disk/install of Ubuntu 9.04.
 
How would I go about updating the kernel headers?
 
Thank you for your help.
 
-Az

---

### Post by psyke83 on 2009-05-24
*Do not* follow "quick install" instructions on an upstream page for ALSA! You are really asking for a headache by doing this, because a manual installation of libraries and kernel modules will interfere with the files installed by Ubuntu's packages.

Try to undo the damage those files may have caused (e.g., go to the working directory in which you compiled the libraries and modules, and perform a "make uninstall"). Your output indicates that the ALSA kernel modules were deleted from your system.

Once you have removed the custom-compiled files, perform a re-installation of vital Ubuntu packages whose files you have probably over-written:

```
$ sudo apt-get install --reinstall linux-image-`uname -a` libasound2 libasound2-plugins alsa-base alsa-utils
```

Reboot when you have re-installed the packages, and run the ALSA information script once again to see if it displays any sound cards.

The snd-intel8x0 driver **does** exist in Ubuntu, and you do not need to install/compile/recompile it. You must have inadvertently deleted the kernel modules somehow, but the above commands will restore them. 

To verify:
```
$ sudo updatedb
$ locate snd-intel8x0.ko

```
Installed by package:
```
$ dpkg -S snd-intel8x0.ko
```

---

### Post by xzero1 on 2009-05-24
> How would I go about updating the kernel headers?

It was only a hunch. Don't bother, try other methods first. It only applies when you are compiling your own modules but the modprobe errors looked similar. Anyway, you don't update the headers, you only remove the old ones.

---

### Post by azaraelishanti on 2009-05-24
> **psyke83 said:**
> 
Once you have removed the custom-compiled files, perform a re-installation of vital Ubuntu packages whose files you have probably over-written:

```
$ sudo apt-get install --reinstall linux-image-`uname -a` libasound2 libasound2-plugins alsa-base alsa-utils
```Reboot when you have re-installed the packages, and run the ALSA information script once again to see if it displays any sound cards.


I'm afraid I dont know how to do this...I think some custom files were installed, but I couldnt tell you which ones, and I don't know the working directory :\

-Az

---

### Post by psyke83 on 2009-05-24
> **azaraelishanti said:**
> I'm afraid I dont know how to do this...I think some custom files were installed, but I couldnt tell you which ones, and I don't know the working directory :\

-Az

That's why you shouldn't do manual installations, as you're bypassing the safety of the packaging system.

Your output indicated the working directory was /usr/src/alsa.

---

