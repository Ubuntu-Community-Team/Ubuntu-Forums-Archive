---
title: "[SOLVED] First quiet sound with surround, now no sound (Logitech Z5500)"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by R3N3G4D3 on 2008-02-03
Before I go into the problem, I just want to thank everyone working on Ubuntu for making Linux the operating system I wanted it to be when I first tried it 6 years ago and gave up on it. I have now used Ubuntu for over 7 months and if it wasn't for DirectX 10 wouldn't even have Windows installed.

When I first installed 6.06 on my laptop, the sound worked fine. Later I installed 7.04 on my backup PC with onboard sound (not sure of the device, but Windows used AC97 driver with it), and the sound was considerably quieter, still decent enough to hear but required all settings at max for normal sound through my headphones.  I don't have my laptop or 6.06 with me anymore to test if the issue is due to newer Ubuntu distributions or my hardware. And that didn't really bother me that much, so I never got around to fixing it.

Now I just built a new computer, with onboard 7.1 audio. My new isntallation of Ubuntu 7.10 detected the codec as "Realtek ALC885" using
```
head -1 /proc/asound/card0/codec*
```
command, which is consistent with the motherboard specifications (DFI Bloodiron). However, I had the same problem as on my original PC where I had to raise the sound to maximum to be able to listen to it normally with my headphones. I checked alsamixer and it now seemed to have different tuning layout from either my old laptop or my backup PC (first of all, it's missing the master volume I used to have on the very left next to PCB, and then there are "center, front, and back" which I guess is due to my audio card). But that's not the main problem, I was expecting to buy a sound system which I thought would counter the quiet Linux setup using its own amplification.

Today my Logitech Z-5500 arrived, and I connected it to my PC instead of the headphones, but heard no sound. I then booted into Windows, which played sound fine on all speakers. I came back to Ubuntu and turned up the sound the max both on Ubuntu and my sound system itself, I could then hear the sound but it was barely audible (loud enough to hear the music but not loud enough to make out the words). I then went on these forums trying to find a solution, and went through this guide: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

As a result of the guide, however, after the reboot Ubuntu thinks I have no codecs to play sound at all. I used '6stack-dig' setting for the model since I'm not sure if any of those other settings matches mine closer than it does. Anyway here is my current output for several sound-related commands:
```
alex@genesis:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
alex@genesis:~$ cat /proc/asound/modules
alex@genesis:~$ head -1 /proc/asound/card0/codec*
head: cannot open `/proc/asound/card0/codec*' for reading: No such file or directory
alex@genesis:~$ 

```
I would appreciate any help on getting my surround to work the way it should, although my neighbors probably wouldn't.

---

### Post by R3N3G4D3 on 2008-02-04
I tried purging and installing alsa libraries (alsa-base, alsa-utils, linux-sound-base) to at least revert to original settings, that didn't help and I still have no sound. The /etc/modprobe.d/alsa-base file looks like it was modified by this reinstall process, it's now missing the "options snd-hda-intel model=auto" line that was there before.

---

### Post by R3N3G4D3 on 2008-02-09
Thank you Ubuntu community for not even attempting to help me with my problem, I finally figured it out myself and got full surround sound working. For anyone stumbling upon this problem later, here is my solution:

I had several issues (including alsa not starting automatically, snd not creating relevant symlinks, autoconf failing to add my audio device to a list of available ones), all which which I eventually narrowed down to one problem: I had conflicting versions of snd-hda-intel.ko module. Here is my fix for it:

1: Search for every "snd-hda-intel.ko" instance on the computer, and remove them all
2: Download the latest alsa-driver source code from alsa website, compile it and install it
3. run "snddevices" (should be in alsa-driver directory) to setup the proper symlinks, then run "sudo alsaconf" to configure the card, and then run "alsasound stop" followed by "alsasound start" ("alsasound restart" failed for me for some reason) to load the module and enable sound (alsasound should also be in alsa-driver directory). The sound should now play even without rebooting the system (however, I recommend the reboot to enable the volume applet that allows changing sound volume through keyboard shortcuts)

---

### Post by jimoupas on 2008-02-13
Hi buddie

Thanks , that helped me , i only changed intel-hda with my sound card ( intel8x0 ) on compile.

Does the center speaker work for you ? I tried every possible option and combination of options and cable ports but still it is the only that doesnt work.

I have 7.1 speaker system too.

---

### Post by R3N3G4D3 on 2008-03-15
Well, a quick youtube sound check shows that by default only the front 2 speakers work, switching speaker mode to dual-stereo makes the sound come from all but the central speaker, switching the mode to PLII Music makes the sound come ONLY from the center speaker. If I remember correctly, the PLII mode activated all speakers in Windows even with youtube. But since youtube was never meant to be used with surround sound anyway, I reran the test with an mp3 file using Totem player. Using the regular and dual-stereo modes produces the same results as youtube, but the PLII Music mode does indeed engage all 5 speakers.

For your problem I suggest that you check if your subwoofer is working, because as far as I know it should use the same channel as the central speaker, but with a low-pass filter applied to it. Hence if your subwoofer is getting input, your central speaker should be getting it too.

---

