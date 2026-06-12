---
title: "cs46xx and coaxial"
date: 2013-07-10
forum: Multimedia Software
---

### Post by zagor on 2013-07-10
Dear all,

my pc has an old Lucid 10.04 64bit installed but I've recently decided to change to something newer.
Unfortunately all distros I've tried have the same audio issue.
Besides the onboard audio, I have a quite old Hercules Game Theater XP, very nice and working fine on Lucid and before.
Unfortunately it seems the new distros do not ship with the CS46xx firmware.
The best result achieved so far was on a Mint Debian 2013 (LMDE): after following the debian guide [http://wiki.debian.org/snd-cs46xx](http://wiki.debian.org/snd-cs46xx) I have sound but not completely: the small desk speakers connected directly to the GameTheater box work, but the coaxial output does not.
I use a coaxial cable out from the sound card to a DAC converter eventually reaching the stereo amplifier. My guess is that the coaxial output does not work with this firmware.
alsamixer shows all available volume sliders high and unmuted.
Google and the forums seem not to help.

Kernel is 3.2.0-4-amd64 and the audio part is:
```
$ inxi -Axc 0
Audio:     Card-1 Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] BusID: 05:04.0
           Card-2 NVIDIA CK804 AC'97 Audio Controller driver snd_intel8x0 at ports dc00 e000 BusID: 00:04.0
           Sound: Advanced Linux Sound Architecture Version 1.0.24
```

Any suggestions?

Thanks

---

### Post by zagor on 2013-07-16
Any hints?

thanks!

---

### Post by zagor on 2013-08-08
So, I eventually managed to get the sound through coaxial cable.
I don't know exactly how I did it, for I've been trying things in a fully frantic mood....
Anyway, after installing alsamixer (gnome-alsmixer for a nice and complete GUI) I guess the trick was:
1. enable the IEC958 sliders in alsamixer
2. go in the sound preferences and select the "digital duplex output"
these two might or might not already work, it didn't initially for me. 
I therefore started with
3. try different settings in the VLC preferences. I ended up selecting ALSA and the IEC958 hardware device
THis also was not working. 
At one point I set VLC as in 3 and closed VLC. A sound was heard and the next time I fired it up it was working!
Obviously, only the digital output, not the analog front speakers.
From that on, just selecting the correct template in the sound preferences (as in 2.) allows to switch from front analog to digital coax.Apparently there's no way to get both playing together (in winxp it does).

On LinuxMint, instead, I had to follow the debian wiki, but the sliders for the digital output were not present in alsamixer.
Reading a lot a posts, I've got the hint that maybe the kernel was not compiled with the proper parameters, therefore I tried to go back from the 3.2.0-4-amd64 std Mint LMDE kernel, to an old 2.6 as my old Ubuntu. 
Not easy.
I've found instead a pre-compiled [3.9 kernel done in "the ubuntu way" by mr Exton]("http://extonlinux.wordpress.com/2013/05/06/install-the-latest-kernel-3-9-for-ubuntudebian-64bit-systems/").
Installed, rebooted and the digital is there!
Step 1 and 2 gave back the coax output.

It might be an issue with 3.2.0 kernel or maybe a Mint issue, but the 3.9.0 kernel works!

So, my most humble yet highly grateful thanks to mr. Exton!!!

---

