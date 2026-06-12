---
title: "Sapphire IPC-E350M1W and Realtek ALC662 - no sound on 12.10"
date: 2012-12-27
forum: Multimedia Software
---

### Post by Nickroche on 2012-12-27
I've been fighting with this mobo for a week now and cannot get sound to work on it with Ubuntu 12.10 Minimal.
Searching  around the net, there seem to have been issues with this Realtek  chipset and versions of it a long time ago, but they disappeared from  any recent threads, making me think they were solved - but I can't see  where or how. 
To make things worse, I did a test install of Ubuntu 12.10 full and the sound is perfect. Arrr! 

Anyway. Here is what I have done, after a clean install of minimal with XBMC eden: 

- Installed Asla
- Installed Pulse Audio
- Uninstalled Pulse Audio
- Added various versions of this to asla-base.conf:
options snd_hda_intel model=auto
-  Installed the "realtek" drivers from their website. I followed all the  instructions in the tarball Audio Installation guide and they seem  happy, except for an error about not being able to copy about 5 files,  all called snd.ko and variations on that name.

But I seem to be  chasing my tail. I'm running XBMC and when I play anything it always  says it can't initialise the audio, except when I use the Pulse Audio  drivers, but then I still don't get sound (just no error). I've tried  all the hardware available to me in the XBMC GUI, but none work. 

So,  the obvious thing to do is to see how Ubuntu "full" got it working and  so I had a look at the alsa-base.conf and couldn't see anything exciting  in there. But I copied it to the "minimal" system anyway, but it made  no difference. 

Now I have followed the Ubuntu Sound Troubleshooter thread which suggested: 
sudo aplay -l

which replies with "no soundcards found". 

Following the thread, I check if I have the sound modules 
installed, which I apparently don't. Then it says to try:

sudo apt-get install linux-restricted-modules-`uname -r` linux-generic
Now my machine says "unable to locate package linux-restricted-modules-3.5.0-19-generic"

Why not? I can't find good info on why that package is not available, other than 
"its not available for 12.10 yet". 

ARRRRRR....please...help me, before I run in front of a bus!

---

