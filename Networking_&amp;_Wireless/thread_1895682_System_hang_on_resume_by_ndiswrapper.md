---
title: "System hang on resume by ndiswrapper"
date: 2011-12-15
forum: Networking &amp; Wireless
---

### Post by MHaaZ on 2011-12-15
Hello there dear community!

First, I want to thank the OP of [this thread ]("http://ubuntuforums.org/showthread.php?t=1679651")for referring me to ndiswrapper. I have  the exact same netbook model (Asus eeePC 1000H) and I must say after switching to Ubuntu  having such unrelliable wifi was a real pain. I seriously considered going back to Window$, but luckily found the aforementioned thread first.

I followed his directions and everything started looking better:
I installed ndiswrapper and use the Windows driver for my netbook, my wifi is reliable and strong... AS LONG AS MY SYSTEM IS STARTING UP COLD.

My system hangs on resume after a suspend (to RAM) or hibernate (to disk). The referenced thread also includes a solution for this: putting a script in /etc/pm/sleep.d/ which unloads the module before sleeping and reloads it after wakeup. Simple enough, but it doesn't seem to work. My system still freezes when thawing from a hibernate  or when waking up from a suspend from time to time, and when it actually  starts up, the wifi is broken since the network-manager applet just  reports "device not ready". Removing the kernel module, and loading it back in with:

```
  modprobe -r ndiswrapper; modprobe ndiswrapper
```doesn't seem to do the trick either. The only way to fix is to reboot.

The only thing that comes to mind  is that I am using natty (11.04) and t**here might well have been some  changes to the way the scripts at /etc/pm/ get called on system sleep or  wakeup**, since the original thread worked for maverick (10.10).

Any further insight anyone has into this would be greatly appreciated.

Greetings,
Dave

---

### Post by Toz on 2011-12-15
Hello and welcome to the forums.

First, lets make sure the script was installed properly. Can you post back the results of:
```
ls -l /etc/pm/sleep.d/*
```
...and
```
cat /etc/pm/sleep.d/ndiswrapper
```

Secondly, lets see what the log files say. Post back the contents of **/var/log/pm-suspend.log** and the results of:
```
cat /var/log/syslog* | grep PM:
```

---

### Post by MHaaZ on 2011-12-21
**Edit: I highlighted the sections in the code that caught my interest, to make anyone's job easier who is willing to check it out :-)**

Hello!

Thanks for the warm welcoming and the swift reply, and sorry I wasn't able to reply; I was very busy the last few days because of preparations for the holiday festivities.

Anyhow, back to topic. I followed your suggestions, here are the results:

```

mhaaz@mhaaz-netbook:~$** ls -l /etc/pm/sleep.d/***
-rwxr-xr-x 1 root root 210 2011-04-21 15:33 /etc/pm/sleep.d/10_grub-common
-rwxr-xr-x 1 root root 482 2011-02-03 20:49 /etc/pm/sleep.d/10_unattended-upgrades-hibernate
-rw-r--r-- 1 root root 184 2011-11-15 20:01 /etc/pm/sleep.d/ndiswrapper

```So the script is obviously in the right place. Now on to its contents:

```

mhaaz@mhaaz-netbook:~$ **cat /etc/pm/sleep.d/ndiswrapper**
#!/bin/bash
case "$1" in
    hibernate|suspend)
        sudo rmmod ndiswrapper
        ;;
    thaw|resume)
        sudo modprobe ndiswrapper
        ;;
    *)
        ;;
esac
exit $?

```This seems to be the script as described in the thread I refered to in my previous post; so nothing strange there. Next up, the suspend log. The following section shows the last time I suspended and resumed from suspend:

```

...
Initial commandline parameters: 
Tue Dec 20 08:40:44 CET 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux mhaaz-netbook 2.6.38-13-generic #52-Ubuntu SMP Tue Nov 8 16:48:07 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
sha256_generic         20911  2 
cryptd                 19801  0 
aes_i586               16956  347 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
dm_crypt               22463  1 
ppdev                  12849  0 
binfmt_misc            13213  1 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
joydev                 17322  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
uvcvideo               66851  0 
videodev               75143  1 uvcvideo
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
soundcore              12600  1 snd
eeepc_laptop           19417  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
sparse_keymap          13666  1 eeepc_laptop
ndiswrapper           192828  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
i915                  451053  2 
drm_kms_helper         40971  1 i915
drm                   184164  3 i915,drm_kms_helper
atl1e                  32576  0 
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
             total       used       free     shared    buffers     cached
Mem:       1015892     855760     160132          0      45960     432360
-/+ buffers/cache:     377440     638452
Swap:      1034236          0    1034236

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/91wicd suspend suspend:

/usr/lib/pm-utils/sleep.d/91wicd suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/ndiswrapper suspend suspend:

/etc/pm/sleep.d/ndiswrapper suspend suspend: success.
Tue Dec 20 08:40:49 CET 2011: performing suspend


Tue Dec 20 08:41:07 CET 2011: Awake.
Tue Dec 20 08:41:07 CET 2011: Running hooks for resume
Running hook /etc/pm/sleep.d/ndiswrapper resume suspend:

/etc/pm/sleep.d/ndiswrapper resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/91wicd resume suspend:

/usr/lib/pm-utils/sleep.d/91wicd resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...method return sender=:1.4 -> dest=:1.68 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Tue Dec 20 08:41:12 CET 2011: Finished.
...

```Aside from PulseAudio misbehaving (which I doubt has anything to do with my problem), it caught my attention that NetworkManager **failed** when trying to put the interfaces to sleep... Still, my system resumes fine after suspend, although recent experiments have shown me that WiFi is still **sometimes** not working after a resume from suspend (but sometimes it is!).

At last, the syslog filtered for the lines with "PM:", as you requested:

```
mhaaz@mhaaz-netbook:~$ cat /var/log/syslog* | grep PM:
Dec 20 10:40:24 mhaaz-netbook kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec 20 10:40:24 mhaaz-netbook kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
Dec 20 10:40:24 mhaaz-netbook kernel: [    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
Dec 20 10:40:24 mhaaz-netbook kernel: [    1.238131] PM: Hibernation image not present or could not be loaded.
Dec 20 14:12:24 mhaaz-netbook kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec 20 14:12:24 mhaaz-netbook kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
Dec 20 14:12:24 mhaaz-netbook kernel: [    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
Dec 20 14:12:24 mhaaz-netbook kernel: [    1.235597] PM: Hibernation image not present or could not be loaded.
Dec 20 17:22:54 mhaaz-netbook kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec 20 17:22:54 mhaaz-netbook kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
Dec 20 17:22:54 mhaaz-netbook kernel: [    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
Dec 20 17:22:54 mhaaz-netbook kernel: [    1.235265] PM: Hibernation image not present or could not be loaded.
Dec 21 09:14:16 mhaaz-netbook kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec 21 09:14:16 mhaaz-netbook kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
Dec 21 09:14:16 mhaaz-netbook kernel: [    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
Dec 21 09:14:16 mhaaz-netbook kernel: [    1.242795] PM: Hibernation image not present or could not be loaded.

```Looking at that last one, it clearly shows my real problem is hibernate (=suspend to disk), although I don't know what exactly is going wrong. Since I got your last reply, I started trying to hibernate more often, and two things happened every time:

1. The system would hang when trying to hibernate, with the power clearly still on but a blank screen and an unresponsive keyboard, mouse, etc. I finally had to hold the power button for a couple of seconds to force a shutdown.

2. The system would (apparently) hibernate with success, but when starting up it would not reload my hibernated state but start up cold as I had just shut it down.

I checked every time the second thing happened, and this is what I found in the pm-suspend.log:

```

Initial commandline parameters: 
Tue Dec 20 08:43:13 CET 2011: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux mhaaz-netbook 2.6.38-13-generic #52-Ubuntu SMP Tue Nov 8 16:48:07 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
sha256_generic         20911  2 
cryptd                 19801  0 
aes_i586               16956  347 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
dm_crypt               22463  1 
ppdev                  12849  0 
binfmt_misc            13213  1 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
joydev                 17322  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
uvcvideo               66851  0 
videodev               75143  1 uvcvideo
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
soundcore              12600  1 snd
eeepc_laptop           19417  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
sparse_keymap          13666  1 eeepc_laptop
ndiswrapper           192828  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
i915                  451053  2 
drm_kms_helper         40971  1 i915
drm                   184164  3 i915,drm_kms_helper
atl1e                  32576  0 
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
             total       used       free     shared    buffers     cached
Mem:       1015892     856212     159680          0      46184     433560
-/+ buffers/cache:     376468     639424
Swap:      1034236          0    1034236

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/91wicd hibernate hibernate:

/usr/lib/pm-utils/sleep.d/91wicd hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/ndiswrapper hibernate hibernate:

/etc/pm/sleep.d/ndiswrapper hibernate hibernate: success.
Tue Dec 20 08:43:17 CET 2011: performing hibernate

```Still, this log doesn't show ANY ATTEMPT TO TRYING TO RESUME FROM HIBERNATE. I am more than a little clueless but hopeful that you might give me some further clues to look into and learn about my problem.

Thanks for the help so far, and happy holidays!

P.S. I am going to change the topic name, since my problem now is a little different. Actually, now I understand:  my system never hung on resuming from hibernate, I just had tried to hibernate and shut the lid. Hours later, I popped it open and pressed space, and saw the system hanging (presumably still stuck in the hibernation procedure).

---

### Post by Toz on 2011-12-21
> Looking at that last one, it clearly shows my real problem is hibernate (=suspend to disk), although I don't know what exactly is going wrong. Since I got your last reply, I started trying to hibernate more often, and two things happened every time:

1. The system would hang when trying to hibernate, with the power clearly still on but a blank screen and an unresponsive keyboard, mouse, etc. I finally had to hold the power button for a couple of seconds to force a shutdown.

2. The system would (apparently) hibernate with success, but when starting up it would not reload my hibernated state but start up cold as I had just shut it down.Is your swap file encrypted? If so, on resume it won't be able to read the contents.
```
cat /etc/fstab
```

Also, what are the results of:
```
sudo blkid
```
```
cat /etc/initramfs-tools/conf.d/resume
```
...the swap UUID from *sudo blkid* should match the contents of *at /etc/initramfs-tools/conf.d/resume*

---

### Post by MHaaZ on 2012-01-09
Hi again, and sorry for the long silence. It was a crazy holiday season for me.

```

mhaaz@mhaaz-netbook:~$ **cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a2d57d55-4d55-43c1-843f-0a035baf6f71 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
#UUID=5c7798ff-86d6-486e-b363-ca8481a229dd none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```I can't tell wheter my swap file is encrypted or not, although the "cryptswap" makes me think it is: What would be a clear indicator in the above code (trying to learn, not just bash commands into my shell)?

On to the next command you suggested:

```
mhaaz@mhaaz-netbook:/etc/pm/sleep.d$ **sudo blkid**
/dev/sda1: UUID="a2d57d55-4d55-43c1-843f-0a035baf6f71" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="75a0f2c6-a2ff-4e42-934c-7b33855d27e4" TYPE="swap" 
```So the swap partition hast UUID 75a0f2c6-a2ff-4e42-934c-7b33855d27e4. I wanted to compare it to the one in **/etc/initramfs-tools/conf.d/resume**, but it turns out I have no such file in my file system. The directory is there but it's empty, there is no file named resume.

May I humbly ask you to briefly explain to me what this shows, and what the overall situation of my system is according to the conclusions you might draw? Of course I'm very thankful for your suggestions, but I would like to understand a little bit of what I'm doing so I'm not as uneducated as before asking these questions.

Thanks a lot for all the input so far, and a happy start into 2012! :D

**Edit**: Can anyone (mods or such?) tell me how to change the **Thread** title, since it doesn't accurately reflect my problem anymore? I tried changing the title of my first post, but the topic name remained the same. Thanks!

---

### Post by Toz on 2012-01-09
> **MHaaZ said:**
> Hi again, and sorry for the long silence. It was a crazy holiday season for me.

```

mhaaz@mhaaz-netbook:~$ **cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a2d57d55-4d55-43c1-843f-0a035baf6f71 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
#UUID=5c7798ff-86d6-486e-b363-ca8481a229dd none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```I can't tell wheter my swap file is encrypted or not, although the "cryptswap" makes me think it is: What would be a clear indicator in the above code (trying to learn, not just bash commands into my shell)?
cryptswap is a clear indicator that your swap file is encrypted. That being the case, hibernate simply won't work for you because on resume, it won't be able to access the resume file on the swap partition.

> On to the next command you suggested:

```
mhaaz@mhaaz-netbook:/etc/pm/sleep.d$ **sudo blkid**
/dev/sda1: UUID="a2d57d55-4d55-43c1-843f-0a035baf6f71" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="75a0f2c6-a2ff-4e42-934c-7b33855d27e4" TYPE="swap" 
```So the swap partition hast UUID 75a0f2c6-a2ff-4e42-934c-7b33855d27e4. I wanted to compare it to the one in **/etc/initramfs-tools/conf.d/resume**, but it turns out I have no such file in my file system. The directory is there but it's empty, there is no file named resume.
There are a number of recommendations that state that for hibernate to work properly, you need to specify the correct UID of the swap partition in the file /etc/initramfs-tools/conf.d/resume. However, because of the fact that your swap file is encrypted, this is a moot point now.

> May I humbly ask you to briefly explain to me what this shows, and what the overall situation of my system is according to the conclusions you might draw? Of course I'm very thankful for your suggestions, but I would like to understand a little bit of what I'm doing so I'm not as uneducated as before asking these questions.
I think that you have a couple of options here:
1. Don't use hibernate but use suspend instead (of course, this is dependent on whether you absolutely need the hibernate function)
2. Unencrypt your swap file (or create a second unencrypted swap file) so that you can use hibernate functionality. See this link for more info: [http://webcache.googleusercontent.com/search?q=cache:iBwp13eGGqwJ:www.logilab.org/29155+ecryptfs-setup-swap&cd=10&hl=en&ct=clnk&gl=ca&client=firefox-a]("http://webcache.googleusercontent.com/search?q=cache:iBwp13eGGqwJ:www.logilab.org/29155+ecryptfs-setup-swap&cd=10&hl=en&ct=clnk&gl=ca&client=firefox-a") (sorry, the main link seems to be done and this is the google cached version of that link)

> Thanks a lot for all the input so far, and a happy start into 2012! :D
No worries - hope its helpful. And a happy 2012 to you as well.

---

