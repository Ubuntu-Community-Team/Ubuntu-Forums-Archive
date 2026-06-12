---
title: "Please help me iv got some errors after instal of OSS4 instal creative soundblaster"
date: 2008-10-10
forum: Multimedia Software
---

### Post by H4ck3rz on 2008-10-10
Ok iv tryed the alsa install for my creative X-FI sound blaster exstreme gamer no luck so now im trying OSS4 & i get these errors please help me i need sound for my course work lolz ```
h4ck3rz@h4ck3rz-desktop:~$ aplay
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:546: audio open error: No such file or directory
h4ck3rz@h4ck3rz-desktop:~$ aplay -l
aplay: device_list:205: no soundcards found...
h4ck3rz@h4ck3rz-desktop:~$ ossinfo
Version info: OSS 4.1 (b rc2/200810091939) (0x00040090) 
Hg revision: changeset: 473:d79ebde9987e, tag: tip, date: Tue Oct 07 17:50:26 2008 +0300, summary: Suported rate fix for envy24
Platform: Linux/x86_64 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 (h4ck3rz-desktop)

Number of audio devices:	2
Number of audio engines:	6
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: oss_sbxfi0 Sound Blaster X-Fi (UAA) interrupts=20776 (20776)
    PCI device 1102:0005, subdevice 1102:6002
 2: oss_usb0 USB audio core services


Mixer devices
 0: Sound Blaster X-Fi (UAA) (Mixer 0 of device object 1)

Audio devices
Sound Blaster X-Fi (UAA) output   /dev/oss/oss_sbxfi0/pcm0  (device index 0)
Sound Blaster X-Fi (UAA) input    /dev/oss/oss_sbxfi0/pcmin0  (device index 1)
h4ck3rz@h4ck3rz-desktop:~$
```any one got any ideas of no how to fix these errors

---

### Post by H4ck3rz on 2008-10-10
no worrys fixed it

---

### Post by Jaz969 on 2008-10-10
i use a creative x-fi ca0106 if u figure out how to get a working microphone on it, pm me lol

---

### Post by H4ck3rz on 2008-10-10
now iv got this problem sound is showing playing in ossxmix 
& osstest still no sound on ther 
& jst no sound all togeather hope some one can give me away to fix this ```
h4ck3rz@h4ck3rz-desktop:~$ ossinfo
Version info: OSS 4.1 (b rc2/200810091939) (0x00040090) 
Hg revision: changeset: 473:d79ebde9987e, tag: tip, date: Tue Oct 07 17:50:26 2008 +0300, summary: Suported rate fix for envy24
Platform: Linux/x86_64 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 (h4ck3rz-desktop)

Number of audio devices:	2
Number of audio engines:	6
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: oss_sbxfi0 Sound Blaster X-Fi (UAA) interrupts=89425 (89425)
    PCI device 1102:0005, subdevice 1102:6002
 2: oss_usb0 USB audio core services


Mixer devices
 0: Sound Blaster X-Fi (UAA) (Mixer 0 of device object 1)

Audio devices
Sound Blaster X-Fi (UAA) output   /dev/oss/oss_sbxfi0/pcm0  (device index 0)
Sound Blaster X-Fi (UAA) input    /dev/oss/oss_sbxfi0/pcmin0  (device index 1)
h4ck3rz@h4ck3rz-desktop:~$ ossxmix
/home/h4ck3rz/.themes/diehard/gtk-2.0/gtkrc:53: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
h4ck3rz@h4ck3rz-desktop:~$ ls -l /dev/dsp
lrwxrwxrwx 1 root root 24 2008-10-10 18:32 /dev/dsp -> /dev/oss/oss_sbxfi0/pcm0
h4ck3rz@h4ck3rz-desktop:~$ 


```

---

