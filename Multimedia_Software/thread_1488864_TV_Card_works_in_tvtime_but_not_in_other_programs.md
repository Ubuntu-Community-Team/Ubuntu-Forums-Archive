---
title: "TV Card works in tvtime but not in other programs"
date: 2010-05-20
forum: Multimedia Software
---

### Post by flux7d on 2010-05-20
Hello everybody :)
This is my problem, I get perfect picture with Tvtime, but can't watch /dev/video0 with any other programs, I've checked if some proccess use it, and it's not it.

I wan't to watch this with vlc, tv-viewer or other programs to record, but when it doesn't recognize anything!

Anyone can help?

---

### Post by xzero1 on 2010-05-20
In your case, tvtime is probably controlling your capture card and /dev/video0 is not a video stream. Tvtime has been configured with specific parameters such as tvinput,broadcast type (pal,ntsc) etc which are unknown to vlc. Vlc can probably be made to work, once these parameters are correctly set in vlc. I don't know anything about tv-viewer but it might have the same issues as vlc.

---

### Post by flux7d on 2010-05-20
So is there any solution?

---

### Post by xc3RnbFO8P on 2010-05-20
Is your TVcard **pci** or **usb**?

---

### Post by flux7d on 2010-05-20
pci... it's winfast 2000 something can't remember..
this is lspci output:

04:01.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
04:01.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

---

### Post by xc3RnbFO8P on 2010-05-20
In Terminal show the output of:
> lspci -vnn

---

### Post by flux7d on 2010-05-20
04:01.0 Multimedia video controller [0400]: Brooktree Corporation Bt878 Video Capture [109e:036e] (rev 11)
    Subsystem: LeadTek Research Inc. Device [107d:6609]
    Flags: bus master, medium devsel, latency 32, IRQ 19
    Memory at e3200000 (32-bit, prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: bttv
    Kernel modules: bttv

04:01.1 Multimedia controller [0480]: Brooktree Corporation Bt878 Audio Capture [109e:0878] (rev 11)
    Subsystem: LeadTek Research Inc. Device [107d:6609]
    Flags: bus master, medium devsel, latency 32, IRQ 11
    Memory at e3201000 (32-bit, prefetchable) [size=4K]
    Capabilities: <access denied>


thank you for helping me :)

---

### Post by xc3RnbFO8P on 2010-05-20
This is a Analog TVcard so TVtime is the only program that will work :(
[http://www.linuxtv.org/wiki/index.php/Leadtek_WinFast_2000]("http://www.linuxtv.org/wiki/index.php/Leadtek_WinFast_2000")

---

### Post by flux7d on 2010-05-20
Ok i think i understand, I think i tried some config a week ago, and now I can watch through vlc from /dev/vbi0

But vlc crash when I try to capture ?? 
any other program recommended for capturing (not myth tv)

ty

---

### Post by xc3RnbFO8P on 2010-05-20
Read this:
[http://ubuntuforums.org/showthread.php?t=921233]("http://ubuntuforums.org/showthread.php?t=921233")

---

### Post by flux7d on 2010-05-20
Well Again, thank you for helping :)

To tell you the truth i came across this, but i'm using #! (openbox) and can't figure how to do this, I'm kind of newbie

---

### Post by xc3RnbFO8P on 2010-05-20
Read this:
[http://foxmediacenter-extension.blogspot.com/p/features.html]("http://foxmediacenter-extension.blogspot.com/p/features.html")

---

