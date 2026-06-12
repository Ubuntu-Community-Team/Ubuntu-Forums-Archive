---
title: "Only left channel has sound"
date: 2006-06-23
forum: Multimedia &amp; Video
---

### Post by trigg3r on 2006-06-23
On a VIA 823x rev 70 device and
Realtek ALC655 rev 1 chipset, only the left channel has sound. I've tried adjusting levels in alsamixer, to no avail.

Has anyone gone through the same problem and tried solutions? Thank you!

---

### Post by Gannin on 2006-06-24
I know this may seem simple, but have you tried twisting the plug on the speaker cable back and forth a few times where it plugs into the computer?

---

### Post by trigg3r on 2006-06-25
[QUOTE=Gannin]I know this may seem simple, but have you tried twisting the plug on the speaker cable back and forth a few times where it plugs into the computer?[/QUOTE]
Hi Gannin! I wish the problem was just that, but yes, I did try swapping headsets, and still just the left channel. I'm using a headset by the way. I don't have a speaker set to try it out with.

---

### Post by Gannin on 2006-06-26
Have you tried playing around in alsamixer to see if there was anything interesting in there that might help you?

---

### Post by ronoholiv on 2006-07-03
I have a Biostar M7VIG400 motherboard with onboard VIA 823x AC'97 chip (CHIP: CMI9761A), and it presents the same problem when speakers or headsets are plugged into it completely.  I have found that both channels work when the speaker/headset is not completely plugged into the port.  The GNOME Volume Applet says I'm using GStreamer 0.10.  I hope that helps those who may know how to fix the problem.

Edit: Actual chip is C-Media CMI9761, according to alsamixer
Edit2: Okay, my fault, both channels are not working, just sound coming from both speakers.

---

### Post by trigg3r on 2006-07-05
[QUOTE=Gannin]Have you tried playing around in alsamixer to see if there was anything interesting in there that might help you?[/QUOTE]

Hi there, Gannin. Been out of town. Yes, I've actually played around with it and still nothing. But I was able to make it work when I removed alsamixer, and installed it back again. Very weird behavior, but it works now, and thanks for your comments.

---

