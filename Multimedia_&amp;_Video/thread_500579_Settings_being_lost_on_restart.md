---
title: "Settings being lost on restart?"
date: 2007-07-14
forum: Multimedia &amp; Video
---

### Post by joshua29 on 2007-07-14
I am setting up a PC to record from a mixing desk and playback through a PA system in an auditorium setting. It's almost done except for a niggling problem that when the PC is shutdown and restarted,  the application used for recording (Audacity) won't start from either the menus or the terminal prompt, instead giving a message:

sysadmin@evangel2:~$ audacity
audacity: src/hostapi/alsa/pa_linux_alsa.c:608: BuildDeviceList: Assertion `snd_config' failed.
Aborted (core dumped)
sysadmin@evangel2:~$ 

By going into Synaptic Package manager and re-installing alsa-oss or alsa-base (and possibly other alsa related packages - sorry I've lost track of all the trials I've done) Audacity will start up and run fine.

PC  has a ASUS M2N 1394 motherboard and amd 4600x2 cpu with a M-Audio Audiophile 192 sound card installed. OS is Ubuntu Fiesty amd64 version.

I have installed the OSS drivers [http://www.4front-tech.com/release/oss-linux_v4.0-1004_amd64.deb](http://www.4front-tech.com/release/oss-linux_v4.0-1004_amd64.deb) from 4Front and can playback and record sound through the card without difficulty.

This behaviour occurs with Audacity v1.2.6, v1.3.2beta, and v1.3.3beta and alsa v1.0.13 and v1.0.14

Any suggestions would be much appreciated.

Thanks

---

### Post by deadgobby on 2007-07-14
I had pretty much the same error
[http://ubuntuforums.org/showthread.php?t=486439](http://ubuntuforums.org/showthread.php?t=486439)

---

### Post by joshua29 on 2007-07-15
Thanks for the response.

I did try ALSA (the default install with v1.0.13) and got screeching audio. Also installed v1.0.14 which gave playback OK, but I couldn't get recording to work. Audacity started up fine without having to resort to any workarounds after restarting.

Thanks for the link. It may just be a case of getting to grips with configuring ALSA for the envy24ht chipset.
I'll give it another try.

cheers

---

### Post by joshua29 on 2007-07-18
After trawling the Net for posts on M-Audio Audiophile 192 and ALSA, and trying every relevant tip I could find, it appears that the ALSA drivers are a work in progress and of limited use for the Audiophile 192 card. The Envy24HT chip appears to be used in a number of sound cards most of them giving 7.1 output and driver development seems to have focussed on them so far. 

The Audiophile 192 will play back with ALSA v1.0.14 setup but doesn't seem to have any way to capture/record which is sort of consistent with the "input not tested" note in the wiki soundcard matrix [http://bugtrack.alsa-project.org/main/index.php/Matrix:Vendor-MAudio](http://bugtrack.alsa-project.org/main/index.php/Matrix:Vendor-MAudio).  ALSA v1.0.13 as packaged with Ubuntu Fiesty gives overdriven sound and is unusable with the Audiophile 192.

Using the alternative Opensound sound setup (oss-linux) from [www.4front-tech.com](www.4front-tech.com) does give access to record and playback, however the Portable Audio package used in building the Audacity application I was trying to use has a conflict as outlined in opening post of this thread.

Neither oss-linux nor ALSA have functioning MIDI capability in their Audiophile 192 drivers.

Perhaps the good news is that I came across a Sept 2006 post that a driver for FreeBSD had been written (though it didn't describe the driver capabilities) so maybe a fully functional ALSA driver isn't too far away.

I was trying to avoid going to the dark side (Windows). It seems like the shift to ALSA from OSS in the distributions in the 2.6 linux kernel packaging has been detrimental for Audiophile 192 users. Perhaps I should try an older distribution.

Does anyone know of a fully working Audiophile 192 + LINUX system?

---

### Post by joshua29 on 2007-08-01
Thanks for the replies. Problem has been solved by installing oss-linux and compiling Audacity (1.3.3beta) from sources using:

./configure --with-portaudio=v18
make
sudo make install

This forces Audacity to use OSS instead of ALSA. The ALSA driver for the Audiophile 192 does not have working record capability.

The problem appeared to lie in the Portable Audio sub-component of Audacity. I did try using the latest Portable Audio snapshot too, but was unsuccessful.

Audacity starts fine everytime now.

---

