---
title: "ALSA works OSS does not"
date: 2008-11-27
forum: Multimedia Software
---

### Post by sirhalos on 2008-11-27
I just purchased a new computer and brought it home and installed Ubuntu on it. Everything was detected and works however OSS does NOT work.

I play World of Warcraft and the sound quality using ALSA is just horrible however in winecfg when doing a test for OSS it doesn't find it.

Going into sound preferences and trying OSS in there also gives no sound.

I tried just going ahead and setting my winecfg to OSS then using aoss but that doesn't seem to produce any sound either.

I can't seem to figure out how to see if OSS is even is installed. It should be it works on my old system unless some reason it didn't install it on this one.

**UPDATE:**

Since this is a new system I want to make sure it's working correctly. I installed Fedora 10 and I was able to use OSS just fine but since I don't like Fedora I put Ubuntu back on hoping I can fix this problem.

Doing a lspci | grep Audio comes up with nothing at all.

Doing a cat /proc/asound/cards comes up with this

1 [default        ]: USB-Audio - PnP Audio Device        
                      PnP Audio Device         at usb-0000:00:02.0-7, full speed

Which is odd since it's not a USB device.


Anyway if anyone has any ideas or thoughts I can look into I would greatly appreciate it.

The motherboard is Asus M2N-SLI my internet searching is not coming up with much.

---

### Post by IQRules on 2008-11-29
Since this is a new system I want to make sure it's working correctly. I installed Fedora 10 and I was able to use OSS just fine but since I don't like Fedora I put Ubuntu back on hoping I can fix this problem.

So winecfg no problem under Fedora?

I have this issue.

g@ubuntu:~$ winecfg
ALSA lib pcm_dsnoop.c:593:(snd_pcm_dsnoop_open) unable to open slave

How about your?

@ubuntu:/proc/asound$ cat cards
 0 [I82801CAICH3   ]: ICH - Intel 82801CA-ICH3
                      Intel 82801CA-ICH3 with AD1881A at irq 11

I do get the sound from YouTube, but no sound under Wine env.

---

