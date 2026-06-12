---
title: "Rosegarden crashes every time it's started"
date: 2008-01-04
forum: Multimedia Production
---

### Post by hellomynameisphil on 2008-01-04
I am using Ubuntu Studio on Gutsy Gibbon. Until recently, I was happily using rosegarden, but now it crashes on startup. 

```

uzer@koobi:~$ rosegarden
JACK tmpdir identified as [/dev/shm]
uzer@koobi:~$ PluginFactory::instance(dssi): creating new DSSIPluginFactory
LADSPAPluginFactory::discoverPlugins - discovering plugins; path is [/home/uzer/.dssi] [/usr/local/lib/dssi] [/usr/lib/dssi]
LADSPAPluginFactory::discoverPlugins - trace is Rosegarden 1.5.1 - AlsaDriver - alsa-lib version 1.0.14a
JACK tmpdir identified as [/dev/shm]

JackDriver::initialiseAudio - JACK server not running

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)                  (DUPLEX) [ctype 2, ptype 655362, cap 99]
    128,0 - (TiMidity, TiMidity port 0)         (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,1 - (TiMidity, TiMidity port 1)         (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,2 - (TiMidity, TiMidity port 2)         (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,3 - (TiMidity, TiMidity port 3)         (WRITE ONLY) [ctype 1, ptype 2, cap 66]

CREATED OUTPUT PORT 3:out 1 - MIDI software device for device 0
Connecting my port 3 to 128:0 on initialisation
done
Creating device 0 in Play mode for connection 128:0 TiMidity port 0 (write)
Default device name for this device is MIDI software device
CREATED OUTPUT PORT 4:out 2 - MIDI software device 2 for device 1
Connecting my port 4 to 128:1 on initialisation
done
Creating device 1 in Play mode for connection 128:1 TiMidity port 1 (write)
Default device name for this device is MIDI software device 2
CREATED OUTPUT PORT 5:out 3 - MIDI software device 3 for device 2
Connecting my port 5 to 128:2 on initialisation
done
Creating device 2 in Play mode for connection 128:2 TiMidity port 2 (write)
Default device name for this device is MIDI software device 3
CREATED OUTPUT PORT 6:out 4 - MIDI software device 4 for device 3
Connecting my port 6 to 128:3 on initialisation
done
Creating device 3 in Play mode for connection 128:3 TiMidity port 3 (write)
Default device name for this device is MIDI software device 4
CREATED OUTPUT PORT 7:out 5 - MIDI output system device for device 4
done
Creating device 4 in Play mode for connection 14:0 Midi Through Port-0 (duplex) (not connecting)
Default device name for this device is MIDI output system device
Creating device 5 in Record mode for connection 14:0 Midi Through Port-0 (duplex) (not connecting)
Default device name for this device is MIDI input system device
AlsaDriver::setCurrentTimer((auto))
    Current timer set to "system timer"
AlsaDriver::initialiseMidi -  initialised MIDI subsystem

SoundDriver::getMappedDevice(0) - name = "MIDI software device" type = 0 direction = 0 connection = "128:0 TiMidity port 0 (write)" recording = 0
SoundDriver::getMappedDevice(1) - name = "MIDI software device 2" type = 0 direction = 0 connection = "128:1 TiMidity port 1 (write)" recording = 0
SoundDriver::getMappedDevice(2) - name = "MIDI software device 3" type = 0 direction = 0 connection = "128:2 TiMidity port 2 (write)" recording = 0
SoundDriver::getMappedDevice(3) - name = "MIDI software device 4" type = 0 direction = 0 connection = "128:3 TiMidity port 3 (write)" recording = 0
SoundDriver::getMappedDevice(4) - name = "MIDI output system device" type = 0 direction = 0 connection = "" recording = 0
SoundDriver::getMappedDevice(5) - name = "MIDI input system device" type = 0 direction = 1 connection = "" recording = 0
Renamed 129:3 to General MIDI Device
KCrash: Application 'rosegarden' crashing...
rosegarden: Fatal IO error: client killed

```

I get a KDE Crash Handler Message about rosegarden crashing and causing the signal 11 (SIGSEGV). The backtrace is useless: 

```

This backtrace appears to be of no use.
This is probably because your packages are built in a way which prevents creation of proper backtraces, or the stack frame was seriously corrupted in the crash.

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".

```

The "rosegardensequencer" process continues to run at around 75% CPU until killed, but no windows are open or anything. 

I've tried "apt-get install remove --purge rosegarden" and then re-installing, but to no avail. Rosegarden crashes whether or not Jack is running. 

What's my next step?

---

### Post by deadgobby on 2008-01-04
You may just want to run just Ubie Gusty. I do and not have the problems of any thing crashing just running Ubie.
Gobby

---

### Post by hellomynameisphil on 2008-01-05
I believe the rosegarden in the mainstream Ubuntu repositories is the same as the one in the Ubuntu Studio package. Do you know differently? If you're right, how do I get a less buggy version of the Rosegarden package?

---

### Post by deadgobby on 2008-01-06
You could try Version 2.

---

### Post by hellomynameisphil on 2008-01-06
no joy. same thing happens. I think I'll try the rosegarden mailing list. Thanks!

---

### Post by deadgobby on 2008-01-09
open up the terminal and type in 

rosegarden

it will give a error message on the crash. Please post that message here. Thanks

Gobby

---

### Post by hellomynameisphil on 2008-01-11
> 
open up the terminal and type in

rosegarden

it will give a error message on the crash. Please post that message here. Thanks

Gobby


I did that in my first post. But here is /var/crash/_usr_bin_rosegarden.1000.crash

Perhaps this will help:

```

ProblemType: Crash
Architecture: i386
Date: Sun Jan  6 19:28:39 2008
DistroRelease: Ubuntu 7.10
ExecutablePath: /usr/bin/rosegarden
NonfreeKernelModules: fglrx cdrom
ProcCmdline: rosegarden
ProcCwd: /home/uzer
ProcEnviron:
 PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
 LANG=en_CA.UTF-8
 SHELL=/bin/bash
ProcMaps:
 08048000-08817000 r-xp 00000000 08:01 6979641    /usr/bin/rosegarden
 08817000-0881b000 rw-p 007ce000 08:01 6979641    /usr/bin/rosegarden
 0881b000-08b77000 rw-p 0881b000 00:00 0          [heap]
 b4f00000-b4fc9000 rw-p b4f00000 00:00 0 
 b4fc9000-b5000000 ---p b4fc9000 00:00 0 
 b50b0000-b5186000 r-xp 00000000 08:01 2525607    /usr/lib/libscim-1.0.so.8.2.3
 b5186000-b5194000 rw-p 000d6000 08:01 2525607    /usr/lib/libscim-1.0.so.8.2.3
 b5194000-b5300000 r--s 00000000 08:01 2966785    /var/tmp/kdecache-uzer/ksycoca
 b5300000-b5400000 rw-p b5300000 00:00 0 
 b5465000-b548a000 r-xp 00000000 08:01 2656930    /usr/lib/qt3/plugins/inputmethods/libqsimple.so
 b548a000-b548b000 rw-p 00024000 08:01 2656930    /usr/lib/qt3/plugins/inputmethods/libqsimple.so
 b548b000-b5500000 r--p 00000000 08:01 2837557    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Oblique.ttf
 b5500000-b55fb000 rw-p b5500000 00:00 0 
 b55fb000-b5600000 ---p b55fb000 00:00 0 
 b5605000-b5624000 r-xp 00000000 08:01 2656392    /usr/lib/qt3/plugins/inputmethods/libqscim.so
 b5624000-b5625000 rw-p 0001f000 08:01 2656392    /usr/lib/qt3/plugins/inputmethods/libqscim.so
 b5625000-b5629000 r-xp 00000000 08:01 2656929    /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
 b5629000-b562a000 rw-p 00003000 08:01 2656929    /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
 b562a000-b56ae000 r--p 00000000 08:01 2834542    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
 b56ae000-b56af000 ---p b56ae000 00:00 0 
 b56af000-b5eaf000 rwxp b56af000 00:00 0 
 b5eaf000-b5f3a000 r--p 00000000 08:01 2834543    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
 b5f3a000-b5f67000 r-xp 00000000 08:01 2525449    /usr/lib/liblcms.so.1.0.16
 b5f67000-b5f69000 rw-p 0002c000 08:01 2525449    /usr/lib/liblcms.so.1.0.16
 b5f69000-b5f6b000 rw-p b5f69000 00:00 0 
 b5f6b000-b5fd6000 r-xp 00000000 08:01 2525479    /usr/lib/libmng.so.1.1.0.9
 b5fd6000-b5fd9000 rw-p 0006a000 08:01 2525479    /usr/lib/libmng.so.1.1.0.9
 b5fd9000-b5fda000 rw-p b5fd9000 00:00 0 
 b5fe6000-b5ff1000 r-xp 00000000 08:01 2656931    /usr/lib/qt3/plugins/inputmethods/libqxim.so
 b5ff1000-b5ff2000 rw-p 0000a000 08:01 2656931    /usr/lib/qt3/plugins/inputmethods/libqxim.so
 b5ff4000-b601c000 r-xp 00000000 08:01 2605078    /usr/lib/kde3/plugins/styles/polyester.so
 b601c000-b601d000 rw-p 00028000 08:01 2605078    /usr/lib/kde3/plugins/styles/polyester.so
 b601d000-b6026000 r-xp 00000000 08:01 4833366    /lib/tls/i686/cmov/libnss_files-2.6.1.so
 b6026000-b6028000 rw-p 00008000 08:01 4833366    /lib/tls/i686/cmov/libnss_files-2.6.1.so
 b6028000-b603c000 r-xp 00000000 08:01 4833357    /lib/tls/i686/cmov/libnsl-2.6.1.so
 b603c000-b603e000 rw-p 00013000 08:01 4833357    /lib/tls/i686/cmov/libnsl-2.6.1.so
 b603e000-b6040000 rw-p b603e000 00:00 0 
 b6040000-b6047000 r-xp 00000000 08:01 4833362    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
 b6047000-b6049000 rw-p 00006000 08:01 4833362    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
 b604b000-b604c000 rw-p b604b000 00:00 0 
 b604c000-b6055000 r-xp 00000000 08:01 2656928    /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
 b6055000-b6056000 rw-p 00009000 08:01 2656928    /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
 b6056000-b6058000 r-xp 00000000 08:01 2525611    /usr/lib/libscim-x11utils-1.0.so.8.2.3
 b6058000-b6059000 rw-p 00001000 08:01 2525611    /usr/lib/libscim-x11utils-1.0.so.8.2.3
 b6059000-b605d000 r-xp 00000000 08:01 2526381    /usr/lib/kde3/kgzipfilter.so
 b605d000-b605e000 rw-p 00003000 08:01 2526381    /usr/lib/kde3/kgzipfilter.so
 b605e000-b6063000 r-xp 00000000 08:01 2656927    /usr/lib/qt3/plugins/imageformats/libqmng.so
 b6063000-b6064000 rw-p 00004000 08:01 2656927    /usr/lib/qt3/plugins/imageformats/libqmng.so
 b6064000-b606a000 r--s 00000000 08:01 2935231    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
 b606a000-b606d000 r--s 00000000 08:01 2935229    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
 b606d000-b6071000 r--s 00000000 08:01 2935228    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
 b6071000-b6072000 r--s 00000000 08:01 2935227    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
 b6072000-b6073000 r--s 00000000 08:01 2935226    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
 b6073000-b6076000 r--s 00000000 08:01 2935225    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
 b6076000-b6077000 r--s 00000000 08:01 2935224    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
 b6077000-b607d000 r--s 00000000 08:01 2935223    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
 b607d000-b607f000 r--s 00000000 08:01 2935222    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
 b607f000-b6087000 r--s 00000000 08:01 2935221    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
 b6087000-b608d000 r--s 00000000 08:01 2935220    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
 b608d000-b608e000 r--s 00000000 08:01 2935219    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
 b608e000-b6090000 r--s 00000000 08:01 2935218    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
 b6090000-b6096000 r--s 00000000 08:01 2935217    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
 b6096000-b609a000 r--s 00000000 08:01 2935309    /var/cache/fontconfig/105b9c7e6f0a4f82d8c9b6e39c52c6f9-x86.cache-2
 b609a000-b609e000 r--s 00000000 08:01 2935216    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
 b609e000-b60a0000 r--s 00000000 08:01 2935209    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
 b60a0000-b60a1000 r--s 00000000 08:01 2935255    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
 b60a1000-b60a2000 r--s 00000000 08:01 2935254    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
 b60a2000-b60a3000 r--s 00000000 08:01 2935267    /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
 b60a3000-b60a4000 r--s 00000000 08:01 2935253    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
 b60a4000-b60a7000 r--s 00000000 08:01 2935252    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
 b60a7000-b60aa000 r--s 00000000 08:01 2935251    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
 b60aa000-b60ac000 r--s 00000000 08:01 2935266    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
 b60ac000-b60ad000 r--s 00000000 08:01 2935249    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
 b60ad000-b60af000 r--s 00000000 08:01 2935265    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
 b60af000-b60b0000 r--s 00000000 08:01 2935247    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
 b60b0000-b60b5000 r--s 00000000 08:01 2935246    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
 b60b5000-b60ba000 r--s 00000000 08:01 2935264    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
 b60ba000-b60bc000 r--s 00000000 08:01 2935244    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
 b60bc000-b60bf000 r--s 00000000 08:01 2935243    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
 b60bf000-b60c0000 r--s 00000000 08:01 2935233    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
 b60c0000-b60c1000 r--s 00000000 08:01 2935241    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
 b60c1000-b60c4000 r--s 00000000 08:01 2935240    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
 b60c4000-b60ca000 r--s 00000000 08:01 2935239    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
 b60ca000-b60cb000 r--s 00000000 08:01 2933884    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
 b60cb000-b60d4000 r--s 00000000 08:01 2933883    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
 b60d4000-b60d6000 r--s 00000000 08:01 2935236    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
 b60d6000-b60da000 r--s 00000000 08:01 2933879    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
 b60da000-b60dd000 r--s 00000000 08:01 2935234    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
 b60dd000-b60e0000 r--s 00000000 08:01 2935214    /var/cache/fontconfig/b67b32625a2bb51b023d3814a918f351-x86.cache-2
 b60e0000-b611f000 r--p 00000000 08:01 2605412    /usr/lib/locale/en_CA.utf8/LC_CTYPE
 b611f000-b61ff000 r--p 00000000 08:01 2605411    /usr/lib/locale/en_CA.utf8/LC_COLLATE
 b61ff000-b6203000 rw-p b61ff000 00:00 0 
 b6203000-b6204000 r-xp 00000000 08:01 4833353    /lib/libkeyutils-1.2.so
 b6204000-b6205000 rw-p 00001000 08:01 4833353    /lib/libkeyutils-1.2.so
 b6205000-b6209000 r-xp 00000000 08:01 2524784    /usr/lib/libXfixes.so.3.1.0
 b6209000-b620a000 rw-p 00003000 08:01 2524784    /usr/lib/libXfixes.so.3.1.0
 b620a000-b620b000 rw-p b620a000 00:00 0 
 b620b000-b624c000 r-xp 00000000 08:01 2526500    /usr/lib/libkparts.so.2.1.0
 b624c000-b6251000 rw-p 00040000 08:01 2526500    /usr/lib/libkparts.so.2.1.0
 b6251000-b6254000 r-xp 00000000 08:01 4833312    /lib/libattr.so.1.1.0
 b6254000-b6255000 rw-p 00002000 08:01 4833312    /lib/libattr.so.1.1.0
 b6255000-b625b000 r-xp 00000000 08:01 4833306    /lib/libacl.so.1.1.0
 b625b000-b625c000 rw-p 00005000 08:01 4833306    /lib/libacl.so.1.1.0
 b625c000-b626c000 r-xp 00000000 08:01 2526648    /usr/lib/libkwalletclient.so.1.0.1
 b626c000-b626d000 rw-p 00010000 08:01 2526648    /usr/lib/libkwalletclient.so.1.0.1
 b626d000-b6282000 r-xp 00000000 08:01 2526486    /usr/lib/libkdesu.so.4.2.0
 b6282000-b6283000 rw-p 00015000 08:01 2526486    /usr/lib/libkdesu.so.4.2.0
 b6283000-b6284000 rw-p b6283000 00:00 0 
 b6284000-b62a2000 r-xp 00000000 08:01 2524966    /usr/lib/libexpat.so.1.0.0
 b62a2000-b62a4000 rw-p 0001e000 08:01 2524966    /usr/lib/libexpat.so.1.0.0
 b62a4000-b63bc000 r-xp 00000000 08:01 2525723    /usr/lib/libxml2.so.2.6.30
 b63bc000-b63c1000 rw-p 00118000 08:01 2525723    /usr/lib/libxml2.so.2.6.30
 b63c1000-b63c2000 rw-p b63c1000 00:00 0 
 b63c2000-b63f5000 r-xp 00000000 08:01 2525727    /usr/lib/libxslt.so.1.1.21
 b63f5000-b63f6000 rw-p 00032000 08:01 2525727    /usr/lib/libxslt.so.1.1.21
 b63f6000-b6521000 r-xp 00000000 08:01 2524408    /usr/lib/i686/cmov/libcrypto.so.0.9.8
 b6521000-b6536000 rw-p 0012a000 08:01 2524408    /usr/lib/i686/cmov/libcrypto.so.0.9.8
 b6536000-b6539000 rw-p b6536000 00:00 0 
 b6539000-b6576000 r-xp 00000000 08:01 2525730    /usr/lib/i686/cmov/libssl.so.0.9.8
 b6576000-b657a000 rw-p 0003c000 08:01 2525730    /usr/lib/i686/cmov/libssl.so.0.9.8
 b657a000-b657b000 rw-p b657a000 00:00 0 
 b657b000-b657d000 r-xp 00000000 08:01 4833313    /lib/libcom_err.so.2.1
 b657d000-b657e000 rw-p 00001000 08:01 4833313    /lib/libcom_err.so.2.1
 b657e000-b6585000 r-xp 00000000 08:01 2525405    /usr/lib/libkrb5support.so.0.1
 b6585000-b6586000 rw-p 00006000 08:01 2525405    /usr/lib/libkrb5support.so.0.1
 b6586000-b65aa000 r-xp 00000000 08:01 2525165    /usr/lib/libk5crypto.so.3.1
 b65aa000-b65ab000 rw-p 00024000 08:01 2525165    /usr/lib/libk5crypto.so.3.1
 b65ab000-b6631000 r-xp 00000000 08:01 2525403    /usr/lib/libkrb5.so.3.3
 b6631000-b6633000 rw-p 00086000 08:01 2525403    /usr/lib/libkrb5.so.3.3
 b6633000-b665b000 r-xp 00000000 08:01 2525065    /usr/lib/libgssapi_krb5.so.2.2
 b665b000-b665c000 rw-p 00027000 08:01 2525065    /usr/lib/libgssapi_krb5.so.2.2
 b665c000-b6695000 r-xp 00000000 08:01 2529808    /usr/lib/libcurl.so.4.0.0
 b6695000-b6696000 rw-p 00038000 08:01 2529808    /usr/lib/libcurl.so.4.0.0
 b6696000-b6697000 rw-p b6696000 00:00 0 
 b6697000-b66d7000 r-xp 00000000 08:01 2529811    /usr/lib/libraptor.so.1.1.0
 b66d7000-b66e6000 rw-p 00040000 08:01 2529811    /usr/lib/libraptor.so.1.1.0
 b66e6000-b6710000 r-xp 00000000 08:01 2526471    /usr/lib/libkdefx.so.4.2.0
 b6710000-b6711000 rw-p 0002a000 08:01 2526471    /usr/lib/libkdefx.so.4.2.0
 b6711000-b6741000 r-xp 00000000 08:01 2525140    /usr/lib/libidn.so.11.5.29
 b6741000-b6742000 rw-p 0002f000 08:01 2525140    /usr/lib/libidn.so.11.5.29
 b6742000-b6757000 r-xp 00000000 08:01 2524845    /usr/lib/libart_lgpl_2.so.2.3.19
 b6757000-b6758000 rw-p 00014000 08:01 2524845    /usr/lib/libart_lgpl_2.so.2.3.19
 b6758000-b675a000 r-xp 00000000 08:01 4833419    /lib/tls/i686/cmov/libutil-2.6.1.so
 b675a000-b675c000 rw-p 00001000 08:01 4833419    /lib/tls/i686/cmov/libutil-2.6.1.so
 b675c000-b675d000 rw-p b675c000 00:00 0 
 b675d000-b676c000 r-xp 00000000 08:01 4833396    /lib/tls/i686/cmov/libresolv-2.6.1.so
 b676c000-b676e000 rw-p 0000f000 08:01 4833396    /lib/tls/i686/cmov/libresolv-2.6.1.so
 b676e000-b6770000 rw-p b676e000 00:00 0 
 b6770000-b6774000 r-xp 00000000 08:01 2524780    /usr/lib/libXdmcp.so.6.0.0
 b6774000-b6775000 rw-p 00003000 08:01 2524780    /usr/lib/libXdmcp.so.6.0.0
 b6775000-b6777000 r-xp 00000000 08:01 2524769    /usr/lib/libXau.so.6.0.0
 b6777000-b6778000 rw-p 00001000 08:01 2524769    /usr/lib/libXau.so.6.0.0
 b6778000-b67e4000 r-xp 00000000 08:01 2524990    /usr/lib/libfreetype.so.6.3.16
 b67e4000-b67e8000 rw-p 0006b000 08:01 2524990    /usr/lib/libfreetype.so.6.3.16
 b67e8000-b67ea000 r-xp 00000000 08:01 2524792    /usr/lib/libXinerama.so.1.0.0
 b67ea000-b67eb000 rw-p 00001000 08:01 2524792    /usr/lib/libXinerama.so.1.0.0
 b67eb000-b67ec000 rw-p b67eb000 00:00 0 
 b67ec000-b67f4000 r-xp 00000000 08:01 2524776    /usr/lib/libXcursor.so.1.0.2
 b67f4000-b67f5000 rw-p 00007000 08:01 2524776    /usr/lib/libXcursor.so.1.0.2
 b67f5000-b67fa000 r-xp 00000000 08:01 2524802    /usr/lib/libXrandr.so.2.1.0
 b67fa000-b67fb000 rw-p 00005000 08:01 2524802    /usr/lib/libXrandr.so.2.1.0
 b67fb000-b6802000 r-xp 00000000 08:01 2524804    /usr/lib/libXrender.so.1.3.0
 b6802000-b6803000 rw-p 00006000 08:01 2524804    /usr/lib/libXrender.so.1.3.0
 b6803000-b680a000 r-xp 00000000 08:01 2524790    /usr/lib/libXi.so.6.0.0
 b680a000-b680b000 rw-p 00006000 08:01 2524790    /usr/lib/libXi.so.6.0.0
 b680b000-b681f000 r-xp 00000000 08:01 2525729    /usr/lib/libz.so.1.2.3.3
 b681f000-b6820000 rw-p 00013000 08:01 2525729    /usr/lib/libz.so.1.2.3.3
 b6820000-b6842000 r-xp 00000000 08:01 2524911    /usr/lib/libpng12.so.0.15.0
 b6842000-b6843000 rw-p 00021000 08:01 2524911    /usr/lib/libpng12.so.0.15.0
 b6843000-b6844000 rw-p b6843000 00:00 0 
 b6844000-b6863000 r-xp 00000000 08:01 2525155    /usr/lib/libjpeg.so.62.0.0
 b6863000-b6864000 rw-p 0001e000 08:01 2525155    /usr/lib/libjpeg.so.62.0.0
 b6864000-b68b1000 r-xp 00000000 08:01 2524808    /usr/lib/libXt.so.6.0.0
 b68b1000-b68b5000 rw-p 0004c000 08:01 2524808    /usr/lib/libXt.so.6.0.0
 b68b5000-b68ca000 r-xp 00000000 08:01 2524880    /usr/lib/libaudio.so.2.4
 b68ca000-b68cb000 rw-p 00014000 08:01 2524880    /usr/lib/libaudio.so.2.4
 b68cb000-b68fc000 r-xp 00000000 08:01 2526463    /usr/lib/libDCOP.so.4.2.0
 b68fc000-b68fd000 rw-p 00031000 08:01 2526463    /usr/lib/libDCOP.so.4.2.0
 b68fd000-b68ff000 rw-p b68fd000 00:00 0 
 b68ff000-b6a43000 r-xp 00000000 08:01 4833307    /lib/tls/i686/cmov/libc-2.6.1.so
 b6a43000-b6a44000 r--p 00143000 08:01 4833307    /lib/tls/i686/cmov/libc-2.6.1.so
 b6a44000-b6a46000 rw-p 00144000 08:01 4833307    /lib/tls/i686/cmov/libc-2.6.1.so
 b6a46000-b6a49000 rw-p b6a46000 00:00 0 
 b6a49000-b6a53000 r-xp 00000000 08:01 4833347    /lib/libgcc_s.so.1
 b6a53000-b6a54000 rw-p 0000a000 08:01 4833347    /lib/libgcc_s.so.1
 b6a54000-b6a55000 rw-p b6a54000 00:00 0 
 b6a55000-b6a78000 r-xp 00000000 08:01 4833339    /lib/tls/i686/cmov/libm-2.6.1.so
 b6a78000-b6a7a000 rw-p 00023000 08:01 4833339    /lib/tls/i686/cmov/libm-2.6.1.so
 b6a7a000-b6b62000 r-xp 00000000 08:01 2525644    /usr/lib/libstdc++.so.6.0.9
 b6b62000-b6b65000 r--p 000e8000 08:01 2525644    /usr/lib/libstdc++.so.6.0.9
 b6b65000-b6b67000 rw-p 000eb000 08:01 2525644    /usr/lib/libstdc++.so.6.0.9
 b6b67000-b6b6d000 rw-p b6b67000 00:00 0 
 b6b6d000-b6c35000 r-xp 00000000 08:01 2526484    /usr/lib/libkdeprint.so.4.2.0
 b6c35000-b6c3d000 rw-p 000c8000 08:01 2526484    /usr/lib/libkdeprint.so.4.2.0
 b6c3d000-b6f02000 r-xp 00000000 08:01 2526487    /usr/lib/libkdeui.so.4.2.0
 b6f02000-b6f2d000 rw-p 002c4000 08:01 2526487    /usr/lib/libkdeui.so.4.2.0
 b6f2d000-b6f2e000 rw-p b6f2d000 00:00 0 
 b6f2e000-b7260000 r-xp 00000000 08:01 2526491    /usr/lib/libkio.so.4.2.0
 b7260000-b727f000 rw-p 00332000 08:01 2526491    /usr/lib/libkio.so.4.2.0
 b727f000-b7286000 r-xp 00000000 08:01 4833400    /lib/tls/i686/cmov/librt-2.6.1.so
 b7286000-b7288000 rw-p 00006000 08:01 4833400    /lib/tls/i686/cmov/librt-2.6.1.so
 b7288000-b7289000 rw-p b7288000 00:00 0 
 b7289000-b7298000 r-xp 00000000 08:01 2526823    /usr/lib/libjack.so.0.0.23
 b7298000-b729a000 rw-p 0000e000 08:01 2526823    /usr/lib/libjack.so.0.0.23
 b729a000-b72a2000 rw-p b729a000 00:00 0 
 b72a2000-b72a7000 r-xp 00000000 08:01 2529329    /usr/lib/liblirc_client.so.0.2.0
 b72a7000-b72a8000 rw-p 00004000 08:01 2529329    /usr/lib/liblirc_client.so.0.2.0
 b72a8000-b72cb000 r-xp 00000000 08:01 2524982    /usr/lib/libfontconfig.so.1.2.0
 b72cb000-b72d3000 rw-p 00023000 08:01 2524982    /usr/lib/libfontconfig.so.1.2.0
 b72d3000-b72e4000 r-xp 00000000 08:01 2524788    /usr/lib/libXft.so.2.1.2
 b72e4000-b72e5000 rw-p 00010000 08:01 2524788    /usr/lib/libXft.so.2.1.2
 b72e5000-b73bc000 r-xp 00000000 08:01 2524974    /usr/lib/libfftw3f.so.3.1.2
 b73bc000-b73c2000 rw-p 000d7000 08:01 2524974    /usr/lib/libfftw3f.so.3.1.2
 b73c2000-b73c8000 r-xp 00000000 08:01 2529813    /usr/lib/liblrdf.so.0.0.0
 b73c8000-b73c9000 rw-p 00005000 08:01 2529813    /usr/lib/liblrdf.so.0.0.0
 b73c9000-b73d1000 rw-p b73c9000 00:00 0 
 b73d1000-b73da000 r-xp 00000000 08:01 2529806    /usr/lib/liblo.so.0.6.0
 b73da000-b73db000 rw-p 00008000 08:01 2529806    /usr/lib/liblo.so.0.6.0
 b73db000-b7612000 r-xp 00000000 08:01 2526469    /usr/lib/libkdecore.so.4.2.0
 b7612000-b7623000 rw-p 00236000 08:01 2526469    /usr/lib/libkdecore.so.4.2.0
 b7623000-b7625000 rw-p b7623000 00:00 0 
 b7625000-b7639000 r-xp 00000000 08:01 4833392    /lib/tls/i686/cmov/libpthread-2.6.1.so
 b7639000-b763b000 rw-p 00013000 08:01 4833392    /lib/tls/i686/cmov/libpthread-2.6.1.so
 b763b000-b763d000 rw-p b763b000 00:00 0 
 b763d000-b763f000 r-xp 00000000 08:01 4833332    /lib/tls/i686/cmov/libdl-2.6.1.so
 b763f000-b7641000 rw-p 00001000 08:01 4833332    /lib/tls/i686/cmov/libdl-2.6.1.so
 b7641000-b764e000 r-xp 00000000 08:01 2524782    /usr/lib/libXext.so.6.4.0
 b764e000-b764f000 rw-p 0000d000 08:01 2524782    /usr/lib/libXext.so.6.4.0
 b764f000-b773c000 r-xp 00000000 08:01 2524765    /usr/lib/libX11.so.6.2.0
 b773c000-b7740000 rw-p 000ed000 08:01 2524765    /usr/lib/libX11.so.6.2.0
 b7740000-b7741000 rw-p b7740000 00:00 0 
 b7741000-b7756000 r-xp 00000000 08:01 2524711    /usr/lib/libICE.so.6.3.0
 b7756000-b7758000 rw-p 00014000 08:01 2524711    /usr/lib/libICE.so.6.3.0
 b7758000-b7759000 rw-p b7758000 00:00 0 
 b7759000-b7760000 r-xp 00000000 08:01 2524761    /usr/lib/libSM.so.6.0.0
 b7760000-b7761000 rw-p 00006000 08:01 2524761    /usr/lib/libSM.so.6.0.0
 b7761000-b7f27000 r-xp 00000000 08:01 2525556    /usr/lib/libqt-mt.so.3.3.7
 b7f27000-b7f6d000 rw-p 007c5000 08:01 2525556    /usr/lib/libqt-mt.so.3.3.7
 b7f6d000-b7f71000 rw-p b7f6d000 00:00 0 
 b7f71000-b7f79000 r-xp 00000000 08:01 4833370    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
 b7f79000-b7f7b000 rw-p 00007000 08:01 4833370    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
 b7f7b000-b7f7c000 r--p 00000000 08:01 2605417    /usr/lib/locale/en_CA.utf8/LC_NUMERIC
 b7f7c000-b7f7d000 r--p 00000000 08:01 2605420    /usr/lib/locale/en_CA.utf8/LC_TIME
 b7f7d000-b7f7e000 r--p 00000000 08:01 2605415    /usr/lib/locale/en_CA.utf8/LC_MONETARY
 b7f7e000-b7f7f000 r--p 00000000 08:01 2605421    /usr/lib/locale/en_CA.utf8/LC_MESSAGES/SYS_LC_MESSAGES
 b7f7f000-b7f80000 r--p 00000000 08:01 2605418    /usr/lib/locale/en_CA.utf8/LC_PAPER
 b7f80000-b7f81000 r--p 00000000 08:01 2605416    /usr/lib/locale/en_CA.utf8/LC_NAME
 b7f81000-b7f82000 r--p 00000000 08:01 2605410    /usr/lib/locale/en_CA.utf8/LC_ADDRESS
 b7f82000-b7f83000 r--p 00000000 08:01 2605419    /usr/lib/locale/en_CA.utf8/LC_TELEPHONE
 b7f83000-b7f84000 r--p 00000000 08:01 2605414    /usr/lib/locale/en_CA.utf8/LC_MEASUREMENT
 b7f84000-b7f8b000 r--s 00000000 08:01 2525291    /usr/lib/gconv/gconv-modules.cache
 b7f8b000-b7f8c000 r--p 00000000 08:01 2605413    /usr/lib/locale/en_CA.utf8/LC_IDENTIFICATION
 b7f8c000-b7f8e000 rw-p b7f8c000 00:00 0 
 b7f8e000-b7fa8000 r-xp 00000000 08:01 4833293    /lib/ld-2.6.1.so
 b7fa8000-b7faa000 rw-p 00019000 08:01 4833293    /lib/ld-2.6.1.so
 bffbc000-bffd1000 rwxp bffbc000 00:00 0          [stack]
 ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
ProcStatus:
 Name:	rosegarden
 State:	D (disk sleep)
 Tgid:	25462
 Pid:	25462
 PPid:	1
 TracerPid:	0
 Uid:	1000	1000	1000	1000
 Gid:	1000	1000	1000	1000
 FDSize:	32
 Groups:	4 20 24 25 29 30 44 46 104 106 108 109 115 117 1000 
 VmPeak:	   64512 kB
 VmSize:	   60176 kB
 VmLck:	       0 kB
 VmHWM:	   26180 kB
 VmRSS:	   23976 kB
 VmData:	   14968 kB
 VmStk:	      84 kB
 VmExe:	    7996 kB
 VmLib:	   31012 kB
 VmPTE:	      64 kB
 Threads:	2
 SigQ:	0/11251
 SigPnd:	0000000000000000
 ShdPnd:	0000000000000000
 SigBlk:	0000000000000000
 SigIgn:	0000000000001000
 SigCgt:	00000001800104a8
 CapInh:	0000000000000000
 CapPrm:	0000000000000000
 CapEff:	0000000000000000
 Cpus_allowed:	01
 Mems_allowed:	1
Signal: 5
Uname: Linux koobi 2.6.22-14-rt #1 SMP PREEMPT RT Tue Dec 18 10:01:34 UTC 2007 i686 GNU/Linux
UserGroups: adm admin audio cdrom dialout dip floppy fuse lpadmin netdev plugdev powerdev scanner video
CoreDump: base64
[long string of random characters follows]

```

---

### Post by jorgis on 2008-05-11
I have a similar problem, although the crash Rosegarden triggers on my computer is a bit more severe: my entire computer freezes up totally, and the only thing I can do is to do a hard reset. Checking dmesg or any logs in the System Log reveals no information about the crash at all. 

I recall having the same problem in earlier versions of Ubuntu (7.04, I think), but never bothered to fix it. I really want to have Rosegarden up and working this time, does anybody have any idea as to how I can fix this, or why this is happening?

---

