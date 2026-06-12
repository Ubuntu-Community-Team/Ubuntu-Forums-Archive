---
title: "Issues with gnomad2 and Zen X-Fi"
date: 2009-08-18
forum: Multimedia Software
---

### Post by I[AM]SMRT on 2009-08-18
So I've just recently uninstalled my windows/ubuntu dual boot and moved to Arch, mainly because I never used windows and wanted something more lightweight than Ubuntu. The one thing I used windows for was to update my creative zen x-fi, which was pretty simple on xp but I'm having quite a bit more trouble doing it on linux distros.

I've actually gotten a lot farther than I had before, my laptop now recognizes when my mp3 player is connected and I can access it with mtp-detect and gnomad2, with one condition, I have to first unmount it from nautilus otherwise I get this:

```
brian@brian-laptop:~$ mtp-detect
libmtp version: 0.3.7

Listing raw device(s)
   Found 1 device(s):
   Creative: ZEN X-Fi (041e:4162) @ bus 0, dev 6
Attempting to connect device(s)
usb_claim_interface(): Device or resource busy
LIBMTP PANIC: Unable to initialize device
Unable to open raw device 0
OK.
```

Now that's just a minor annoyance, I can deal with that. Going about my business, I transfer files from my computer to the device but wait, the metadata tags I have on my computer don't get transferred. grrr, ok whatever, I can change those tags on the device, really annoying but I can deal with it if it just transfers my music. Ok, all done, close gnomad2, it freezes, causing my mp3 player to freeze and when I hard reset my mp3 player, I find that none of the music has transferred. MAJOR ANNOYANCE.

Please help :(,
SMRT

---

