---
title: "No Audio but &quot;test speakers&quot; works"
date: 2011-02-28
forum: Multimedia Software
---

### Post by Lastb0isct on 2011-02-28
I haven't had a problem with audio before but i'm stumped now.  I have my computer hooked up to a reciever which has four speakers connected to it.  I recently tried to watch a flash video on the computer and wasn't getting any sound.  Later on I tried to watch a DVD and still wasn't getting any sound.  I restarted the computer and it didn't help but when I went into the sound settings and properties I clicked the "test" for each speaker and i'm getting noise through them.  But ALL other programs will not push any sound to the speakers.

What is there I can do?

I have been perfecting my xbmc setup but now I can't even get sound out of my systems...

---

### Post by Jose Catre-Vandis on 2011-02-28
How are you connected to your receiver? HDMI? Jacks? Phonos?

Try connecting up some PC speakers to test your PC is issuing sound.

from a terminal run:
[code]aplay -l && aplay -L[code]
This should give you output regarding your sound card set up.

---

### Post by Lastb0isct on 2011-02-28
> **Jose Catre-Vandis said:**
> How are you connected to your receiver? HDMI? Jacks? Phonos?

Try connecting up some PC speakers to test your PC is issuing sound.

from a terminal run:
[code]aplay -l && aplay -L[code]
This should give you output regarding your sound card set up.

It does push out the "test speakers" white noise.  But when it's a video or music it doesn't...

---

### Post by lidex on 2011-03-01
Run this in a terminal:
```
gstreamer-properties
```
Make sure you are set to pulseaudio or autodetect

---

### Post by Lastb0isct on 2011-03-01
> **lidex said:**
> Run this in a terminal:
```
gstreamer-properties
```Make sure you are set to pulseaudio or autodetect

It was set to autodetect, but i changed it to pulseaudio and it didn't make a difference.  I am getting default system "error" noises though, when I type something where I can't type and all that kind of stuff.  i looks like something didn't install correctly when I updated ffmpeg on my htpc though. When i just came back to the computer it said there was an error when installing it.  So i'm re-installing it and we'll see if that makes a difference.  I'll report back here. Thanks for the advise.

---

### Post by Lastb0isct on 2011-03-01
Alright, sorry to keep dropping the ball here but i'm not able to get any sound from any media player still.  I get the test speakers white noise but in VLC i'm not getting anything and same with the built in ubuntu media player.  What other suggestions do you guys have?

Correction = My XBMC is able to play audio but everything else isn't!! This problem started after installing ffmpeg to my computer. What can I do?!

---

### Post by lidex on 2011-03-01
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Lastb0isct on 2011-03-01
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

[http://www.alsa-project.org/db/?f=b3939a946da5b6beff60ff8c11967e70b53f555b](http://www.alsa-project.org/db/?f=b3939a946da5b6beff60ff8c11967e70b53f555b)

Thanks!

---

### Post by Jose Catre-Vandis on 2011-03-02
> **Jose Catre-Vandis said:**
> How are you connected to your receiver? HDMI? Jacks? Phonos?

Try connecting up some PC speakers to test your PC is issuing sound.

from a terminal run:
[code]aplay -l && aplay -L[code]
This should give you output regarding your sound card set up.

Still waiting..... :)

---

### Post by lidex on 2011-03-02
This may not be the entire problem, but not good either:
```
!!ALSA Version
!!------------
Driver version:     1.0.23
Library version:    1.0.24.1
Utilities version:  1.0.24.2

```
Try re-installing alsa. Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

You're using the audigy, correct? May help to disable onboard in bios.

---

### Post by Lastb0isct on 2011-03-02
> **Jose Catre-Vandis said:**
> Still waiting..... :)

Woops! Sorry I never got back to you. I did this and it showed a bunch of stuff in the terminal. I am connected via rca to phono.

---

### Post by Lastb0isct on 2011-03-02
> **lidex said:**
> This may not be the entire problem, but not good either:
```
!!ALSA Version
!!------------
Driver version:     1.0.23
Library version:    1.0.24.1
Utilities version:  1.0.24.2

```
Try re-installing alsa. Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

You're using the audigy, correct? May help to disable onboard in bios.

Ill try and see if this helps later tonight when I get home from work.

My setup is a little weird in that I have the audigy installed but im using the onboard card. I have an older asus mobo that uses a via chipset. The older via chipsets give a crackling noise when using the audigy. I haven't found a solid solution for that so I've just been using the onboard. Hasn't been a problem until the ffmpeg install.

---

### Post by Jose Catre-Vandis on 2011-03-02
> **Lastb0isct said:**
> Woops! Sorry I never got back to you. I did this and it showed a bunch of stuff in the terminal. I am connected via rca to phono.

And please check you are getting sound out of your PC with PC speakers, helps to narrow things down, also sounds like you need to sort your alsa versions out and probably remove that audigy sound card to avoid conflicts and **** ups.

---

### Post by Lastb0isct on 2011-03-05
> **Lastb0isct said:**
> Ill try and see if this helps later tonight when I get home from work.

My setup is a little weird in that I have the audigy installed but im using the onboard card. I have an older asus mobo that uses a via chipset. The older via chipsets give a crackling noise when using the audigy. I haven't found a solid solution for that so I've just been using the onboard. Hasn't been a problem until the ffmpeg install.

I tried to run that command in the terminal but i got an error saying "sudo: aptitude: command not found".  Why am i getting that error?

---

### Post by lidex on 2011-03-06
> **Lastb0isct said:**
> I tried to run that command in the terminal but i got an error saying "sudo: aptitude: command not found".  Why am i getting that error?

Apparently aptitude is not installed by default anymore. Just run this first:
```
sudo apt-get install aptitude
```

---

### Post by coolercooler on 2011-04-24
I've got exactly the same problem, no audio with any of the applications, but test works and alsa test sound file works too. No flash sound either

this is my log
[http://www.alsa-project.org/db/?f=5a0c529f66cf02eb9e88835b66a40789ef3f8244](http://www.alsa-project.org/db/?f=5a0c529f66cf02eb9e88835b66a40789ef3f8244)

and when I do this:
```

# sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2

```
I get this error
```

Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.35-28-generic"
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.35-28-generic"
The following packages will be REINSTALLED:
  alsa-base alsa-utils libasound2 linux-image-2.6.35-28-generic 
  linux-sound-base 
0 packages upgraded, 0 newly installed, 5 reinstalled, 0 to remove and 25 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the linux-image-2.6.35-28-generic package. This might mean you need to manually fix this package.
E: I wasn't able to locate file for the linux-image-2.6.35-28-generic package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

```

Reinstalling 10.10 again still doesn't work, am also using 9.10 dual boot which works perfectly on the same hardware.

---

### Post by lidex on 2011-04-24
> **coolercooler said:**
> I've got exactly the same problem, no audio with any of the applications, but test works and alsa test sound file works too. No flash sound either

this is my log
[http://www.alsa-project.org/db/?f=5a0c529f66cf02eb9e88835b66a40789ef3f8244](http://www.alsa-project.org/db/?f=5a0c529f66cf02eb9e88835b66a40789ef3f8244)

and when I do this:
```

# sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2

```
I get this error
```

Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.35-28-generic"
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.35-28-generic"
The following packages will be REINSTALLED:
  alsa-base alsa-utils libasound2 linux-image-2.6.35-28-generic 
  linux-sound-base 
0 packages upgraded, 0 newly installed, 5 reinstalled, 0 to remove and 25 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the linux-image-2.6.35-28-generic package. This might mean you need to manually fix this package.
E: I wasn't able to locate file for the linux-image-2.6.35-28-generic package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

```

Reinstalling 10.10 again still doesn't work, am also using 9.10 dual boot which works perfectly on the same hardware.

You're trying to use hdmi?
Your onboard soundcard is default. What profile are you using in 'Sound Preferences'? What happens when you remove /etc/asound.conf?

---

### Post by coolercooler on 2011-04-25
Hi lidex.

Yes I am trying to use sound through hdmi, and situation is exactly the same without the file /etc/asound.conf, as I added that to make sure hdmi was selected on start-up, but that made no difference.
```
aplay -l**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 
```


In the sound preferences I have digital stereo (HDMI) output in the hardware and RS780 Azila controler on the output.

---

### Post by lidex on 2011-04-27
> **coolercooler said:**
> Hi lidex.

Yes I am trying to use sound through hdmi, and situation is exactly the same without the file /etc/asound.conf, as I added that to make sure hdmi was selected on start-up, but that made no difference.
```
aplay -l**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 
```


In the sound preferences I have digital stereo (HDMI) output in the hardware and RS780 Azila controler on the output.

I believe those should both be set to digital. Your asound.conf wasn't doing anything really.

Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=6stack-dig" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

