---
title: "Video streaming on ancient hardware"
date: 2011-01-10
forum: Multimedia Software
---

### Post by alanpol on 2011-01-10
I've recently found a Dell Optiplex GX110 - about 10 years old with a Pentium III.  I installed Ubuntu 10.04 no problems, and it behaves quite well, despite its age.

However, if I try and stream video from web sites (youtube, bbc etc), the result is underwhelming - very jumpy images, although sound is fine.  Interestingly, viewing video files through VLC does not have such an issue - it seems to be OK - it is just http streaming (typically Flash) where I observed the issue.

I found an old graphics card - a ATI Radeon 7000 and installed it.  However, I saw no improvement in streaming video performance.  I was a little surprised, but would like to understand the reason - is it:

[LIST]
[*]the card is so low spec it would not make a difference, or is it that:
[/LIST]

[LIST]
[*]the card *ought* to make a difference, but is not configured and/or performing correctly
[/LIST]
Note that Ubuntu appears to correctly find the card - lspci shows it correctly identified.  The integrated VGA controller still shows, but cannot be disabled from the BIOS.

---

### Post by BicyclerBoy on 2011-01-10
That CPU must be older than that?

Streamed video is heavy compressed so is CPU intensive.

Your CPU is not very MMX capable.

Video playback is decode & presentation.
A GPU and supporting player can decode in hardware (vdpau etc)

The presentation part is overlaying/moving/de-interlacing etc.
Your video hardware could do the overlay part with a correct driver.

Your machine has low bus bandwidth & all the video has to be CPU decompressed & sent to the video card for display.

I doubt there is any video card that can help.

---

### Post by cchhrriiss121212 on 2011-01-10
Flash runs poorly on Linux, but it is getting better. The best you can do with that hardware is to open the flv files from the temporary browser cache. In firefox type about:plugins into the address bar to see where they are stored then play with VLC.

---

