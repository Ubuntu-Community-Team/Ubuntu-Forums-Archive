---
title: "Can't Get Hauppauge PVR 150 MCE to work"
date: 2008-05-05
forum: Multimedia Software
---

### Post by Krumar on 2008-05-05
Hey,
I've got an Hauppauge PVR 150 MCE that I can't seem to get to work. This is the out put i get from dmesg:

[   32.822287] ivtv:  Start initialization, version 1.1.0
[   32.822383] ivtv0: Initializing card #0
[   32.822386] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   32.839195] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   32.839201] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [APC2] -> GSI 17 (lev
el, low) -> IRQ 17
[   32.871792] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   32.940561] tveeprom 2-0050: Hauppauge model 26552, rev F0A3, serial# 10413454
[   32.940564] tveeprom 2-0050: tuner model is TCL MFNM05-4 (idx 103, type 43)
[   32.940566] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[   32.940567] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[   32.940569] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[   32.940570] tveeprom 2-0050: has radio, has no IR receiver, has no IR transmitter
[   32.940572] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   32.989559] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   32.989576] tda9887 2-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   32.989577] tuner 2-0043: type set to tda9887
[   32.996059] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   33.148592] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   33.162709] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   33.172698] tuner-simple 2-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[   33.172701] tuner 2-0061: type set to Philips NTSC MK3 (F
[   33.172939] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   33.172950] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   33.172964] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   33.172976] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   33.172989] ivtv0: Registered device radio0 for encoder radio
[   33.172991] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   33.173001] ivtv:  End initialization


I don't see anything that makes me think that anything went wrong recognizing the card, but when I try to view television through either VLC or mplayer I don't get anything. I have installed ivtv-utils and tried the scantv command, but it was unable to find any channels. I'm on ubuntu 8.04, I live in the US, and I'm using standard cable for TV. The cable is good, I've tried it out on an actual TV. If anyone can help or needs any more information, please leave me a reply.


Thanks

---

### Post by msrinath80 on 2008-05-05
It would help if you post the mplayer command and transcript of the mplayer session that you used from the terminal.

---

### Post by Krumar on 2008-05-05
one of the commands i saw was simply ```
mplayer /dev/video0
```

I'm really new to tuner cards under linux, if there is a better program for viewing tv I would be more than happy to give it a shot, and thanks for the quick response

---

### Post by msrinath80 on 2008-05-05
And where is the transcript of the mplayer session... the log from mplayer? And you can of course try TVTime. It works quite nicely.

---

### Post by Krumar on 2008-05-05
Sorry about that. This is what I get when I try that command

$ mplayer /dev/video0
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6700  @ 2.66GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/video0.




No windows come up, and there is no sound.

---

### Post by msrinath80 on 2008-05-05
Cool. Now try this:

mplayer -vf crop=600:440 -vo x11 -zoom tv://3 -tv driver=v4l2:norm=ntsc:chanlist=us-cable -tv channels=2-2,3-3,4-4,5-5,6-6

and post the transcript of the session.

Also tell me the output of:

cat /proc/asound/cards

---

### Post by Krumar on 2008-05-05
when I run the mplayer command I get this output:

[HTML]$ mplayer -vf crop=600:440 -vo x11 -zoom tv://3 -tv driver=v4l2:norm=ntsc:chanlist=us-cable -tv channels=2-2,3-3,4-4,5-5,6-6
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6700  @ 2.66GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://3.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Hauppauge WinTV PVR-150
 Tuner cap: STEREO
 Tuner rxs: STEREO
 Capabilites:  video capture  VBI capture device  tuner  audio  read/write
 supported norms: 0 = PAL-BGH; 1 = PAL-DK; 2 = PAL-I; 3 = PAL-M; 4 = PAL-N; 5 = PAL-Nc; 6 = SECAM-BGH; 7 = SECAM-DK; 8 = SECAM-L; 9 = SECAM-L'; 10 = NTSC-M; 11 = NTSC-J; 12 = NTSC-K;
 inputs: 0 = Tuner 1; 1 = S-Video 1; 2 = Composite 1; 3 = S-Video 2; 4 = Composite 2;
 Current input: 0
 Current format: unknown (0x4745504d)
v4l2: current audio mode is : STEREO
tv.c: norm_from_string(ntsc): Bogus norm parameter, setting default.
v4l2: ioctl set norm failed: Device or resource busy
Error: Cannot set norm!
TV channel names detected.
Selected channel: 4 - 4 (freq: 67.250)
v4l2: ioctl request buffers failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.


MPlayer interrupted by signal 11 in module: demux_open
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.[/HTML]


when I do the cat command I get:

$ cat /proc/asound/cards 
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xcfff0000 irq 20

---

### Post by msrinath80 on 2008-05-05
OK, cool. Try just the video first:

mplayer -ao null -vf crop=600:440 -vo x11 -zoom tv://3 -tv driver=v4l2:norm=****:chanlist=us-cable -tv channels=2-2,3-3,4-4,5-5,6-6

Replace the **** with ntsc-m, ntsc-j and ntsc-k one by one and post the output.

Also please install tvtime using:

sudo apt-get install tvtime

Then run tvtime from the terminal. It has a pretty decent GUI. Press F1 to go to the menu and try to scan for channels.

---

### Post by msrinath80 on 2008-05-05
Please also check the following threads:

1) [http://ph.ubuntuforums.com/showthread.php?t=758845](http://ph.ubuntuforums.com/showthread.php?t=758845)

2) [http://ubuntuforums.org/showthread.php?t=490530](http://ubuntuforums.org/showthread.php?t=490530)

3) tvtime might not work (see [http://www.linuxactionshow.com/forum/comments.php?DiscussionID=2037](http://www.linuxactionshow.com/forum/comments.php?DiscussionID=2037))

4) [http://www.uluga.ubuntuforums.org/showthread.php?t=108826](http://www.uluga.ubuntuforums.org/showthread.php?t=108826)

---

### Post by Krumar on 2008-05-05
ok, here comes the output:


ntsc-m
[PHP]$ mplayer -vf crop=600:440 -vo x11 -zoom tv://3 -tv driver=v4l2:norm=ntsc-m:chanlist=us-cable -tv channels=2-2,3-3,4-4,5-5,6-6
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6700  @ 2.66GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://3.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Hauppauge WinTV PVR-150
 Tuner cap:
 Tuner rxs:
 Capabilites:  video capture  VBI capture device  tuner  audio  read/write
 supported norms: 0 = PAL-BGH; 1 = PAL-DK; 2 = PAL-I; 3 = PAL-M; 4 = PAL-N; 5 = PAL-Nc; 6 = SECAM-BGH; 7 = SECAM-DK; 8 = SECAM-L; 9 = SECAM-L'; 10 = NTSC-M; 11 = NTSC-J; 12 = NTSC-K;
 inputs: 0 = Tuner 1; 1 = S-Video 1; 2 = Composite 1; 3 = S-Video 2; 4 = Composite 2;
 Current input: 0
 Current format: unknown (0x4745504d)
v4l2: current audio mode is : MONO
TV channel names detected.
Selected channel: 4 - 4 (freq: 67.250)
v4l2: ioctl request buffers failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.


MPlayer interrupted by signal 11 in module: demux_open
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
[/PHP]

ntsc-j
[PHP]$ mplayer -vf crop=600:440 -vo x11 -zoom tv://3 -tv driver=v4l2:norm=ntsc-j:chanlist=us-cable -tv channels=2-2,3-3,4-4,5-5,6-6
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6700  @ 2.66GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://3.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Hauppauge WinTV PVR-150
 Tuner cap:
 Tuner rxs:
 Capabilites:  video capture  VBI capture device  tuner  audio  read/write
 supported norms: 0 = PAL-BGH; 1 = PAL-DK; 2 = PAL-I; 3 = PAL-M; 4 = PAL-N; 5 = PAL-Nc; 6 = SECAM-BGH; 7 = SECAM-DK; 8 = SECAM-L; 9 = SECAM-L'; 10 = NTSC-M; 11 = NTSC-J; 12 = NTSC-K;
 inputs: 0 = Tuner 1; 1 = S-Video 1; 2 = Composite 1; 3 = S-Video 2; 4 = Composite 2;
 Current input: 0
 Current format: unknown (0x4745504d)
v4l2: current audio mode is : MONO
v4l2: ioctl set norm failed: Device or resource busy
Error: Cannot set norm!
TV channel names detected.
Selected channel: 4 - 4 (freq: 67.250)
v4l2: ioctl request buffers failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.


MPlayer interrupted by signal 11 in module: demux_open
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
[/PHP]


and finally ntsc-k
[PHP]$ mplayer -vf crop=600:440 -vo x11 -zoom tv://3 -tv driver=v4l2:norm=ntsc-k:chanlist=us-cable -tv channels=2-2,3-3,4-4,5-5,6-6
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6700  @ 2.66GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://3.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Hauppauge WinTV PVR-150
 Tuner cap:
 Tuner rxs:
 Capabilites:  video capture  VBI capture device  tuner  audio  read/write
 supported norms: 0 = PAL-BGH; 1 = PAL-DK; 2 = PAL-I; 3 = PAL-M; 4 = PAL-N; 5 = PAL-Nc; 6 = SECAM-BGH; 7 = SECAM-DK; 8 = SECAM-L; 9 = SECAM-L'; 10 = NTSC-M; 11 = NTSC-J; 12 = NTSC-K;
 inputs: 0 = Tuner 1; 1 = S-Video 1; 2 = Composite 1; 3 = S-Video 2; 4 = Composite 2;
 Current input: 0
 Current format: unknown (0x4745504d)
v4l2: current audio mode is : MONO
v4l2: ioctl set norm failed: Device or resource busy
Error: Cannot set norm!
TV channel names detected.
Selected channel: 4 - 4 (freq: 67.250)
v4l2: ioctl request buffers failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.


MPlayer interrupted by signal 11 in module: demux_open
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
[/PHP]

I can't get to an option that allows me to scan for channels, but I think the terminal output looks pretty helpful


[PHP]$ tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/user/.tvtime/tvtime.xml"
I/O error : Permission denied
I/O error : Permission denied
Cannot change owner of /home/user/.tvtime/tvtime.xml: Permission denied.
videoinput: Card failed to allocate capture buffers: Invalid argument
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O error : Permission denied
I/O warning : failed to load external entity "/home/user/.tvtime/stationlist.xml"
station: No station file found, creating a new one.
I/O error : Permission denied
I/O error : Permission denied
Thank you for using tvtime.
[/PHP]

---

### Post by msrinath80 on 2008-05-05
Not recommended for daily use, but try running tvtime as root:

sudo tvtime

to see if the permission denied errors go away.

I also told you to use -ao null in the mplayer command. Check the command I posted earlier.

---

### Post by Krumar on 2008-05-05
when I do sudo I get this:

[HTML]$ sudo tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/user/.tvtime/tvtime.xml"
videoinput: Card failed to allocate capture buffers: Invalid argument
I/O warning : failed to load external entity "/home/user/.tvtime/stationlist.xml"
station: No station file found, creating a new one.
Thank you for using tvtime.
[/HTML]

And I have tried those links already before I started this post. I've read a lot of posts from people saying that the pvr 150 that I got was supposed to have wonderful support, but so far, I'm not having as much luck. And by the way, thanks a lot for you help so far, I do feel like this is moving forward.

---

### Post by OldGaf on 2008-05-05
R U sure the card is good..... I have had a "hit and miss" experiance with Hauppauge.... no errors, but a few card wold just not work. I replaced with a new on, changed nothing else and boom.... TV.

---

### Post by Krumar on 2008-05-05
I'm not one hundred percent sure of the card, this is the first computer it's been installed in, and I have not seen it work yet. I'm pretty sure the computer is in good shape, I know cable is working, the only thing I'm not sure of is the tuner. Can anyone tell me what I should see when I start up an Ubuntu system with a functioning card?

Thanks,
Krumar

---

### Post by msrinath80 on 2008-05-05
I'm kinda out of options here. I had problems getting my Hauppauge WINTV HVR 950 to work with Hardy so I will be switching to Fedora 9 in a week or so where it works flawlessly. I'm surprised that the PVR 150 has trouble with GNU/Linux. Did you try using VLC too?

Also does the card work in Windoze?

---

### Post by Krumar on 2008-05-05
I have tried the card with VLC, it doesn't seem to want to pick up on it. I've tried various channels, but I don't get anything. I don't know much about using VLC though, and I don't kmnow how to give you useful out put other than I don't get sound or video under it either.

And no, I have not tried the card under windows, but I'm thinking that may be the next step.

---

### Post by Krumar on 2008-05-05
I have tried out the tuner card in a friends windows vista computer and it did work so I know the card is good. I've read somewhere that Linux support for a 1600 chip on some Hauppauges' is non existent, could anyone tell me how I tell if mine is a 1600. And also, anyone with a functioning Hauppauge PVR 150 MCE card, could you tell me how you view TV on it?

---

### Post by little_penguin on 2008-05-06
Hi, tvtime will not work with the PVR-150 because this card is an mpeg encoder and needs programs that play mpeg to work. I have the PVR-150 non MCE version and I can use the following programs with it, for example:

- MythTV
- vlc
- mplayer

In vlc, select the PVR tab and /dev/video0 or /dev/video1, depending on where your tv tuner is.

---

### Post by Krumar on 2008-05-06
Hey, thanks for the info on tvtime. I've tried to use vlc to watch tv but no success yet. My video card is under /dev/video0, I've switched to pvr, but haven't changed anything else, what other settings should I use?

---

### Post by little_penguin on 2008-05-07
If your tv card is on /dev/video0, you shouldn't have to set anything else on the PVR tab because that's the VLC default anyway. It should just work when you click OK. You might need to click NTSC or PAL, depending on where you live, in the Norm drop-down menu if Default doesn't work.

---

### Post by Krumar on 2008-05-07
When I try to view cable from VLC all I get is a black screen. I also do not get any error messages in the terminal. Changing to NTSC also didnt get me anywhere. I know that the card is good, I have tried it in a windows computer, can anyone tell me how I can tell if the chip in the card is not supported in linux? I've heard something about the 150's being shippied with a 1600 card or something and linux has no support for them at the moment.

Thanks

---

### Post by little_penguin on 2008-05-08
I don't how you check whether you have an unsupported 1600 one or not, but have you tried the following method?:

Open 2 terminals side by side, and in one terminal type, assuming your tv card is on /dev/video0:

```
mplayer /dev/video0
```

and in the second terminal, type

```
scantv -c /dev/video0 -C /dev/vbi0
```
or
```
ivtv-tune --freqtable=us-cable -cE8
```

and see whether it picks anything up.

"ivtv-tune --help" shows you all the options, same with scantv --help (or the manpages of course. I suspect you just need to tune the TV card, "ivtv-tune -L" lists the frequency tables you can select, so try different settings out. Good luck.

---

### Post by little_penguin on 2008-05-08
If you do discover you it's a substitute 1600, this is what it says on Mythtv.org:

Regarding PVR-150 Issues and Problems, I quote:

#  Hauppauge substituting HVR-1600s for PVR-150s. Current PVR-150 boxes actually contain HVR-1600s. Included is a note that says, "We have had a shortage of the WinTV-PVR-150 boards during the holiday season. Therefore, in place of the WinTV-PVR-150, we are including our new WinTV-HVR-1600" It seems the HVR-1600 is NOT supported by IVTV. People receiving the HVR-1600 but paying for a PVR-150 should return the card to their vendor and demand a refund or a replacement with a real PVR-150.

---

### Post by herteljt on 2008-06-08
> **Krumar said:**
> When I try to view cable from VLC all I get is a black screen. I also do not get any error messages in the terminal. Changing to NTSC also didnt get me anywhere. I know that the card is good, I have tried it in a windows computer, can anyone tell me how I can tell if the chip in the card is not supported in linux? I've heard something about the 150's being shippied with a 1600 card or something and linux has no support for them at the moment.

Thanks

Have you gotten your card to work?  I bought a 150 last week and I have been able to watch tv using VLC and MythTV (although Myth has some issues)

---

### Post by kb7ypf on 2008-06-09
Hi-

I finally got my PVR working with VLC, however I can't seem to change the channel.  Any suggestions?   Thanks.

---

### Post by herteljt on 2008-06-10
> **kb7ypf said:**
> Hi-

I finally got my PVR working with VLC, however I can't seem to change the channel.  Any suggestions?   Thanks.


See Wolfen69's response on the following thread

[http://www.backports.ubuntuforums.org/showthread.php?t=550409](http://www.backports.ubuntuforums.org/showthread.php?t=550409)

---

### Post by kb7ypf on 2008-06-10
herteljt-

Thanks very much for your help.  It solved the problem and works great.  

kb7ypf
Sierra Vista, az

---

### Post by herteljt on 2008-06-11
You're welcome!  I have also been able to record using the cat command (e.x. sudo cat /dev/video0 > /videos/test.mpg) and then edit out commercials using Avudemux (just look for it in synaptic).  

Two quirky things about recording (and I've only been doing this for two weeks)  1)  I needed to make the file test.mpg first (I used nano) and then set the permissions to rw  2) I cannot view and record at the same time (I get a device or resource busy error)  Anyway, I hope that helps you!

EDIT:  I figured out my first problem (permissions) but I still cannot view and record at the same time.

---

### Post by saedelaere on 2008-06-15
> **kb7ypf said:**
> Hi-

I finally got my PVR working with VLC, however I can't seem to change the channel.  Any suggestions?   Thanks.

Or you could try [this one]("http://ubuntuforums.org/showthread.php?t=763698") :)

Regards

---

