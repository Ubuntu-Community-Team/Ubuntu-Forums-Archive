---
title: "Mythubuntu segmentation fault at Watch TV"
date: 2012-04-08
forum: Mythbuntu
---

### Post by alzyee on 2012-04-08
When I click on Watch TV mythfrontend quits and a popup in the top right of the screen says there was a segmentation fault error code 139 and restarts mythfrontend. 

This was not the case after a clean install before updating and installing drivers for capture card. Before the updates it would display tv without any sound.

if I run the command below I can get into Watch TV (without sound).
```
strace mythfrontend
```

I am using a Hauppauge WinTV-HVR-950 as the capture card. I followed the instruction near the bottom of [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950) . I used the file from here for the pl script [www.kernel.org/doc/Documentation/video4linux/extract_xc3028.pl](www.kernel.org/doc/Documentation/video4linux/extract_xc3028.pl)  
I was not able to get sox -r 48000 -w -c 2 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp command to work but the rest of it was okay


Opening mythfrontend from CLI results in the following output when it crashes
```

2012-04-08 20:31:55.027 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2012-04-08 20:31:55.052 OSD: Base theme size: 1280x720
2012-04-08 20:31:55.056 OSD: Scaling factors: 0.375x0.666667
2012-04-08 20:31:55.249 AO: Resampling from 44 kHz to 48 kHz with quality medium
2012-04-08 20:31:55.249 AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2012-04-08 20:31:55.251 ALSA, Error: Setting hardware audio buffer size to 128
2012-04-08 20:31:55.251 ALSA, Error: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
2012-04-08 20:31:55.252 ALSA, Error: Try to manually increase audio buffer with: echo 128 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
2012-04-08 20:31:55.252 ALSA, Error: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
2012-04-08 20:31:55.256 AudioPlayer: Enabling Audio
Segmentation fault

```

Here is the last bit of file from the code below. It did crash when I opened Watch TV.
```

strace -o log.txt mythfrontend

```


```

ioctl(20, USBDEVFS_CONTROL or USBDEVFS_CONTROL32, 0x7fff4913db9c) = 0
ioctl(20, 0x40045532, 0x7fff4913dbec)   = 0
open("/dev/snd/pcmC0D0p", O_RDWR|O_NONBLOCK|O_CLOEXEC) = 37
fcntl(37, F_SETFD, FD_CLOEXEC)          = 0
close(20)                               = 0
ioctl(37, AGPIOC_ACQUIRE or APM_IOC_STANDBY, 0x7fff4913da10) = 0
fcntl(37, F_GETFL)                      = 0x88802 (flags O_RDWR|O_NONBLOCK|O_LARGEFILE|O_CLOEXEC)
ioctl(37, AGPIOC_INFO, 0x7fff4913da08)  = 0
ioctl(37, AGPIOC_SETUP, 0x7fff4913da0c) = 0
mmap(NULL, 4096, PROT_READ, MAP_SHARED, 37, 0x80000000) = 0x7f0f12ee6000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_SHARED, 37, 0x81000000) = 0x7f0f12ee5000
fcntl(37, F_GETFL)                      = 0x88802 (flags O_RDWR|O_NONBLOCK|O_LARGEFILE|O_CLOEXEC)
fcntl(37, F_SETFL, O_RDWR|O_LARGEFILE|O_CLOEXEC) = 0
open("/dev/snd/controlC0", O_RDONLY|O_CLOEXEC) = 20
fcntl(20, F_SETFD, FD_CLOEXEC)          = 0
ioctl(20, UI_DEV_CREATE, 0x7fff4913db90) = 0
close(20)                               = 0
stat("/usr/share/alsa/alsa.conf", {st_mode=S_IFREG|0644, st_size=9096, ...}) = 0
open("/dev/snd/controlC0", O_RDONLY|O_CLOEXEC) = 20
fcntl(20, F_SETFD, FD_CLOEXEC)          = 0
ioctl(20, UI_DEV_CREATE, 0x7fff4913d9c0) = 0
close(20)                               = 0
open("/dev/snd/controlC0", O_RDWR|O_CLOEXEC) = 20
fcntl(20, F_SETFD, FD_CLOEXEC)          = 0
ioctl(20, USBDEVFS_CONTROL or USBDEVFS_CONTROL32, 0x7fff4913dcfc) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dd60) = 0
close(20)                               = 0
ioctl(37, 0xc2604110, 0x7fff4913d170)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cae0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cdb0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cdb0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913d170)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cdb0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cdb0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913d170)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cec0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cb00)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cb00)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cec0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cec0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cb00)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cb00)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cec0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cec0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cb00)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cb00)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cec0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cec0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cec0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cec0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cec0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cec0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cec0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cec0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cec0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cec0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cec0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cc00)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cc00)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cc00)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cc00)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cc00)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cc00)   = 0
ioctl(37, AGPIOC_ACQUIRE or APM_IOC_STANDBY, 0x7fff4913e160) = 0
open("/proc/asound/card0/pcm0p/sub0/prealloc", O_RDONLY|O_CLOEXEC) = 20
fcntl(20, F_SETFD, FD_CLOEXEC)          = 0
fstat(20, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
open("/proc/asound/card0/pcm0p/sub0/prealloc_max", O_RDONLY|O_CLOEXEC) = 38
fcntl(38, F_SETFD, FD_CLOEXEC)          = 0
fstat(38, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
fstat(20, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
fstat(20, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
read(20, "64\n", 16384)                 = 3
read(20, "", 16381)                     = 0
read(20, "", 32765)                     = 0
fstat(38, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
fstat(38, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
read(38, "16384\n", 16384)              = 6
read(38, "", 16378)                     = 0
read(38, "", 32762)                     = 0
close(20)                               = 0
close(38)                               = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
write(1, "2012-04-08 20:43:33.028 ALSA, Er"..., 79) = 79
close(37)                               = 0
munmap(0x7f0f12ee6000, 4096)            = 0
munmap(0x7f0f12ee5000, 4096)            = 0
open("/proc/asound/card0/pcm0p/sub0/prealloc", O_RDWR|O_CREAT|O_CLOEXEC, 0666) = -1 EACCES (Permission denied)
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
write(1, "2012-04-08 20:43:33.029 ALSA, Er"..., 111) = 111
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
write(1, "2012-04-08 20:43:33.029 ALSA, Er"..., 140) = 140
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
write(1, "2012-04-08 20:43:33.029 ALSA, Er"..., 118) = 118
stat("/usr/share/alsa/alsa.conf", {st_mode=S_IFREG|0644, st_size=9096, ...}) = 0
open("/dev/snd/controlC0", O_RDONLY|O_CLOEXEC) = 20
fcntl(20, F_SETFD, FD_CLOEXEC)          = 0
ioctl(20, UI_DEV_CREATE, 0x7fff4913daf0) = 0
close(20)                               = 0
stat("/usr/share/alsa/alsa.conf", {st_mode=S_IFREG|0644, st_size=9096, ...}) = 0
open("/dev/snd/controlC0", O_RDONLY|O_CLOEXEC) = 20
fcntl(20, F_SETFD, FD_CLOEXEC)          = 0
ioctl(20, UI_DEV_CREATE, 0x7fff4913d950) = 0
close(20)                               = 0
open("/dev/snd/controlC0", O_RDWR|O_CLOEXEC) = 20
fcntl(20, F_SETFD, FD_CLOEXEC)          = 0
ioctl(20, USBDEVFS_CONTROL or USBDEVFS_CONTROL32, 0x7fff4913dc8c) = 0
ioctl(20, UI_DEV_CREATE, 0x7fff4913dcb0) = 0
close(20)                               = 0
open("/dev/snd/controlC0", O_RDONLY|O_CLOEXEC) = 20
fcntl(20, F_SETFD, FD_CLOEXEC)          = 0
ioctl(20, UI_DEV_CREATE, 0x7fff4913d740) = 0
close(20)                               = 0
open("/dev/snd/controlC0", O_RDWR|O_CLOEXEC) = 20
fcntl(20, F_SETFD, FD_CLOEXEC)          = 0
ioctl(20, USBDEVFS_CONTROL or USBDEVFS_CONTROL32, 0x7fff4913d8bc) = 0
ioctl(20, 0x40045532, 0x7fff4913d90c)   = 0
open("/dev/snd/pcmC0D0p", O_RDWR|O_NONBLOCK|O_CLOEXEC) = 37
fcntl(37, F_SETFD, FD_CLOEXEC)          = 0
close(20)                               = 0
ioctl(37, AGPIOC_ACQUIRE or APM_IOC_STANDBY, 0x7fff4913d730) = 0
fcntl(37, F_GETFL)                      = 0x88802 (flags O_RDWR|O_NONBLOCK|O_LARGEFILE|O_CLOEXEC)
ioctl(37, AGPIOC_INFO, 0x7fff4913d728)  = 0
ioctl(37, AGPIOC_SETUP, 0x7fff4913d72c) = 0
mmap(NULL, 4096, PROT_READ, MAP_SHARED, 37, 0x80000000) = 0x7f0f12ee6000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_SHARED, 37, 0x81000000) = 0x7f0f12ee5000
fcntl(37, F_GETFL)                      = 0x88802 (flags O_RDWR|O_NONBLOCK|O_LARGEFILE|O_CLOEXEC)
fcntl(37, F_SETFL, O_RDWR|O_LARGEFILE|O_CLOEXEC) = 0
open("/dev/snd/controlC0", O_RDONLY|O_CLOEXEC) = 20
fcntl(20, F_SETFD, FD_CLOEXEC)          = 0
ioctl(20, UI_DEV_CREATE, 0x7fff4913d8b0) = 0
close(20)                               = 0
stat("/usr/share/alsa/alsa.conf", {st_mode=S_IFREG|0644, st_size=9096, ...}) = 0
open("/dev/snd/controlC0", O_RDONLY|O_CLOEXEC) = 20
fcntl(20, F_SETFD, FD_CLOEXEC)          = 0
ioctl(20, UI_DEV_CREATE, 0x7fff4913d6e0) = 0
close(20)                               = 0
open("/dev/snd/controlC0", O_RDWR|O_CLOEXEC) = 20
fcntl(20, F_SETFD, FD_CLOEXEC)          = 0
ioctl(20, USBDEVFS_CONTROL or USBDEVFS_CONTROL32, 0x7fff4913da1c) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913da80) = 0
close(20)                               = 0
ioctl(37, 0xc2604110, 0x7fff4913ce90)   = 0
ioctl(37, 0xc2604110, 0x7fff4913c800)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cad0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cad0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913ce90)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cad0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cad0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913ce90)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cbe0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913c820)   = 0
ioctl(37, 0xc2604110, 0x7fff4913c820)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cbe0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cbe0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913c820)   = 0
ioctl(37, 0xc2604110, 0x7fff4913c820)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cbe0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cbe0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913c820)   = 0
ioctl(37, 0xc2604110, 0x7fff4913c820)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cbe0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cbe0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cbe0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cbe0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cbe0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cbe0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cbe0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cbe0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cbe0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cbe0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cbe0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913c920)   = 0
ioctl(37, 0xc2604110, 0x7fff4913c920)   = 0
ioctl(37, 0xc2604110, 0x7fff4913c920)   = 0
ioctl(37, 0xc2604110, 0x7fff4913c920)   = 0
ioctl(37, 0xc2604110, 0x7fff4913c920)   = 0
ioctl(37, 0xc2604110, 0x7fff4913c920)   = 0
ioctl(37, 0xc2604110, 0x7fff4913c690)   = 0
ioctl(37, 0xc2604110, 0x7fff4913c690)   = 0
ioctl(37, 0xc2604110, 0x7fff4913c690)   = 0
ioctl(37, 0xc2604110, 0x7fff4913c690)   = 0
ioctl(37, 0xc2604110, 0x7fff4913c690)   = 0
ioctl(37, 0xc2604110, 0x7fff4913c920)   = 0
ioctl(37, 0xc2604110, 0x7fff4913c920)   = 0
ioctl(37, 0xc2604110, 0x7fff4913c920)   = 0
ioctl(37, 0xc2604110, 0x7fff4913c920)   = 0
ioctl(37, 0xc2604110, 0x7fff4913c920)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cdc0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cdc0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cdc0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cdc0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cd90)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cd90)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cd90)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cd90)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cd90)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cde0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cde0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913cde0)   = 0
ioctl(37, 0xc2604110, 0x7fff4913d200)   = 0
ioctl(37, 0xc2604111, 0x7fff4913d200)   = 0
ioctl(37, 0xc0884113, 0x7fff4913cce0)   = 0
ioctl(37, 0x80184132, 0x7fff4913cc40)   = 0
ioctl(37, 0x80184132, 0x7fff4913cc40)   = 0
mmap(NULL, 65536, PROT_READ|PROT_WRITE, MAP_SHARED, 37, 0) = 0x7f0f0d7d9000
ioctl(37, 0x4140, 0)                    = 0
ioctl(37, 0xc0884113, 0x7fff4913d160)   = 0
ioctl(37, 0x4140, 0x1000)               = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
poll([{fd=14, events=POLLIN|POLLPRI}], 1, 0) = 0 (Timeout)
write(14, ";\0\0\0\26SELECT data FROM settings W"..., 63) = 63
read(14, "\f\0\0\1\0\f\2\0\0\1\0\2\0\0\0\0\27\0\0\2\3def\0\0\0\1?\0\f?"..., 16384) = 149
poll([{fd=14, events=POLLIN|POLLPRI}], 1, 0) = 0 (Timeout)
write(14, "\5\0\0\0\32\f\2\0\0", 9)     = 9
read(14, "\7\0\0\1\0\0\0\2\0\0\0", 16384) = 11
poll([{fd=14, events=POLLIN|POLLPRI}], 1, 0) = 0 (Timeout)
poll([{fd=14, events=POLLIN|POLLPRI}], 1, 0) = 0 (Timeout)
write(14, ",\0\0\0\27\f\2\0\0\0\1\0\0\0\0\1\376\0\376\0\fmixercontro"..., 48) = 48
read(14, "\1\0\0\1\0019\0\0\2\3def\vmythconverg\10settin"..., 16384) = 94
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
poll([{fd=14, events=POLLIN|POLLPRI}], 1, 0) = 0 (Timeout)
write(14, "\5\0\0\0\31\f\2\0\0", 9)     = 9
stat("/usr/share/alsa/alsa.conf", {st_mode=S_IFREG|0644, st_size=9096, ...}) = 0
open("/dev/snd/controlC0", O_RDONLY|O_CLOEXEC) = 20
fcntl(20, F_SETFD, FD_CLOEXEC)          = 0
ioctl(20, UI_DEV_CREATE, 0x7fff4913d940) = 0
close(20)                               = 0
open("/dev/snd/controlC0", O_RDWR|O_CLOEXEC) = 20
fcntl(20, F_SETFD, FD_CLOEXEC)          = 0
ioctl(20, USBDEVFS_CONTROL or USBDEVFS_CONTROL32, 0x7fff4913dc7c) = 0
fcntl(20, F_GETFL)                      = 0x88002 (flags O_RDWR|O_LARGEFILE|O_CLOEXEC)
fcntl(20, F_SETFL, O_RDWR|O_NONBLOCK|O_LARGEFILE|O_CLOEXEC) = 0
ioctl(20, USBDEVFS_RELEASEINTERFACE, 0x7fff4913ddd0) = 0
ioctl(20, USBDEVFS_RELEASEINTERFACE, 0x7fff4913ddd0) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d2f0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d2f0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d2f0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d2f0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d2f0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d2f0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d2f0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d2f0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d2f0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d2f0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d2f0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913db50) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913db50) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913d9a0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d1d0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d1e0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d230) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913db50) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913d9a0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d1d0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d1e0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d230) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913db50) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913d9a0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d230) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913db50) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913d9a0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d1d0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d1e0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d230) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913db50) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913d9a0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d1d0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d1e0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d230) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913db50) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913d9a0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d230) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913db50) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913d9a0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d230) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913db50) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913d9a0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d1d0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d1e0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d230) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d2f0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d2f0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d2f0) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d2f0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_CONNECTINFO, 0x7fff4913dac0) = 0
ioctl(20, USBDEVFS_IOCTL or USBDEVFS_IOCTL32, 0x7fff4913d300) = 0
ioctl(20, USBDEVFS_DISCONNECT, 0x7fff4913dd9c) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
poll([{fd=21, events=POLLIN|POLLPRI}], 1, 0) = 0 (Timeout)
write(21, ";\0\0\0\26SELECT data FROM settings W"..., 63) = 63
read(21, "\f\0\0\1\0\205\1\0\0\1\0\2\0\0\0\0\27\0\0\2\3def\0\0\0\1?\0\f?"..., 16384) = 149
poll([{fd=21, events=POLLIN|POLLPRI}], 1, 0) = 0 (Timeout)
write(21, "\5\0\0\0\32\205\1\0\0", 9)   = 9
read(21, "\7\0\0\1\0\0\0\2\0\0\0", 16384) = 11
poll([{fd=21, events=POLLIN|POLLPRI}], 1, 0) = 0 (Timeout)
poll([{fd=21, events=POLLIN|POLLPRI}], 1, 0) = 0 (Timeout)
write(21, ".\0\0\0\27\205\1\0\0\0\1\0\0\0\0\1\376\0\376\0\16pcmmixervol"..., 50) = 50
read(21, "\1\0\0\1\0019\0\0\2\3def\vmythconverg\10settin"..., 16384) = 94
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
poll([{fd=21, events=POLLIN|POLLPRI}], 1, 0) = 0 (Timeout)
write(21, "\5\0\0\0\31\205\1\0\0", 9)   = 9
mmap(NULL, 8392704, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS|MAP_STACK, -1, 0) = 0x7f0efedc0000
mprotect(0x7f0efedc0000, 4096, PROT_NONE) = 0
clone(child_stack=0x7f0eff5bff30, flags=CLONE_VM|CLONE_FS|CLONE_FILES|CLONE_SIGHAND|CLONE_THREAD|CLONE_SYSVSEM|CLONE_SETTLS|CLONE_PARENT_SETTID|CLONE_CHILD_CLEARTID, parent_tidptr=0x7f0eff5c09d0, tls=0x7f0eff5c0700, child_tidptr=0x7f0eff5c09d0) = 3466
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
write(1, "2012-04-08 20:43:33.049 AudioPla"..., 52) = 52
futex(0x207c78c, FUTEX_WAIT_PRIVATE, 1, NULL) = 0
futex(0x207c760, FUTEX_WAKE_PRIVATE, 1) = 0
futex(0x20797dc, FUTEX_CMP_REQUEUE_PRIVATE, 1, 2147483647, 0x20797b0, 2) = 1
futex(0x20797b0, FUTEX_WAKE_PRIVATE, 1) = 1
futex(0x172a1ac, FUTEX_WAKE_OP_PRIVATE, 1, 1, 0x172a1a8, {FUTEX_OP_SET, 0, FUTEX_OP_CMP_GT, 1}) = 1
futex(0x172a180, FUTEX_WAKE_PRIVATE, 1) = 1
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
poll([{fd=14, events=POLLIN|POLLPRI}], 1, 0) = 0 (Timeout)
write(14, "X\0\0\0\26SELECT mark, offset FROM re"..., 92) = 92
read(14, "\f\0\0\1\0\r\2\0\0\2\0\3\0\0\0\0\27\0\0\2\3def\0\0\0\1?\0\f?"..., 16384) = 257
poll([{fd=14, events=POLLIN|POLLPRI}], 1, 0) = 0 (Timeout)
write(14, "\5\0\0\0\32\r\2\0\0", 9)     = 9
read(14, "\7\0\0\1\0\0\0\2\0\0\0", 16384) = 11
poll([{fd=14, events=POLLIN|POLLPRI}], 1, 0) = 0 (Timeout)
poll([{fd=14, events=POLLIN|POLLPRI}], 1, 0) = 0 (Timeout)
write(14, "\"\0\0\0\27\r\2\0\0\0\1\0\0\0\0\1\3\200\f\0\3\0\302\v\0\0\7\334\7\4\10\24"..., 38) = 38
read(14, "\1\0\0\1\2A\0\0\2\3def\vmythconverg\frecord"..., 16384) = 165
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
poll([{fd=14, events=POLLIN|POLLPRI}], 1, 0) = 0 (Timeout)
write(14, "\5\0\0\0\31\r\2\0\0", 9)     = 9
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
write(31, "51      QUERY_RECORDER 1[]:[]FIL"..., 59) = 59
select(32, [31], NULL, NULL, {0, 0})    = 1 (in [31], left {0, 0})
ioctl(31, FIONREAD, [10])               = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
select(32, [31], NULL, NULL, {0, 5000}) = 1 (in [31], left {0, 4998})
ioctl(31, FIONREAD, [10])               = 0
read(31, "2       ", 8)                 = 8
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
read(31, "ok", 2)                       = 2
write(29, "0", 1)                       = 1
futex(0x127e32c, FUTEX_WAKE_OP_PRIVATE, 1, 1, 0x127e328, {FUTEX_OP_SET, 0, FUTEX_OP_CMP_GT, 1}) = 1
futex(0x127e300, FUTEX_WAKE_PRIVATE, 1) = 1
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++

```


I am running Mythubuntu 11.10 64bit with a Hauppauge WinTV-HVR-950.

---

### Post by superm1 on 2012-04-09
So what you'll need to do is upgrade to the latest 0.25 snapshot on the PPA.  0.25 is days away, but if this persists it's best to get this bug reported ASAP in hopes that it can be fixed in 0.25.

You can upgrade to a 0.25 release using the mythbuntu repos ([www.mythbuntu.org/repos](www.mythbuntu.org/repos))

Once you've upgraded to 0.25, if the problem persists, create a bug report using these steps:
[http://www.mythtv.org/wiki/Debugging#Ubuntu_packages](http://www.mythtv.org/wiki/Debugging#Ubuntu_packages)

---

### Post by alzyee on 2012-04-11
I installed the repo then executed the code below and the bug persisted.
```

sudo apt-get update
sudo apt-get upgrade -y
sudo reboot

```


I submitted a bug report ([https://bugs.launchpad.net/mythbuntu/+bug/979509](https://bugs.launchpad.net/mythbuntu/+bug/979509)). Sadly it looks like 0.25 came out on 4-10 (Yesterday). Thank you for pointing me the right direction.

---

