---
title: "Sound missing????"
date: 2006-08-06
forum: Multimedia &amp; Video
---

### Post by mamato on 2006-08-06
Hi all, i got this annoying problem just now. My sound card is intel ich7, I use the snd-hda-intel module. I try to compile a new alsa module since I am not very satisfied with the current one. I follow the step from [http://ubuntuforums.org/showthread.php?t=205449&page=8 ]("http://ubuntuforums.org/showthread.php?t=205449&page=8")
but now, my sound dissappear. I have check all, but the sound still does not come out.
Here is my ```
aplay -l
``` output :
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``` 
And my ```
lspci -v | grep -i audio
``` output :
```

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

``` 
My ```
lsmod | grep snd 
``` output:
```

snd_hda_intel          19472  1
snd_hda_codec          93312  1 snd_hda_intel
snd_pcm_oss            55552  0
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                96804  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26980  1 snd_pcm
snd                    61220  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11336  2 snd_hda_intel,snd_pcm

``` 
And at last, my ```
/etc/modutils/alsa
``` content:
```

snd_hda_intel          19472  1
snd_hda_codec          93312  1 snd_hda_intel
snd_pcm_oss            55552  0
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                96804  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26980  1 snd_pcm
snd                    61220  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11336  2 snd_hda_intel,snd_pcm

``` 
I have tried these solutions :[LIST=1]
[*] I remove with configuration and reinstalling these packages : ```
linux-base-sound, alsa-base, alsa-utils
```
[*]I tried to recompile the module based on the thread above[/LIST]but no luck.. :(

This is my dmesg output :
```
[17180093.048000] flags:0x80000414 mapping:00000000 mapcount:0 count:0
[17180093.048000] Backtrace:
[17180093.048000]  [<c0153dd7>] bad_page+0x87/0xc0
[17180093.048000]  [<c015476c>] free_hot_cold_page+0x4c/0x140
[17180093.048000]  [<c01550be>] __pagevec_free+0x3e/0x60
[17180093.048000]  [<c015b8d3>] release_pages+0x163/0x190
[17180093.048000]  [<c01609e6>] unmap_page_range+0xf6/0x130
[17180093.048000]  [<c0169ee6>] free_pages_and_swap_cache+0x86/0xb0
[17180093.048000]  [<c0160c31>] unmap_vmas+0x211/0x250
[17180093.048000]  [<c0165802>] unmap_region+0xb2/0x160
[17180093.048000]  [<c0165ba9>] do_munmap+0x109/0x150
[17180093.048000]  [<c0165c41>] sys_munmap+0x51/0x80
[17180093.048000]  [<c0103487>] sysenter_past_esp+0x54/0x75
[17180093.048000] Trying to fix it up, but a reboot is needed

```
Please help me.. I am stuck in here..

---

### Post by mamato on 2006-08-06
Hi guys, I have solved the problem :p, I follow this thread [http://ubuntuforums.org/showpost.php?p=1208533&postcount=6](http://ubuntuforums.org/showpost.php?p=1208533&postcount=6) and after that i create the file in /etc/modutils/alsa with this content:
```

# ALSA portion
        alias char-major-116 snd
        alias snd-card-0 snd-hda-intel
        # module options should go here
options snd-card-0 index=0
options snd-hda-intel index=0 model=basic
remove snd-hda-intel { /usr/sbin/alsactl store 0 >/dev/null 2>&1 || : ; }; /sbin/modprobe -r --ignore-remove snd-hda-intel  
        # OSS/Free portion
        alias char-major-14 soundcore
        alias sound-slot-0 snd-card-0
        
        # card #1
        alias sound-service-0-0 snd-mixer-oss
        alias sound-service-0-1 snd-seq-oss
        alias sound-service-0-3 snd-pcm-oss
        alias sound-service-0-8 snd-seq-oss
        alias sound-service-0-12 snd-pcm-oss

```

Hope that helps :D

---

