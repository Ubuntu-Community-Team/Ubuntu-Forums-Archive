---
title: "Bizarre playback issues in Rhythmbox/Musepack/OSS"
date: 2009-05-13
forum: Multimedia Software
---

### Post by leptogenesis on 2009-05-13
I currently have 2 ubuntu boxes--a desktop and a laptop.  Whenever I try to play a musepack audio file on my desktop using rhythmbox, the playback is really weird--it cycles about once every half second between silence and playing the song (the sound is really distorted, too, although it doesn't sound like it's sped up).  

Even stranger, the same files play fine in the same version of rhythmbox on my laptop.  They also play fine on my desktop when I use totem (also using gstreamer).  The only important difference I can think of is that I use OSS on my desktop (I know I know...not technically supported, but on Intrepid, I couldn't get ALSA to work for the life of me).  Of course, if OSS were causing the problems, I would have expected to hear the same thing whenever I used gstreamer with muspack...but I didn't.

I'm currently running Ubuntu Jaunty on both boxes.  

Any suggestions on how to go about troubleshooting this?

---

### Post by psyke83 on 2009-05-13
> **leptogenesis said:**
> I currently have 2 ubuntu boxes--a desktop and a laptop.  Whenever I try to play a musepack audio file on my desktop using rhythmbox, the playback is really weird--it cycles about once every half second between silence and playing the song (the sound is really distorted, too, although it doesn't sound like it's sped up).  

Even stranger, the same files play fine in the same version of rhythmbox on my laptop.  They also play fine on my desktop when I use totem (also using gstreamer).  The only important difference I can think of is that I use OSS on my desktop (I know I know...not technically supported, but on Intrepid, I couldn't get ALSA to work for the life of me).  Of course, if OSS were causing the problems, I would have expected to hear the same thing whenever I used gstreamer with muspack...but I didn't.

I'm currently running Ubuntu Jaunty on both boxes.  

Any suggestions on how to go about troubleshooting this?

PulseAudio is responsible for sound mixing and playback (using the ALSA kernel drivers). It so happens that there are bugs in the intel8x0 and intel-hda ALSA kernel drivers in conjunction with PulseAudio that causes issues similar to what you describe.

Enable the "proposed" repository and upgrade to kernel 2.6.28-12-generic, as it contains fixes for those drivers, which I'm guessing you have.

P.S. Don't use OSS output, it's too messy. It's actually OSS emulation via the ALSA kernel drivers, and OSS output doesn't support sound mixing (and also causes mixing errors with other applications that rely on PulseAudio too). See my PulseAudio guide for more information.

---

### Post by leptogenesis on 2009-05-17
Sorry I took so long...been busy...

I'm now running 2.6.28-12-generic, but the problem isn't fixed.

Also, I actually was using OSS--that is, I uninstalled alsa and installed OSS by downloading .deb files from the Open Sound website.  When installing, it would tell me it was building kernel modules.  Anyway, I completely uninstalled OSS and switched back to ALSA (I've been meaning to try for a while).  However, it doesn't seem to have changed--only musepack in rhythmbox fails.  So I guess this isn't an OSS-specific issue, it's more a sound card issue.

Any other ideas?

Edit: Actually, after the changes, when I open a musepack file with rhythmbox, it seems more commonly to try to play the file for a few seconds (the slider moves, but there's no sound), and then hang.

---

### Post by leptogenesis on 2009-05-20
Just as an update: musepack now appears to make rhythmbox hang on my laptop, too.

---

### Post by andrew.46 on 2009-05-24
Hi leptogenesis,

> **leptogenesis said:**
> Just as an update: musepack now appears to make rhythmbox hang on my laptop, too.

Can you post one of these troublesome files somewhere? Bear in mind that version 8 has been released, have you found some files with the new format?

All the best,

Andrew

---

