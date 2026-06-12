---
title: "Frustrating Sound Issue .. followed every guide still stuck!"
date: 2012-04-26
forum: Multimedia Software
---

### Post by coopz81 on 2012-04-26
Im running Kubuntu 11.10 and im having problems with my onboard sound card for a Dell Optiplex620.

My problem first stemmed when I tried installing a new soundcard, seperate to my onboard sound. I tried compiling the drivers for the new card but could never get it working. Now with the new soundcard removed from my machine the onboard soundcard wont work.

If I do
```
aplay -l
```i get
```
 aplay: device_list:240: no soundcards found...
```If i do 
```
echo  "Sound cards recognized by the system:"; lspci -nn | grep --color=none  '\[04[80][13]\]'; echo "Sound cards recognized by ALSA:"; lspci -nn |  grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3  '\[04[80][13]\]' | grep -e 'Kernel modules: ..*' -e '\[04[80][13]\]' |  grep --color=none -F "$line"; done; echo "Sound cards recognized by  ALSA, and activated:"; lspci -nn | grep '\[04[80][13]\]' | while read  line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel  drivers in use: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line";  done
```I get
```
Sound cards recognized by the system:
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller [8086:27de] (rev 01)
Sound cards recognized by ALSA:
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller [8086:27de] (rev 01)
Sound cards recognized by ALSA, and activated:
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller [8086:27de] (rev 01)
```When following this guide [http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0](http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0) to install the alsa drivers manually i get an error when i try the command
```
modprobe snd-intel8x0 ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss
```I get
```
FATAL: Error inserting snd_intel8x0 (/lib/modules/3.0.0-17-generic/kernel/sound/pci/snd-intel8x0.ko): Invalid argument
WARNING: Error inserting snd_page_alloc (/lib/modules/3.0.0-17-generic/kernel/sound/core/snd-page-alloc.ko): Invalid argument
WARNING: Error inserting snd_timer (/lib/modules/3.0.0-17-generic/kernel/sound/core/snd-timer.ko): Invalid argument
WARNING: Error inserting snd_pcm (/lib/modules/3.0.0-17-generic/kernel/sound/core/snd-pcm.ko): Invalid argument
FATAL: Error inserting snd_pcm_oss (/lib/modules/3.0.0-17-generic/kernel/sound/acore/oss/snd-pcm-oss.ko): Invalid argument
FATAL: Error inserting snd_mixer_oss (/lib/modules/3.0.0-17-generic/kernel/sound/acore/oss/snd-mixer-oss.ko): Invalid argument
FATAL: Error inserting snd_seq_oss (/lib/modules/3.0.0-17-generic/kernel/sound/acore/seq/oss/snd-seq-oss.ko): Invalid argument
```When I try 
```
sudo module-assistant a-i   alsa-source
```I get
```
gcc -M -D__KERNEL__ -D__isapnp_now__ -DMODULE=1 -I/usr/src/modules/alsa-driver/include  -I/usr/src/linux-headers-3.0.0-17-generic/include -I/usr/src/linux-headers-3.0.0-17-generic/include -I/usr/src/linux-headers-3.0.0-17-generic/arch/x86/include -O2 -mpreferred-stack-boundary=2 -march=i686 -Wdeclaration-after-statement -Wno-pointer-sign -D__SMP__ -DCONFIG_SMP -DLINUX -DALSA_BUILD -nostdinc -iwithprefix include -fno-omit-frame-pointer -I/usr/src/modules/alsa-driver/alsa-kernel/core/oss -fno-omit-frame-pointer mixer_oss.c pcm_oss.c pcm_plugin.c io.c copy.c linear.c mulaw.c route.c rate.c > .depend
mixer_oss.c:24:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
pcm_oss.c:31:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[5]: *** [fastdep] Error 1
make[5]: Leaving directory `/usr/src/modules/alsa-driver/acore/oss'
make[4]: *** [_sfdep_oss] Error 2
make[4]: Leaving directory `/usr/src/modules/alsa-driver/acore'
make[3]: *** [dep] Error 1
make[3]: Leaving directory `/usr/src/modules/alsa-driver'
make[2]: *** [include/sndversions.h] Error 2
make[2]: Leaving directory `/usr/src/modules/alsa-driver'
make[1]: *** [build-stamp] Error 2
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make: *** [kdist_image] Error 2
```

Lastly if i try open alsamixer gui I get the error
```

No protocol specified
xcb_connection_has_error() returned true

No protocol specified
Can't open display: :0
```Can anyone out there help me ? Without having to reinstall Kubuntu

Many thousands of thanks in advance :)

---

### Post by SeijiSensei on 2012-04-26
I don't know if you can recover from all those changes. Remember that Ubuntu uses pulseaudio as its primary sound system.  ALSA is managed by pulse. 

On a vanilla system like mine (12.04b2), you control the audio system by going to System Settings > Multimedia > Phonon and selecting the appropriate device for each of the listed tasks.  I'd start there and see if you can fix the problem.  If not, I don't know how to roll back the changes you made.

If you decide to reinstall, I'd use [12.04]("http://cdimage.ubuntu.com/kubuntu/releases/12.04/release/") which has long-term support and is now available.

---

