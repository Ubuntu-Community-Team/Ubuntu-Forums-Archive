---
title: "Live TV freezes"
date: 2007-12-10
forum: Mythbuntu
---

### Post by e1jones on 2007-12-10
within 10 seconds of switching to watching live TV, the entire computer locks up and requires forced reboot.

saw the post here [http://ubuntuforums.org/showthread.php?t=582459](http://ubuntuforums.org/showthread.php?t=582459) so tried mplayer, which said

```
eddie@mythbox:~$ mplayer -tv driver=v4l:width=640:height=480:outfmt=i420 -vc rawi420 -vo xv tv://
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 43, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Creating config file: /home/eddie/.mplayer/config

Playing tv://.
TV file format detected.
Selected driver: v4l
 name: Video 4 Linux input
 author: Alex Beregszaszi
 comment: under development
=================================================================
 WARNING: YOU ARE USING V4L DEMUXER WITH V4L2 DRIVERS!!!
 As the V4L1 compatibility layer is broken, this may not work.
 If you encounter any problems, use driver=v4l2 instead.
 Bugreports on driver=v4l with v4l2 drivers will be ignored.
=================================================================
Selected device: WinTV PVR 500 (unit #1)
 Capabilites: capture tuner teletext 
 Device type: 7
 Supported sizes: 48x32 => 720x480
 Inputs: 5eddie@mythbox:~$ mplayer -tv driver=v4l:width=640:height=480:outfmt=i420 -vc rawi420 -vo xv tv://
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 43, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Creating config file: /home/eddie/.mplayer/config

Playing tv://.
TV file format detected.
Selected driver: v4l
 name: Video 4 Linux input
 author: Alex Beregszaszi
 comment: under development
=================================================================
 WARNING: YOU ARE USING V4L DEMUXER WITH V4L2 DRIVERS!!!
 As the V4L1 compatibility layer is broken, this may not work.
 If you encounter any problems, use driver=v4l2 instead.
 Bugreports on driver=v4l with v4l2 drivers will be ignored.
=================================================================
Selected device: WinTV PVR 500 (unit #1)
 Capabilites: capture tuner teletext 
 Device type: 7
 Supported sizes: 48x32 => 720x480
 Inputs: 5
  0: Tuner 1: tuner tv  (tuner:1, norm:ntsc)
  1: S-Video 1:  (tuner:0, norm:ntsc)
  2: Composite 1:  (tuner:0, norm:ntsc)
  3: S-Video 2:  (tuner:0, norm:ntsc)
  4: Composite 2:  (tuner:0, norm:ntsc)
Using input 'Tuner 1'
ioctl get mbuf failed: Invalid argument


MPlayer interrupted by signal 11 in module: demux_open
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

  0: Tuner 1: tuner tv  (tuner:1, norm:ntsc)
  1: S-Video 1:  (tuner:0, norm:ntsc)
  2: Composite 1:  (tuner:0, norm:ntsc)
  3: S-Video 2:  (tuner:0, norm:ntsc)
  4: Composite 2:  (tuner:0, norm:ntsc)
Using input 'Tuner 1'
ioctl get mbuf failed: Invalid argument


MPlayer interrupted by signal 11 in module: demux_open
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

```

this is off a mythbuntu final release that has been fully patched.  Not really sure  whats going wrong.

secondary issue, its only displaying anything on the low channels, mostly 2-10 or so.  but with it locking up, i'm not sure exactly.

Hardware:
Foxconn 6150K8MA-8EKRS 939 NVIDIA GeForce 6150
AMD 3800X2
1 gig ram
Hauppauge WinTV-PVR 500 MCE PVR
GIGABYTE GV-NX73L128D-RH GeForce 7300LE
500gig hard drive

suggestions appreciated...  Thanks.

---

### Post by e1jones on 2007-12-11
fiddled with it some last night with no luck.  might dig out the PVR-150 and replace the -500 to see if thats an issue.  

any other ideas appreciated.

---

