---
title: "A/V playback stuttery and getting worse - how to troubleshoot?"
date: 2011-01-02
forum: Multimedia Software
---

### Post by pickarooney on 2011-01-02
I've been having a problem with intermittent stuttering in video and audio playback since upgrading to Maverick (it also happened when I briefly installed Lucid). It started out as the odd skip every 20 minutes or so but now it can happen 5 or 6 times in 10 minutes when watching a film.

I've tried:

reformatting and clean installing
using a half-dozen players
installing every codec I could think of (only after the normal ones wouldn't help)
diangosing my 3 hard drives (the problem occurs on them all and they're not in a RAID setup)
changing then changing back my video drivers
disabling pulseaudio and ubuntuone-sync (these were not installed in my previous, working setup)
looking at every relevant log file (mplayer, smplayer, demsg...) I know of
running ubuntu's testing utilities

I'm out of ideas. Going back to Jaunty is the only solution I'm pretty sure will work but it's not exactly ideal. It will be a few months at least before I'm able to install a completely new distro.

---

### Post by BicyclerBoy on 2011-01-02
Start with:
What hardware is this machine ?
What GPU & driver version ?

Lucid by default installed nouveaux drivers for nvidia hardware ..

---

### Post by pickarooney on 2011-01-03
> **BicyclerBoy said:**
> Start with:
What hardware is this machine ?
What GPU & driver version ?

Lucid by default installed nouveaux drivers for nvidia hardware ..

CPU: AMD Athlon(tm) 64 Processor 3400+
RAM: 2GB, swap 2GB
GFX card: GeForce 8400 GS PCI-E 16x 512MB
nVidia drivers: 173.14.28 (I had the later ones initially after updating to Maverick but reverted to see if they would work better.
This install is Ubuntu 10.10 with XFCE desktop environment. Just prior I had a Xubuntu Lucid base install (for all of three days) and before that Xubuntu Jaunty.

---

### Post by pickarooney on 2011-01-04
Anyone got any clues?

---

### Post by cchhrriiss121212 on 2011-01-04
Try using newer drivers, 173 is quite old. Also try using smplayer with vdpau output, I have checked that your card supports it (vdpau requires >185 series drivers).
[URL="https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates"]
A PPA for newer drivers.[/URL]

---

### Post by pickarooney on 2011-01-04
I've tried with the latest video drivers initially but that's when I first noticed the problem. I get the same problem playing mp3s so I think maybe it's a kernel issue?

Also, I added that PPA and ran all the upgrades from update-manager but the gfx drivers did not update.

---

### Post by cchhrriiss121212 on 2011-01-04
Read this for the newer drivers:
[http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html](http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html)
When you say latest drivers, what do you mean? 260 series?

> I get the same problem playing mp3s so I think maybe it's a kernel issue?
Have you tried using another kernel?

---

### Post by lidex on 2011-01-04
So this is **not** using pulseaudio, correct?

---

### Post by pickarooney on 2011-01-05
I have removed pulseaudio as of two weeks ago and am using a basic ALSA sound server. I reinstalled the 260 series drivers directly from the Additional Drivers (jockey?) menu entry last night, with no change in performance. 

I will try a new kernel tonight. I'm currently using the latest one avaialble for Maverick via update-manager. Can anyone recommend a more recent kernel? I've looked at a tutorial on this site on how to install a new one, so know the procedure but am a bit wary of breaking dependencies if I get something too recent. 

Thanks for all the help so far, by the way :)

---

### Post by cchhrriiss121212 on 2011-01-05
If the sound is jerky, you could try installing alsa-backports which you should find in the repos.

A new kernel should not break any dependencies, but if it gives you trouble you can still switch back to the current version.

Edit: If you want a newer kernel give Zen a go:
[http://zen-kernel.org/tutorials/distribution-specific-installation/debian-ubuntu-installation](http://zen-kernel.org/tutorials/distribution-specific-installation/debian-ubuntu-installation)

---

### Post by pickarooney on 2011-01-09
I tried installing alsa backports and updating the kernel to 2.6.36-020636-generic but it's made absolutely no difference :(

---

