---
title: "Sound Blaster X-Fi Fatal1ty"
date: 2010-05-16
forum: Multimedia Software
---

### Post by Flawd on 2010-05-16
I've done a couple days of searching before I finally decided to ask for some real help. Forgive me if I missed something in all my searching.

I just installed Ubuntu 10.04 x86_64bit, and everything is working great but my sound.

To save time and some tl;dr. I tried a couple different versions of Creative's driver, ALSA, and OSS.

It seems that the OSS drivers are installed and working, but I can't get them set as default.

Here's ossinfo
```
flawd@flawd-desktop:~$ ossinfo
Version info: OSS 4.2 (b 2002/200911060720) (0x00040100) TRIAL
Platform: Linux/x86_64 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 (flawd-desktop)

Number of audio devices:    2
Number of audio engines:    6
Number of MIDI devices:        0
Number of mixer devices:    1


Device objects
 0: osscore0 OSS core services
 1: oss_sbxfi0 Sound Blaster X-Fi (SB046x/067x/076x) interrupts=7356613 (7356613)
    PCI device 1102:0005, subdevice 1102:002c
 2: oss_usb0 USB audio core services

MIDI devices (/dev/midi*)

Mixer devices
 0: Sound Blaster X-Fi (SB046x/067x (Mixer 0 of device object 1)

Audio devices
Sound Blaster X-Fi (SB046x/067x/076x) output  /dev/oss/oss_sbxfi0/pcm0  (device index 0)
Sound Blaster X-Fi (SB046x/067x/076x) input  /dev/oss/oss_sbxfi0/pcmin0  (device index 1)

Nodes
  /dev/dsp -> /dev/oss/oss_sbxfi0/pcm0
  /dev/dsp_in -> /dev/oss/oss_sbxfi0/pcm0
  /dev/dsp_out -> /dev/oss/oss_sbxfi0/pcm0
  /dev/dsp_mmap -> /dev/oss/oss_sbxfi0/pcm0

```Here's osstest
```
Sound subsystem and version: OSS 4.2 (b 2002/200911060720) (0x00040100)
Platform: Linux/x86_64 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010

*** Scanning sound adapter #-1 ***
/dev/oss/oss_sbxfi0/pcm0 (audio engine 0): Sound Blaster X-Fi (SB046x/067x/076x) output
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47526.00 Hz (-0.99%)> 
/dev/oss/oss_sbxfi0/pcmin0 (audio engine 1): Sound Blaster X-Fi (SB046x/067x/076x) input
- Skipping input only device

*** All tests completed OK ***
```osstest does output sound. So I know the driver is, in fact, working.

If I go into the sound preferences, under the Hardware tab, there is nothing under "Choose a device to configure:".

The OSS drivers see the sound card, and can use it, but that's as far as I can get. I would appreciate any input...

Thanks in advance!



I'll post a few more command outputs that I've seen asked for in other forums, just in case:

```
flawd@flawd-desktop:~$ dmesg | tail
[ 1768.197678] type=1505 audit(1273719700.789:23):  operation="profile_replace" pid=3716 name="/usr/sbin/cupsd"
[ 1768.239743] type=1505 audit(1273719700.829:24):  operation="profile_load" pid=3717 name="/usr/sbin/mysqld-akonadi"
[ 9312.435677] __ratelimit: 3 callbacks suppressed
[ 9312.435682] npviewer.bin[6078]: segfault at 418 ip 00000000f610f586 sp 00000000ffaf8eb8 error 6 in libflashplayer.so[f5ec1000+b02000]
[106805.204126] npviewer.bin[10800]: segfault at f59de04c ip 00000000f61cb717 sp 00000000ffb79d10 error 4 in libflashplayer.so[f5e2d000+b02000]
[124660.628998] npviewer.bin[11179]: segfault at 418 ip 00000000f60a4586 sp 00000000ff88d1c8 error 6 in libflashplayer.so[f5e56000+b02000]
[194095.150037] usbcore: deregistering interface driver oss_usb
[194095.180156] oss_sbxfi 0000:02:06.0: PCI INT A disabled
[194139.427619] oss_sbxfi 0000:02:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[194139.727722] usbcore: registered new interface driver oss_usb
flawd@flawd-desktop:~$ 

```From lspci -v
```
02:06.0 Multimedia audio controller: Creative Labs SB X-Fi
    Subsystem: Creative Labs Device 002c
    Flags: bus master, medium devsel, latency 32, IRQ 16
    I/O ports at 9c00 [size=32]
    Memory at efc00000 (64-bit, non-prefetchable) [size=2M]
    Memory at e8000000 (64-bit, non-prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: oss_sbxfi
    Kernel modules: snd-ctxfi
``````
flawd@flawd-desktop:~$ fgrep -ie 'audio' /etc/group
audio:x:29:pulse
``````
flawd@flawd-desktop:~$ sudo aplay -l
[sudo] password for flawd: 
aplay: device_list:223: no soundcards found...
```




Edit: I did try the troubleshooting in the sticky of this forum, and got the sound card to show up in the sound preferences, but it still isn't working.

Here's the output after trying to install ALSA from the sticky thread:
```
checking for which soundcards to compile driver for... configure: error: Unknown soundcard sbxfi
flawd@flawd-desktop:~/src/alsa/alsa-driver-1.0.12rc2$ sudo make
make all-deps
make[1]: Entering directory `/home/flawd/src/alsa/alsa-driver-1.0.12rc2'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/home/flawd/src/alsa/alsa-driver-1.0.12rc2'

Please, run the configure script as first...
```

---

### Post by lidex on 2010-05-16
That is an ancient alsa version. 
Check out these links for OSS:
[http://ubuntuforums.org/showthread.php?t=1420745]("http://ubuntuforums.org/showthread.php?t=1420745")
[http://ubuntuforums.org/showthread.php?t=1355676]("http://ubuntuforums.org/showthread.php?t=1355676")
[http://ubuntuforums.org/showthread.php?t=1217259]("http://ubuntuforums.org/showthread.php?t=1217259")
[http://ubuntuforums.org/showthread.php?t=866106]("http://ubuntuforums.org/showthread.php?t=866106")

---

