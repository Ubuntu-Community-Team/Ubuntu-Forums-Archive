---
title: "Only VLC can play it, but only the Windows version! OR Envidia does it again!"
date: 2010-04-04
forum: Multimedia Software
---

### Post by gwm on 2010-04-04
I recently upgraded my hardware to 64 bit dual core and a new Nvidia graphics card - GeForce 210.
When I tried to play a BBC documentary, nothing happened. I think movie player starts up and promptly crashes. I tried starting the program manually and asking it to play the DVD. The program crashed and "vanished before my eyes". Oh well! another nvidia story!
I dual booted and even Windows Media Player (latest version), refused to play the DVD, complaining of some security mismatch or something to do with the video card driver.
I downloaded and installed VLC, windows version and all went well. Returning to Ubuntu, I found that the Linux version of VLC failed. (I have installed the proprietary drivers)

---

### Post by LuridCinema on 2010-04-04
Did you re-install the OS ? 64 or 32 bit OS ?  more info plz

---

### Post by Jive Turkey on 2010-04-04
Do you have the libdvdcss2 package installed?  I might have the package name wrong but its in the medibuntu repositories.  You need it to play encrypted DVDs.

---

### Post by gwm on 2010-05-16
I just install - no fancies.
As mentioned, Windows XP also misbehaved. I noticed that My Windows Update provided new Nvidia drivers recently. Upgrading to Lucid Lynx has resolved the problem. I believe it was a driver issue.

Yes I reinstalled from the live CD (64 bit).

I thought the problem was solved but it has resurfaced. What has changed? I seem to remember turning on visual effects so that I could have wobbly windows.

I'm going to check out libdvdcss2 and try removing visual effects again.

---

### Post by gwm on 2010-06-01
Thank you Jive Turkey,

libdvdcss2 did it.

I've bookmarked medibuntu so that I (hopefully) won't keep forgetting about it each time I upgrade. What a nice helpful site.

---

