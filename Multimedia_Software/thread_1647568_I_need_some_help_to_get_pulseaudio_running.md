---
title: "I need some help to get pulseaudio running"
date: 2010-12-17
forum: Multimedia Software
---

### Post by khatarnak on 2010-12-17
Hello,

I'm trying to run a command-line ubuntu system (10.10) as a  music-player. I want to use pulseaudio and it's network capailities and  mpd as well.

unfortunately, I don't get it running. Sound in general works (using live-CD for example).

My system is configured as are as follows:

```
cat /proc/asound/cards
  0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with ALC650F at irq 11
```

```
aplay -l
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: I82801DBICH4 [Intel 82801DB-ICH4], Gerät 0: Intel ICH [Intel 82801DB-ICH4]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 0: I82801DBICH4 [Intel 82801DB-ICH4], Gerät 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
```


```
pkill pulseaudio; sleep 2; pulseaudio -vv
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) fehlgeschlagen: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) fehlgeschlagen: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
I: core-util.c: Failed to acquire high-priority scheduling: Input/output error
I: main.c: Dies ist PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Kompilier-Host: i686-pc-linux-gnu
D: main.c: Kompilier-CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe  -Wno-long-long -Winline -Wvla -Wno-overlength-strings  -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op  -Wsign-compare -Wformat-security -Wmissing-include-dirs  -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self  -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes  -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations  -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align  -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math  -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Laufe auf Host: Linux i686 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010
D: main.c: 1 CPUs gefunden.
I: main.c: Seitengröße ist 4096 Bytes.
D: main.c: Kompiliere mit Valgrind-Unterstützung: nein
D: main.c: Läuft im Valgrind-Modus: no
D: main.c: Running in VM: no
D: main.c: Optimiertes Build: ja
D: main.c: Alle Ansprüche aktiviert.
I: main.c: System- ID ist 49dcdd0b374327837e7d58d200000756.
I: main.c: System- ID ist 49dcdd0b374327837e7d58d200000756-1292608677.215415-1465211344.
I: main.c: Nutze Laufzeit-Verzeichnis /home/mucke/.pulse/49dcdd0b374327837e7d58d200000756-runtime.
I: main.c: Nutze Zustands-Verzeichnis /home/mucke/.pulse.
I: main.c: Modul-Verzeichnis /usr/lib/pulse-0.9.21/modules benutzen.
I: main.c: Laufe im System-Modus: no
I: main.c: Neue hochauslösende Timer verfügbar! Guten Appetit!
I: cpu-x86.c: CPU flags: CMOV MMX SSE 
I: svolume_mmx.c: Initialising MMX optimized functions.
I: remap_mmx.c: Initialising MMX optimized remappers.
I: sconv_sse.c: Initialising SSE optimized conversions.
D: memblock.c: Using shared memory pool with 1024 slots of size 64,0 KB  each, total size is 64,0 MB, maximum usable slot size is 65496
D: database-tdb.c: Opened TDB database '/home/mucke/.pulse/49dcdd0b374327837e7d58d200000756-device-volumes.tdb'
I: module-device-restore.c: Sucessfully opened database file  '/home/mucke/.pulse/49dcdd0b374327837e7d58d200000756-device-volumes'.
I: module.c: Loaded "module-device-restore" (index: #0; argument: "").
D: database-tdb.c: Opened TDB database '/home/mucke/.pulse/49dcdd0b374327837e7d58d200000756-stream-volumes.tdb'
I: module-stream-restore.c: Sucessfully opened database file  '/home/mucke/.pulse/49dcdd0b374327837e7d58d200000756-stream-volumes'.
I: module.c: Loaded "module-stream-restore" (index: #1; argument: "").
D: database-tdb.c: Opened TDB database '/home/mucke/.pulse/49dcdd0b374327837e7d58d200000756-card-database.tdb'
I: module-card-restore.c: Sucessfully opened database file '/home/mucke/.pulse/49dcdd0b374327837e7d58d200000756-card-database'.
I: module.c: Loaded "module-card-restore" (index: #2; argument: "").
I: module.c: Loaded "module-augment-properties" (index: #3; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-udev-detect.so': success
D: module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
D: module-udev-detect.c: /devices/pci0000:00/0000:00:1f.5/sound/card0 is busy: no
D: module-udev-detect.c: Loading module-alsa-card with arguments  'device_id="0" name="pci-0000_00_1f.5"  card_name="alsa_card.pci-0000_00_1f.5" tsched=yes ignore_dB=no  card_properties="module-udev-detect.discovered=1"'
D: reserve-wrap.c: Unable to contact D-Bus session bus:  org.freedesktop.DBus.Error.Spawn.ExecFailed: /bin/dbus-launch terminated  abnormally with the following error: Autolaunch error: X11  initialization failed.
D: alsa-mixer.c: Looking at profile output:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-mono+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-mono+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-mono+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-mono+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 371 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile output:analog-stereo supported.
D: alsa-mixer.c: Looking at profile output:analog-stereo+input:analog-mono
D: alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-stereo+input:analog-stereo
D: alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 371 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile output:analog-stereo+input:analog-stereo supported.
D: alsa-mixer.c: Looking at profile output:analog-stereo+input:iec958-stereo
D: alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D4c' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-stereo+input:iec958-surround-40
D: alsa-mixer.c: Checking for recording on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D4c' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround40:0
D: alsa-util.c: Maximum hw buffer size is 185 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile output:analog-surround-40 supported.
D: alsa-mixer.c: Looking at profile output:analog-surround-40+input:analog-mono
D: alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-40+input:analog-stereo
D: alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 371 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile output:analog-surround-40+input:analog-stereo supported.
D: alsa-mixer.c: Looking at profile output:analog-surround-40+input:iec958-stereo
D: alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D4c' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-40+input:iec958-surround-40
D: alsa-mixer.c: Checking for recording on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D4c' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-41
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround41:0
D: alsa-util.c: Maximum hw buffer size is 123 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile output:analog-surround-41 supported.
D: alsa-mixer.c: Looking at profile output:analog-surround-41+input:analog-mono
D: alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-41+input:analog-stereo
D: alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 371 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile output:analog-surround-41+input:analog-stereo supported.
D: alsa-mixer.c: Looking at profile output:analog-surround-41+input:iec958-stereo
D: alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D4c' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-41+input:iec958-surround-40
D: alsa-mixer.c: Checking for recording on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D4c' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-50
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround50:0
D: alsa-util.c: Maximum hw buffer size is 123 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile output:analog-surround-50 supported.
D: alsa-mixer.c: Looking at profile output:analog-surround-50+input:analog-mono
D: alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-50+input:analog-stereo
D: alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 371 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile output:analog-surround-50+input:analog-stereo supported.
D: alsa-mixer.c: Looking at profile output:analog-surround-50+input:iec958-stereo
D: alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D4c' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-50+input:iec958-surround-40
D: alsa-mixer.c: Checking for recording on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D4c' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-51
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround51:0
D: alsa-util.c: Maximum hw buffer size is 123 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile output:analog-surround-51 supported.
D: alsa-mixer.c: Looking at profile output:analog-surround-51+input:analog-mono
D: alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-51+input:analog-stereo
D: alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 371 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile output:analog-surround-51+input:analog-stereo supported.
D: alsa-mixer.c: Looking at profile output:analog-surround-51+input:iec958-stereo
D: alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D4c' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-51+input:iec958-surround-40
D: alsa-mixer.c: Checking for recording on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D4c' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-71
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM surround71:0
I: alsa-util.c: Error opening PCM device surround71:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-71+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM surround71:0
I: alsa-util.c: Error opening PCM device surround71:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-71+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM surround71:0
I: alsa-util.c: Error opening PCM device surround71:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-71+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM surround71:0
I: alsa-util.c: Error opening PCM device surround71:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:analog-surround-71+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM surround71:0
I: alsa-util.c: Error opening PCM device surround71:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: Maximum hw buffer size is 371 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile output:iec958-stereo supported.
D: alsa-mixer.c: Looking at profile output:iec958-stereo+input:analog-mono
D: alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:iec958-stereo+input:analog-stereo
D: alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 371 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile output:iec958-stereo+input:analog-stereo supported.
D: alsa-mixer.c: Looking at profile output:iec958-stereo+input:iec958-stereo
D: alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D4c' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-stereo+input:iec958-surround-40
D: alsa-mixer.c: Checking for recording on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D4c' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:hdmi-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM hdmi:0
I: alsa-util.c: Error opening PCM device hdmi:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM hdmi:0
I: alsa-util.c: Error opening PCM device hdmi:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM hdmi:0
I: alsa-util.c: Error opening PCM device hdmi:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM hdmi:0
I: alsa-util.c: Error opening PCM device hdmi:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM hdmi:0
I: alsa-util.c: Error opening PCM device hdmi:0: Invalid argument
D: alsa-mixer.c: Looking at profile input:analog-mono
D: alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile input:analog-stereo
D: alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 371 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile input:analog-stereo supported.
D: alsa-mixer.c: Looking at profile input:iec958-stereo
D: alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D4c' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile input:iec958-surround-40
D: alsa-mixer.c: Checking for recording on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D4c' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
I: card.c: Created 0 "alsa_card.pci-0000_00_1f.5"
D: reserve-wrap.c: Unable to contact D-Bus session bus:  org.freedesktop.DBus.Error.Spawn.ExecFailed: /bin/dbus-launch terminated  abnormally with the following error: Autolaunch error: X11  initialization failed.
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 371 ms
D: alsa-util.c: Set buffer size first (to 88200 samples), period size second (to 88200 samples).
I: alsa-sink.c: Successfully opened device front:0.
I: alsa-sink.c: Selected mapping 'Analog Stereo' (analog-stereo).
I: alsa-sink.c: Successfully enabled mmap() mode.
I: alsa-sink.c: Successfully enabled timer-based scheduling mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-mixer.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-mixer.c: Successfully attached to mixer 'hw:0'
D: alsa-mixer.c: Probing path 'analog-output'
D: alsa-mixer.c: Probing path 'analog-output-speaker'
D: alsa-mixer.c: Probe of element 'Speaker' failed.
D: alsa-mixer.c: Probing path 'analog-output-speaker'
D: alsa-mixer.c: Probe of element 'Desktop Speaker' failed.
D: alsa-mixer.c: Probing path 'analog-output-headphones'
D: alsa-mixer.c: Probe of element 'Headphone' failed.
D: alsa-mixer.c: Probing path 'analog-output-headphones'
D: alsa-mixer.c: Probe of element 'Headphone2' failed.
D: alsa-mixer.c: Probing path 'analog-output-mono'
D: alsa-mixer.c: Probing path 'analog-output-lfe-on-mono'
D: alsa-sink.c: Probed mixer paths:
D: alsa-mixer.c: Path Set 0xa0488f8, direction=1, probed=yes
D: alsa-mixer.c: Path analog-output (Analog Output), direction=1,  priority=99, probed=yes, supported=yes, has_mute=yes, has_volume=yes,  has_dB=yes, min_volume=0, max_volume=31, min_dB=-127,5, max_dB=12
D: alsa-mixer.c: Element Master, direction=1, switch=1, volume=1,  enumeration=0, required=0, required_absent=0, mask=0x3600000000f66,  n_channels=2, override_map=yes
D: alsa-mixer.c: Element Master Mono, direction=1, switch=2, volume=2,  enumeration=0, required=0, required_absent=0, mask=0x7ffffffffffff,  n_channels=1, override_map=no
D: alsa-mixer.c: Element Surround, direction=1, switch=1, volume=1,  enumeration=0, required=0, required_absent=0, mask=0x60, n_channels=2,  override_map=yes
D: alsa-mixer.c: Element Center, direction=1, switch=1, volume=1,  enumeration=0, required=0, required_absent=0, mask=0x4900000000018,  n_channels=1, override_map=yes
D: alsa-mixer.c: Element LFE, direction=1, switch=1, volume=1,  enumeration=0, required=0, required_absent=0, mask=0x80, n_channels=1,  override_map=yes
D: alsa-mixer.c: Element PCM, direction=1, switch=1, volume=1,  enumeration=0, required=0, required_absent=0, mask=0x402b600000000f66,  n_channels=2, override_map=yes
D: alsa-mixer.c: Element External Amplifier, direction=1, switch=4,  volume=0, enumeration=0, required=0, required_absent=0, mask=0x0,  n_channels=0, override_map=no
D: alsa-mixer.c: Option on (output-amplifier-on/Amplifier) index=1, priority=10
D: alsa-mixer.c: Option off (output-amplifier-off/No Amplifier) index=0, priority=0
D: alsa-mixer.c: Setting output-amplifier-on (Amplifier) priority=10
D: alsa-mixer.c: Setting output-amplifier-off (No Amplifier) priority=0
D: alsa-mixer.c: Path analog-output-mono (Analog Mono Output),  direction=1, priority=50, probed=yes, supported=yes, has_mute=yes,  has_volume=yes, has_dB=yes, min_volume=0, max_volume=31, min_dB=-81,  max_dB=12
D: alsa-mixer.c: Element Master, direction=1, switch=2, volume=2,  enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2,  override_map=no
D: alsa-mixer.c: Element Master Mono, direction=1, switch=1, volume=1,  enumeration=0, required=4, required_absent=0, mask=0x7ffffffffffff,  n_channels=1, override_map=yes
D: alsa-mixer.c: Element Surround, direction=1, switch=2, volume=2,  enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2,  override_map=no
D: alsa-mixer.c: Element Center, direction=1, switch=2, volume=2,  enumeration=0, required=0, required_absent=0, mask=0x7ffffffffffff,  n_channels=1, override_map=no
D: alsa-mixer.c: Element LFE, direction=1, switch=2, volume=2,  enumeration=0, required=0, required_absent=0, mask=0x7ffffffffffff,  n_channels=1, override_map=no
D: alsa-mixer.c: Element PCM, direction=1, switch=1, volume=1,  enumeration=0, required=0, required_absent=0, mask=0x402b600000000f66,  n_channels=2, override_map=yes
D: alsa-mixer.c: Element External Amplifier, direction=1, switch=4,  volume=0, enumeration=0, required=0, required_absent=0, mask=0x0,  n_channels=0, override_map=no
D: alsa-mixer.c: Option on (output-amplifier-on/Amplifier) index=1, priority=10
D: alsa-mixer.c: Option off (output-amplifier-off/No Amplifier) index=0, priority=0
D: alsa-mixer.c: Setting output-amplifier-on (Amplifier) priority=10
D: alsa-mixer.c: Setting output-amplifier-off (No Amplifier) priority=0
D: alsa-mixer.c: Path analog-output-lfe-on-mono (Analog Output (LFE)),  direction=1, priority=40, probed=yes, supported=yes, has_mute=yes,  has_volume=yes, has_dB=yes, min_volume=0, max_volume=31, min_dB=-81,  max_dB=12
D: alsa-mixer.c: Element Master, direction=1, switch=1, volume=1,  enumeration=0, required=0, required_absent=0, mask=0x3600000000f66,  n_channels=2, override_map=yes
D: alsa-mixer.c: Element Master Mono, direction=1, switch=1, volume=1,  enumeration=0, required=4, required_absent=0, mask=0x80, n_channels=1,  override_map=yes
D: alsa-mixer.c: Element Surround, direction=1, switch=2, volume=2,  enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2,  override_map=no
D: alsa-mixer.c: Element Center, direction=1, switch=2, volume=2,  enumeration=0, required=0, required_absent=0, mask=0x7ffffffffffff,  n_channels=1, override_map=no
D: alsa-mixer.c: Element LFE, direction=1, switch=2, volume=2,  enumeration=0, required=0, required_absent=0, mask=0x7ffffffffffff,  n_channels=1, override_map=no
D: alsa-mixer.c: Element PCM, direction=1, switch=1, volume=1,  enumeration=0, required=0, required_absent=0, mask=0x402b600000000f66,  n_channels=2, override_map=yes
D: alsa-mixer.c: Element External Amplifier, direction=1, switch=4,  volume=0, enumeration=0, required=0, required_absent=0, mask=0x0,  n_channels=0, override_map=no
D: alsa-mixer.c: Option on (output-amplifier-on/Amplifier) index=1, priority=10
D: alsa-mixer.c: Option off (output-amplifier-off/No Amplifier) index=0, priority=0
D: alsa-mixer.c: Setting output-amplifier-on (Amplifier) priority=10
D: alsa-mixer.c: Setting output-amplifier-off (No Amplifier) priority=0
D: alsa-mixer.c: Added 6 ports
I: sink.c: Created sink 0 "alsa_output.pci-0000_00_1f.5.analog-stereo"  with sample spec s16le 2ch 44100Hz and channel map  front-left,front-right
I: sink.c:     alsa.resolution_bits = "16"
I: sink.c:     device.api = "alsa"
I: sink.c:     device.class = "sound"
I: sink.c:     alsa.class = "generic"
I: sink.c:     alsa.subclass = "generic-mix"
I: sink.c:     alsa.name = "Intel 82801DB-ICH4"
I: sink.c:     alsa.id = "Intel ICH"
I: sink.c:     alsa.subdevice = "0"
I: sink.c:     alsa.subdevice_name = "subdevice #0"
I: sink.c:     alsa.device = "0"
I: sink.c:     alsa.card = "0"
I: sink.c:     alsa.card_name = "Intel 82801DB-ICH4"
I: sink.c:     alsa.long_card_name = "Intel 82801DB-ICH4 with ALC650F at irq 11"
I: sink.c:     alsa.driver_name = "snd_intel8x0"
I: sink.c:     device.bus_path = "pci-0000:00:1f.5"
I: sink.c:     sysfs.path = "/devices/pci0000:00/0000:00:1f.5/sound/card0"
I: sink.c:     device.bus = "pci"
I: sink.c:     device.vendor.id = "8086"
I: sink.c:     device.vendor.name = "Intel Corporation"
I: sink.c:     device.product.id = "24c5"
I: sink.c:     device.product.name = "82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller"
I: sink.c:     device.form_factor = "internal"
I: sink.c:     device.string = "front:0"
I: sink.c:     device.buffering.buffer_size = "65536"
I: sink.c:     device.buffering.fragment_size = "65536"
I: sink.c:     device.access_mode = "mmap+timer"
I: sink.c:     device.profile.name = "analog-stereo"
I: sink.c:     device.profile.description = "Analog Stereo"
I: sink.c:     device.description = "Internes Audio Analog Stereo"
I: sink.c:     alsa.mixer_name = "Realtek ALC650F"
I: sink.c:     alsa.components = "AC97a:414c4723"
I: sink.c:     module-udev-detect.discovered = "1"
I: sink.c:     device.icon_name = "audio-card-pci"
D: core-subscribe.c: Dropped redundant event due to change event.
I: source.c: Created source 0  "alsa_output.pci-0000_00_1f.5.analog-stereo.monitor" with sample spec  s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     device.description = "Monitor of Internes Audio Analog Stereo"
I: source.c:     device.class = "monitor"
I: source.c:     alsa.card = "0"
I: source.c:     alsa.card_name = "Intel 82801DB-ICH4"
I: source.c:     alsa.long_card_name = "Intel 82801DB-ICH4 with ALC650F at irq 11"
I: source.c:     alsa.driver_name = "snd_intel8x0"
I: source.c:     device.bus_path = "pci-0000:00:1f.5"
I: source.c:     sysfs.path = "/devices/pci0000:00/0000:00:1f.5/sound/card0"
I: source.c:     device.bus = "pci"
I: source.c:     device.vendor.id = "8086"
I: source.c:     device.vendor.name = "Intel Corporation"
I: source.c:     device.product.id = "24c5"
I: source.c:     device.product.name = "82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller"
I: source.c:     device.form_factor = "internal"
I: source.c:     device.string = "0"
I: source.c:     module-udev-detect.discovered = "1"
I: source.c:     device.icon_name = "audio-card-pci"
I: alsa-sink.c: Using 1,0 fragments of size 65536 bytes (371,52ms), buffer size is 65536 bytes (371,52ms)
I: alsa-sink.c: Time scheduling watermark is 20,00ms
D: alsa-sink.c: hwbuf_unused=0
D: alsa-sink.c: setting avail_min=15502
D: alsa-mixer.c: Activating path analog-output
D: alsa-mixer.c: Path analog-output (Analog Output), direction=1,  priority=99, probed=yes, supported=yes, has_mute=yes, has_volume=yes,  has_dB=yes, min_volume=0, max_volume=31, min_dB=-127,5, max_dB=12
D: alsa-mixer.c: Element Master, direction=1, switch=1, volume=1,  enumeration=0, required=0, required_absent=0, mask=0x3600000000f66,  n_channels=2, override_map=yes
D: alsa-mixer.c: Element Master Mono, direction=1, switch=2, volume=2,  enumeration=0, required=0, required_absent=0, mask=0x7ffffffffffff,  n_channels=1, override_map=no
D: alsa-mixer.c: Element Surround, direction=1, switch=1, volume=1,  enumeration=0, required=0, required_absent=0, mask=0x60, n_channels=2,  override_map=yes
D: alsa-mixer.c: Element Center, direction=1, switch=1, volume=1,  enumeration=0, required=0, required_absent=0, mask=0x4900000000018,  n_channels=1, override_map=yes
D: alsa-mixer.c: Element LFE, direction=1, switch=1, volume=1,  enumeration=0, required=0, required_absent=0, mask=0x80, n_channels=1,  override_map=yes
D: alsa-mixer.c: Element PCM, direction=1, switch=1, volume=1,  enumeration=0, required=0, required_absent=0, mask=0x402b600000000f66,  n_channels=2, override_map=yes
D: alsa-mixer.c: Element External Amplifier, direction=1, switch=4,  volume=0, enumeration=0, required=0, required_absent=0, mask=0x0,  n_channels=0, override_map=no
D: alsa-mixer.c: Option on (output-amplifier-on/Amplifier) index=1, priority=10
D: alsa-mixer.c: Option off (output-amplifier-off/No Amplifier) index=0, priority=0
D: alsa-mixer.c: Setting output-amplifier-on (Amplifier) priority=10
D: alsa-mixer.c: Setting output-amplifier-off (No Amplifier) priority=0
I: alsa-sink.c: Hardware volume ranges from -127,50 dB to 12,00 dB.
I: alsa-sink.c: Fixing base volume to -12,00 dB
I: alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
I: alsa-sink.c: Using hardware mute control.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Hardware PCM card 0 'Intel 82801DB-ICH4' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 16384
D: alsa-util.c:   period_size  : 16384
D: alsa-util.c:   period_time  : 371519
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 16384
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1073741824
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1073741824
D: alsa-util.c:   appl_ptr     : 0
D: alsa-util.c:   hw_ptr       : 0
D: alsa-sink.c: Read hardware volume: 0:  42% 1:  42%
D: alsa-sink.c: Thread starting up
I: core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 4, which is lower than the requested 5.
I: alsa-sink.c: Starting playback.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 371 ms
D: alsa-util.c: Set buffer size first (to 88200 samples), period size second (to 88200 samples).
I: alsa-source.c: Successfully opened device front:0.
I: alsa-source.c: Selected mapping 'Analog Stereo' (analog-stereo).
I: alsa-source.c: Successfully enabled mmap() mode.
I: alsa-source.c: Successfully enabled timer-based scheduling mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-mixer.c: Unable to attach to mixer front:0: No such file or directory
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
I: alsa-mixer.c: Successfully attached to mixer 'hw:0'
D: alsa-mixer.c: Probing path 'analog-input'
D: alsa-mixer.c: Probe of element 'Mic' failed.
D: alsa-mixer.c: Probing path 'analog-input-microphone'
D: alsa-mixer.c: Probing path 'analog-input-linein'
D: alsa-mixer.c: Probing path 'analog-input'
D: alsa-mixer.c: Probing path 'analog-input-video'
D: alsa-mixer.c: Probing path 'analog-input-video'
D: alsa-mixer.c: Probe of element 'TV Tuner' failed.
D: alsa-mixer.c: Probing path 'analog-input-radio'
D: alsa-mixer.c: Probe of element 'FM' failed.
D: alsa-mixer.c: Probing path 'analog-input'
D: alsa-mixer.c: Probe of element 'Mic/Line' failed.
D: alsa-source.c: Probed mixer paths:
D: alsa-mixer.c: Path Set 0xa0743c8, direction=2, probed=yes
D: alsa-mixer.c: Path analog-input-microphone (Analog Microphone),  direction=2, priority=100, probed=yes, supported=yes, has_mute=yes,  has_volume=yes, has_dB=yes, min_volume=0, max_volume=15, min_dB=0,  max_dB=22,5
D: alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1,  enumeration=0, required=0, required_absent=0, mask=0x4037e00000000f66,  n_channels=2, override_map=yes
D: alsa-mixer.c: Element Mic, direction=2, switch=1, volume=0,  enumeration=0, required=4, required_absent=0, mask=0x0, n_channels=0,  override_map=yes
D: alsa-mixer.c: Element Line, direction=2, switch=2, volume=0,  enumeration=0, required=0, required_absent=0, mask=0x0, n_channels=0,  override_map=no
D: alsa-mixer.c: Element Aux, direction=2, switch=2, volume=0,  enumeration=0, required=0, required_absent=0, mask=0x0, n_channels=0,  override_map=no
D: alsa-mixer.c: Element Video, direction=2, switch=2, volume=0,  enumeration=0, required=0, required_absent=0, mask=0x0, n_channels=0,  override_map=no
D: alsa-mixer.c: Element Mic Select, direction=2, switch=0, volume=0,  enumeration=1, required=0, required_absent=0, mask=0x0, n_channels=0,  override_map=no
D: alsa-mixer.c: Option Mic1 (input-microphone-1/Microphone 1) index=0, priority=20
D: alsa-mixer.c: Option Mic2 (input-microphone-2/Microphone 2) index=1, priority=19
D: alsa-mixer.c: Setting input-microphone-1 (Microphone 1) priority=20
D: alsa-mixer.c: Setting input-microphone-2 (Microphone 2) priority=19
D: alsa-mixer.c: Path analog-input-linein (Analog Line-In), direction=2,  priority=90, probed=yes, supported=yes, has_mute=yes, has_volume=yes,  has_dB=yes, min_volume=0, max_volume=15, min_dB=0, max_dB=22,5
D: alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1,  enumeration=0, required=0, required_absent=0, mask=0x4037e00000000f66,  n_channels=2, override_map=yes
D: alsa-mixer.c: Element Mic, direction=2, switch=2, volume=0,  enumeration=0, required=0, required_absent=0, mask=0x0, n_channels=0,  override_map=no
D: alsa-mixer.c: Element Line, direction=2, switch=1, volume=0,  enumeration=0, required=4, required_absent=0, mask=0x0, n_channels=0,  override_map=yes
D: alsa-mixer.c: Element Aux, direction=2, switch=2, volume=0,  enumeration=0, required=0, required_absent=0, mask=0x0, n_channels=0,  override_map=no
D: alsa-mixer.c: Element Video, direction=2, switch=2, volume=0,  enumeration=0, required=0, required_absent=0, mask=0x0, n_channels=0,  override_map=no
D: alsa-mixer.c: Path analog-input (Analog Input), direction=2,  priority=90, probed=yes, supported=yes, has_mute=yes, has_volume=yes,  has_dB=yes, min_volume=0, max_volume=15, min_dB=0, max_dB=22,5
D: alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1,  enumeration=0, required=0, required_absent=0, mask=0x4037e00000000f66,  n_channels=2, override_map=yes
D: alsa-mixer.c: Element Mic, direction=2, switch=2, volume=0,  enumeration=0, required=0, required_absent=0, mask=0x0, n_channels=0,  override_map=no
D: alsa-mixer.c: Element Line, direction=2, switch=2, volume=0,  enumeration=0, required=0, required_absent=0, mask=0x0, n_channels=0,  override_map=no
D: alsa-mixer.c: Element Aux, direction=2, switch=1, volume=0,  enumeration=0, required=4, required_absent=0, mask=0x0, n_channels=0,  override_map=yes
D: alsa-mixer.c: Element Video, direction=2, switch=2, volume=0,  enumeration=0, required=0, required_absent=0, mask=0x0, n_channels=0,  override_map=no
D: alsa-mixer.c: Path analog-input-video (Analog Video), direction=2,  priority=70, probed=yes, supported=yes, has_mute=yes, has_volume=yes,  has_dB=yes, min_volume=0, max_volume=15, min_dB=0, max_dB=22,5
D: alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1,  enumeration=0, required=0, required_absent=0, mask=0x4037e00000000f66,  n_channels=2, override_map=yes
D: alsa-mixer.c: Element Mic, direction=2, switch=2, volume=0,  enumeration=0, required=0, required_absent=0, mask=0x0, n_channels=0,  override_map=no
D: alsa-mixer.c: Element Line, direction=2, switch=2, volume=0,  enumeration=0, required=0, required_absent=0, mask=0x0, n_channels=0,  override_map=no
D: alsa-mixer.c: Element Aux, direction=2, switch=2, volume=0,  enumeration=0, required=0, required_absent=0, mask=0x0, n_channels=0,  override_map=no
D: alsa-mixer.c: Element Video, direction=2, switch=1, volume=0,  enumeration=0, required=4, required_absent=0, mask=0x0, n_channels=0,  override_map=yes
D: alsa-mixer.c: Added 5 ports
D: core-subscribe.c: Dropped redundant event due to change event.
I: source.c: Created source 1  "alsa_input.pci-0000_00_1f.5.analog-stereo" with sample spec s16le 2ch  44100Hz and channel map front-left,front-right
I: source.c:     alsa.resolution_bits = "16"
I: source.c:     device.api = "alsa"
I: source.c:     device.class = "sound"
I: source.c:     alsa.class = "generic"
I: source.c:     alsa.subclass = "generic-mix"
I: source.c:     alsa.name = "Intel 82801DB-ICH4"
I: source.c:     alsa.id = "Intel ICH"
I: source.c:     alsa.subdevice = "0"
I: source.c:     alsa.subdevice_name = "subdevice #0"
I: source.c:     alsa.device = "0"
I: source.c:     alsa.card = "0"
I: source.c:     alsa.card_name = "Intel 82801DB-ICH4"
I: source.c:     alsa.long_card_name = "Intel 82801DB-ICH4 with ALC650F at irq 11"
I: source.c:     alsa.driver_name = "snd_intel8x0"
I: source.c:     device.bus_path = "pci-0000:00:1f.5"
I: source.c:     sysfs.path = "/devices/pci0000:00/0000:00:1f.5/sound/card0"
I: source.c:     device.bus = "pci"
I: source.c:     device.vendor.id = "8086"
I: source.c:     device.vendor.name = "Intel Corporation"
I: source.c:     device.product.id = "24c5"
I: source.c:     device.product.name = "82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller"
I: source.c:     device.form_factor = "internal"
I: source.c:     device.string = "front:0"
I: source.c:     device.buffering.buffer_size = "65536"
I: source.c:     device.buffering.fragment_size = "65536"
I: source.c:     device.access_mode = "mmap+timer"
I: source.c:     device.profile.name = "analog-stereo"
I: source.c:     device.profile.description = "Analog Stereo"
I: source.c:     device.description = "Internes Audio Analog Stereo"
I: source.c:     alsa.mixer_name = "Realtek ALC650F"
I: source.c:     alsa.components = "AC97a:414c4723"
I: source.c:     module-udev-detect.discovered = "1"
I: source.c:     device.icon_name = "audio-card-pci"
I: alsa-source.c: Using 1,0 fragments of size 65536 bytes (371,52ms), buffer size is 65536 bytes (371,52ms)
I: alsa-source.c: Time scheduling watermark is 20,00ms
D: alsa-source.c: hwbuf_unused=0
D: alsa-source.c: setting avail_min=15502
D: alsa-mixer.c: Activating path analog-input-microphone
D: alsa-mixer.c: Path analog-input-microphone (Analog Microphone),  direction=2, priority=100, probed=yes, supported=yes, has_mute=yes,  has_volume=yes, has_dB=yes, min_volume=0, max_volume=15, min_dB=0,  max_dB=22,5
D: alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1,  enumeration=0, required=0, required_absent=0, mask=0x4037e00000000f66,  n_channels=2, override_map=yes
D: alsa-mixer.c: Element Mic, direction=2, switch=1, volume=0,  enumeration=0, required=4, required_absent=0, mask=0x0, n_channels=0,  override_map=yes
D: alsa-mixer.c: Element Line, direction=2, switch=2, volume=0,  enumeration=0, required=0, required_absent=0, mask=0x0, n_channels=0,  override_map=no
D: alsa-mixer.c: Element Aux, direction=2, switch=2, volume=0,  enumeration=0, required=0, required_absent=0, mask=0x0, n_channels=0,  override_map=no
D: alsa-mixer.c: Element Video, direction=2, switch=2, volume=0,  enumeration=0, required=0, required_absent=0, mask=0x0, n_channels=0,  override_map=no
D: alsa-mixer.c: Element Mic Select, direction=2, switch=0, volume=0,  enumeration=1, required=0, required_absent=0, mask=0x0, n_channels=0,  override_map=no
D: alsa-mixer.c: Option Mic1 (input-microphone-1/Microphone 1) index=0, priority=20
D: alsa-mixer.c: Option Mic2 (input-microphone-2/Microphone 2) index=1, priority=19
D: alsa-mixer.c: Setting input-microphone-1 (Microphone 1) priority=20
D: alsa-mixer.c: Setting input-microphone-2 (Microphone 2) priority=19
I: alsa-source.c: Hardware volume ranges from 0,00 dB to 22,50 dB.
I: alsa-source.c: Fixing base volume to -22,50 dB
I: alsa-source.c: Using hardware volume control. Hardware dB scale supported.
I: alsa-source.c: Using hardware mute control.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Hardware PCM card 0 'Intel 82801DB-ICH4' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 16384
D: alsa-util.c:   period_size  : 16384
D: alsa-util.c:   period_time  : 371519
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 16384
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1073741824
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1073741824
D: alsa-util.c:   appl_ptr     : 0
D: alsa-util.c:   hw_ptr       : 0
D: alsa-source.c: Read hardware volume: 0:  42% 1:  42%
D: alsa-source.c: Thread starting up
I: core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 4, which is lower than the requested 5.
I: module.c: Loaded "module-alsa-card" (index: #4; argument:  "device_id="0" name="pci-0000_00_1f.5"  card_name="alsa_card.pci-0000_00_1f.5" tsched=yes ignore_dB=no  card_properties="module-udev-detect.discovered=1"").
I: module-udev-detect.c: Card /devices/pci0000:00/0000:00:1f.5/sound/card0 (alsa_card.pci-0000_00_1f.5) module loaded.
I: module-udev-detect.c: Found 1 cards.
I: module.c: Loaded "module-udev-detect" (index: #5; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-bluetooth-discover.so': failure
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-esound-protocol-unix.so': success
I: alsa-source.c: Starting capture.
I: module.c: Loaded "module-esound-protocol-unix" (index: #6; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #7; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #8; argument: "").
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-default-device-restore.c: Restored default sink 'alsa_output.pci-0000_00_1f.5.analog-stereo'.
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-default-device-restore.c: Restored default source 'alsa_input.pci-0000_00_1f.5.analog-stereo'.
I: module.c: Loaded "module-default-device-restore" (index: #9; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #10; argument: "").
I: module.c: Loaded "module-always-sink" (index: #11; argument: "").
I: module.c: Loaded "module-intended-roles" (index: #12; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo becomes idle, timeout in 5 seconds.
D: module-suspend-on-idle.c: Source alsa_input.pci-0000_00_1f.5.analog-stereo becomes idle, timeout in 5 seconds.
I: module.c: Loaded "module-suspend-on-idle" (index: #13; argument: "").
D: dbus-util.c: Successfully connected to D-Bus system bus 50739e1c56883ceef7ea115e0000000f as :1.13
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session1
I: client.c: Created 1 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session2"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session2
I: module.c: Loaded "module-console-kit" (index: #14; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #15; argument: "").
W: main.c: Unable to contact D-Bus:  org.freedesktop.DBus.Error.Spawn.ExecFailed: /bin/dbus-launch terminated  abnormally with the following error: Autolaunch error: X11  initialization failed.
I: main.c: Start des Daemons abgeschlossen.
D: module-console-kit.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
D: alsa-sink.c: Wakeup from ALSA!
I: alsa-sink.c: Underrun!
I: alsa-sink.c: Increasing wakeup watermark to 30,00 ms
D: alsa-sink.c: Wakeup from ALSA!
I: alsa-sink.c: Underrun!
I: alsa-sink.c: Increasing wakeup watermark to 40,00 ms
D: alsa-sink.c: Wakeup from ALSA!
I: alsa-sink.c: Underrun!
I: alsa-sink.c: Increasing wakeup watermark to 50,00 ms
D: alsa-source.c: Wakeup from ALSA!
D: alsa-sink.c: Wakeup from ALSA!
I: alsa-sink.c: Underrun!
I: alsa-sink.c: Increasing wakeup watermark to 60,00 ms
I: module-suspend-on-idle.c: Source alsa_input.pci-0000_00_1f.5.analog-stereo idle for too long, suspending ...
D: source.c: Suspend cause of source alsa_input.pci-0000_00_1f.5.analog-stereo is 0x0004, suspending
I: alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1f.5.analog-stereo idle for too long, suspending ...
D: sink.c: Suspend cause of sink alsa_output.pci-0000_00_1f.5.analog-stereo is 0x0004, suspending
I: alsa-sink.c: Device suspended...
D: module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
```

when I try to playback a mp3-file with aplay, it says:

```
aplay test.mp3 
ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Zugriff abgelehnt

aplay: main:654: Fehler beim Öffnen des Gerätes: Connection refused
```

```
paplay test.mp3 
Öffnen der Audio-Datei fehlgeschlagen.
```

sorry for the german, the last error means "open audio file failed"

What might be the problem? What information can i additionally provide?

---

### Post by CheetoBandito on 2010-12-17
Have you added your user to the pulse-access and pulse-rt groups?

---

### Post by khatarnak on 2010-12-17
ok, now the user is in pulse-access

the group pulse-rt does not exist on my system - do I need it?

while trying "paplay" it's still the same error

using "aplay", now I get 

```
aplay test.mp3 
Wiedergabe: Rohdaten 'test.mp3' : Unsigned 8 bit, Rate: 8000 Hz, mono
```

it seems to playback something in theory, but there is absolutely no output. the mp3 file by the way is definitely not at 8kHz only and stereo.

---

### Post by CheetoBandito on 2010-12-17
What's your  ~/.asoundrc file look like?

---

### Post by khatarnak on 2010-12-17
Sorry, I don't have such a file. Whether as user nor as root. There also is no /etc/asound.conf on my system.

---

### Post by CheetoBandito on 2010-12-17
Scratch that last thought, I don't think those configs have anything to do with the network portion of pulse.  It does seem like enabling those features does require extra attention though.  Non-gui I can only find this info for arch
[https://wiki.archlinux.org/index.php/PulseAudio#PulseAudio_over_network](https://wiki.archlinux.org/index.php/PulseAudio#PulseAudio_over_network)

There is a document for Ubuntu but it only deals with the GUI.
[https://wiki.ubuntu.com/PulseAudio#Installation](https://wiki.ubuntu.com/PulseAudio#Installation)

If you have gnone installed, then try that... otherwise I hope the first link points you in the right direction.

---

### Post by khatarnak on 2010-12-17
I don't hve gnome or any other windowmanager installed.

Meanwhile I think the problem is located deeper in my system. I just found the hint to do

```
sudo alsa-utils reset
```

now aplay is running, and provides sound output! i have no idea what was wrong, because my alsamixer configuration for example is still the same.


paplay now gives:

```
paplay /usr/share/sounds/alsa/Front_Center.wav 
Verbindungsfehler: Verbindung verweigert
pa_context_new() fehlgeschlagen: Verbindung verweigert
```

which means "connection error: connection refused
pa_context_new failed: connection refused

Any idea? :popcorn:

btw many thanks for helping!

---

