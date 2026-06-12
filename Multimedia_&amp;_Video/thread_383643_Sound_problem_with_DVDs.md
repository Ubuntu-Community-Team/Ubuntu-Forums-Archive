---
title: "Sound problem with DVDs"
date: 2007-03-13
forum: Multimedia &amp; Video
---

### Post by Snyper64 on 2007-03-13
As my title states I am having problems with my sound when playing DVDs, I have my dvd decoders downloaded from Automatix and I can play .avi and .ogg/.mkv files just fine(sound plays through my Logitech z-5500s just fine). When I play a DVD in mplayer I get the error message: Error opening/inializing the selected video_out (-vo) device. When using Totem I get the following error: The audio device is busy, is another program using it? VLC player on the other hand will jump right into the movie(bypassing the main menu) and play the dvd, but it will only play in stereo, not Dolby Digital or DTS surround. I know my surround sound system works, I just recently switched to Linux 2 days ago and before that I was using Cyperlink Power DVD, VLC, and Zoom player for all of my needs(they all played Dolby Digital and DTS just fine with AC3 or packaged decoders for Power DVD). If someone would tell me where the log files are at for each player I would gladly post them up.

I have searched around for support on how to get Dolby Digital and DTS decoding and found that I should use alsa-utils, though I have not been successful in figuring out how to install them, though I have found a how to on how to set up alsa-utils once I get them installed [HERE]("http://www.ubuntuforums.org/newthread.php?do=newthread&f=138") .

As you can see I think my problem lies within my decoding the sound but I figured I would get a second opinion and some help on downloading and installing the alsa utilities pack and finding my log files so that i can see where the problem lies.

My pc has 2 sound cards, the built in one that has no spdif output, and my external(Turtle Beach Audio Advantage Amigo) that has toslink out and I am currently using. Again the Turtle Beach card is outputting sound over the fiber for avi and system sounds so it does work.

Thanks
Snyper64

---

### Post by panch0 on 2007-03-14
To get the log for MPlayer, run

mplayer -v -vo xv dvd://

from the console. If you can't make sense of it, post it here.

---

### Post by Snyper64 on 2007-03-14
Most of these codes remind me of DOS and the old Win 98 days. Anyways heres a copy of my log file:```
snyper64@Snyper64-laptop:~$ mplayer -v -vo xv dvd://
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 4, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


get_path('codecs.conf') -> '/home/snyper64/.mplayer/codecs.conf'
Reading /home/snyper64/.mplayer/codecs.conf: Can't open '/home/snyper64/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
CommandLine: '-v' '-vo' 'xv' 'dvd://'
init_freetype
get_path('font/font.desc') -> '/home/snyper64/.mplayer/font/font.desc'
font: can't open file: /home/snyper64/.mplayer/font/font.desc
Font /usr/share/mplayer/font/font.desc loaded successfully! (206 chars)
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Using nanosleep() timing
get_path('input.conf') -> '/home/snyper64/.mplayer/input.conf'
Can't open input config file /home/snyper64/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 60 binds
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
get_path('.conf') -> '/home/snyper64/.mplayer/.conf'

Playing dvd://.
get_path('sub/') -> '/home/snyper64/.mplayer/sub/'
URL: dvd://
Couldn't open DVD device: /dev/dvd
[file] No filename
Failed to open dvd://.

vo: x11 uninit called but X11 not inited..

Exiting... (End of file)
```

It looks like it can't find any of my codecs like I thought, though why it can't find the video codecs I do not know? Also I found the Alsa-utils pack for amd64.deb but everytime I try to install it I get the following error: Dependency is not satisfiable: libasound2. Did I download the wrong package?

---

### Post by panch0 on 2007-03-14
Nah, just ignore what it says about codecs, it doesn't even get to the point where it tries any codecs. It cannot find your DVD device to begin with. Do you know where it is? The standard is /dev/dvd, but if it something else you would have to tell MPlayer about it like for example

mplayer -v -vo xv -dvd-device /dev/hdc dvd://

if your DVD device is /dev/hdc. If you are not sure what it is, post the output of

ls -l /dev

---

### Post by Snyper64 on 2007-03-14
Am I just supposed to type ls -l /dev into the terminal? Because its not working?

---

### Post by Snyper64 on 2007-03-15
bump

---

### Post by Snyper64 on 2007-03-15
I don't think my dvd drive is in the standard area:
```
snyper64@Snyper64-laptop:~$ mplayer -v -vo xv -dvd-device /dev/hdc dvd://
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 4, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


get_path('codecs.conf') -> '/home/snyper64/.mplayer/codecs.conf'
Reading /home/snyper64/.mplayer/codecs.conf: Can't open '/home/snyper64/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
CommandLine: '-v' '-vo' 'xv' '-dvd-device' '/dev/hdc' 'dvd://'
init_freetype
get_path('font/font.desc') -> '/home/snyper64/.mplayer/font/font.desc'
font: can't open file: /home/snyper64/.mplayer/font/font.desc
Font /usr/share/mplayer/font/font.desc loaded successfully! (206 chars)
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Using nanosleep() timing
get_path('input.conf') -> '/home/snyper64/.mplayer/input.conf'
Can't open input config file /home/snyper64/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 60 binds
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
get_path('.conf') -> '/home/snyper64/.mplayer/.conf'

Playing dvd://.
get_path('sub/') -> '/home/snyper64/.mplayer/sub/'
URL: dvd://
Couldn't open DVD device: /dev/hdc
[file] No filename
Failed to open dvd://.

vo: x11 uninit called but X11 not inited..

Exiting... (End of file)
snyper64@Snyper64-laptop:~$ 

```

Can somebody tell me how to post my dev file so we can find out where my dvd drive is located.

---

### Post by panch0 on 2007-03-15
Yes, type "ls -l /dev" in the terminal, hit Enter. Post what you get.

---

### Post by Snyper64 on 2007-03-15
This what you wanted?

```
crw-rw-rw- 1 root tty       2,  54 2007-03-15 11:07 ptys6
crw-rw-rw- 1 root tty       2,  55 2007-03-15 11:07 ptys7
crw-rw-rw- 1 root tty       2,  56 2007-03-15 11:07 ptys8
crw-rw-rw- 1 root tty       2,  57 2007-03-15 11:07 ptys9
crw-rw-rw- 1 root tty       2,  58 2007-03-15 11:07 ptysa
crw-rw-rw- 1 root tty       2,  59 2007-03-15 11:07 ptysb
crw-rw-rw- 1 root tty       2,  60 2007-03-15 11:07 ptysc
crw-rw-rw- 1 root tty       2,  61 2007-03-15 11:07 ptysd
crw-rw-rw- 1 root tty       2,  62 2007-03-15 11:07 ptyse
crw-rw-rw- 1 root tty       2,  63 2007-03-15 11:07 ptysf
crw-rw-rw- 1 root tty       2,  64 2007-03-15 11:07 ptyt0
crw-rw-rw- 1 root tty       2,  65 2007-03-15 11:07 ptyt1
crw-rw-rw- 1 root tty       2,  66 2007-03-15 11:07 ptyt2
crw-rw-rw- 1 root tty       2,  67 2007-03-15 11:07 ptyt3
crw-rw-rw- 1 root tty       2,  68 2007-03-15 11:07 ptyt4
crw-rw-rw- 1 root tty       2,  69 2007-03-15 11:07 ptyt5
crw-rw-rw- 1 root tty       2,  70 2007-03-15 11:07 ptyt6
crw-rw-rw- 1 root tty       2,  71 2007-03-15 11:07 ptyt7
crw-rw-rw- 1 root tty       2,  72 2007-03-15 11:07 ptyt8
crw-rw-rw- 1 root tty       2,  73 2007-03-15 11:07 ptyt9
crw-rw-rw- 1 root tty       2,  74 2007-03-15 11:07 ptyta
crw-rw-rw- 1 root tty       2,  75 2007-03-15 11:07 ptytb
crw-rw-rw- 1 root tty       2,  76 2007-03-15 11:07 ptytc
crw-rw-rw- 1 root tty       2,  77 2007-03-15 11:07 ptytd
crw-rw-rw- 1 root tty       2,  78 2007-03-15 11:07 ptyte
crw-rw-rw- 1 root tty       2,  79 2007-03-15 11:07 ptytf
crw-rw-rw- 1 root tty       2,  80 2007-03-15 11:07 ptyu0
crw-rw-rw- 1 root tty       2,  81 2007-03-15 11:07 ptyu1
crw-rw-rw- 1 root tty       2,  82 2007-03-15 11:07 ptyu2
crw-rw-rw- 1 root tty       2,  83 2007-03-15 11:07 ptyu3
crw-rw-rw- 1 root tty       2,  84 2007-03-15 11:07 ptyu4
crw-rw-rw- 1 root tty       2,  85 2007-03-15 11:07 ptyu5
crw-rw-rw- 1 root tty       2,  86 2007-03-15 11:07 ptyu6
crw-rw-rw- 1 root tty       2,  87 2007-03-15 11:07 ptyu7
crw-rw-rw- 1 root tty       2,  88 2007-03-15 11:07 ptyu8
crw-rw-rw- 1 root tty       2,  89 2007-03-15 11:07 ptyu9
crw-rw-rw- 1 root tty       2,  90 2007-03-15 11:07 ptyua
crw-rw-rw- 1 root tty       2,  91 2007-03-15 11:07 ptyub
crw-rw-rw- 1 root tty       2,  92 2007-03-15 11:07 ptyuc
crw-rw-rw- 1 root tty       2,  93 2007-03-15 11:07 ptyud
crw-rw-rw- 1 root tty       2,  94 2007-03-15 11:07 ptyue
crw-rw-rw- 1 root tty       2,  95 2007-03-15 11:07 ptyuf
crw-rw-rw- 1 root tty       2,  96 2007-03-15 11:07 ptyv0
crw-rw-rw- 1 root tty       2,  97 2007-03-15 11:07 ptyv1
crw-rw-rw- 1 root tty       2,  98 2007-03-15 11:07 ptyv2
crw-rw-rw- 1 root tty       2,  99 2007-03-15 11:07 ptyv3
crw-rw-rw- 1 root tty       2, 100 2007-03-15 11:07 ptyv4
crw-rw-rw- 1 root tty       2, 101 2007-03-15 11:07 ptyv5
crw-rw-rw- 1 root tty       2, 102 2007-03-15 11:07 ptyv6
crw-rw-rw- 1 root tty       2, 103 2007-03-15 11:07 ptyv7
crw-rw-rw- 1 root tty       2, 104 2007-03-15 11:07 ptyv8
crw-rw-rw- 1 root tty       2, 105 2007-03-15 11:07 ptyv9
crw-rw-rw- 1 root tty       2, 106 2007-03-15 11:07 ptyva
crw-rw-rw- 1 root tty       2, 107 2007-03-15 11:07 ptyvb
crw-rw-rw- 1 root tty       2, 108 2007-03-15 11:07 ptyvc
crw-rw-rw- 1 root tty       2, 109 2007-03-15 11:07 ptyvd
crw-rw-rw- 1 root tty       2, 110 2007-03-15 11:07 ptyve
crw-rw-rw- 1 root tty       2, 111 2007-03-15 11:07 ptyvf
crw-rw-rw- 1 root tty       2, 112 2007-03-15 11:07 ptyw0
crw-rw-rw- 1 root tty       2, 113 2007-03-15 11:07 ptyw1
crw-rw-rw- 1 root tty       2, 114 2007-03-15 11:07 ptyw2
crw-rw-rw- 1 root tty       2, 115 2007-03-15 11:07 ptyw3
crw-rw-rw- 1 root tty       2, 116 2007-03-15 11:07 ptyw4
crw-rw-rw- 1 root tty       2, 117 2007-03-15 11:07 ptyw5
crw-rw-rw- 1 root tty       2, 118 2007-03-15 11:07 ptyw6
crw-rw-rw- 1 root tty       2, 119 2007-03-15 11:07 ptyw7
crw-rw-rw- 1 root tty       2, 120 2007-03-15 11:07 ptyw8
crw-rw-rw- 1 root tty       2, 121 2007-03-15 11:07 ptyw9
crw-rw-rw- 1 root tty       2, 122 2007-03-15 11:07 ptywa
crw-rw-rw- 1 root tty       2, 123 2007-03-15 11:07 ptywb
crw-rw-rw- 1 root tty       2, 124 2007-03-15 11:07 ptywc
crw-rw-rw- 1 root tty       2, 125 2007-03-15 11:07 ptywd
crw-rw-rw- 1 root tty       2, 126 2007-03-15 11:07 ptywe
crw-rw-rw- 1 root tty       2, 127 2007-03-15 11:07 ptywf
crw-rw-rw- 1 root tty       2, 128 2007-03-15 11:07 ptyx0
crw-rw-rw- 1 root tty       2, 129 2007-03-15 11:07 ptyx1
crw-rw-rw- 1 root tty       2, 130 2007-03-15 11:07 ptyx2
crw-rw-rw- 1 root tty       2, 131 2007-03-15 11:07 ptyx3
crw-rw-rw- 1 root tty       2, 132 2007-03-15 11:07 ptyx4
crw-rw-rw- 1 root tty       2, 133 2007-03-15 11:07 ptyx5
crw-rw-rw- 1 root tty       2, 134 2007-03-15 11:07 ptyx6
crw-rw-rw- 1 root tty       2, 135 2007-03-15 11:07 ptyx7
crw-rw-rw- 1 root tty       2, 136 2007-03-15 11:07 ptyx8
crw-rw-rw- 1 root tty       2, 137 2007-03-15 11:07 ptyx9
crw-rw-rw- 1 root tty       2, 138 2007-03-15 11:07 ptyxa
crw-rw-rw- 1 root tty       2, 139 2007-03-15 11:07 ptyxb
crw-rw-rw- 1 root tty       2, 140 2007-03-15 11:07 ptyxc
crw-rw-rw- 1 root tty       2, 141 2007-03-15 11:07 ptyxd
crw-rw-rw- 1 root tty       2, 142 2007-03-15 11:07 ptyxe
crw-rw-rw- 1 root tty       2, 143 2007-03-15 11:07 ptyxf
crw-rw-rw- 1 root tty       2, 144 2007-03-15 11:07 ptyy0
crw-rw-rw- 1 root tty       2, 145 2007-03-15 11:07 ptyy1
crw-rw-rw- 1 root tty       2, 146 2007-03-15 11:07 ptyy2
crw-rw-rw- 1 root tty       2, 147 2007-03-15 11:07 ptyy3
crw-rw-rw- 1 root tty       2, 148 2007-03-15 11:07 ptyy4
crw-rw-rw- 1 root tty       2, 149 2007-03-15 11:07 ptyy5
crw-rw-rw- 1 root tty       2, 150 2007-03-15 11:07 ptyy6
crw-rw-rw- 1 root tty       2, 151 2007-03-15 11:07 ptyy7
crw-rw-rw- 1 root tty       2, 152 2007-03-15 11:07 ptyy8
crw-rw-rw- 1 root tty       2, 153 2007-03-15 11:07 ptyy9
crw-rw-rw- 1 root tty       2, 154 2007-03-15 11:07 ptyya
crw-rw-rw- 1 root tty       2, 155 2007-03-15 11:07 ptyyb
crw-rw-rw- 1 root tty       2, 156 2007-03-15 11:07 ptyyc
crw-rw-rw- 1 root tty       2, 157 2007-03-15 11:07 ptyyd
crw-rw-rw- 1 root tty       2, 158 2007-03-15 11:07 ptyye
crw-rw-rw- 1 root tty       2, 159 2007-03-15 11:07 ptyyf
crw-rw-rw- 1 root tty       2, 160 2007-03-15 11:07 ptyz0
crw-rw-rw- 1 root tty       2, 161 2007-03-15 11:07 ptyz1
crw-rw-rw- 1 root tty       2, 162 2007-03-15 11:07 ptyz2
crw-rw-rw- 1 root tty       2, 163 2007-03-15 11:07 ptyz3
crw-rw-rw- 1 root tty       2, 164 2007-03-15 11:07 ptyz4
crw-rw-rw- 1 root tty       2, 165 2007-03-15 11:07 ptyz5
crw-rw-rw- 1 root tty       2, 166 2007-03-15 11:07 ptyz6
crw-rw-rw- 1 root tty       2, 167 2007-03-15 11:07 ptyz7
crw-rw-rw- 1 root tty       2, 168 2007-03-15 11:07 ptyz8
crw-rw-rw- 1 root tty       2, 169 2007-03-15 11:07 ptyz9
crw-rw-rw- 1 root tty       2, 170 2007-03-15 11:07 ptyza
crw-rw-rw- 1 root tty       2, 171 2007-03-15 11:07 ptyzb
crw-rw-rw- 1 root tty       2, 172 2007-03-15 11:07 ptyzc
crw-rw-rw- 1 root tty       2, 173 2007-03-15 11:07 ptyzd
crw-rw-rw- 1 root tty       2, 174 2007-03-15 11:07 ptyze
crw-rw-rw- 1 root tty       2, 175 2007-03-15 11:07 ptyzf
brw-rw---- 1 root disk      1,   0 2007-03-15 11:07 ram0
brw-rw---- 1 root disk      1,   1 2007-03-15 11:07 ram1
brw-rw---- 1 root disk      1,  10 2007-03-15 11:07 ram10
brw-rw---- 1 root disk      1,  11 2007-03-15 11:07 ram11
brw-rw---- 1 root disk      1,  12 2007-03-15 11:07 ram12
brw-rw---- 1 root disk      1,  13 2007-03-15 11:07 ram13
brw-rw---- 1 root disk      1,  14 2007-03-15 11:07 ram14
brw-rw---- 1 root disk      1,  15 2007-03-15 11:07 ram15
brw-rw---- 1 root disk      1,   2 2007-03-15 11:07 ram2
brw-rw---- 1 root disk      1,   3 2007-03-15 11:07 ram3
brw-rw---- 1 root disk      1,   4 2007-03-15 11:07 ram4
brw-rw---- 1 root disk      1,   5 2007-03-15 11:07 ram5
brw-rw---- 1 root disk      1,   6 2007-03-15 11:07 ram6
brw-rw---- 1 root disk      1,   7 2007-03-15 11:07 ram7
brw-rw---- 1 root disk      1,   8 2007-03-15 11:07 ram8
brw-rw---- 1 root disk      1,   9 2007-03-15 11:07 ram9
crw-rw-rw- 1 root root      1,   8 2007-03-15 11:07 random
crw-rw---- 1 root audio    10, 135 2007-03-15 11:07 rtc
brw-rw---- 1 root plugdev   8,   0 2007-03-15 11:08 sda
brw-rw---- 1 root plugdev   8,   1 2007-03-15 11:08 sda1
crw-rw---- 1 root audio    14,   1 2007-03-15 11:07 sequencer
crw-rw---- 1 root audio    14,   8 2007-03-15 11:07 sequencer2
crw-rw---- 1 root root     21,   0 2007-03-15 11:08 sg0
drwxrwxrwt 2 root root          40 2007-03-15 11:07 shm
crw-rw---- 1 root root     10, 231 2007-03-15 11:07 snapshot
drwxr-xr-x 2 root root         240 2007-03-15 11:07 snd
lrwxrwxrwx 1 root root          24 2007-03-15 11:07 sndstat -> /proc/asound/oss/sndstat
lrwxrwxrwx 1 root root          15 2007-03-15 11:07 stderr -> /proc/self/fd/2
lrwxrwxrwx 1 root root          15 2007-03-15 11:07 stdin -> /proc/self/fd/0
lrwxrwxrwx 1 root root          15 2007-03-15 11:07 stdout -> /proc/self/fd/1
crw-rw-rw- 1 root root      5,   0 2007-03-15 11:07 tty
crw-rw---- 1 root root      4,   0 2007-03-15 11:07 tty0
crw------- 1 root root      4,   1 2007-03-15 11:08 tty1
crw-rw---- 1 root root      4,  10 2007-03-15 11:07 tty10
crw-rw---- 1 root root      4,  11 2007-03-15 11:07 tty11
crw-rw---- 1 root root      4,  12 2007-03-15 11:07 tty12
crw-rw---- 1 root root      4,  13 2007-03-15 11:07 tty13
crw-rw---- 1 root root      4,  14 2007-03-15 11:07 tty14
crw-rw---- 1 root root      4,  15 2007-03-15 11:07 tty15
crw-rw---- 1 root root      4,  16 2007-03-15 11:07 tty16
crw-rw---- 1 root root      4,  17 2007-03-15 11:07 tty17
crw-rw---- 1 root root      4,  18 2007-03-15 11:07 tty18
crw-rw---- 1 root root      4,  19 2007-03-15 11:07 tty19
crw------- 1 root root      4,   2 2007-03-15 11:08 tty2
crw-rw---- 1 root root      4,  20 2007-03-15 11:07 tty20
crw-rw---- 1 root root      4,  21 2007-03-15 11:07 tty21
crw-rw---- 1 root root      4,  22 2007-03-15 11:07 tty22
crw-rw---- 1 root root      4,  23 2007-03-15 11:07 tty23
crw-rw---- 1 root root      4,  24 2007-03-15 11:07 tty24
crw-rw---- 1 root root      4,  25 2007-03-15 11:07 tty25
crw-rw---- 1 root root      4,  26 2007-03-15 11:07 tty26
crw-rw---- 1 root root      4,  27 2007-03-15 11:07 tty27
crw-rw---- 1 root root      4,  28 2007-03-15 11:07 tty28
crw-rw---- 1 root root      4,  29 2007-03-15 11:07 tty29
crw------- 1 root root      4,   3 2007-03-15 11:08 tty3
crw-rw---- 1 root root      4,  30 2007-03-15 11:07 tty30
crw-rw---- 1 root root      4,  31 2007-03-15 11:07 tty31
crw-rw---- 1 root root      4,  32 2007-03-15 11:07 tty32
crw-rw---- 1 root root      4,  33 2007-03-15 11:07 tty33
crw-rw---- 1 root root      4,  34 2007-03-15 11:07 tty34
crw-rw---- 1 root root      4,  35 2007-03-15 11:07 tty35
crw-rw---- 1 root root      4,  36 2007-03-15 11:07 tty36
crw-rw---- 1 root root      4,  37 2007-03-15 11:07 tty37
crw-rw---- 1 root root      4,  38 2007-03-15 11:07 tty38
crw-rw---- 1 root root      4,  39 2007-03-15 11:07 tty39
crw------- 1 root root      4,   4 2007-03-15 11:08 tty4
crw-rw---- 1 root root      4,  40 2007-03-15 11:07 tty40
crw-rw---- 1 root root      4,  41 2007-03-15 11:07 tty41
crw-rw---- 1 root root      4,  42 2007-03-15 11:07 tty42
crw-rw---- 1 root root      4,  43 2007-03-15 11:07 tty43
crw-rw---- 1 root root      4,  44 2007-03-15 11:07 tty44
crw-rw---- 1 root root      4,  45 2007-03-15 11:07 tty45
crw-rw---- 1 root root      4,  46 2007-03-15 11:07 tty46
crw-rw---- 1 root root      4,  47 2007-03-15 11:07 tty47
crw-rw---- 1 root root      4,  48 2007-03-15 11:07 tty48
crw-rw---- 1 root root      4,  49 2007-03-15 11:07 tty49
crw------- 1 root root      4,   5 2007-03-15 11:08 tty5
crw-rw---- 1 root root      4,  50 2007-03-15 11:07 tty50
crw-rw---- 1 root root      4,  51 2007-03-15 11:07 tty51
crw-rw---- 1 root root      4,  52 2007-03-15 11:07 tty52
crw-rw---- 1 root root      4,  53 2007-03-15 11:07 tty53
crw-rw---- 1 root root      4,  54 2007-03-15 11:07 tty54
crw-rw---- 1 root root      4,  55 2007-03-15 11:07 tty55
crw-rw---- 1 root root      4,  56 2007-03-15 11:07 tty56
crw-rw---- 1 root root      4,  57 2007-03-15 11:07 tty57
crw-rw---- 1 root root      4,  58 2007-03-15 11:07 tty58
crw-rw---- 1 root root      4,  59 2007-03-15 11:07 tty59
crw------- 1 root root      4,   6 2007-03-15 11:08 tty6
crw-rw---- 1 root root      4,  60 2007-03-15 11:07 tty60
crw-rw---- 1 root root      4,  61 2007-03-15 11:07 tty61
crw-rw---- 1 root root      4,  62 2007-03-15 11:07 tty62
crw-rw---- 1 root root      4,  63 2007-03-15 11:07 tty63
crw-rw---- 1 root root      4,   7 2007-03-15 11:07 tty7
crw-rw---- 1 root root      4,   8 2007-03-15 11:08 tty8
crw-rw---- 1 root root      4,   9 2007-03-15 11:07 tty9
crw-rw-rw- 1 root tty       3, 176 2007-03-15 11:07 ttya0
crw-rw-rw- 1 root tty       3, 177 2007-03-15 11:07 ttya1
crw-rw-rw- 1 root tty       3, 178 2007-03-15 11:07 ttya2
crw-rw-rw- 1 root tty       3, 179 2007-03-15 11:07 ttya3
crw-rw-rw- 1 root tty       3, 180 2007-03-15 11:07 ttya4
crw-rw-rw- 1 root tty       3, 181 2007-03-15 11:07 ttya5
crw-rw-rw- 1 root tty       3, 182 2007-03-15 11:07 ttya6
crw-rw-rw- 1 root tty       3, 183 2007-03-15 11:07 ttya7
crw-rw-rw- 1 root tty       3, 184 2007-03-15 11:07 ttya8
crw-rw-rw- 1 root tty       3, 185 2007-03-15 11:07 ttya9
crw-rw-rw- 1 root tty       3, 186 2007-03-15 11:07 ttyaa
crw-rw-rw- 1 root tty       3, 187 2007-03-15 11:07 ttyab
crw-rw-rw- 1 root tty       3, 188 2007-03-15 11:07 ttyac
crw-rw-rw- 1 root tty       3, 189 2007-03-15 11:07 ttyad
crw-rw-rw- 1 root tty       3, 190 2007-03-15 11:07 ttyae
crw-rw-rw- 1 root tty       3, 191 2007-03-15 11:07 ttyaf
crw-rw-rw- 1 root tty       3, 192 2007-03-15 11:07 ttyb0
crw-rw-rw- 1 root tty       3, 193 2007-03-15 11:07 ttyb1
crw-rw-rw- 1 root tty       3, 194 2007-03-15 11:07 ttyb2
crw-rw-rw- 1 root tty       3, 195 2007-03-15 11:07 ttyb3
crw-rw-rw- 1 root tty       3, 196 2007-03-15 11:07 ttyb4
crw-rw-rw- 1 root tty       3, 197 2007-03-15 11:07 ttyb5
crw-rw-rw- 1 root tty       3, 198 2007-03-15 11:07 ttyb6
crw-rw-rw- 1 root tty       3, 199 2007-03-15 11:07 ttyb7
crw-rw-rw- 1 root tty       3, 200 2007-03-15 11:07 ttyb8
crw-rw-rw- 1 root tty       3, 201 2007-03-15 11:07 ttyb9
crw-rw-rw- 1 root tty       3, 202 2007-03-15 11:07 ttyba
crw-rw-rw- 1 root tty       3, 203 2007-03-15 11:07 ttybb
crw-rw-rw- 1 root tty       3, 204 2007-03-15 11:07 ttybc
crw-rw-rw- 1 root tty       3, 205 2007-03-15 11:07 ttybd
crw-rw-rw- 1 root tty       3, 206 2007-03-15 11:07 ttybe
crw-rw-rw- 1 root tty       3, 207 2007-03-15 11:07 ttybf
crw-rw-rw- 1 root tty       3, 208 2007-03-15 11:07 ttyc0
crw-rw-rw- 1 root tty       3, 209 2007-03-15 11:07 ttyc1
crw-rw-rw- 1 root tty       3, 210 2007-03-15 11:07 ttyc2
crw-rw-rw- 1 root tty       3, 211 2007-03-15 11:07 ttyc3
crw-rw-rw- 1 root tty       3, 212 2007-03-15 11:07 ttyc4
crw-rw-rw- 1 root tty       3, 213 2007-03-15 11:07 ttyc5
crw-rw-rw- 1 root tty       3, 214 2007-03-15 11:07 ttyc6
crw-rw-rw- 1 root tty       3, 215 2007-03-15 11:07 ttyc7
crw-rw-rw- 1 root tty       3, 216 2007-03-15 11:07 ttyc8
crw-rw-rw- 1 root tty       3, 217 2007-03-15 11:07 ttyc9
crw-rw-rw- 1 root tty       3, 218 2007-03-15 11:07 ttyca
crw-rw-rw- 1 root tty       3, 219 2007-03-15 11:07 ttycb
crw-rw-rw- 1 root tty       3, 220 2007-03-15 11:07 ttycc
crw-rw-rw- 1 root tty       3, 221 2007-03-15 11:07 ttycd
crw-rw-rw- 1 root tty       3, 222 2007-03-15 11:07 ttyce
crw-rw-rw- 1 root tty       3, 223 2007-03-15 11:07 ttycf
crw-rw-rw- 1 root tty       3, 224 2007-03-15 11:07 ttyd0
crw-rw-rw- 1 root tty       3, 225 2007-03-15 11:07 ttyd1
crw-rw-rw- 1 root tty       3, 226 2007-03-15 11:07 ttyd2
crw-rw-rw- 1 root tty       3, 227 2007-03-15 11:07 ttyd3
crw-rw-rw- 1 root tty       3, 228 2007-03-15 11:07 ttyd4
crw-rw-rw- 1 root tty       3, 229 2007-03-15 11:07 ttyd5
crw-rw-rw- 1 root tty       3, 230 2007-03-15 11:07 ttyd6
crw-rw-rw- 1 root tty       3, 231 2007-03-15 11:07 ttyd7
crw-rw-rw- 1 root tty       3, 232 2007-03-15 11:07 ttyd8
crw-rw-rw- 1 root tty       3, 233 2007-03-15 11:07 ttyd9
crw-rw-rw- 1 root tty       3, 234 2007-03-15 11:07 ttyda
crw-rw-rw- 1 root tty       3, 235 2007-03-15 11:07 ttydb
crw-rw-rw- 1 root tty       3, 236 2007-03-15 11:07 ttydc
crw-rw-rw- 1 root tty       3, 237 2007-03-15 11:07 ttydd
crw-rw-rw- 1 root tty       3, 238 2007-03-15 11:07 ttyde
crw-rw-rw- 1 root tty       3, 239 2007-03-15 11:07 ttydf
crw-rw-rw- 1 root tty       3, 240 2007-03-15 11:07 ttye0
crw-rw-rw- 1 root tty       3, 241 2007-03-15 11:07 ttye1
crw-rw-rw- 1 root tty       3, 242 2007-03-15 11:07 ttye2
crw-rw-rw- 1 root tty       3, 243 2007-03-15 11:07 ttye3
crw-rw-rw- 1 root tty       3, 244 2007-03-15 11:07 ttye4
crw-rw-rw- 1 root tty       3, 245 2007-03-15 11:07 ttye5
crw-rw-rw- 1 root tty       3, 246 2007-03-15 11:07 ttye6
crw-rw-rw- 1 root tty       3, 247 2007-03-15 11:07 ttye7
crw-rw-rw- 1 root tty       3, 248 2007-03-15 11:07 ttye8
crw-rw-rw- 1 root tty       3, 249 2007-03-15 11:07 ttye9
crw-rw-rw- 1 root tty       3, 250 2007-03-15 11:07 ttyea
crw-rw-rw- 1 root tty       3, 251 2007-03-15 11:07 ttyeb
crw-rw-rw- 1 root tty       3, 252 2007-03-15 11:07 ttyec
crw-rw-rw- 1 root tty       3, 253 2007-03-15 11:07 ttyed
crw-rw-rw- 1 root tty       3, 254 2007-03-15 11:07 ttyee
crw-rw-rw- 1 root tty       3, 255 2007-03-15 11:07 ttyef
crw-rw-rw- 1 root tty       3,   0 2007-03-15 11:07 ttyp0
crw-rw-rw- 1 root tty       3,   1 2007-03-15 11:07 ttyp1
crw-rw-rw- 1 root tty       3,   2 2007-03-15 11:07 ttyp2
crw-rw-rw- 1 root tty       3,   3 2007-03-15 11:07 ttyp3
crw-rw-rw- 1 root tty       3,   4 2007-03-15 11:07 ttyp4
crw-rw-rw- 1 root tty       3,   5 2007-03-15 11:07 ttyp5
crw-rw-rw- 1 root tty       3,   6 2007-03-15 11:07 ttyp6
crw-rw-rw- 1 root tty       3,   7 2007-03-15 11:07 ttyp7
crw-rw-rw- 1 root tty       3,   8 2007-03-15 11:07 ttyp8
crw-rw-rw- 1 root tty       3,   9 2007-03-15 11:07 ttyp9
crw-rw-rw- 1 root tty       3,  10 2007-03-15 11:07 ttypa
crw-rw-rw- 1 root tty       3,  11 2007-03-15 11:07 ttypb
crw-rw-rw- 1 root tty       3,  12 2007-03-15 11:07 ttypc
crw-rw-rw- 1 root tty       3,  13 2007-03-15 11:07 ttypd
crw-rw-rw- 1 root tty       3,  14 2007-03-15 11:07 ttype
crw-rw-rw- 1 root tty       3,  15 2007-03-15 11:07 ttypf
crw-rw-rw- 1 root tty       3,  16 2007-03-15 11:07 ttyq0
crw-rw-rw- 1 root tty       3,  17 2007-03-15 11:07 ttyq1
crw-rw-rw- 1 root tty       3,  18 2007-03-15 11:07 ttyq2
crw-rw-rw- 1 root tty       3,  19 2007-03-15 11:07 ttyq3
crw-rw-rw- 1 root tty       3,  20 2007-03-15 11:07 ttyq4
crw-rw-rw- 1 root tty       3,  21 2007-03-15 11:07 ttyq5
crw-rw-rw- 1 root tty       3,  22 2007-03-15 11:07 ttyq6
crw-rw-rw- 1 root tty       3,  23 2007-03-15 11:07 ttyq7
crw-rw-rw- 1 root tty       3,  24 2007-03-15 11:07 ttyq8
crw-rw-rw- 1 root tty       3,  25 2007-03-15 11:07 ttyq9
crw-rw-rw- 1 root tty       3,  26 2007-03-15 11:07 ttyqa
crw-rw-rw- 1 root tty       3,  27 2007-03-15 11:07 ttyqb
crw-rw-rw- 1 root tty       3,  28 2007-03-15 11:07 ttyqc
crw-rw-rw- 1 root tty       3,  29 2007-03-15 11:07 ttyqd
crw-rw-rw- 1 root tty       3,  30 2007-03-15 11:07 ttyqe
crw-rw-rw- 1 root tty       3,  31 2007-03-15 11:07 ttyqf
crw-rw-rw- 1 root tty       3,  32 2007-03-15 11:07 ttyr0
crw-rw-rw- 1 root tty       3,  33 2007-03-15 11:07 ttyr1
crw-rw-rw- 1 root tty       3,  34 2007-03-15 11:07 ttyr2
crw-rw-rw- 1 root tty       3,  35 2007-03-15 11:07 ttyr3
crw-rw-rw- 1 root tty       3,  36 2007-03-15 11:07 ttyr4
crw-rw-rw- 1 root tty       3,  37 2007-03-15 11:07 ttyr5
crw-rw-rw- 1 root tty       3,  38 2007-03-15 11:07 ttyr6
crw-rw-rw- 1 root tty       3,  39 2007-03-15 11:07 ttyr7
crw-rw-rw- 1 root tty       3,  40 2007-03-15 11:07 ttyr8
crw-rw-rw- 1 root tty       3,  41 2007-03-15 11:07 ttyr9
crw-rw-rw- 1 root tty       3,  42 2007-03-15 11:07 ttyra
crw-rw-rw- 1 root tty       3,  43 2007-03-15 11:07 ttyrb
crw-rw-rw- 1 root tty       3,  44 2007-03-15 11:07 ttyrc
crw-rw-rw- 1 root tty       3,  45 2007-03-15 11:07 ttyrd
crw-rw-rw- 1 root tty       3,  46 2007-03-15 11:07 ttyre
crw-rw-rw- 1 root tty       3,  47 2007-03-15 11:07 ttyrf
crw-rw-rw- 1 root tty       3,  48 2007-03-15 11:07 ttys0
crw-rw---- 1 root dialout   4,  64 2007-03-15 11:07 ttyS0
crw-rw-rw- 1 root tty       3,  49 2007-03-15 11:07 ttys1
crw-rw---- 1 root dialout   4,  65 2007-03-15 11:07 ttyS1
crw-rw-rw- 1 root tty       3,  50 2007-03-15 11:07 ttys2
crw-rw---- 1 root dialout   4,  66 2007-03-15 11:07 ttyS2
crw-rw-rw- 1 root tty       3,  51 2007-03-15 11:07 ttys3
crw-rw---- 1 root dialout   4,  67 2007-03-15 11:07 ttyS3
crw-rw-rw- 1 root tty       3,  52 2007-03-15 11:07 ttys4
crw-rw-rw- 1 root tty       3,  53 2007-03-15 11:07 ttys5
crw-rw-rw- 1 root tty       3,  54 2007-03-15 11:07 ttys6
crw-rw-rw- 1 root tty       3,  55 2007-03-15 11:07 ttys7
crw-rw-rw- 1 root tty       3,  56 2007-03-15 11:07 ttys8
crw-rw-rw- 1 root tty       3,  57 2007-03-15 11:07 ttys9
crw-rw-rw- 1 root tty       3,  58 2007-03-15 11:07 ttysa
crw-rw-rw- 1 root tty       3,  59 2007-03-15 11:07 ttysb
crw-rw-rw- 1 root tty       3,  60 2007-03-15 11:07 ttysc
crw-rw-rw- 1 root tty       3,  61 2007-03-15 11:07 ttysd
crw-rw-rw- 1 root tty       3,  62 2007-03-15 11:07 ttyse
crw-rw-rw- 1 root tty       3,  63 2007-03-15 11:07 ttysf
crw-rw-rw- 1 root tty       3,  64 2007-03-15 11:07 ttyt0
crw-rw-rw- 1 root tty       3,  65 2007-03-15 11:07 ttyt1
crw-rw-rw- 1 root tty       3,  66 2007-03-15 11:07 ttyt2
crw-rw-rw- 1 root tty       3,  67 2007-03-15 11:07 ttyt3
crw-rw-rw- 1 root tty       3,  68 2007-03-15 11:07 ttyt4
crw-rw-rw- 1 root tty       3,  69 2007-03-15 11:07 ttyt5
crw-rw-rw- 1 root tty       3,  70 2007-03-15 11:07 ttyt6
crw-rw-rw- 1 root tty       3,  71 2007-03-15 11:07 ttyt7
crw-rw-rw- 1 root tty       3,  72 2007-03-15 11:07 ttyt8
crw-rw-rw- 1 root tty       3,  73 2007-03-15 11:07 ttyt9
crw-rw-rw- 1 root tty       3,  74 2007-03-15 11:07 ttyta
crw-rw-rw- 1 root tty       3,  75 2007-03-15 11:07 ttytb
crw-rw-rw- 1 root tty       3,  76 2007-03-15 11:07 ttytc
crw-rw-rw- 1 root tty       3,  77 2007-03-15 11:07 ttytd
crw-rw-rw- 1 root tty       3,  78 2007-03-15 11:07 ttyte
crw-rw-rw- 1 root tty       3,  79 2007-03-15 11:07 ttytf
crw-rw-rw- 1 root tty       3,  80 2007-03-15 11:07 ttyu0
crw-rw-rw- 1 root tty       3,  81 2007-03-15 11:07 ttyu1
crw-rw-rw- 1 root tty       3,  82 2007-03-15 11:07 ttyu2
crw-rw-rw- 1 root tty       3,  83 2007-03-15 11:07 ttyu3
crw-rw-rw- 1 root tty       3,  84 2007-03-15 11:07 ttyu4
crw-rw-rw- 1 root tty       3,  85 2007-03-15 11:07 ttyu5
crw-rw-rw- 1 root tty       3,  86 2007-03-15 11:07 ttyu6
crw-rw-rw- 1 root tty       3,  87 2007-03-15 11:07 ttyu7
crw-rw-rw- 1 root tty       3,  88 2007-03-15 11:07 ttyu8
crw-rw-rw- 1 root tty       3,  89 2007-03-15 11:07 ttyu9
crw-rw-rw- 1 root tty       3,  90 2007-03-15 11:07 ttyua
crw-rw-rw- 1 root tty       3,  91 2007-03-15 11:07 ttyub
crw-rw-rw- 1 root tty       3,  92 2007-03-15 11:07 ttyuc
crw-rw-rw- 1 root tty       3,  93 2007-03-15 11:07 ttyud
crw-rw-rw- 1 root tty       3,  94 2007-03-15 11:07 ttyue
crw-rw-rw- 1 root tty       3,  95 2007-03-15 11:07 ttyuf
crw-rw-rw- 1 root tty       3,  96 2007-03-15 11:07 ttyv0
crw-rw-rw- 1 root tty       3,  97 2007-03-15 11:07 ttyv1
crw-rw-rw- 1 root tty       3,  98 2007-03-15 11:07 ttyv2
crw-rw-rw- 1 root tty       3,  99 2007-03-15 11:07 ttyv3
crw-rw-rw- 1 root tty       3, 100 2007-03-15 11:07 ttyv4
crw-rw-rw- 1 root tty       3, 101 2007-03-15 11:07 ttyv5
crw-rw-rw- 1 root tty       3, 102 2007-03-15 11:07 ttyv6
crw-rw-rw- 1 root tty       3, 103 2007-03-15 11:07 ttyv7
crw-rw-rw- 1 root tty       3, 104 2007-03-15 11:07 ttyv8
crw-rw-rw- 1 root tty       3, 105 2007-03-15 11:07 ttyv9
crw-rw-rw- 1 root tty       3, 106 2007-03-15 11:07 ttyva
crw-rw-rw- 1 root tty       3, 107 2007-03-15 11:07 ttyvb
crw-rw-rw- 1 root tty       3, 108 2007-03-15 11:07 ttyvc
crw-rw-rw- 1 root tty       3, 109 2007-03-15 11:07 ttyvd
crw-rw-rw- 1 root tty       3, 110 2007-03-15 11:07 ttyve
crw-rw-rw- 1 root tty       3, 111 2007-03-15 11:07 ttyvf
crw-rw-rw- 1 root tty       3, 112 2007-03-15 11:07 ttyw0
crw-rw-rw- 1 root tty       3, 113 2007-03-15 11:07 ttyw1
crw-rw-rw- 1 root tty       3, 114 2007-03-15 11:07 ttyw2
crw-rw-rw- 1 root tty       3, 115 2007-03-15 11:07 ttyw3
crw-rw-rw- 1 root tty       3, 116 2007-03-15 11:07 ttyw4
crw-rw-rw- 1 root tty       3, 117 2007-03-15 11:07 ttyw5
crw-rw-rw- 1 root tty       3, 118 2007-03-15 11:07 ttyw6
crw-rw-rw- 1 root tty       3, 119 2007-03-15 11:07 ttyw7
crw-rw-rw- 1 root tty       3, 120 2007-03-15 11:07 ttyw8
crw-rw-rw- 1 root tty       3, 121 2007-03-15 11:07 ttyw9
crw-rw-rw- 1 root tty       3, 122 2007-03-15 11:07 ttywa
crw-rw-rw- 1 root tty       3, 123 2007-03-15 11:07 ttywb
crw-rw-rw- 1 root tty       3, 124 2007-03-15 11:07 ttywc
crw-rw-rw- 1 root tty       3, 125 2007-03-15 11:07 ttywd
crw-rw-rw- 1 root tty       3, 126 2007-03-15 11:07 ttywe
crw-rw-rw- 1 root tty       3, 127 2007-03-15 11:07 ttywf
crw-rw-rw- 1 root tty       3, 128 2007-03-15 11:07 ttyx0
crw-rw-rw- 1 root tty       3, 129 2007-03-15 11:07 ttyx1
crw-rw-rw- 1 root tty       3, 130 2007-03-15 11:07 ttyx2
crw-rw-rw- 1 root tty       3, 131 2007-03-15 11:07 ttyx3
crw-rw-rw- 1 root tty       3, 132 2007-03-15 11:07 ttyx4
crw-rw-rw- 1 root tty       3, 133 2007-03-15 11:07 ttyx5
crw-rw-rw- 1 root tty       3, 134 2007-03-15 11:07 ttyx6
crw-rw-rw- 1 root tty       3, 135 2007-03-15 11:07 ttyx7
crw-rw-rw- 1 root tty       3, 136 2007-03-15 11:07 ttyx8
crw-rw-rw- 1 root tty       3, 137 2007-03-15 11:07 ttyx9
crw-rw-rw- 1 root tty       3, 138 2007-03-15 11:07 ttyxa
crw-rw-rw- 1 root tty       3, 139 2007-03-15 11:07 ttyxb
crw-rw-rw- 1 root tty       3, 140 2007-03-15 11:07 ttyxc
crw-rw-rw- 1 root tty       3, 141 2007-03-15 11:07 ttyxd
crw-rw-rw- 1 root tty       3, 142 2007-03-15 11:07 ttyxe
crw-rw-rw- 1 root tty       3, 143 2007-03-15 11:07 ttyxf
crw-rw-rw- 1 root tty       3, 144 2007-03-15 11:07 ttyy0
crw-rw-rw- 1 root tty       3, 145 2007-03-15 11:07 ttyy1
crw-rw-rw- 1 root tty       3, 146 2007-03-15 11:07 ttyy2
crw-rw-rw- 1 root tty       3, 147 2007-03-15 11:07 ttyy3
crw-rw-rw- 1 root tty       3, 148 2007-03-15 11:07 ttyy4
crw-rw-rw- 1 root tty       3, 149 2007-03-15 11:07 ttyy5
crw-rw-rw- 1 root tty       3, 150 2007-03-15 11:07 ttyy6
crw-rw-rw- 1 root tty       3, 151 2007-03-15 11:07 ttyy7
crw-rw-rw- 1 root tty       3, 152 2007-03-15 11:07 ttyy8
crw-rw-rw- 1 root tty       3, 153 2007-03-15 11:07 ttyy9
crw-rw-rw- 1 root tty       3, 154 2007-03-15 11:07 ttyya
crw-rw-rw- 1 root tty       3, 155 2007-03-15 11:07 ttyyb
crw-rw-rw- 1 root tty       3, 156 2007-03-15 11:07 ttyyc
crw-rw-rw- 1 root tty       3, 157 2007-03-15 11:07 ttyyd
crw-rw-rw- 1 root tty       3, 158 2007-03-15 11:07 ttyye
crw-rw-rw- 1 root tty       3, 159 2007-03-15 11:07 ttyyf
crw-rw-rw- 1 root tty       3, 160 2007-03-15 11:07 ttyz0
crw-rw-rw- 1 root tty       3, 161 2007-03-15 11:07 ttyz1
crw-rw-rw- 1 root tty       3, 162 2007-03-15 11:07 ttyz2
crw-rw-rw- 1 root tty       3, 163 2007-03-15 11:07 ttyz3
crw-rw-rw- 1 root tty       3, 164 2007-03-15 11:07 ttyz4
crw-rw-rw- 1 root tty       3, 165 2007-03-15 11:07 ttyz5
crw-rw-rw- 1 root tty       3, 166 2007-03-15 11:07 ttyz6
crw-rw-rw- 1 root tty       3, 167 2007-03-15 11:07 ttyz7
crw-rw-rw- 1 root tty       3, 168 2007-03-15 11:07 ttyz8
crw-rw-rw- 1 root tty       3, 169 2007-03-15 11:07 ttyz9
crw-rw-rw- 1 root tty       3, 170 2007-03-15 11:07 ttyza
crw-rw-rw- 1 root tty       3, 171 2007-03-15 11:07 ttyzb
crw-rw-rw- 1 root tty       3, 172 2007-03-15 11:07 ttyzc
crw-rw-rw- 1 root tty       3, 173 2007-03-15 11:07 ttyzd
crw-rw-rw- 1 root tty       3, 174 2007-03-15 11:07 ttyze
crw-rw-rw- 1 root tty       3, 175 2007-03-15 11:07 ttyzf
```
```
crw-rw-rw- 1 root root      1,   9 2007-03-16 15:08 urandom
crw-rw---- 1 root root      7,   0 2007-03-16 15:07 vcs
crw-rw---- 1 root root      7,   1 2007-03-16 15:07 vcs1
crw-rw---- 1 root root      7,   2 2007-03-16 15:08 vcs2
crw-rw---- 1 root root      7,   3 2007-03-16 15:08 vcs3
crw-rw---- 1 root root      7,   4 2007-03-16 15:08 vcs4
crw-rw---- 1 root root      7,   5 2007-03-16 15:08 vcs5
crw-rw---- 1 root root      7,   6 2007-03-16 15:08 vcs6
crw-rw---- 1 root root      7,   7 2007-03-16 15:08 vcs7
crw-rw---- 1 root root      7,   8 2007-03-16 15:07 vcs8
crw-rw---- 1 root root      7, 128 2007-03-16 15:07 vcsa
crw-rw---- 1 root root      7, 129 2007-03-16 15:07 vcsa1
crw-rw---- 1 root root      7, 130 2007-03-16 15:08 vcsa2
crw-rw---- 1 root root      7, 131 2007-03-16 15:08 vcsa3
crw-rw---- 1 root root      7, 132 2007-03-16 15:08 vcsa4
crw-rw---- 1 root root      7, 133 2007-03-16 15:08 vcsa5
crw-rw---- 1 root root      7, 134 2007-03-16 15:08 vcsa6
crw-rw---- 1 root root      7, 135 2007-03-16 15:08 vcsa7
crw-rw---- 1 root root      7, 136 2007-03-16 15:07 vcsa8
prw-r----- 1 root adm            0 2007-03-17 12:50 xconsole
crw-rw-rw- 1 root root      1,   5 2007-03-16 15:07 zero
snyper64@Snyper64-laptop:~$
```

---

### Post by Snyper64 on 2007-03-16
bump

---

### Post by 351W on 2007-03-16
It cut off half the listing because it's too long. Type "ls /dev" and post that instead.

---

### Post by Snyper64 on 2007-03-16
```
snyper64@Snyper64-laptop:~$ ls /dev
acpi       ptybe  ptyq9  ptyv4  ptyzf       tty50  ttyd9  ttys2  ttywb
adsp       ptybf  ptyqa  ptyv5  ram0        tty51  ttyda  ttyS2  ttywc
agpgart    ptyc0  ptyqb  ptyv6  ram1        tty52  ttydb  ttys3  ttywd
audio      ptyc1  ptyqc  ptyv7  ram10       tty53  ttydc  ttyS3  ttywe
audio1     ptyc2  ptyqd  ptyv8  ram11       tty54  ttydd  ttys4  ttywf
bus        ptyc3  ptyqe  ptyv9  ram12       tty55  ttyde  ttys5  ttyx0
cdrom      ptyc4  ptyqf  ptyva  ram13       tty56  ttydf  ttys6  ttyx1
cdrw       ptyc5  ptyr0  ptyvb  ram14       tty57  ttye0  ttys7  ttyx2
console    ptyc6  ptyr1  ptyvc  ram15       tty58  ttye1  ttys8  ttyx3
core       ptyc7  ptyr2  ptyvd  ram2        tty59  ttye2  ttys9  ttyx4
disk       ptyc8  ptyr3  ptyve  ram3        tty6   ttye3  ttysa  ttyx5
dsp        ptyc9  ptyr4  ptyvf  ram4        tty60  ttye4  ttysb  ttyx6
dsp1       ptyca  ptyr5  ptyw0  ram5        tty61  ttye5  ttysc  ttyx7
dvd        ptycb  ptyr6  ptyw1  ram6        tty62  ttye6  ttysd  ttyx8
fb0        ptycc  ptyr7  ptyw2  ram7        tty63  ttye7  ttyse  ttyx9
fd         ptycd  ptyr8  ptyw3  ram8        tty7   ttye8  ttysf  ttyxa
full       ptyce  ptyr9  ptyw4  ram9        tty8   ttye9  ttyt0  ttyxb
fuse       ptycf  ptyra  ptyw5  random      tty9   ttyea  ttyt1  ttyxc
hda        ptyd0  ptyrb  ptyw6  rtc         ttya0  ttyeb  ttyt2  ttyxd
hda1       ptyd1  ptyrc  ptyw7  sequencer   ttya1  ttyec  ttyt3  ttyxe
hda2       ptyd2  ptyrd  ptyw8  sequencer2  ttya2  ttyed  ttyt4  ttyxf
hda5       ptyd3  ptyre  ptyw9  shm         ttya3  ttyee  ttyt5  ttyy0
hdc        ptyd4  ptyrf  ptywa  snapshot    ttya4  ttyef  ttyt6  ttyy1
hpet       ptyd5  ptys0  ptywb  snd         ttya5  ttyp0  ttyt7  ttyy2
initctl    ptyd6  ptys1  ptywc  sndstat     ttya6  ttyp1  ttyt8  ttyy3
input      ptyd7  ptys2  ptywd  stderr      ttya7  ttyp2  ttyt9  ttyy4
kmem       ptyd8  ptys3  ptywe  stdin       ttya8  ttyp3  ttyta  ttyy5
kmsg       ptyd9  ptys4  ptywf  stdout      ttya9  ttyp4  ttytb  ttyy6
log        ptyda  ptys5  ptyx0  tty         ttyaa  ttyp5  ttytc  ttyy7
loop0      ptydb  ptys6  ptyx1  tty0        ttyab  ttyp6  ttytd  ttyy8
lp0        ptydc  ptys7  ptyx2  tty1        ttyac  ttyp7  ttyte  ttyy9
MAKEDEV    ptydd  ptys8  ptyx3  tty10       ttyad  ttyp8  ttytf  ttyya
mcelog     ptyde  ptys9  ptyx4  tty11       ttyae  ttyp9  ttyu0  ttyyb
mem        ptydf  ptysa  ptyx5  tty12       ttyaf  ttypa  ttyu1  ttyyc
mixer      ptye0  ptysb  ptyx6  tty13       ttyb0  ttypb  ttyu2  ttyyd
mixer1     ptye1  ptysc  ptyx7  tty14       ttyb1  ttypc  ttyu3  ttyye
net        ptye2  ptysd  ptyx8  tty15       ttyb2  ttypd  ttyu4  ttyyf
null       ptye3  ptyse  ptyx9  tty16       ttyb3  ttype  ttyu5  ttyz0
nvidia0    ptye4  ptysf  ptyxa  tty17       ttyb4  ttypf  ttyu6  ttyz1
nvidiactl  ptye5  ptyt0  ptyxb  tty18       ttyb5  ttyq0  ttyu7  ttyz2
port       ptye6  ptyt1  ptyxc  tty19       ttyb6  ttyq1  ttyu8  ttyz3
ppp        ptye7  ptyt2  ptyxd  tty2        ttyb7  ttyq2  ttyu9  ttyz4
psaux      ptye8  ptyt3  ptyxe  tty20       ttyb8  ttyq3  ttyua  ttyz5
ptmx       ptye9  ptyt4  ptyxf  tty21       ttyb9  ttyq4  ttyub  ttyz6
pts        ptyea  ptyt5  ptyy0  tty22       ttyba  ttyq5  ttyuc  ttyz7
ptya0      ptyeb  ptyt6  ptyy1  tty23       ttybb  ttyq6  ttyud  ttyz8
ptya1      ptyec  ptyt7  ptyy2  tty24       ttybc  ttyq7  ttyue  ttyz9
ptya2      ptyed  ptyt8  ptyy3  tty25       ttybd  ttyq8  ttyuf  ttyza
ptya3      ptyee  ptyt9  ptyy4  tty26       ttybe  ttyq9  ttyv0  ttyzb
ptya4      ptyef  ptyta  ptyy5  tty27       ttybf  ttyqa  ttyv1  ttyzc
ptya5      ptyp0  ptytb  ptyy6  tty28       ttyc0  ttyqb  ttyv2  ttyzd
ptya6      ptyp1  ptytc  ptyy7  tty29       ttyc1  ttyqc  ttyv3  ttyze
ptya7      ptyp2  ptytd  ptyy8  tty3        ttyc2  ttyqd  ttyv4  ttyzf
ptya8      ptyp3  ptyte  ptyy9  tty30       ttyc3  ttyqe  ttyv5  urandom
ptya9      ptyp4  ptytf  ptyya  tty31       ttyc4  ttyqf  ttyv6  vcs
ptyaa      ptyp5  ptyu0  ptyyb  tty32       ttyc5  ttyr0  ttyv7  vcs1
ptyab      ptyp6  ptyu1  ptyyc  tty33       ttyc6  ttyr1  ttyv8  vcs2
ptyac      ptyp7  ptyu2  ptyyd  tty34       ttyc7  ttyr2  ttyv9  vcs3
ptyad      ptyp8  ptyu3  ptyye  tty35       ttyc8  ttyr3  ttyva  vcs4
ptyae      ptyp9  ptyu4  ptyyf  tty36       ttyc9  ttyr4  ttyvb  vcs5
ptyaf      ptypa  ptyu5  ptyz0  tty37       ttyca  ttyr5  ttyvc  vcs6
ptyb0      ptypb  ptyu6  ptyz1  tty38       ttycb  ttyr6  ttyvd  vcs7
ptyb1      ptypc  ptyu7  ptyz2  tty39       ttycc  ttyr7  ttyve  vcs8
ptyb2      ptypd  ptyu8  ptyz3  tty4        ttycd  ttyr8  ttyvf  vcsa
ptyb3      ptype  ptyu9  ptyz4  tty40       ttyce  ttyr9  ttyw0  vcsa1
ptyb4      ptypf  ptyua  ptyz5  tty41       ttycf  ttyra  ttyw1  vcsa2
ptyb5      ptyq0  ptyub  ptyz6  tty42       ttyd0  ttyrb  ttyw2  vcsa3
ptyb6      ptyq1  ptyuc  ptyz7  tty43       ttyd1  ttyrc  ttyw3  vcsa4
ptyb7      ptyq2  ptyud  ptyz8  tty44       ttyd2  ttyrd  ttyw4  vcsa5
ptyb8      ptyq3  ptyue  ptyz9  tty45       ttyd3  ttyre  ttyw5  vcsa6
ptyb9      ptyq4  ptyuf  ptyza  tty46       ttyd4  ttyrf  ttyw6  vcsa7
ptyba      ptyq5  ptyv0  ptyzb  tty47       ttyd5  ttys0  ttyw7  vcsa8
ptybb      ptyq6  ptyv1  ptyzc  tty48       ttyd6  ttyS0  ttyw8  xconsole
ptybc      ptyq7  ptyv2  ptyzd  tty49       ttyd7  ttys1  ttyw9  zero
ptybd      ptyq8  ptyv3  ptyze  tty5        ttyd8  ttyS1  ttywa
snyper64@Snyper64-laptop:~$ 
```

---

### Post by Snyper64 on 2007-03-17
I added the other half of the dev file to my previous post.

---

### Post by Snyper64 on 2007-03-23
> **Snyper64 said:**
> This what you wanted?

```
crw-rw-rw- 1 root tty       2,  54 2007-03-15 11:07 ptys6
crw-rw-rw- 1 root tty       2,  55 2007-03-15 11:07 ptys7
crw-rw-rw- 1 root tty       2,  56 2007-03-15 11:07 ptys8
crw-rw-rw- 1 root tty       2,  57 2007-03-15 11:07 ptys9
crw-rw-rw- 1 root tty       2,  58 2007-03-15 11:07 ptysa
crw-rw-rw- 1 root tty       2,  59 2007-03-15 11:07 ptysb
crw-rw-rw- 1 root tty       2,  60 2007-03-15 11:07 ptysc
crw-rw-rw- 1 root tty       2,  61 2007-03-15 11:07 ptysd
crw-rw-rw- 1 root tty       2,  62 2007-03-15 11:07 ptyse
crw-rw-rw- 1 root tty       2,  63 2007-03-15 11:07 ptysf
crw-rw-rw- 1 root tty       2,  64 2007-03-15 11:07 ptyt0
crw-rw-rw- 1 root tty       2,  65 2007-03-15 11:07 ptyt1
crw-rw-rw- 1 root tty       2,  66 2007-03-15 11:07 ptyt2
crw-rw-rw- 1 root tty       2,  67 2007-03-15 11:07 ptyt3
crw-rw-rw- 1 root tty       2,  68 2007-03-15 11:07 ptyt4
crw-rw-rw- 1 root tty       2,  69 2007-03-15 11:07 ptyt5
crw-rw-rw- 1 root tty       2,  70 2007-03-15 11:07 ptyt6
crw-rw-rw- 1 root tty       2,  71 2007-03-15 11:07 ptyt7
crw-rw-rw- 1 root tty       2,  72 2007-03-15 11:07 ptyt8
crw-rw-rw- 1 root tty       2,  73 2007-03-15 11:07 ptyt9
crw-rw-rw- 1 root tty       2,  74 2007-03-15 11:07 ptyta
crw-rw-rw- 1 root tty       2,  75 2007-03-15 11:07 ptytb
crw-rw-rw- 1 root tty       2,  76 2007-03-15 11:07 ptytc
crw-rw-rw- 1 root tty       2,  77 2007-03-15 11:07 ptytd
crw-rw-rw- 1 root tty       2,  78 2007-03-15 11:07 ptyte
crw-rw-rw- 1 root tty       2,  79 2007-03-15 11:07 ptytf
crw-rw-rw- 1 root tty       2,  80 2007-03-15 11:07 ptyu0
crw-rw-rw- 1 root tty       2,  81 2007-03-15 11:07 ptyu1
crw-rw-rw- 1 root tty       2,  82 2007-03-15 11:07 ptyu2
crw-rw-rw- 1 root tty       2,  83 2007-03-15 11:07 ptyu3
crw-rw-rw- 1 root tty       2,  84 2007-03-15 11:07 ptyu4
crw-rw-rw- 1 root tty       2,  85 2007-03-15 11:07 ptyu5
crw-rw-rw- 1 root tty       2,  86 2007-03-15 11:07 ptyu6
crw-rw-rw- 1 root tty       2,  87 2007-03-15 11:07 ptyu7
crw-rw-rw- 1 root tty       2,  88 2007-03-15 11:07 ptyu8
crw-rw-rw- 1 root tty       2,  89 2007-03-15 11:07 ptyu9
crw-rw-rw- 1 root tty       2,  90 2007-03-15 11:07 ptyua
crw-rw-rw- 1 root tty       2,  91 2007-03-15 11:07 ptyub
crw-rw-rw- 1 root tty       2,  92 2007-03-15 11:07 ptyuc
crw-rw-rw- 1 root tty       2,  93 2007-03-15 11:07 ptyud
crw-rw-rw- 1 root tty       2,  94 2007-03-15 11:07 ptyue
crw-rw-rw- 1 root tty       2,  95 2007-03-15 11:07 ptyuf
crw-rw-rw- 1 root tty       2,  96 2007-03-15 11:07 ptyv0
crw-rw-rw- 1 root tty       2,  97 2007-03-15 11:07 ptyv1
crw-rw-rw- 1 root tty       2,  98 2007-03-15 11:07 ptyv2
crw-rw-rw- 1 root tty       2,  99 2007-03-15 11:07 ptyv3
crw-rw-rw- 1 root tty       2, 100 2007-03-15 11:07 ptyv4
crw-rw-rw- 1 root tty       2, 101 2007-03-15 11:07 ptyv5
crw-rw-rw- 1 root tty       2, 102 2007-03-15 11:07 ptyv6
crw-rw-rw- 1 root tty       2, 103 2007-03-15 11:07 ptyv7
crw-rw-rw- 1 root tty       2, 104 2007-03-15 11:07 ptyv8
crw-rw-rw- 1 root tty       2, 105 2007-03-15 11:07 ptyv9
crw-rw-rw- 1 root tty       2, 106 2007-03-15 11:07 ptyva
crw-rw-rw- 1 root tty       2, 107 2007-03-15 11:07 ptyvb
crw-rw-rw- 1 root tty       2, 108 2007-03-15 11:07 ptyvc
crw-rw-rw- 1 root tty       2, 109 2007-03-15 11:07 ptyvd
crw-rw-rw- 1 root tty       2, 110 2007-03-15 11:07 ptyve
crw-rw-rw- 1 root tty       2, 111 2007-03-15 11:07 ptyvf
crw-rw-rw- 1 root tty       2, 112 2007-03-15 11:07 ptyw0
crw-rw-rw- 1 root tty       2, 113 2007-03-15 11:07 ptyw1
crw-rw-rw- 1 root tty       2, 114 2007-03-15 11:07 ptyw2
crw-rw-rw- 1 root tty       2, 115 2007-03-15 11:07 ptyw3
crw-rw-rw- 1 root tty       2, 116 2007-03-15 11:07 ptyw4
crw-rw-rw- 1 root tty       2, 117 2007-03-15 11:07 ptyw5
crw-rw-rw- 1 root tty       2, 118 2007-03-15 11:07 ptyw6
crw-rw-rw- 1 root tty       2, 119 2007-03-15 11:07 ptyw7
crw-rw-rw- 1 root tty       2, 120 2007-03-15 11:07 ptyw8
crw-rw-rw- 1 root tty       2, 121 2007-03-15 11:07 ptyw9
crw-rw-rw- 1 root tty       2, 122 2007-03-15 11:07 ptywa
crw-rw-rw- 1 root tty       2, 123 2007-03-15 11:07 ptywb
crw-rw-rw- 1 root tty       2, 124 2007-03-15 11:07 ptywc
crw-rw-rw- 1 root tty       2, 125 2007-03-15 11:07 ptywd
crw-rw-rw- 1 root tty       2, 126 2007-03-15 11:07 ptywe
crw-rw-rw- 1 root tty       2, 127 2007-03-15 11:07 ptywf
crw-rw-rw- 1 root tty       2, 128 2007-03-15 11:07 ptyx0
crw-rw-rw- 1 root tty       2, 129 2007-03-15 11:07 ptyx1
crw-rw-rw- 1 root tty       2, 130 2007-03-15 11:07 ptyx2
crw-rw-rw- 1 root tty       2, 131 2007-03-15 11:07 ptyx3
crw-rw-rw- 1 root tty       2, 132 2007-03-15 11:07 ptyx4
crw-rw-rw- 1 root tty       2, 133 2007-03-15 11:07 ptyx5
crw-rw-rw- 1 root tty       2, 134 2007-03-15 11:07 ptyx6
crw-rw-rw- 1 root tty       2, 135 2007-03-15 11:07 ptyx7
crw-rw-rw- 1 root tty       2, 136 2007-03-15 11:07 ptyx8
crw-rw-rw- 1 root tty       2, 137 2007-03-15 11:07 ptyx9
crw-rw-rw- 1 root tty       2, 138 2007-03-15 11:07 ptyxa
crw-rw-rw- 1 root tty       2, 139 2007-03-15 11:07 ptyxb
crw-rw-rw- 1 root tty       2, 140 2007-03-15 11:07 ptyxc
crw-rw-rw- 1 root tty       2, 141 2007-03-15 11:07 ptyxd
crw-rw-rw- 1 root tty       2, 142 2007-03-15 11:07 ptyxe
crw-rw-rw- 1 root tty       2, 143 2007-03-15 11:07 ptyxf
crw-rw-rw- 1 root tty       2, 144 2007-03-15 11:07 ptyy0
crw-rw-rw- 1 root tty       2, 145 2007-03-15 11:07 ptyy1
crw-rw-rw- 1 root tty       2, 146 2007-03-15 11:07 ptyy2
crw-rw-rw- 1 root tty       2, 147 2007-03-15 11:07 ptyy3
crw-rw-rw- 1 root tty       2, 148 2007-03-15 11:07 ptyy4
crw-rw-rw- 1 root tty       2, 149 2007-03-15 11:07 ptyy5
crw-rw-rw- 1 root tty       2, 150 2007-03-15 11:07 ptyy6
crw-rw-rw- 1 root tty       2, 151 2007-03-15 11:07 ptyy7
crw-rw-rw- 1 root tty       2, 152 2007-03-15 11:07 ptyy8
crw-rw-rw- 1 root tty       2, 153 2007-03-15 11:07 ptyy9
crw-rw-rw- 1 root tty       2, 154 2007-03-15 11:07 ptyya
crw-rw-rw- 1 root tty       2, 155 2007-03-15 11:07 ptyyb
crw-rw-rw- 1 root tty       2, 156 2007-03-15 11:07 ptyyc
crw-rw-rw- 1 root tty       2, 157 2007-03-15 11:07 ptyyd
crw-rw-rw- 1 root tty       2, 158 2007-03-15 11:07 ptyye
crw-rw-rw- 1 root tty       2, 159 2007-03-15 11:07 ptyyf
crw-rw-rw- 1 root tty       2, 160 2007-03-15 11:07 ptyz0
crw-rw-rw- 1 root tty       2, 161 2007-03-15 11:07 ptyz1
crw-rw-rw- 1 root tty       2, 162 2007-03-15 11:07 ptyz2
crw-rw-rw- 1 root tty       2, 163 2007-03-15 11:07 ptyz3
crw-rw-rw- 1 root tty       2, 164 2007-03-15 11:07 ptyz4
crw-rw-rw- 1 root tty       2, 165 2007-03-15 11:07 ptyz5
crw-rw-rw- 1 root tty       2, 166 2007-03-15 11:07 ptyz6
crw-rw-rw- 1 root tty       2, 167 2007-03-15 11:07 ptyz7
crw-rw-rw- 1 root tty       2, 168 2007-03-15 11:07 ptyz8
crw-rw-rw- 1 root tty       2, 169 2007-03-15 11:07 ptyz9
crw-rw-rw- 1 root tty       2, 170 2007-03-15 11:07 ptyza
crw-rw-rw- 1 root tty       2, 171 2007-03-15 11:07 ptyzb
crw-rw-rw- 1 root tty       2, 172 2007-03-15 11:07 ptyzc
crw-rw-rw- 1 root tty       2, 173 2007-03-15 11:07 ptyzd
crw-rw-rw- 1 root tty       2, 174 2007-03-15 11:07 ptyze
crw-rw-rw- 1 root tty       2, 175 2007-03-15 11:07 ptyzf
brw-rw---- 1 root disk      1,   0 2007-03-15 11:07 ram0
brw-rw---- 1 root disk      1,   1 2007-03-15 11:07 ram1
brw-rw---- 1 root disk      1,  10 2007-03-15 11:07 ram10
brw-rw---- 1 root disk      1,  11 2007-03-15 11:07 ram11
brw-rw---- 1 root disk      1,  12 2007-03-15 11:07 ram12
brw-rw---- 1 root disk      1,  13 2007-03-15 11:07 ram13
brw-rw---- 1 root disk      1,  14 2007-03-15 11:07 ram14
brw-rw---- 1 root disk      1,  15 2007-03-15 11:07 ram15
brw-rw---- 1 root disk      1,   2 2007-03-15 11:07 ram2
brw-rw---- 1 root disk      1,   3 2007-03-15 11:07 ram3
brw-rw---- 1 root disk      1,   4 2007-03-15 11:07 ram4
brw-rw---- 1 root disk      1,   5 2007-03-15 11:07 ram5
brw-rw---- 1 root disk      1,   6 2007-03-15 11:07 ram6
brw-rw---- 1 root disk      1,   7 2007-03-15 11:07 ram7
brw-rw---- 1 root disk      1,   8 2007-03-15 11:07 ram8
brw-rw---- 1 root disk      1,   9 2007-03-15 11:07 ram9
crw-rw-rw- 1 root root      1,   8 2007-03-15 11:07 random
crw-rw---- 1 root audio    10, 135 2007-03-15 11:07 rtc
brw-rw---- 1 root plugdev   8,   0 2007-03-15 11:08 sda
brw-rw---- 1 root plugdev   8,   1 2007-03-15 11:08 sda1
crw-rw---- 1 root audio    14,   1 2007-03-15 11:07 sequencer
crw-rw---- 1 root audio    14,   8 2007-03-15 11:07 sequencer2
crw-rw---- 1 root root     21,   0 2007-03-15 11:08 sg0
drwxrwxrwt 2 root root          40 2007-03-15 11:07 shm
crw-rw---- 1 root root     10, 231 2007-03-15 11:07 snapshot
drwxr-xr-x 2 root root         240 2007-03-15 11:07 snd
lrwxrwxrwx 1 root root          24 2007-03-15 11:07 sndstat -> /proc/asound/oss/sndstat
lrwxrwxrwx 1 root root          15 2007-03-15 11:07 stderr -> /proc/self/fd/2
lrwxrwxrwx 1 root root          15 2007-03-15 11:07 stdin -> /proc/self/fd/0
lrwxrwxrwx 1 root root          15 2007-03-15 11:07 stdout -> /proc/self/fd/1
crw-rw-rw- 1 root root      5,   0 2007-03-15 11:07 tty
crw-rw---- 1 root root      4,   0 2007-03-15 11:07 tty0
crw------- 1 root root      4,   1 2007-03-15 11:08 tty1
crw-rw---- 1 root root      4,  10 2007-03-15 11:07 tty10
crw-rw---- 1 root root      4,  11 2007-03-15 11:07 tty11
crw-rw---- 1 root root      4,  12 2007-03-15 11:07 tty12
crw-rw---- 1 root root      4,  13 2007-03-15 11:07 tty13
crw-rw---- 1 root root      4,  14 2007-03-15 11:07 tty14
crw-rw---- 1 root root      4,  15 2007-03-15 11:07 tty15
crw-rw---- 1 root root      4,  16 2007-03-15 11:07 tty16
crw-rw---- 1 root root      4,  17 2007-03-15 11:07 tty17
crw-rw---- 1 root root      4,  18 2007-03-15 11:07 tty18
crw-rw---- 1 root root      4,  19 2007-03-15 11:07 tty19
crw------- 1 root root      4,   2 2007-03-15 11:08 tty2
crw-rw---- 1 root root      4,  20 2007-03-15 11:07 tty20
crw-rw---- 1 root root      4,  21 2007-03-15 11:07 tty21
crw-rw---- 1 root root      4,  22 2007-03-15 11:07 tty22
crw-rw---- 1 root root      4,  23 2007-03-15 11:07 tty23
crw-rw---- 1 root root      4,  24 2007-03-15 11:07 tty24
crw-rw---- 1 root root      4,  25 2007-03-15 11:07 tty25
crw-rw---- 1 root root      4,  26 2007-03-15 11:07 tty26
crw-rw---- 1 root root      4,  27 2007-03-15 11:07 tty27
crw-rw---- 1 root root      4,  28 2007-03-15 11:07 tty28
crw-rw---- 1 root root      4,  29 2007-03-15 11:07 tty29
crw------- 1 root root      4,   3 2007-03-15 11:08 tty3
crw-rw---- 1 root root      4,  30 2007-03-15 11:07 tty30
crw-rw---- 1 root root      4,  31 2007-03-15 11:07 tty31
crw-rw---- 1 root root      4,  32 2007-03-15 11:07 tty32
crw-rw---- 1 root root      4,  33 2007-03-15 11:07 tty33
crw-rw---- 1 root root      4,  34 2007-03-15 11:07 tty34
crw-rw---- 1 root root      4,  35 2007-03-15 11:07 tty35
crw-rw---- 1 root root      4,  36 2007-03-15 11:07 tty36
crw-rw---- 1 root root      4,  37 2007-03-15 11:07 tty37
crw-rw---- 1 root root      4,  38 2007-03-15 11:07 tty38
crw-rw---- 1 root root      4,  39 2007-03-15 11:07 tty39
crw------- 1 root root      4,   4 2007-03-15 11:08 tty4
crw-rw---- 1 root root      4,  40 2007-03-15 11:07 tty40
crw-rw---- 1 root root      4,  41 2007-03-15 11:07 tty41
crw-rw---- 1 root root      4,  42 2007-03-15 11:07 tty42
crw-rw---- 1 root root      4,  43 2007-03-15 11:07 tty43
crw-rw---- 1 root root      4,  44 2007-03-15 11:07 tty44
crw-rw---- 1 root root      4,  45 2007-03-15 11:07 tty45
crw-rw---- 1 root root      4,  46 2007-03-15 11:07 tty46
crw-rw---- 1 root root      4,  47 2007-03-15 11:07 tty47
crw-rw---- 1 root root      4,  48 2007-03-15 11:07 tty48
crw-rw---- 1 root root      4,  49 2007-03-15 11:07 tty49
crw------- 1 root root      4,   5 2007-03-15 11:08 tty5
crw-rw---- 1 root root      4,  50 2007-03-15 11:07 tty50
crw-rw---- 1 root root      4,  51 2007-03-15 11:07 tty51
crw-rw---- 1 root root      4,  52 2007-03-15 11:07 tty52
crw-rw---- 1 root root      4,  53 2007-03-15 11:07 tty53
crw-rw---- 1 root root      4,  54 2007-03-15 11:07 tty54
crw-rw---- 1 root root      4,  55 2007-03-15 11:07 tty55
crw-rw---- 1 root root      4,  56 2007-03-15 11:07 tty56
crw-rw---- 1 root root      4,  57 2007-03-15 11:07 tty57
crw-rw---- 1 root root      4,  58 2007-03-15 11:07 tty58
crw-rw---- 1 root root      4,  59 2007-03-15 11:07 tty59
crw------- 1 root root      4,   6 2007-03-15 11:08 tty6
crw-rw---- 1 root root      4,  60 2007-03-15 11:07 tty60
crw-rw---- 1 root root      4,  61 2007-03-15 11:07 tty61
crw-rw---- 1 root root      4,  62 2007-03-15 11:07 tty62
crw-rw---- 1 root root      4,  63 2007-03-15 11:07 tty63
crw-rw---- 1 root root      4,   7 2007-03-15 11:07 tty7
crw-rw---- 1 root root      4,   8 2007-03-15 11:08 tty8
crw-rw---- 1 root root      4,   9 2007-03-15 11:07 tty9
crw-rw-rw- 1 root tty       3, 176 2007-03-15 11:07 ttya0
crw-rw-rw- 1 root tty       3, 177 2007-03-15 11:07 ttya1
crw-rw-rw- 1 root tty       3, 178 2007-03-15 11:07 ttya2
crw-rw-rw- 1 root tty       3, 179 2007-03-15 11:07 ttya3
crw-rw-rw- 1 root tty       3, 180 2007-03-15 11:07 ttya4
crw-rw-rw- 1 root tty       3, 181 2007-03-15 11:07 ttya5
crw-rw-rw- 1 root tty       3, 182 2007-03-15 11:07 ttya6
crw-rw-rw- 1 root tty       3, 183 2007-03-15 11:07 ttya7
crw-rw-rw- 1 root tty       3, 184 2007-03-15 11:07 ttya8
crw-rw-rw- 1 root tty       3, 185 2007-03-15 11:07 ttya9
crw-rw-rw- 1 root tty       3, 186 2007-03-15 11:07 ttyaa
crw-rw-rw- 1 root tty       3, 187 2007-03-15 11:07 ttyab
crw-rw-rw- 1 root tty       3, 188 2007-03-15 11:07 ttyac
crw-rw-rw- 1 root tty       3, 189 2007-03-15 11:07 ttyad
crw-rw-rw- 1 root tty       3, 190 2007-03-15 11:07 ttyae
crw-rw-rw- 1 root tty       3, 191 2007-03-15 11:07 ttyaf
crw-rw-rw- 1 root tty       3, 192 2007-03-15 11:07 ttyb0
crw-rw-rw- 1 root tty       3, 193 2007-03-15 11:07 ttyb1
crw-rw-rw- 1 root tty       3, 194 2007-03-15 11:07 ttyb2
crw-rw-rw- 1 root tty       3, 195 2007-03-15 11:07 ttyb3
crw-rw-rw- 1 root tty       3, 196 2007-03-15 11:07 ttyb4
crw-rw-rw- 1 root tty       3, 197 2007-03-15 11:07 ttyb5
crw-rw-rw- 1 root tty       3, 198 2007-03-15 11:07 ttyb6
crw-rw-rw- 1 root tty       3, 199 2007-03-15 11:07 ttyb7
crw-rw-rw- 1 root tty       3, 200 2007-03-15 11:07 ttyb8
crw-rw-rw- 1 root tty       3, 201 2007-03-15 11:07 ttyb9
crw-rw-rw- 1 root tty       3, 202 2007-03-15 11:07 ttyba
crw-rw-rw- 1 root tty       3, 203 2007-03-15 11:07 ttybb
crw-rw-rw- 1 root tty       3, 204 2007-03-15 11:07 ttybc
crw-rw-rw- 1 root tty       3, 205 2007-03-15 11:07 ttybd
crw-rw-rw- 1 root tty       3, 206 2007-03-15 11:07 ttybe
crw-rw-rw- 1 root tty       3, 207 2007-03-15 11:07 ttybf
crw-rw-rw- 1 root tty       3, 208 2007-03-15 11:07 ttyc0
crw-rw-rw- 1 root tty       3, 209 2007-03-15 11:07 ttyc1
crw-rw-rw- 1 root tty       3, 210 2007-03-15 11:07 ttyc2
crw-rw-rw- 1 root tty       3, 211 2007-03-15 11:07 ttyc3
crw-rw-rw- 1 root tty       3, 212 2007-03-15 11:07 ttyc4
crw-rw-rw- 1 root tty       3, 213 2007-03-15 11:07 ttyc5
crw-rw-rw- 1 root tty       3, 214 2007-03-15 11:07 ttyc6
crw-rw-rw- 1 root tty       3, 215 2007-03-15 11:07 ttyc7
crw-rw-rw- 1 root tty       3, 216 2007-03-15 11:07 ttyc8
crw-rw-rw- 1 root tty       3, 217 2007-03-15 11:07 ttyc9
crw-rw-rw- 1 root tty       3, 218 2007-03-15 11:07 ttyca
crw-rw-rw- 1 root tty       3, 219 2007-03-15 11:07 ttycb
crw-rw-rw- 1 root tty       3, 220 2007-03-15 11:07 ttycc
crw-rw-rw- 1 root tty       3, 221 2007-03-15 11:07 ttycd
crw-rw-rw- 1 root tty       3, 222 2007-03-15 11:07 ttyce
crw-rw-rw- 1 root tty       3, 223 2007-03-15 11:07 ttycf
crw-rw-rw- 1 root tty       3, 224 2007-03-15 11:07 ttyd0
crw-rw-rw- 1 root tty       3, 225 2007-03-15 11:07 ttyd1
crw-rw-rw- 1 root tty       3, 226 2007-03-15 11:07 ttyd2
crw-rw-rw- 1 root tty       3, 227 2007-03-15 11:07 ttyd3
crw-rw-rw- 1 root tty       3, 228 2007-03-15 11:07 ttyd4
crw-rw-rw- 1 root tty       3, 229 2007-03-15 11:07 ttyd5
crw-rw-rw- 1 root tty       3, 230 2007-03-15 11:07 ttyd6
crw-rw-rw- 1 root tty       3, 231 2007-03-15 11:07 ttyd7
crw-rw-rw- 1 root tty       3, 232 2007-03-15 11:07 ttyd8
crw-rw-rw- 1 root tty       3, 233 2007-03-15 11:07 ttyd9
crw-rw-rw- 1 root tty       3, 234 2007-03-15 11:07 ttyda
crw-rw-rw- 1 root tty       3, 235 2007-03-15 11:07 ttydb
crw-rw-rw- 1 root tty       3, 236 2007-03-15 11:07 ttydc
crw-rw-rw- 1 root tty       3, 237 2007-03-15 11:07 ttydd
crw-rw-rw- 1 root tty       3, 238 2007-03-15 11:07 ttyde
crw-rw-rw- 1 root tty       3, 239 2007-03-15 11:07 ttydf
crw-rw-rw- 1 root tty       3, 240 2007-03-15 11:07 ttye0
crw-rw-rw- 1 root tty       3, 241 2007-03-15 11:07 ttye1
crw-rw-rw- 1 root tty       3, 242 2007-03-15 11:07 ttye2
crw-rw-rw- 1 root tty       3, 243 2007-03-15 11:07 ttye3
crw-rw-rw- 1 root tty       3, 244 2007-03-15 11:07 ttye4
crw-rw-rw- 1 root tty       3, 245 2007-03-15 11:07 ttye5
crw-rw-rw- 1 root tty       3, 246 2007-03-15 11:07 ttye6
crw-rw-rw- 1 root tty       3, 247 2007-03-15 11:07 ttye7
crw-rw-rw- 1 root tty       3, 248 2007-03-15 11:07 ttye8
crw-rw-rw- 1 root tty       3, 249 2007-03-15 11:07 ttye9
crw-rw-rw- 1 root tty       3, 250 2007-03-15 11:07 ttyea
crw-rw-rw- 1 root tty       3, 251 2007-03-15 11:07 ttyeb
crw-rw-rw- 1 root tty       3, 252 2007-03-15 11:07 ttyec
crw-rw-rw- 1 root tty       3, 253 2007-03-15 11:07 ttyed
crw-rw-rw- 1 root tty       3, 254 2007-03-15 11:07 ttyee
crw-rw-rw- 1 root tty       3, 255 2007-03-15 11:07 ttyef
crw-rw-rw- 1 root tty       3,   0 2007-03-15 11:07 ttyp0
crw-rw-rw- 1 root tty       3,   1 2007-03-15 11:07 ttyp1
crw-rw-rw- 1 root tty       3,   2 2007-03-15 11:07 ttyp2
crw-rw-rw- 1 root tty       3,   3 2007-03-15 11:07 ttyp3
crw-rw-rw- 1 root tty       3,   4 2007-03-15 11:07 ttyp4
crw-rw-rw- 1 root tty       3,   5 2007-03-15 11:07 ttyp5
crw-rw-rw- 1 root tty       3,   6 2007-03-15 11:07 ttyp6
crw-rw-rw- 1 root tty       3,   7 2007-03-15 11:07 ttyp7
crw-rw-rw- 1 root tty       3,   8 2007-03-15 11:07 ttyp8
crw-rw-rw- 1 root tty       3,   9 2007-03-15 11:07 ttyp9
crw-rw-rw- 1 root tty       3,  10 2007-03-15 11:07 ttypa
crw-rw-rw- 1 root tty       3,  11 2007-03-15 11:07 ttypb
crw-rw-rw- 1 root tty       3,  12 2007-03-15 11:07 ttypc
crw-rw-rw- 1 root tty       3,  13 2007-03-15 11:07 ttypd
crw-rw-rw- 1 root tty       3,  14 2007-03-15 11:07 ttype
crw-rw-rw- 1 root tty       3,  15 2007-03-15 11:07 ttypf
crw-rw-rw- 1 root tty       3,  16 2007-03-15 11:07 ttyq0
crw-rw-rw- 1 root tty       3,  17 2007-03-15 11:07 ttyq1
crw-rw-rw- 1 root tty       3,  18 2007-03-15 11:07 ttyq2
crw-rw-rw- 1 root tty       3,  19 2007-03-15 11:07 ttyq3
crw-rw-rw- 1 root tty       3,  20 2007-03-15 11:07 ttyq4
crw-rw-rw- 1 root tty       3,  21 2007-03-15 11:07 ttyq5
crw-rw-rw- 1 root tty       3,  22 2007-03-15 11:07 ttyq6
crw-rw-rw- 1 root tty       3,  23 2007-03-15 11:07 ttyq7
crw-rw-rw- 1 root tty       3,  24 2007-03-15 11:07 ttyq8
crw-rw-rw- 1 root tty       3,  25 2007-03-15 11:07 ttyq9
crw-rw-rw- 1 root tty       3,  26 2007-03-15 11:07 ttyqa
crw-rw-rw- 1 root tty       3,  27 2007-03-15 11:07 ttyqb
crw-rw-rw- 1 root tty       3,  28 2007-03-15 11:07 ttyqc
crw-rw-rw- 1 root tty       3,  29 2007-03-15 11:07 ttyqd
crw-rw-rw- 1 root tty       3,  30 2007-03-15 11:07 ttyqe
crw-rw-rw- 1 root tty       3,  31 2007-03-15 11:07 ttyqf
crw-rw-rw- 1 root tty       3,  32 2007-03-15 11:07 ttyr0
crw-rw-rw- 1 root tty       3,  33 2007-03-15 11:07 ttyr1
crw-rw-rw- 1 root tty       3,  34 2007-03-15 11:07 ttyr2
crw-rw-rw- 1 root tty       3,  35 2007-03-15 11:07 ttyr3
crw-rw-rw- 1 root tty       3,  36 2007-03-15 11:07 ttyr4
crw-rw-rw- 1 root tty       3,  37 2007-03-15 11:07 ttyr5
crw-rw-rw- 1 root tty       3,  38 2007-03-15 11:07 ttyr6
crw-rw-rw- 1 root tty       3,  39 2007-03-15 11:07 ttyr7
crw-rw-rw- 1 root tty       3,  40 2007-03-15 11:07 ttyr8
crw-rw-rw- 1 root tty       3,  41 2007-03-15 11:07 ttyr9
crw-rw-rw- 1 root tty       3,  42 2007-03-15 11:07 ttyra
crw-rw-rw- 1 root tty       3,  43 2007-03-15 11:07 ttyrb
crw-rw-rw- 1 root tty       3,  44 2007-03-15 11:07 ttyrc
crw-rw-rw- 1 root tty       3,  45 2007-03-15 11:07 ttyrd
crw-rw-rw- 1 root tty       3,  46 2007-03-15 11:07 ttyre
crw-rw-rw- 1 root tty       3,  47 2007-03-15 11:07 ttyrf
crw-rw-rw- 1 root tty       3,  48 2007-03-15 11:07 ttys0
crw-rw---- 1 root dialout   4,  64 2007-03-15 11:07 ttyS0
crw-rw-rw- 1 root tty       3,  49 2007-03-15 11:07 ttys1
crw-rw---- 1 root dialout   4,  65 2007-03-15 11:07 ttyS1
crw-rw-rw- 1 root tty       3,  50 2007-03-15 11:07 ttys2
crw-rw---- 1 root dialout   4,  66 2007-03-15 11:07 ttyS2
crw-rw-rw- 1 root tty       3,  51 2007-03-15 11:07 ttys3
crw-rw---- 1 root dialout   4,  67 2007-03-15 11:07 ttyS3
crw-rw-rw- 1 root tty       3,  52 2007-03-15 11:07 ttys4
crw-rw-rw- 1 root tty       3,  53 2007-03-15 11:07 ttys5
crw-rw-rw- 1 root tty       3,  54 2007-03-15 11:07 ttys6
crw-rw-rw- 1 root tty       3,  55 2007-03-15 11:07 ttys7
crw-rw-rw- 1 root tty       3,  56 2007-03-15 11:07 ttys8
crw-rw-rw- 1 root tty       3,  57 2007-03-15 11:07 ttys9
crw-rw-rw- 1 root tty       3,  58 2007-03-15 11:07 ttysa
crw-rw-rw- 1 root tty       3,  59 2007-03-15 11:07 ttysb
crw-rw-rw- 1 root tty       3,  60 2007-03-15 11:07 ttysc
crw-rw-rw- 1 root tty       3,  61 2007-03-15 11:07 ttysd
crw-rw-rw- 1 root tty       3,  62 2007-03-15 11:07 ttyse
crw-rw-rw- 1 root tty       3,  63 2007-03-15 11:07 ttysf
crw-rw-rw- 1 root tty       3,  64 2007-03-15 11:07 ttyt0
crw-rw-rw- 1 root tty       3,  65 2007-03-15 11:07 ttyt1
crw-rw-rw- 1 root tty       3,  66 2007-03-15 11:07 ttyt2
crw-rw-rw- 1 root tty       3,  67 2007-03-15 11:07 ttyt3
crw-rw-rw- 1 root tty       3,  68 2007-03-15 11:07 ttyt4
crw-rw-rw- 1 root tty       3,  69 2007-03-15 11:07 ttyt5
crw-rw-rw- 1 root tty       3,  70 2007-03-15 11:07 ttyt6
crw-rw-rw- 1 root tty       3,  71 2007-03-15 11:07 ttyt7
crw-rw-rw- 1 root tty       3,  72 2007-03-15 11:07 ttyt8
crw-rw-rw- 1 root tty       3,  73 2007-03-15 11:07 ttyt9
crw-rw-rw- 1 root tty       3,  74 2007-03-15 11:07 ttyta
crw-rw-rw- 1 root tty       3,  75 2007-03-15 11:07 ttytb
crw-rw-rw- 1 root tty       3,  76 2007-03-15 11:07 ttytc
crw-rw-rw- 1 root tty       3,  77 2007-03-15 11:07 ttytd
crw-rw-rw- 1 root tty       3,  78 2007-03-15 11:07 ttyte
crw-rw-rw- 1 root tty       3,  79 2007-03-15 11:07 ttytf
crw-rw-rw- 1 root tty       3,  80 2007-03-15 11:07 ttyu0
crw-rw-rw- 1 root tty       3,  81 2007-03-15 11:07 ttyu1
crw-rw-rw- 1 root tty       3,  82 2007-03-15 11:07 ttyu2
crw-rw-rw- 1 root tty       3,  83 2007-03-15 11:07 ttyu3
crw-rw-rw- 1 root tty       3,  84 2007-03-15 11:07 ttyu4
crw-rw-rw- 1 root tty       3,  85 2007-03-15 11:07 ttyu5
crw-rw-rw- 1 root tty       3,  86 2007-03-15 11:07 ttyu6
crw-rw-rw- 1 root tty       3,  87 2007-03-15 11:07 ttyu7
crw-rw-rw- 1 root tty       3,  88 2007-03-15 11:07 ttyu8
crw-rw-rw- 1 root tty       3,  89 2007-03-15 11:07 ttyu9
crw-rw-rw- 1 root tty       3,  90 2007-03-15 11:07 ttyua
crw-rw-rw- 1 root tty       3,  91 2007-03-15 11:07 ttyub
crw-rw-rw- 1 root tty       3,  92 2007-03-15 11:07 ttyuc
crw-rw-rw- 1 root tty       3,  93 2007-03-15 11:07 ttyud
crw-rw-rw- 1 root tty       3,  94 2007-03-15 11:07 ttyue
crw-rw-rw- 1 root tty       3,  95 2007-03-15 11:07 ttyuf
crw-rw-rw- 1 root tty       3,  96 2007-03-15 11:07 ttyv0
crw-rw-rw- 1 root tty       3,  97 2007-03-15 11:07 ttyv1
crw-rw-rw- 1 root tty       3,  98 2007-03-15 11:07 ttyv2
crw-rw-rw- 1 root tty       3,  99 2007-03-15 11:07 ttyv3
crw-rw-rw- 1 root tty       3, 100 2007-03-15 11:07 ttyv4
crw-rw-rw- 1 root tty       3, 101 2007-03-15 11:07 ttyv5
crw-rw-rw- 1 root tty       3, 102 2007-03-15 11:07 ttyv6
crw-rw-rw- 1 root tty       3, 103 2007-03-15 11:07 ttyv7
crw-rw-rw- 1 root tty       3, 104 2007-03-15 11:07 ttyv8
crw-rw-rw- 1 root tty       3, 105 2007-03-15 11:07 ttyv9
crw-rw-rw- 1 root tty       3, 106 2007-03-15 11:07 ttyva
crw-rw-rw- 1 root tty       3, 107 2007-03-15 11:07 ttyvb
crw-rw-rw- 1 root tty       3, 108 2007-03-15 11:07 ttyvc
crw-rw-rw- 1 root tty       3, 109 2007-03-15 11:07 ttyvd
crw-rw-rw- 1 root tty       3, 110 2007-03-15 11:07 ttyve
crw-rw-rw- 1 root tty       3, 111 2007-03-15 11:07 ttyvf
crw-rw-rw- 1 root tty       3, 112 2007-03-15 11:07 ttyw0
crw-rw-rw- 1 root tty       3, 113 2007-03-15 11:07 ttyw1
crw-rw-rw- 1 root tty       3, 114 2007-03-15 11:07 ttyw2
crw-rw-rw- 1 root tty       3, 115 2007-03-15 11:07 ttyw3
crw-rw-rw- 1 root tty       3, 116 2007-03-15 11:07 ttyw4
crw-rw-rw- 1 root tty       3, 117 2007-03-15 11:07 ttyw5
crw-rw-rw- 1 root tty       3, 118 2007-03-15 11:07 ttyw6
crw-rw-rw- 1 root tty       3, 119 2007-03-15 11:07 ttyw7
crw-rw-rw- 1 root tty       3, 120 2007-03-15 11:07 ttyw8
crw-rw-rw- 1 root tty       3, 121 2007-03-15 11:07 ttyw9
crw-rw-rw- 1 root tty       3, 122 2007-03-15 11:07 ttywa
crw-rw-rw- 1 root tty       3, 123 2007-03-15 11:07 ttywb
crw-rw-rw- 1 root tty       3, 124 2007-03-15 11:07 ttywc
crw-rw-rw- 1 root tty       3, 125 2007-03-15 11:07 ttywd
crw-rw-rw- 1 root tty       3, 126 2007-03-15 11:07 ttywe
crw-rw-rw- 1 root tty       3, 127 2007-03-15 11:07 ttywf
crw-rw-rw- 1 root tty       3, 128 2007-03-15 11:07 ttyx0
crw-rw-rw- 1 root tty       3, 129 2007-03-15 11:07 ttyx1
crw-rw-rw- 1 root tty       3, 130 2007-03-15 11:07 ttyx2
crw-rw-rw- 1 root tty       3, 131 2007-03-15 11:07 ttyx3
crw-rw-rw- 1 root tty       3, 132 2007-03-15 11:07 ttyx4
crw-rw-rw- 1 root tty       3, 133 2007-03-15 11:07 ttyx5
crw-rw-rw- 1 root tty       3, 134 2007-03-15 11:07 ttyx6
crw-rw-rw- 1 root tty       3, 135 2007-03-15 11:07 ttyx7
crw-rw-rw- 1 root tty       3, 136 2007-03-15 11:07 ttyx8
crw-rw-rw- 1 root tty       3, 137 2007-03-15 11:07 ttyx9
crw-rw-rw- 1 root tty       3, 138 2007-03-15 11:07 ttyxa
crw-rw-rw- 1 root tty       3, 139 2007-03-15 11:07 ttyxb
crw-rw-rw- 1 root tty       3, 140 2007-03-15 11:07 ttyxc
crw-rw-rw- 1 root tty       3, 141 2007-03-15 11:07 ttyxd
crw-rw-rw- 1 root tty       3, 142 2007-03-15 11:07 ttyxe
crw-rw-rw- 1 root tty       3, 143 2007-03-15 11:07 ttyxf
crw-rw-rw- 1 root tty       3, 144 2007-03-15 11:07 ttyy0
crw-rw-rw- 1 root tty       3, 145 2007-03-15 11:07 ttyy1
crw-rw-rw- 1 root tty       3, 146 2007-03-15 11:07 ttyy2
crw-rw-rw- 1 root tty       3, 147 2007-03-15 11:07 ttyy3
crw-rw-rw- 1 root tty       3, 148 2007-03-15 11:07 ttyy4
crw-rw-rw- 1 root tty       3, 149 2007-03-15 11:07 ttyy5
crw-rw-rw- 1 root tty       3, 150 2007-03-15 11:07 ttyy6
crw-rw-rw- 1 root tty       3, 151 2007-03-15 11:07 ttyy7
crw-rw-rw- 1 root tty       3, 152 2007-03-15 11:07 ttyy8
crw-rw-rw- 1 root tty       3, 153 2007-03-15 11:07 ttyy9
crw-rw-rw- 1 root tty       3, 154 2007-03-15 11:07 ttyya
crw-rw-rw- 1 root tty       3, 155 2007-03-15 11:07 ttyyb
crw-rw-rw- 1 root tty       3, 156 2007-03-15 11:07 ttyyc
crw-rw-rw- 1 root tty       3, 157 2007-03-15 11:07 ttyyd
crw-rw-rw- 1 root tty       3, 158 2007-03-15 11:07 ttyye
crw-rw-rw- 1 root tty       3, 159 2007-03-15 11:07 ttyyf
crw-rw-rw- 1 root tty       3, 160 2007-03-15 11:07 ttyz0
crw-rw-rw- 1 root tty       3, 161 2007-03-15 11:07 ttyz1
crw-rw-rw- 1 root tty       3, 162 2007-03-15 11:07 ttyz2
crw-rw-rw- 1 root tty       3, 163 2007-03-15 11:07 ttyz3
crw-rw-rw- 1 root tty       3, 164 2007-03-15 11:07 ttyz4
crw-rw-rw- 1 root tty       3, 165 2007-03-15 11:07 ttyz5
crw-rw-rw- 1 root tty       3, 166 2007-03-15 11:07 ttyz6
crw-rw-rw- 1 root tty       3, 167 2007-03-15 11:07 ttyz7
crw-rw-rw- 1 root tty       3, 168 2007-03-15 11:07 ttyz8
crw-rw-rw- 1 root tty       3, 169 2007-03-15 11:07 ttyz9
crw-rw-rw- 1 root tty       3, 170 2007-03-15 11:07 ttyza
crw-rw-rw- 1 root tty       3, 171 2007-03-15 11:07 ttyzb
crw-rw-rw- 1 root tty       3, 172 2007-03-15 11:07 ttyzc
crw-rw-rw- 1 root tty       3, 173 2007-03-15 11:07 ttyzd
crw-rw-rw- 1 root tty       3, 174 2007-03-15 11:07 ttyze
crw-rw-rw- 1 root tty       3, 175 2007-03-15 11:07 ttyzf
```
```
crw-rw-rw- 1 root root      1,   9 2007-03-16 15:08 urandom
crw-rw---- 1 root root      7,   0 2007-03-16 15:07 vcs
crw-rw---- 1 root root      7,   1 2007-03-16 15:07 vcs1
crw-rw---- 1 root root      7,   2 2007-03-16 15:08 vcs2
crw-rw---- 1 root root      7,   3 2007-03-16 15:08 vcs3
crw-rw---- 1 root root      7,   4 2007-03-16 15:08 vcs4
crw-rw---- 1 root root      7,   5 2007-03-16 15:08 vcs5
crw-rw---- 1 root root      7,   6 2007-03-16 15:08 vcs6
crw-rw---- 1 root root      7,   7 2007-03-16 15:08 vcs7
crw-rw---- 1 root root      7,   8 2007-03-16 15:07 vcs8
crw-rw---- 1 root root      7, 128 2007-03-16 15:07 vcsa
crw-rw---- 1 root root      7, 129 2007-03-16 15:07 vcsa1
crw-rw---- 1 root root      7, 130 2007-03-16 15:08 vcsa2
crw-rw---- 1 root root      7, 131 2007-03-16 15:08 vcsa3
crw-rw---- 1 root root      7, 132 2007-03-16 15:08 vcsa4
crw-rw---- 1 root root      7, 133 2007-03-16 15:08 vcsa5
crw-rw---- 1 root root      7, 134 2007-03-16 15:08 vcsa6
crw-rw---- 1 root root      7, 135 2007-03-16 15:08 vcsa7
crw-rw---- 1 root root      7, 136 2007-03-16 15:07 vcsa8
prw-r----- 1 root adm            0 2007-03-17 12:50 xconsole
crw-rw-rw- 1 root root      1,   5 2007-03-16 15:07 zero
snyper64@Snyper64-laptop:~$
```

Any help, heres the complete file.

---

### Post by Snyper64 on 2007-04-10
Ok, I have gotten movies to play in Totem-xine but if I try to enable ac3 pass through I get an error asking if another program using my audio device. If I change the audio to 5.1 the movie will play up until it gets to the movie(where it changes into DD) and I get the same error as before. If I change the setting in the DVD to Stereo it plays just fine. Trying to play the DVD in Mplayer just gets me an stating that it couldn't detect the right VO device. Heres a new output of my Mplayer log file:

```
snyper64@Snyper64-laptop:~$ mplayer -v -vo xv dvd://
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 4, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


get_path('codecs.conf') -> '/home/snyper64/.mplayer/codecs.conf'
Reading /home/snyper64/.mplayer/codecs.conf: Can't open '/home/snyper64/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
CommandLine: '-v' '-vo' 'xv' 'dvd://'
init_freetype
get_path('font/font.desc') -> '/home/snyper64/.mplayer/font/font.desc'
font: can't open file: /home/snyper64/.mplayer/font/font.desc
Font /usr/share/mplayer/font/font.desc loaded successfully! (206 chars)
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Using nanosleep() timing
get_path('input.conf') -> '/home/snyper64/.mplayer/input.conf'
Can't open input config file /home/snyper64/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 60 binds
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
get_path('.conf') -> '/home/snyper64/.mplayer/.conf'

Playing dvd://.
get_path('sub/') -> '/home/snyper64/.mplayer/sub/'
URL: dvd://
Reading disc structure, please wait...
There are 19 titles on this DVD.
There are 1 chapters in this DVD title.
There are 1 angles in this DVD title.
DVD successfully opened.
[open] audio stream: 0 audio format: ac3 (stereo) language: en aid: 128
[open] number of audio channels on disk: 1.
[open] number of subtitles on disk: 0
DVD start cell: 0  pack: 0x0-0xBC  
DVD start=0 end=188  
STREAM: [null] dvd://
STREAM: Description: DVD stream
STREAM: Author: 
STREAM: Comment: 
DVD Seek! lba=0x0  cell=0  packs: 0x0-0xBC  
Angle-seek synced by cell/vob IDN search!  
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
Searching demuxer type for filename dvd:// ext: (null)
DVD Seek! lba=0x0  cell=0  packs: 0x0-0xBC  
Angle-seek synced by cell/vob IDN search!  
Checking for Nullsoft Streaming Video
DVD Seek! lba=0x0  cell=0  packs: 0x0-0xBC  
Angle-seek synced by cell/vob IDN search!  
Checking for MOV
Checking for VIVO
header block 1 size: 0
Checking for PVA
Checking for MPEG-TS...
TRIED UP TO POSITION 95807, FOUND 47, packet_size= 0, SEEMS A TS? 0
DVD Seek! lba=0x2E  cell=0  packs: 0x0-0xBC  
Angle-seek synced by cell/vob IDN search!  
DVD Seek! lba=0x0  cell=0  packs: 0x0-0xBC  
Angle-seek synced by cell/vob IDN search!  
Checking for LMLM4 Stream Format
Invalid packet in LMLM4 stream: ch=0 size=1140851708
LMLM4 Stream Format not found
system stream synced at 0xD (13)!
==> Found video stream: 0
MPEG-PS file format detected.
==> Found audio stream: 128
Searching for sequence header... OK!
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  3000.0 kbps (375.0 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x480  fps:29.97  ftime:=0.0334
get_path('sub/') -> '/home/snyper64/.mplayer/sub/'
```
Rest of output continues below.
```
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
dec_audio: Allocating 3840 bytes for input buffer.
dec_audio: Allocating 6144 + 65536 = 71680 bytes for output buffer.
Using SSE optimized IMDCT transform
AC3: 2.0 (dolby)  48000 Hz  192.0 kbit/s
A52 flags before a52_frame: 0x2A
A52 flags after a52_frame: 0xA
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1280x800 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Disabling DPMS
DPMSDisable stat: 1
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 2046x2046
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Trying filter chain: vo
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale vo
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
alsa-init: requested format: 48000 Hz, 2 channels, 9
alsa-init: using ALSA 1.0.11
alsa-init: setup for 1/2 channel(s)
alsa-init: using device default
alsa-init: pcm opend in blocking mode
alsa-init: chunksize set to 1024
alsa-init: fragcount=16
alsa-init: got buffersize=65536
alsa-init: got period size 1024
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
AO: Description: ALSA-0.9.x-1.x audio output
AO: Author: Alex Beregszaszi, Zsolt Barat <joy@streamminister.de>
AO: Comment: under developement
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO Config (720x480->720x540,flags=0,'MPlayer',0x32315659)
VO: [xv] 720x480 => 720x540 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x30323449 (I420) planar
using Xvideo port 158 for hw scaling
[xv] dx: 0 dy: 0 dw: 864 dh: 540
*** [vo] Allocating mp_image_t, 720x480x12bpp YUV planar, 518400 bytes
[xv] dx: 0 dy: 0 dw: 864 dh: 540
*** [vo] Allocating mp_image_t, 720x480x12bpp YUV planar, 518400 bytes
*** [vo] Allocating mp_image_t, 720x480x12bpp YUV planar, 518400 bytes
--- END OF CELL !!! --- 0.003 ct:  0.041  22/ 22 32% 24%  1.9% 3 0 
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: audio)  
MPEG Stream reached EOF 0.002 ct:  0.040  30/ 30 25% 18%  1.4% 3 0 
ds_fill_buffer: EOF reached (stream: video)  
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)  
EOF code: 1   1.2 A-V:  0.002 ct:  0.040  30/ 30 25% 18%  1.4% 3 0 

Uninit audio filters...
[libaf] Removing filter dummy 
Uninit audio: liba52
Uninit video: libmpeg2
Successfully enabled DPMS
alsa-uninit: pcm closed
vo: uninit ...

Exiting... (End of file)
snyper64@Snyper64-laptop:~$ 
```

If someone would tell me how to get the log files for Totem-Xine I will post them here as well.

My sound card is a Turtle Beach Audio Advantage Amigo(a USB soundcard) with the passthrough adapter connected going out to a Logitech Z5500 speaker setup. I have also disabled my onboard soundcard so that is no longer interfering with anything.

---

### Post by Snyper64 on 2007-04-12
bump

---

### Post by RJARRRPCGP on 2007-04-15
Getting "Permission denied" followed by "Couldn't open /dev/dvd" (or similar) sounds like a permissions problem.

---

### Post by Snyper64 on 2007-04-15
So how would I change the permissions?

---

### Post by Snyper64 on 2007-04-19
Ok, I now have DTS and DD support on my speakers. I went into terminal and typed int aplay -l and got this:
```
**** List of PLAYBACK Hardware Devices ****
card 1: U0x10f50x210 [USB Device 0x10f5:0x210], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
snyper64@Snyper64-laptop:~$ cat /proc/asound/devices
  2:        : timer
  3: [ 1- 0]: digital audio playback
  4: [ 1- 0]: digital audio capture
  5: [ 1]   : control

```
I went into asoundrc and added this to the file:
```
USB.!default {
        type hw
        card 1
        device 3
}
``` and than went into bleep media player and played 2 sample files, 1 in DTS and the other in DD and they each played in their respective formats on my surround sound reciever(indicated by the LCD screen).

I than inserted a DVD(played just fine in stereo) and tried to play a Dolby Digital sound test but I just got the annoying error in totem about another device using my soundcard.

EDIT: I just updated xine.lib to 1.1.6 since the previous update had problems handling CDs and DVDs and now it is playing everything fine. Now if I could just get mplayer and movieplayer to work I would be in good shape.

---

