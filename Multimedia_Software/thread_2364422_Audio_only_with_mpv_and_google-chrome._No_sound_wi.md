---
title: "Audio only with mpv and google-chrome. No sound with vlc or gnome-player"
date: 2017-06-23
forum: Multimedia Software
---

### Post by vasa1 on 2017-06-23
Background:
```
$ inxi -F
System:    Host: aes-3567 Kernel: 4.4.0-81-generic x86_64 (64 bit)
           Desktop: KDE Plasma 5.8.7 Distro: Ubuntu 16.04 xenial
Machine:   System: Dell (portable) product: Inspiron 15-3567
           Mobo: Dell model: 0FGN4M v: A00 Bios: Dell v: 01.00.00 date: 09/12/2016
CPU:       Dual core Intel Core i3-6006U (-HT-MCP-) cache: 3072 KB 
           clock speeds: max: 2000 MHz 1: 500 MHz 2: 500 MHz 3: 501 MHz 4: 632 MHz
Graphics:  Card: Intel Sky Lake Integrated Graphics
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: radeon,amdgpu)
           Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel HD Graphics 520 (Skylake GT2)
           GLX Version: 3.0 Mesa 12.0.6
Audio:     Card Intel Sunrise Point-LP HD Audio driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.4.0-81-generic
Network:   Card-1: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter
           driver: ath9k
           IF: wlp1s0 state: up mac: 28:56:5a:42:3a:89
           Card-2: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169
           IF: enp2s0 state: down mac: 98:40:bb:26:89:7b
           Card-3: Atheros
           IF: null-if-id state: N/A speed: N/A duplex: N/A mac: N/A
Drives:    HDD Total Size: 1000.2GB (1.9% used)
           ID-1: /dev/sda model: TOSHIBA_MQ01ABD1 size: 1000.2GB
Partition: ID-1: / size: 906G used: 11G (2%) fs: ext4 dev: /dev/sda3
           ID-2: swap-1 size: 8.31GB used: 0.00GB (0%) fs: swap dev: /dev/sda4
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 43.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 201 Uptime: 53 min Memory: 1022.1/7852.0MB
           Client: Shell (bash) inxi: 2.2.35 
$
```
And```
$ lspci -nn | grep -i audio
00:1f.3 Audio device [0403]: Intel Corporation Sunrise Point-LP HD Audio [8086:9d70] (rev 21)
$
```

Long story cut short, I started off with Ubuntu 16.04 pre-installed but I added kubuntu-desktop and removed Unity stuff following 1fallen's guidance (and warning) here: [https://ubuntuforums.org/showthread.php?t=2364085&p=13657415#post13657415](https://ubuntuforums.org/showthread.php?t=2364085&p=13657415#post13657415)

Then I even added a ppa to get to plasma 5.8.7.

So after all that, there's no one to blame but me.

Anyway,
[LIST]
[*]Firefox doesn't play audio in YouTube. I haven't any Flash on the system. And right-clicking on the video confirms it's html5.
[*]gnome-mplayer, mplayer, and vlc don't play audio. Video is fine.
[*]Google Chrome and mpv play both video and audio, whether local or from YouTube.
[/LIST]

What follows is terminal output when I played a locally stored video using mplayer: while the video is fine, there's no audio:
```
$ mplayer /home/vasa1/Downloads/jg.mkv
MPlayer 1.2.1 (Debian), built with gcc-5.3.1 (C) 2000-2016 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/vasa1/Downloads/jg.mkv.
libavformat version 56.40.101 (external)
libavformat file format detected.
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (opus), -aid 0, -alang eng
VIDEO:  [H264]  1280x720  0bpp  23.974 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 COMPATIBLE_BRANDS: iso6avc1mp41
 MAJOR_BRAND: dash
 MINOR_VERSION: 0
 ENCODER: Lavf56.40.101
Load subtitles in /home/vasa1/Downloads/jg.mkv
Failed to open VDPAU backend libvdpau_va_gl.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 56.60.100 (external)
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, floatle, 0.0 kbit/0.00% (ratio: 0->384000)
Selected audio codec: [ffopus] afm: ffmpeg (FFmpeg opus)
==========================================================================
shm_open() failed: No such file or directory
AO: [pulse] Init failed: Protocol error
Failed to initialize audio driver 'pulse'
shm_open() failed: No such file or directory
[AO_ALSA] alsa-lib: pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Protocol error

[AO_ALSA] Playback open error: Connection refused
Failed to initialize audio driver 'alsa'
[AO SDL] Samplerate: 48000Hz Channels: Stereo Format floatle
[AO SDL] using aalib audio driver.
[AO SDL] Unsupported audio format: 0x1d.
[AO SDL] Unable to open audio: No available audio device
Failed to initialize audio driver 'sdl:aalib'
Could not open/initialize audio device -> no sound.
Audio: no sound
Starting playback...
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
V:   5.5   0/  0 44%  1%  0.0% 0 0 

Exiting... (Quit)
$ 

```

Just for completeness, I'd mention that most everything else is fine.

---

### Post by monkeybrain20122 on 2017-06-23
Just a guess. KDE's audio is controlled by phonon. Maybe you can look at its configuration if you haven't already?

---

### Post by vasa1 on 2017-06-23
> **monkeybrain20122 said:**
> Just a guess. KDE's audio is controlled by phonon. Maybe you can look at its configuration if you haven't already?Thanks for replying! I looked but couldn't figure out what to do.

Here's terminal output when playing the same file using mpv without any audio problem:```
$ mpv /home/vasa1/Downloads/yt/jg.mkv
Playing: /home/vasa1/Downloads/jg.mkv
 (+) Video --vid=1 (*) (h264)
 (+) Audio --aid=1 --alang=eng (*) (opus)
shm_open() failed: No such file or directory
[ao/pulse] Init failed: Protocol error
shm_open() failed: No such file or directory
ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Protocol error

[ao/alsa] Playback open error: Connection refused
[ao/oss] Can't open audio device /dev/dsp: No such file or directory
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
[ao/jack] cannot open server
shm_open() failed: No such file or directory
shm_open() failed: No such file or directory
ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Protocol error

AO: [sndio] 48000Hz stereo 2ch s16
[mixer] Hardware volume control unavailable.
VO: [opengl] 1280x720 yuv420p
AV: 00:02:42 / 00:02:42 (99%) A-V:  0.000
Invalid video timestamp: 162.538000 -> 162.538000
AV: 00:02:42 / 00:02:42 (99%) A-V:  0.000


Exiting... (End of file)
[ao/sndio] Blocking until remaining audio is played... (sndio design bug).
$ 
```

---

### Post by Yellow Pasque on 2017-06-23
pulseaudio isn't running for some reason. Try resetting/restarting it:
```
rm -r ~/.config/pulse*; pulseaudio&
```

If pulseaudio can't start, maybe something is grabbing the sound hardware device before pulseaudio:
```
sudo lsof /dev/snd/*
```

Also, make sure "pulse" is a member of "audio" (and your user should **not** be in the audio group):
```
cat /etc/group | grep audio
```

Other than that, you can start digging into the logs:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
[https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

---

### Post by vasa1 on 2017-06-23
@Temüjin, thank you for responding. I ran what you suggested:```
$ rm -r ~/.config/pulse; pulseaudio&
rm: remove 1 argument recursively? y
[1] 13756
07:30 PM ~ $ E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.
^C
[1]+  Exit 1                  pulseaudio


$ sudo lsof /dev/snd/*
[sudo] password for vasa1: 
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/1001/gvfs
      Output information may be incomplete.
COMMAND    PID  USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
pulseaudi 2139 vasa1   16u   CHR  116,2      0t0  488 /dev/snd/controlC0
pulseaudi 2139 vasa1   23u   CHR  116,2      0t0  488 /dev/snd/controlC0
pulseaudi 2139 vasa1   28u   CHR  116,2      0t0  488 /dev/snd/controlC0
$ cat /etc/group | grep audio
audio:x:29:pulse
$
```
Then, I took a chance and purged pulseaudio. Now everything is working! And, to be sure that PA was exorcised, *pgrep pulseaudio* just returns the prompt.

Let's see what happens tomorrow when I boot up again.

---

