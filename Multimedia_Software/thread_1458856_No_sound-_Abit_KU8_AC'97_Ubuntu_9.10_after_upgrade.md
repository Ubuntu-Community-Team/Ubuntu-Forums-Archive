---
title: "No sound- Abit KU8 AC'97 Ubuntu 9.10 after upgrade"
date: 2010-04-20
forum: Multimedia Software
---

### Post by doom3d on 2010-04-20
I have an Abit KU8 motherboard with ali chipset and Realtek AC'97 codec. Something went wrong with update from Ubuntu 9.04 to 9.10.
/ ubuntu-desktop and some other things were removed/
After reinstalling ubuntu-desktop I get no sound. I went trough the sticky tread until recompiling alsa from source. It seems, that alsa is installed, but not loaded. I only have a "pseudo output device". I have a dual-boot system, I get sound under WinXP. (I use win with my voice recorder)

I would like to repair my system without full reinstall. ( I have PATA HDD connected to IDE interface, sometimes not recognised during fresh install)
Thanks in advance.


```

~$ lspci | grep audio
00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)

~$ aplay -l
aplay: device_list:223: no soundcards found...

~# lsmod |grep snd
snd_page_alloc          9124  0 

~# alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/enzo/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/enzo/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload). 
```

---

### Post by lidex on 2010-04-20
Click on the alsa-upgrade-script link in my sig and follow the howto there. That should get your alsa install where it needs to be.

---

### Post by doom3d on 2010-04-21
> **lidex said:**
> Click on the alsa-upgrade-script link in my sig and follow the howto there. That should get your alsa install where it needs to be.

I have run your script. Still get no sound.
BTW,  "cat /proc/asound/version" doesn't exist on my system. 
Attached: results of "wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh".

```

~$ aplay -l
aplay: device_list:223: no soundcards found...

$ lspci -v | less
00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
        Subsystem: ABIT Computer Corp. Device 2205
        Flags: bus master, medium devsel, latency 32, IRQ 7
        I/O ports at fc00 [size=256]
        Memory at fdfff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel modules: snd-intel8x0

root@Picipaci:~# modprobe snd-intel8x0
FATAL: Error inserting snd (/lib/modules/2.6.31-21-generic/updates/alsa/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_pcm (/lib/modules/2.6.31-21-generic/updates/alsa/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ac97_bus (/lib/modules/2.6.31-21-generic/updates/alsa/misc/ac97_bus.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.31-21-generic/updates/alsa/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_intel8x0 (/lib/modules/2.6.31-21-generic/updates/alsa/pci/snd-intel8x0.ko): Unknown symbol in module, or unknown parameter (see dmesg)
root@Picipaci:~# dmesg >> /media/DATA/dmesg.txt


[  994.836740] snd: Unknown symbol unregister_sound_special
[  994.837217] snd: Unknown symbol register_sound_special_device
[  994.838378] snd: Unknown symbol sound_class
[  994.839877] snd_timer: Unknown symbol snd_info_register
[  994.840070] snd_timer: Unknown symbol snd_info_create_module_entry
[  994.840223] snd_timer: Unknown symbol snd_info_free_entry
[  994.840445] snd_timer: Unknown symbol snd_verbose_printk
[  994.840604] snd_timer: Unknown symbol snd_iprintf
[  994.840786] snd_timer: Unknown symbol snd_ecards_limit
[  994.840968] snd_timer: Unknown symbol snd_oss_info_register
[  994.841091] snd_timer: Unknown symbol snd_unregister_device
[  994.841233] snd_timer: Unknown symbol snd_device_new
[  994.841517] snd_timer: Unknown symbol snd_register_device_for_dev
```

---

### Post by lidex on 2010-04-21
Your alsa driver is not installed correctly. Try this:
(1) Remove these packages
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```

(2) Reinstall those same packages
```
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

---

### Post by doom3d on 2010-04-22
As I stated in my first post, I went trough the sound problems sticky guide until (including) reinstalling alsa from source.

Now I repeated this remove-reinstall step you requested (ubuntu-desktop, alsaconf-gtk and the kernel sound upgrade package was also removed), rebooted, and still have the same problem.

Sudo alsaconf finds the card, configures it as intel8x0, then I get a nice error message. This one:```

Running update-modules...
/usr/sbin/alsaconf: line 929: update-modules: parancs nem található [COLOR="Sienna"]( command not found)[/COLOR]
Setting default volumes...
amixer: Mixer attach default error: No such file or directory
Saving the mixer setup used for this in /etc/asound.state.
/usr/sbin/alsactl: save_state:1502: No soundcards found... 
```

Update of kernel modules returns an error:
```

root@Picipaci:~# sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic
Csomaglisták olvasása... Kész
Függ&#337;ségi fa építése       
Állapot adatok olvasása... Kész
A kiterjesztett állapotinformáció beolvasása      
Csomagállapotok inicializálása... Kész       
Kiterjesztett állapotinformáció mentése... Kész
Nem találtam ehhez illeszked&#337; nev&#369; vagy leírású csomagot: "linux-ubuntu-modules-2.6.31-21-generic"
[COLOR="Sienna"]-> can't find this or similar package[/COLOR]
Nem találtam ehhez illeszked&#337; nev&#369; vagy leírású csomagot: "linux-ubuntu-modules-2.6.31-21-generic"

root@Picipaci:~# aptitude install linux-restricted-modules-`uname -r` linux-generic
Csomaglisták olvasása... Kész
Függ&#337;ségi fa építése       
Állapot adatok olvasása... Kész
A kiterjesztett állapotinformáció beolvasása       
Csomagállapotok inicializálása... Kész       
Nem találtam ehhez illeszked&#337; nev&#369; vagy leírású csomagot: "linux-restricted-modules-2.6.31-21-generic"
Nem találtam ehhez illeszked&#337; nev&#369; vagy leírású csomagot: "linux-restricted-modules-2.6.31-21-generic"

```

Also tried this one:
```
root@Picipaci:~# modprobe snd
WARNING: All config files need .conf: /etc/modprobe.d/sound, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/sound, it will be ignored in a future release.
FATAL: Error inserting snd (/lib/modules/2.6.31-21-generic/kernel/sound/modules/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for snd
root@Picipaci:~# dmesg | grep snd >> /media/DATA/modprobe_snd.txt

```
dmesg returns this:
```

[ 3670.885889] snd: Unknown symbol unregister_sound_special
[ 3670.886314] snd: Unknown symbol register_sound_special_device
[ 3670.887594] snd: Unknown symbol sound_class
```

Any idea what to do next?
Thanks.


***************************************************************************

UPDATE: After full clean reinstall from live CD two times, now I get sound.

---

