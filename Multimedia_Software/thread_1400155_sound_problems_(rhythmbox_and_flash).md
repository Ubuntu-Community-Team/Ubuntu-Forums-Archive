---
title: "sound problems (rhythmbox and flash)"
date: 2010-02-06
forum: Multimedia Software
---

### Post by galbez on 2010-02-06
Hello everyone,

My name is Gal, and I've been using Ubuntu 9.10 (installed from scratch on new hard disk) for three weeks now - so I'm quite a newbie with this OS. 
So far, I'm very pleased, but since I use my PC mostly for music,  I do experiance minor problems.

I should mention I play both mp3 files and audio CD's, and that PulseAudio and ALSA mixer are installed.

When opening RB right after turning the PC on, everything works fine. But sometimes, after closing RB, and opening it again, when I try to play anything, it doesn't work - the song stucks at 0:00. This also appears in VLC (in VLC the progress-bar moves, but no sound)!
Sometimes, after playing music in RB, sound on Youtube is gone (I already solved the earlier, known "no sound in flash" issue - it's not the same).

I searched your forums for these issues, but most of them repeated the same things, the answers given were for different issues, or were too complicated (or too many). If there is already a solution to what I described, a link would be enough.

Anyhow, the best solution I found for all of these problems (which I believe are related to each other) is restarting the PC, but doing it several times a day isn't normal...

What's wrong?

Thanks in advance to anyone who would help!

---

### Post by sleepee on 2010-02-06
hey gal.  that's weird, because i have a similar problem i'm dealing with now...and i suspect alsa.

anyway, i'm pretty much a noob with ubuntu too, but i'm pretty sure you're going to have to tell us some things about your setup before anybody can help you.
like your computer model, your "aplay -l" output, and maybe your alsa version for starters...

but just out of curiosity, when you open VLC and it has no sound or RB and it stays stuck at 0:00, do you also happen to have a flash movie playing at the same time??

---

### Post by galbez on 2010-02-11
First of all, I'm sorry for answering just now. I'm not home during all week. Thank you for your quick reply!

Well, my computer model is a Pentium 4 3.0GHz, intel board with integrated sound card. Bought it about 5 years ago. if you need more details specify them.

what is "aplay -l" output?

and where can I check my ALSA version? I can tell you I've installed PulseAudio package (Device Chooser version: 0.9.3-2ubuntu4), if that helps.

about playing both flash and RB/VLC, I'll pay more attention. Why is that problematic?

thanks again!

---

### Post by mukhtar.mohammed on 2010-02-11
Hi,
i have a problem with F-open,
when it opens and all diappears.
i tried typing f-open in terminal and here is the output screen.

 (/usr/lib/f-spot/f-spot.exe:5448): GLib-WARNING **: g_set_prgname() called multiple times
[Info  20:02:12.160] Initializing DBus
[Info  20:02:12.390] Initializing Mono.Addins
[Info  20:02:12.692] Starting new FSpot server (f-spot 0.6.1.5)

** (/usr/lib/f-spot/f-spot.exe:5448): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:5448): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:5448): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:5448): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:5448): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  20:02:14.149] Starting BeagleService
[Info  20:02:14.225] Hack for gnome-settings-daemon engaged

(/usr/lib/f-spot/f-spot.exe:5448): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
The program '/usr/lib/f-spot/f-spot.exe' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 2938 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.



what do i have to do to fix it :(.

---

### Post by sleepee on 2010-02-11
> **galbez said:**
> First of all, I'm sorry for answering just now. I'm not home during all week. Thank you for your quick reply!

Well, my computer model is a Pentium 4 3.0GHz, intel board with integrated sound card. Bought it about 5 years ago. if you need more details specify them.

what is "aplay -l" output?

and where can I check my ALSA version? I can tell you I've installed PulseAudio package (Device Chooser version: 0.9.3-2ubuntu4), if that helps.

about playing both flash and RB/VLC, I'll pay more attention. Why is that problematic?

thanks again!

for your "aplay -l", go into the terminal (Applications -> Accessories -> Terminal), and type in
```
aplay -l
```

it should give you a list that looks something like this

```
sleepee@sleepee-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

as far as the alsa version, in the same terminal, you can type 
```
alsamixer
```

at the top it will tell you the alsa version number..

tbh, i have no idea why there's a sound conflict between flash and the other system sounds, but your problem sounds pretty similar to mine.
that's why i ask you about flash..  it seems to me you're experiencing the same behavior i am, and i think we're in the same boat..

anyway, if you want, you can check out this thread:
[http://ubuntuforums.org/showthread.php?p=8812200#post8812200](http://ubuntuforums.org/showthread.php?p=8812200#post8812200)

the guy named jitachi has tried removing pulseaudio and leaving alsa and apparently that works for him.
i might try that, but i'm hoping there's another solution that doesn't have to take out PA.
or as a temporary workaround for vlc..  you can set vlc to use alsa and then vlc will work while flash plays too.
or, instead of restarting the computer when sound in RB or VLC goes out, i sometimes just close firefox (sometimes through System Monitor)... or sometimes just the tabs with flash in them... and the system sounds come right back..

---

### Post by James M on 2010-02-11
> **mukhtar.mohammed said:**
> Hi,
i have a problem with F-open,
when it opens and all diappears.
i tried typing f-open in terminal and here is the output screen.

 (/usr/lib/f-spot/f-spot.exe:5448): GLib-WARNING **: g_set_prgname() called multiple times
[Info  20:02:12.160] Initializing DBus
[Info  20:02:12.390] Initializing Mono.Addins
[Info  20:02:12.692] Starting new FSpot server (f-spot 0.6.1.5)

** (/usr/lib/f-spot/f-spot.exe:5448): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:5448): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:5448): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:5448): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:5448): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  20:02:14.149] Starting BeagleService
[Info  20:02:14.225] Hack for gnome-settings-daemon engaged

(/usr/lib/f-spot/f-spot.exe:5448): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
The program '/usr/lib/f-spot/f-spot.exe' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 2938 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.



what do i have to do to fix it :(.

ALSA has had these problems since its birth... :/ yet it is still not fixed. I honestly don't know how to fix these issues either. I have toyed and tweaked for hours and never got anything done.

---

### Post by galbez on 2010-02-12
my aplay output:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

my alsamixer output:
```
AlsaMixer v1.0.20
```

btw, I noticed playing both flash and RB/VLC causes this problem (usually).
So, how do I uninstall alsa and replace it with the lastest version?
And asides the thread you posted, isn't there any other solution?

thank you all.

---

### Post by VertexPusher on 2010-02-12
> **James M said:**
> ALSA has had these problems since its birth... :/ yet it is still not fixed.
If you actually read the post that you quoted, you would have noticed that mukhtar.mohammed's problem has nothing to do with sound at all.

---

### Post by VertexPusher on 2010-02-12
> **galbez said:**
> So, how do I uninstall alsa and replace it with the lastest version?
You don't, because the problem you describe is not caused by ALSA but PulseAudio. If you remove PulseAudio, the problem will be gone.

To uninstall PulseAudio, enter these commands:
```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio vlc-plugin-pulse
```
To get PulseAudio back (including all its issues), enter this:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by galbez on 2010-02-12
are you sure?

what does sleepee thinks about it?

I also found it difficult to configure 5.1 support without PA. if I'll uninstall PA, how can I do that again?

---

### Post by sleepee on 2010-02-12
> **galbez said:**
> are you sure?

what does sleepee thinks about it?

I also found it difficult to configure 5.1 support without PA. if I'll uninstall PA, how can I do that again?

lol!!  trust me...vertex probably knows a lot more than i do.  i've only been using ubuntu for a few months.  the little bit i know is from messing around with my setup and trying to fix my own sound issues..

but as as upgrading alsa to the latest version, check out this thread
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)
^^
that makes upgrading alsa very easy... at least it was for me.

and vertex is probably right about PA...
but just in case you might not have to uninstall PA, check out this thread and see if it helps.. it's like a PA troubleshooting guide.
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

if none of that works, i'm guessing you should do what vertex says and just uninstall PA..  and if that doesn't work, i'm sure you can install PA again without too much hassle.

---

### Post by sleepee on 2010-02-12
> **mukhtar.mohammed said:**
> Hi,
i have a problem with F-open,
when it opens and all diappears.
i tried typing f-open in terminal and here is the output screen.

 (/usr/lib/f-spot/f-spot.exe:5448): GLib-WARNING **: g_set_prgname() called multiple times
[Info  20:02:12.160] Initializing DBus
[Info  20:02:12.390] Initializing Mono.Addins
[Info  20:02:12.692] Starting new FSpot server (f-spot 0.6.1.5)

** (/usr/lib/f-spot/f-spot.exe:5448): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:5448): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:5448): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:5448): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:5448): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  20:02:14.149] Starting BeagleService
[Info  20:02:14.225] Hack for gnome-settings-daemon engaged

(/usr/lib/f-spot/f-spot.exe:5448): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
The program '/usr/lib/f-spot/f-spot.exe' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 2938 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.



what do i have to do to fix it :(.

you should probably start your own thread about this problem.  you'll probably get helped out a lot better and faster that way.
because people will come into this thread for galbez's specific sound problem and might not be able to help you...

---

### Post by James M on 2010-02-12
> **VertexPusher said:**
> If you actually read the post that you quoted, you would have noticed that mukhtar.mohammed's problem has nothing to do with sound at all.

Actually it does have something to do with sound. If audio does not play the current audio server is in use by something else and hoggs it. It is about sound.

---

### Post by galbez on 2010-02-18
Hi again, I'm back.

Thanks for your reply (both vertex and sleepee),
I'll put it this way:
I just want 5.1 support in ubuntu, and get it the simplest way. PA was the best option to achieve it, but it had it's issues...

Thank you!

---

