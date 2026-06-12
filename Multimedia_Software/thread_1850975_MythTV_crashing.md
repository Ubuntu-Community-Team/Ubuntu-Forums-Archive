---
title: "MythTV crashing"
date: 2011-09-27
forum: Multimedia Software
---

### Post by Manu311 on 2011-09-27
Hey,

I've tried a lot to finally having useful channels inside of mythtv, after all I suceeded with a channels.conf from the "scan" command.
I've got a big list inside of the backend, but the frontend is now unable to watch since it crashes everytime I try to watch tv inside of it.
Either it crashes (and got restarted automatically) or it just freezes.

Here are some errors (btw hdc and hdd are cd and dvd drives, with nothing in it, I don't need them yet):

1.
```
mythfrontend.real: pthread_mutex_lock.c:62: __pthread_mutex_lock: Assertion `mutex->__data.__owner == 0' failed.
``` 

2.
```
2011-09-27 18:09:04.476 We have a playbackURL(/var/lib/mythtv/livetv/31660_20110927180904.mpg) & cardtype(DUMMY)
2011-09-27 18:09:04.476 We have a RingBuffer
2011-09-27 18:09:04.699 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2011-09-27 18:09:04.762 
XError type: 0
  serial no: 126
   err code: 10 (BadAccess (attempt to access private resource denied))
   req code: 141
 minor code: 1
resource id: 314
....... (a lot of these errors repeat)
2011-09-27 18:09:04.789 OSD: Base theme size: 1280x720
2011-09-27 18:09:04.790 OSD: Scaling factors: 0.5625x0.8
2011-09-27 18:09:04.890 OSD: Base theme size: 1280x720
2011-09-27 18:09:04.890 OSD: Scaling factors: 0.5625x0.8
2011-09-27 18:09:04.909 Player(0): Video timing method: USleep with busy wait
2011-09-27 18:09:04.909 TV: Changing from None to WatchingLiveTV
2011-09-27 18:09:04.910 TV: State is LiveTV & mctx == ctx
2011-09-27 18:09:04.924 TV: UpdateOSDInput done
2011-09-27 18:09:04.924 TV: UpdateLCD done
2011-09-27 18:09:04.924 TV: ITVRestart done
2011-09-27 18:09:04.941 pause_active: 0
2011-09-27 18:09:09.065 RingBuf(/var/lib/mythtv/livetv/31660_20110927180905.mpg) Warning: Taking too long to be allowed to read..
2011-09-27 18:09:09.175 AFD Error: Could not find codec parameters. file was "/var/lib/mythtv/livetv/31660_20110927180905.mpg".
2011-09-27 18:09:09.175 Couldn't open decoder for: /var/lib/mythtv/livetv/31660_20110927180905.mpg
2011-09-27 18:09:09.176 Player(0), Error: JumpToProgram failed.
2011-09-27 18:09:09.176 Player(0), Error: Unknown recorder error, exiting decoder
2011-09-27 18:09:09.246 TV: Attempting to change from WatchingLiveTV to None
2011-09-27 18:09:09.379 TV: Changing from WatchingLiveTV to None
2011-09-27 18:09:09.393 TV: Attempting to change from None to WatchingLiveTV
2011-09-27 18:09:09.393 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-09-27 18:09:09.397 Using protocol version 63
2011-09-27 18:09:09.486 Spawning LiveTV Recorder -- begin
2011-09-27 18:09:09.722 Spawning LiveTV Recorder -- end
2011-09-27 18:09:09.734 We have a playbackURL(/var/lib/mythtv/livetv/31660_20110927180909.mpg) & cardtype(DUMMY)
2011-09-27 18:09:09.734 We have a RingBuffer
2011-09-27 18:09:09.736 TV Error: LiveTV not successfully started
2011-09-27 18:09:09.743 pause_active: 1
QMutex::lock: mutex lock failure: Invalid argument
mount: can't find /dev/sdc in /etc/fstab or /etc/mtab
2011-09-27 18:09:25.744 Failed to mount /dev/sdc.
*** glibc detected *** /usr/bin/mythfrontend.real: corrupted double-linked list: 0x09382e30 ***
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(+0x6b961)[0x1a97961]
/lib/i386-linux-gnu/libc.so.6(+0x6e99c)[0x1a9a99c]
/lib/i386-linux-gnu/libc.so.6(__libc_malloc+0x63)[0x1a9bf53]
/usr/lib/i386-linux-gnu/libstdc++.so.6(_Znwj+0x29)[0x1641679]
/usr/lib/libQtCore.so.4(+0x167cc1)[0x1901cc1]
/usr/lib/libQtCore.so.4(_ZN11QMetaObject8activateEP7QObjectPKS_iPPv+0x1c0)[0x1905440]
/usr/lib/libmythdb-0.24.so.0(_ZN18MythSignalingTimer7timeoutEv+0x37)[0x31fb29]
/usr/lib/libmythdb-0.24.so.0(_ZN18MythSignalingTimer3runEv+0x42)[0x2b6326]
/usr/lib/libQtCore.so.4(+0x60da2)[0x17fada2]
/lib/i386-linux-gnu/libpthread.so.0(+0x5e99)[0x842be99]
/lib/i386-linux-gnu/libc.so.6(clone+0x5e)[0x1afc73e]
======= Memory map: ========
00110000-00160000 r-xp 00000000 08:12 659555     /usr/lib/libmythswscale.so.0.11.0
00160000-00161000 r--p 0004f000 08:12 659555     /usr/lib/libmythswscale.so.0.11.0
00161000-00162000 rw-p 00050000 08:12 659555     /usr/lib/libmythswscale.so.0.11.0
00162000-00218000 r-xp 00000000 08:12 659534     /usr/lib/libmythavformat.so.52.78.3
00218000-0021b000 r--p 000b5000 08:12 659534     /usr/lib/libmythavformat.so.52.78.3
0021b000-00222000 rw-p 000b8000 08:12 659534     /usr/lib/libmythavformat.so.52.78.3
00222000-00226000 rw-p 00000000 00:00 0 
00226000-00228000 r-xp 00000000 08:12 659528     /usr/lib/libmythavcore.so.0.6.0
00228000-00229000 r--p 00001000 08:12 659528     /usr/lib/libmythavcore.so.0.6.0
00229000-0022a000 rw-p 00002000 08:12 659528     /usr/lib/libmythavcore.so.0.6.0
0022a000-00237000 r-xp 00000000 08:12 659536     /usr/lib/libmythavutil.so.50.24.0
00237000-00238000 ---p 0000d000 08:12 659536     /usr/lib/libmythavutil.so.50.24.0
00238000-00239000 r--p 0000d000 08:12 659536     /usr/lib/libmythavutil.so.50.24.0
00239000-0023a000 rw-p 0000e000 08:12 659536     /usr/lib/libmythavutil.so.50.24.0
0023a000-0023d000 rw-p 00000000 00:00 0 
0023d000-00355000 r-xp 00000000 08:12 659539     /usr/lib/libmythdb-0.24.so.0.24.0
00355000-00356000 r--p 00118000 08:12 659539     /usr/lib/libmythdb-0.24.so.0.24.0
00356000-00358000 rw-p 00119000 08:12 659539     /usr/lib/libmythdb-0.24.so.0.24.0
00358000-00359000 rw-p 00000000 00:00 0 
00359000-00367000 r-xp 00000000 08:12 659545     /usr/lib/libmythhdhomerun-0.24.so.0.24.0
00367000-00368000 r--p 0000d000 08:12 659545     /usr/lib/libmythhdhomerun-0.24.so.0.24.0
00368000-00369000 rw-p 0000e000 08:12 659545     /usr/lib/libmythhdhomerun-0.24.so.0.24.0
00369000-00376000 r-xp 00000000 08:12 661031     /usr/lib/i386-linux-gnu/libXext.so.6.4.0
00376000-00377000 r--p 0000c000 08:12 661031     /usr/lib/i386-linux-gnu/libXext.so.6.4.0
00377000-00378000 rw-p 0000d000 08:12 661031     /usr/lib/i386-linux-gnu/libXext.so.6.4.0
00378000-0037a000 r-xp 00000000 08:12 661039     /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
0037a000-0037b000 r--p 00001000 08:12 661039     /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
0037b000-0037c000 rw-p 00002000 08:12 661039     /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
0037c000-00380000 r-xp 00000000 08:12 661047     /usr/lib/i386-linux-gnu/libXxf86vm.so.1.0.0
00380000-00381000 r--p 00003000 08:12 661047     /usr/lib/i386-linux-gnu/libXxf86vm.so.1.0.0
00381000-00382000 rw-p 00004000 08:12 661047     /usr/lib/i386-linux-gnu/libXxf86vm.so.1.0.0
00382000-00386000 r-xp 00000000 08:12 659089     /usr/lib/libXv.so.1.0.0
00386000-00387000 r--p 00003000 08:12 659089     /usr/lib/libXv.so.1.0.0
00387000-00388000 rw-p 00004000 08:12 659089     /usr/lib/libXv.so.1.0.0
00388000-0038e000 r-xp 00000000 08:12 661041     /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
0038e000-0038f000 r--p 00005000 08:12 661041     /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
0038f000-00390000 rw-p 00006000 08:12 661041     /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
00390000-003cf000 r-xp 00000000 08:12 659643     /usr/lib/libpulse.so.0.12.3
003cf000-003d0000 r--p 0003e000 08:12 659643     /usr/lib/libpulse.so.0.12.3
003d0000-003d1000 rw-p 0003f000 08:12 659643     /usr/lib/libpulse.so.0.12.3
003d1000-003d3000 r-xp 00000000 08:12 1049367    /lib/i386-linux-gnu/libdl-2.13.so
003d3000-003d4000 r--p 00001000 08:12 1049367    /lib/i386-linux-gnu/libdl-2.13.so
003d4000-003d5000 rw-p 00002000 08:12 1049367    /lib/i386-linux-gnu/libdl-2.13.so
003d5000-00474000 r-xp 00000000 08:12 659564     /usr/lib/libmythupnp-0.24.so.0.24.0
00474000-00475000 r--p 0009f000 08:12 659564     /usr/lib/libmythupnp-0.24.so.0.24.0
00475000-00477000 rw-p 000a0000 08:12 659564     /usr/lib/libmythupnp-0.24.so.0.24.0
00477000-00482000 r-xp 00000000 08:12 1049434    /lib/i386-linux-gnu/libudev.so.0.11.1
00482000-00483000 r--p 0000a000 08:12 1049434    /lib/i386-linux-gnu/libudev.so.0.11.1
00483000-00484000 rw-p 0000b000 08:12 1049434    /lib/i386-linux-gnu/libudev.so.0.11.1
00484000-0048b000 r-xp 00000000 08:12 1049426    /lib/i386-linux-gnu/librt-2.13.so
0048b000-0048c000 r--p 00006000 08:12 1049426    /lib/i386-linux-gnu/librt-2.13.so
0048c000-0048d000 rw-p 00007000 08:12 1049426    /lib/i386-linux-gnu/librt-2.13.so
0048d000-00490000 r-xp 00000000 08:12 659127     /usr/lib/libavc1394.so.0.3.0
00490000-00491000 r--p 00003000 08:12 659127     /usr/lib/libavc1394.so.0.3.0
00491000-00492000 rw-p 00004000 08:12 659127     /usr/lib/libavc1394.so.0.3.0
00492000-004ae000 r-xp 00000000 08:12 1049344    /lib/i386-linux-gnu/ld-2.13.so
004ae000-004af000 r--p 0001b000 08:12 1049344    /lib/i386-linux-gnu/ld-2.13.so
004af000-004b0000 rw-p 0001c000 08:12 1049344    /lib/i386-linux-gnu/ld-2.13.so
004b0000-006dc000 r-xp 00000000 08:12 659561     /usr/lib/libmythui-0.24.so.0.24.0
006dc000-006e1000 r--p 0022b000 08:12 659561     /usr/lib/libmythui-0.24.so.0.24.0
006e1000-006e7000 rw-p 00230000 08:12 659561     /usr/lib/libmythui-0.24.so.0.24.0
006e7000-007a4000 r-xp 00000000 08:12 659548     /usr/lib/libmythlivemedia-0.24.so.0.24.0
007a4000-007a9000 r--p 000bd000 08:12 659548     /usr/lib/libmythlivemedia-0.24.so.0.24.0
007a9000-007b0000 rw-p 000c2000 08:12 659548     /usr/lib/libmythlivemedia-0.24.so.0.24.0
007b0000-007be000 rw-p 00000000 00:00 0 
007be000-007ca000 r-xp 00000000 08:12 659677     /usr/lib/libraw1394.so.11.0.1
007ca000-007cb000 r--p 0000b000 08:12 659677     /usr/lib/libraw1394.so.11.0.1
007cb000-007cc000 rw-p 0000c000 08:12 659677     /usr/lib/libraw1394.so.11.0.1
007cc000-007cd000 r-xp 00000000 08:12 665279     /usr/lib/nvidia-173/tls/libnvidia-tls.so.173.14.30
007cd000-007ce000 rw-p 00000000 08:12 665279     /usr/lib/nvidia-173/tls/libnvidia-tls.so.173.14.30
007ce000-007cf000 r-xp 00000000 00:00 0          [vdso]Aborted
```
I'm not sure if this is related to the nvidia driver, but till now I haven't tried to install one by hand.

---

### Post by BicyclerBoy on 2011-09-27
There is an error message "X bad access private resource"
Is your user a member of the video & mythtv groups..

Maybe look for errors in:
dmesg
cat /var/log/Xorg.0.log

The nvidia driver is recommended because you could be able to use VDPAU (h/w dependent), just use the repos nvidia-current version..

There is a mythbuntu forum sub-section hidden under "3rd party projects".

---

### Post by Manu311 on 2011-09-27
> **BicyclerBoy said:**
> There is an error message "X bad access private resource"
Is your user a member of the video & mythtv groups..

Maybe look for errors in:
dmesg
cat /var/log/Xorg.0.log

The nvidia driver is recommended, just use the repos version..

There is a mythbuntu forum sub-section hidden under "3rd party projects".

```
manu@ManuMed:~$ groups
manu adm dialout cdrom video plugdev admin mythtv sambashare lpadmin
```
I guess I'm in both groups

I know there's a mythbuntu subsection but this seems more related to mythtv then to mythbuntu itself, so I thought about posting it here is more useful (since the "Prefix: Mythbuntu" would be useless if every question on that version of ubuntu would be posted there.
dmesg seems pretty empty.

I'm now nearly 2 days busy with getting this crap up running, if I don't fix it today, I'll start installing gentoo on it tomorrow (I'm just way more used to it).

---

### Post by BicyclerBoy on 2011-09-27
There are messages with nvidia 173..
You could try using VDPAU playback but your h/w may not be usable.

What's the cardtype(dummy) message ?
You should resolve the mount errors?
Are these errors from storage group paths ?

Note that live tv plays from a real file buffer & it must be writable.

Does you mythtv play media files (recordings/DVD/music/web) okay ?

You need to isolate the problem to the tuner card or the channel lineup..

Does mythfilldatabase run without errors ?

Maybe you need to delete all channels & add just one unencrypted channel.
There is a real art to setting up the channel lineup, I don't have it.

---

### Post by Manu311 on 2011-09-27
Currently I totally crashed it - now it doesn't connect to mysql (although I can connect from everywhere, using every ip (127... and 196....) and I have no clue why not.

I'm installing mythbuntu once more and hope it will work ...., I'll post again after that step.

//EDIT:
Oh I think I can answer your questions out of my memory:
What's VDPAU playback? If it's the other display driver mentioned in mythbuntu, I deciced against that because it doesn't support TV out.
cardtype: SkyStar 2 TV (DVB-S) - I will give you the lspci output later
I don't care for mount errors, they can't (or shouldn't) be related
didn't tested media files
the card works fine under windows (with the delivered software)
mythfilldatabase got no errors
the auto finding "all channels" doesn't find much, just a few - recently not a single one.

---

### Post by Manu311 on 2011-09-27
Well I'm back to my original problem, I don't get the useful channels, but I can see (no crashs) the boring channel with 24/7 advertisement and porn.
It's not due to the signal or anything, they are working fine in windows.

I guess that problem belongs somewhere else.

Btw to fix the original error, I just installed the 11.04 version, without allowing any patching while install or after (so currently I got 180 package to patch).

---

### Post by BicyclerBoy on 2011-09-28
Mythbuntu is MythTV packaged with a purpose built ubuntu.

IP 127.0.0.1 is local loopback
A stand-alone combined FE BE(master) will work with this.
Better to use 192.168.xxx to allow future remote FE BE.

VDPAU is the open std API that nVidia uses to allow for video h/w decode & presentation.
VDPAU is capable of full h/w decode of mpeg2 & mpeg4.
There is different capability with diff cards..

The video you are likely recording/playback is mpeg4/10 AVC H264 in a mpeg2-ts container/stream.
The tuner card just streams mpeg2-ts (possibly encrypted).

The TV output has nothing to do with VDPAU. All video decode occurs at the native resolution & is then scaled to display.
If the video card has s-video or component or VGA, you can drive an old CRT TV. The nVidia drivers seem very good doing this.

This website is hosted in the US, so certain topics are not discussed.

---

