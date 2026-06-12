---
title: "Problems with recording audio"
date: 2009-02-09
forum: Multimedia Software
---

### Post by rfkrocktk on 2009-02-09
Hi all.
I just got a pretty sweet headset for recording audio with. Overall, it sounds great, but I've been experiencing some really weird bugs with recording audio across a bunch of different programs. 

I can use Skype just fine, though sometimes it gets a little bit garbled, I think that might be whatever it's using for encoding, but yeah. I can also use Audacity for recording audio fairly well, though I've noticed the same "garbliness" and some really crazy encoding problems which apparently repeat a segment of the recording, as if something is going wrong with whatever it's using to encode. My main purpose in getting this headset was to make screencasts using recordmydesktop, and that has been the least successful of all of the things I have tried. When I try to use gtk-recordmyDesktop, it pretty much always fails and will not encode my recording after I have finished. When I try to use the commandline client, it will only sometimes actually produce my screencast, and all of the audio will be garbled into the first few seconds of the video. 

When I run the commandline client for recordmydesktop (if it works), I'll get output somewhat like this:

> :~$ recordmydesktop -device hw:default,0
Initial recording window is set to:
X:0   Y:0    Width:1280    Height:800
Adjusted recording window is set to:
X:0   Y:0    Width:1280    Height:800
Your window manager appears to be Metacity

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
Opened PCM device hw:default,0
Playback frequency 22050Hz is not available...
Using 44100Hz instead.
Recording on device hw:default,0 is set to:
1 channels at 44100Hz
Capturing!
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Broken pipe: Underrun occurred.
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7ab6767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7ab68b1]
#2 /usr/lib/libX11.so.6 [0xb7f0f421]
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7ef7734]
#4 recordmydesktop [0x8051776]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7dd54fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b8ee5e]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7ab6767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7ab681e]
#2 /usr/lib/libX11.so.6 [0xb7f0f518]
#3 /usr/lib/libX11.so.6(_XReply+0x140) [0xb7f10200]
#4 /usr/lib/libXfixes.so.3(XFixesGetCursorImage+0xb8) [0xb7c51608]
#5 recordmydesktop [0x804e7e6]
#6 /lib/tls/i686/cmov/libpthread.so.0 [0xb7dd54fb]
#7 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b8ee5e]
Broken pipe: Underrun occurred.
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7ab6767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7ab68b1]
#2 /usr/lib/libX11.so.6 [0xb7f0f421]
#3 /usr/lib/libX11.so.6(XNextEvent+0x74) [0xb7ef7734]
#4 recordmydesktop [0x8051776]
#5 /lib/tls/i686/cmov/libpthread.so.0 [0xb7dd54fb]
#6 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b8ee5e]
Saved 29 frames in a total of 44 requests
Broken pipe: Underrun occurred.
Shutting down.....
Encoding started!
This may take several minutes.
Pressing Ctrl-C will cancel the procedure (resuming will not be possible, but
any portion of the video, which is already encoded won't be deleted).
Please wait...
[82%] 
Encoding finished!
Wait a moment please...
   
Done.
Written 723109 bytes
(688761 of which were video data and 34348 audio data)

Cleanning up cache...
Done!!!
Goodbye!

I don't know how to explain this really strange behavior. One thing I have noticed that's kind of out of the ordinary is on boot. I get an error for my BIOS, something like "Error 81 Detected [XXXXXXXXX]" where X is a bunch of numbers I'm not fast enough to write down. I also get a message saying "Media Check Failure...", but Ubuntu runs relatively fine for me. 

Is there anything I'm missing here, a connection between these two problems?

---

### Post by rfkrocktk on 2009-02-10
Has anyone else noticed if BIOS bug 81 screws things related to sound up?

---

### Post by rfkrocktk on 2009-02-11
The mic is running through USB. I'm going to try and plug a jack mic in and see if that helps at all.

---

### Post by rfkrocktk on 2009-03-01
That's not really helping at all. I can record audio with other programs fine, but if I'm doing any screen capturing at all, I cannot record any audio period. I came up with a workaround idea, which failed. I thought to myself: "I can record my audio with Audacity and record my desktop with recordMyDesktop, and patch it together in post!" Fail. I can record the audio, but it causes recordmydesktop to fail. 

Can anyone help me with this? This, if I can't find a way to do it, will force me to resort to using Windows... :(

---

### Post by grantbuntu on 2009-05-28
Unable to help sorry but I also get garbled, jumbled audio at the beginning of the video plus a whole lot of:

```
2 channels at 44100Hz
Capturing!
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
etc etc
```

Prior to that the feedback is:

```
Opened PCM device hw:0,0
Playback frequency 22050Hz is not available...
Using 44100Hz instead.
```

---

### Post by rfkrocktk on 2009-05-28
Try using different Hz settings, when I set mine to record at 48000 Hz, everything worked great. Hope that helps!

---

### Post by grantbuntu on 2009-05-28
Still doesn't work for me.  Although (annoyingly/interestingly/encouragingly ;-)) I have no problem using gtk-recordmydesktop on my Jaunty notebook.  The defaults worked fine there.

According to 

```
lspci -v
```

I have an Intel 82801H (ICH8 Family) HD Audio Controller on the notebook.

The desktop with the problem has

```
Multimedia audio controller: Creative Labs CA0106 Soundblaster
```

I have another Ubuntu desktop with different hardware and I might see how that goes using what hardware.

---

### Post by grantbuntu on 2009-05-29
SOLVED - see [http://p-s.co.nz/wordpress/?p=490]("http://p-s.co.nz/wordpress/?p=490").  I had to set Advanced>Sound>device from DEFAULT to default (no kidding!).  A frequency of 48000 worked for me.  I need an amazed, head-shaking emoticon to capture how I felt when that worked.

---

