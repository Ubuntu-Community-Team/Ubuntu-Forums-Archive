---
title: "No sound in Flash (Hardy, FF3b5)"
date: 2008-05-11
forum: Multimedia Software
---

### Post by Patness on 2008-05-11
I've trolled through the threads on the forums for 3 days now.

Flash does not output sound in Firefox 3b5. Tried "aoss firefox" after installing the alsa-oss package, tried creating a new user profile, tried uninstalling and/or reinstalling libflashsupport, uninstalling reinstalling flashplugin-nonfree and Java6. I created new user profiles. There is no firefoxrc file to edit, so that's out of the question.

I suspect this might be a pulseaudio issue, and not strictly a flash issue - can I force output on firefox to alsa or oss by any other means?

Anyone in the community at all, get back to me on this. I'll wait as long as I have to.

Edit: I'm running Hardy AMD64, just a head's up.

---

### Post by OiCkilL on 2008-05-11
Me too, No sound in flash and some game, and at some time I can't got any sounds. The Hardy's Alsa is not good.:(

---

### Post by Patness on 2008-05-11
I play Savage 2, and at first gaming didn't work. I switched to OSS for the game and selected a few different combinations of /dev/dsp until I got a set that worked. OSS is a nice workaround for a lot of apps. However, whether or not you can start an app with OSS in mind, not always easy.

---

### Post by user-unit on 2008-05-11
try this directory since its different then the original firfox
```
sudo gedit /etc/firefox-3.0/firefoxrc
```
and change it to
```
FIREFOX_DSP="aoss"
```

---

### Post by thoffland on 2008-05-11
> **user-unit said:**
> try this directory since its different then the original firfox
```
sudo gedit /etc/firefox-3.0/firefoxrc
```
and change it to
```
FIREFOX_DSP="aoss"
```

I'm running the same setup and I don't have this file on my system... as far as I can tell anyhow. 

Looking forward to a solution!

---

### Post by Yellow Pasque on 2008-05-11
From [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
```
wget http://pulseaudio.vdbonline.net/flashplugin-nonfree-pulse_0.1~000.tar.gz
tar xvfz flashplugin-nonfree-pulse_0.1~000.tar.gz
cd flashplugin-nonfree-pulse-0.1~000
sudo apt-get install libpulse-dev
make
sudo make install

```

---

### Post by Patness on 2008-05-11
```
make
cc -shared -O0 -Wall -Wextra -W `pkg-config --cflags libpulse` -g `pkg-config --libs libpulse` flashsupport.c -o libflashsupport.so
/usr/bin/ld: /tmp/cceGqPuI.o: relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/tmp/cceGqPuI.o: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [libflashsupport.so] Error 1

```

No dice so far, but thank you! What happened, any ideas?

---

### Post by Zorael on 2008-05-11
I followed [this guide](http://www.pulseaudio.org/wiki/FlashPlayer9Solution). Sound works now, but flash in itself is buggy.

---

### Post by jleino on 2008-05-11
I can confirm the problem, except I don't have any audio whatsoever (including the audio control panel test button). I have tried various suggestions in this and other forums with not much help.

Do you know if there is a definitive audio guide that I could use for debugging somethere?

This is annoying!

---

### Post by Yellow Pasque on 2008-05-11
> **Patness said:**
> ```
make
cc -shared -O0 -Wall -Wextra -W `pkg-config --cflags libpulse` -g `pkg-config --libs libpulse` flashsupport.c -o libflashsupport.so
/usr/bin/ld: /tmp/cceGqPuI.o: relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/tmp/cceGqPuI.o: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [libflashsupport.so] Error 1

```

No dice so far, but thank you! What happened, any ideas?

Try again with the version I attached to this post. You may need to install the gcc-multilib package as well.
```
sudo apt-get install gcc-4.2-multilib
```

---

### Post by Patness on 2008-05-11
> **jleino said:**
> I can confirm the problem, except I don't have any audio whatsoever (including the audio control panel test button). I have tried various suggestions in this and other forums with not much help.

Do you know if there is a definitive audio guide that I could use for debugging somethere?

This is annoying!

You are, in all likelihood, speaking of a very different problem. Have you gone into System>Prefs>Sound (in GNOME)? Changing your sound preferences (particularly your playback devices) is usually the cause of this. I'm running a Soundblaster Audigy 2 Platinum, and forcing everything to ALSA playback (including installing asoundconf-gtk to let me define my default device), as well as selecting default devices for mixing (both in the mixer itself and in the Sound Preferences) let me get everything except for flash. 

VLC also gave me trouble - I installed the audio plugins for ESD, Pulse, and ALSA in Synaptic.

---

### Post by Patness on 2008-05-11
> **Temüjin said:**
> Try again with the version I attached to this post. You may need to install the gcc-multilib package as well.
```
sudo apt-get install gcc-4.2-multilib
```

Done - and although the make install worked, it didn't result in any sound in firefox flash.

---

### Post by Yellow Pasque on 2008-05-11
> Edit: I'm running Hardy AMD64, just a head's up.
Ah, then we'll try again.
```
gedit Makefile
```
Add the -m32 flag.

---

### Post by Patness on 2008-05-11
> **Temüjin said:**
> Ah, then we'll try again.
```
gedit Makefile
```
Add the -m32 flag.

Done. However, still no flash. Your help is appreciated, however.

---

### Post by jleino on 2008-05-16
> **Patness said:**
> You are, in all likelihood, speaking of a very different problem. Have you gone into System>Prefs>Sound (in GNOME)? Changing your sound preferences (particularly your playback devices) is usually the cause of this. I'm running a Soundblaster Audigy 2 Platinum, and forcing everything to ALSA playback (including installing asoundconf-gtk to let me define my default device), as well as selecting default devices for mixing (both in the mixer itself and in the Sound Preferences) let me get everything except for flash. 

VLC also gave me trouble - I installed the audio plugins for ESD, Pulse, and ALSA in Synaptic.

Thanks for the tips. However I have set everything to Alsa. After boot I get sound even from Flash player. However soon it will be corrupted somehow and all sound is gone.

I have been using Linux about 10 years now. I wonder when the sound will start working without trouble, it should not be that hard? :)

-- Juha

---

### Post by the mighty windle on 2008-05-17
Hello, this is my first post on this forum, so please excuse my gaucheness!
 I too found that flash was bugging out my sound when running multimedia apps at the same time. It would kill the sound entirely. I found like Patness that forcing everything to use Alsa cured it as far as I know. I am however a hardware monkey as opposed to software (although i am s-l-o-w-l-y rectifying this!) and realise that this might help in the interim as a quick fix. I am running a celeron 2.4Ghz cpu on an intel 82845G/Gl mobo.

---

### Post by Izkata on 2008-06-09
The only fix I have found that works for me:

```
pkill pulseaudio
sudo apt-get purge pulseaudio
```

After I restart Rhythmbox and Firefox, all audio works perfectly.  My System->Preferences->Sound settings are all set to Autodetect.

---

