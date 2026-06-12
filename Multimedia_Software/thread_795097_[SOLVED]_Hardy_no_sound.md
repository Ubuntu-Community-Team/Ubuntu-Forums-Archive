---
title: "[SOLVED] Hardy no sound"
date: 2008-05-15
forum: Multimedia Software
---

### Post by Kissell on 2008-05-15
I have a fresh install of Ubuntu 8.04 x64 on an Asus F3T laptop and I'm getting absolutely no sound from anywhere.  

I did:
> sudo modprobe snd-

And it found no sound drivers installed. :(

Here's the kicker...  Ubuntu 8.04 x64 was already installed on this laptop as an upgrade from Ubuntu 7.10 x64 and sound was working in both 7.10 x64 and 8.04 x64 without any problems.  I replaced the hard disk and installed Ubuntu 8.04 fresh instead of upgrading from 7.10 x64, and now I have no sound. :(

---

### Post by Metaljaz on 2008-05-16
Type sudo lspci (assuming you have a pci sound card) in the terminal window and look for Multimedia audio controller. Check to see what sound card is recognized and see if there are drivers available. Post results here if more help is needed.

---

### Post by Gunman1982 on 2008-05-16
> **Kissell said:**
> 
sudo modprobe snd-

First of all that command doesn't tell you if there are sound driver installed, it tries to load the module 'snd-' which it can't find
If you want to know which modules are currently loaded then execute:
cat /proc/modules
however if the driver for your soundcard is compiled in the kernel you won't see it as a module either.

> **Kissell said:**
> 
Here's the kicker...  Ubuntu 8.04 x64 was already installed on this laptop as an upgrade from Ubuntu 7.10 x64 and sound was working in both 7.10 x64 and 8.04 x64 without any problems.  I replaced the hard disk and installed Ubuntu 8.04 fresh instead of upgrading from 7.10 x64, and now I have no sound. :(
What error do you get if you start a program that wants to use a sound device?
What does the command 'lsof | grep snd' return?

---

### Post by Kissell on 2008-05-16
Well, this is the output that I get with that command now that it's working: 
> pulseaudi 11053     kissell  mem       REG      8,161    357520   12278928 /usr/lib/libsndfile.so.1.0.17
pulseaudi 11053     kissell   15u      CHR      116,0                17195 /dev/snd/controlC0
pulseaudi 11053     kissell   21u      CHR      116,0                17195 /dev/snd/controlC0
gconf-hel 11058     kissell  mem       REG      8,161    357520   12278928 /usr/lib/libsndfile.so.1.0.17
mixer_app 11223     kissell   20u      CHR      116,0                17195 /dev/snd/controlC0


It was important, and I know it used to work, and it was a fresh install anyway, so I just reinstalled Ubuntu x64 Gutsy and let it upgrade to Hardy and when I do that my sound works just fine, but when I install Ubuntu x64 Hardy directly, sound doesn't work.  

One big difference I noticed, was when I do > uname -r it now says "2.6.24-16-generic" after letting it upgrade x64 gutsy server, but when the sound wasn't working it said "2.6.24-16-server" as I had installed it from the x64 hardy server disk.  

So in short, the kernel is different when x64 server is upgraded to hardy versus when x64 hardy server is installed directly.  And I have 2.6.24-16-server loaded on a different machine and the sound works there, so whatever I need to make my audio work on this laptop is not part of the 2.6.24-16-server kernel but is part of the 2.6.24-16-generic kernel...  go figure...  
:confused:

---

