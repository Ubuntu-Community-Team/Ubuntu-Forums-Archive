---
title: "Ubuntu 9.04 sound problems...!"
date: 2009-03-23
forum: Multimedia Software
---

### Post by t3ch on 2009-03-23
Hello i have upgrade to ubuntu 9.04 and the sound is not working. I have tryed to install a lot of packages what have I readed on internet but without success.

Here is some information that are useful for you guys here.. :)

**lspci**
```

m5it@ns2:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7600 GT (rev a2)

```

**cat /proc/asound/cards**
```

m5it@ns2:~$ cat /proc/asound/cards
 0 [V8235          ]: VIA8233 - VIA 8235
                      VIA 8235 with AD1980 at 0xe000, irq 22

```

**cat /proc/asound/modules**
```

m5it@ns2:~$ cat /proc/asound/modules
 0 snd_via82xx

```

**aplay -l & arecord -l**
```

aplay -l
aplay: device_list:217: no soundcards found...
m5it@ns2:~$ arecord -l
arecord: device_list:217: no soundcards found...

```

**And here is one trick that i have readed on internet but without luck..**
```

m5it@ns2:~$ killall pulseaudio
m5it@ns2:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/m5it/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/m5it/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-via82xx snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-mpu401-uart snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.
Loading ALSA sound driver modules: snd-via82xx snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-mpu401-uart snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.
m5it@ns2:~$ pulseaudio
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: alsa-util.c: Error opening PCM device hw:0: No such file or directory
E: module.c: Failed to load  module "module-alsa-source" (argument: "device_id=0 source_name=alsa_input.pci_1106_3059_sound_card_0_alsa_capture_0 tsched=0"): initialization failed.
E: alsa-util.c: Error opening PCM device hw:0: No such file or directory
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_1106_3059_sound_card_0_alsa_playback_0 tsched=0"): initialization failed.

```

Can someone help about that?
tnx in advance...

---

### Post by binbash on 2009-03-23
This should be at development forum > Jaunty section since it is alpha

---

### Post by t3ch on 2009-03-23
if i move that there you will give me the smartest answer?

---

