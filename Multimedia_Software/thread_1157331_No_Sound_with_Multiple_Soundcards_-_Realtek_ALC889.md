---
title: "No Sound with Multiple Soundcards - Realtek ALC889A and HDMI Audio"
date: 2009-05-12
forum: Multimedia Software
---

### Post by rtarrigo on 2009-05-12
:guitar:  

I have two sound cards on my system:

1.  ATI HDMI Audio (on the ATI 4870 x2 GPU)

2.  Onboard Realtek ALC889A

I want to use the optical output in stereo mode from my realtek soundcard, and I do not want to use the ATI HDMI audio or any analog outputs.  Just one connection to my receiver - optical from the back of the motherboard (Gigabyte GA-EP35-DS3P).

I have searched this site, a few other forums, read some how-tos, etc., but I can't find the solution.  My problem is that I have no sound - no startup sound, no sound from Amarok, nothing.  The same physical setup works fine with Win XP (dual-boot) so I know that the physical connections are correct.  In the sound preferences panel, I have lots of options:

[IMG]http://img401.imageshack.us/img401/1548/screenshotsoundpreferen.png[/IMG]

Basically, in each of the main sections above (Sound Events, Music and Movies, Default Audio Conferencing, Defualt Mixer Tracks), I've got many options.  For instance, under **Sound Events**, I can select from:

Autodetect
HDA Intel ALC 885 Digital (ALSA)
HDA Intel ALC 885 Analog (ALSA)
HDA ATI HDMI ATI HDMI (ALSA) 
HDA Intel ALC 885 Analog (OSS)
HDA Intel ALC 885 Analog (OSS)
HDA Intel ALC 885 Analog (OSS)  (yeah, listed three times)
ALSA - Advanced Linux Sound Architecture
OSS - Onboard Sound System
PulseAudio Sound Server


Under **Default Mixer Tracks**, I can select from:
Capture: HDA Intel - ALC885 Analog (PulseAudio Mi...)
Capture: Monitor of HDA Intel - ALC885 Analog (Pu...)
HDA ATI HDMI (ALSA Mixer)
HDA Intel (ALSA Mixer)
Playback: HDA Intel - ALC885 Analog (PulseAudio M...)
Realtek ALC889A (OSS Mixer)

I've tried different selections and combos in the Sound Preferences panel - especially trying to set everything to Intel Digital (i.e. not picking anything that has ATI or Analog in the title).

Running _~$ cat /proc/asound/card0/codec#* | grep Codec _ Results in output:
Codec: Realtek ALC889A

I've made sure that the volume isn't muted.  (System->Preferences->Volume Control).  Nothing seems to work.

Also, when I load up PulseAudio Volume Control, the Output Devices tab only shows HDA Intel - ALC885 Analog when the Show: is set to All Output Devices.  Weird.

Running commaned: _aplay -l_ results in output:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC885 Analog [ALC885 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC885 Digital [ALC885 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


So basically, I think that something is messed up because I have two sound cards on my system (one on the graphics card, one on the mobo), and the mobo has analog and digital outputs, but I can only use the digital output.

Can anyone advise me?  I will follow all instructions exactly and post all results and post a resolution if we can come up with one.

Thank you for your help.

-Bob

---

### Post by rtarrigo on 2009-05-12
Testing thread subscription feature.

---

### Post by psyke83 on 2009-05-12
You need to understand that the user interface for sound is a little convoluted lately.

The Sound preference application (presented in your screenshot) is misleading. It does not control the sound output for your entire system; it only affects applications which use the GStreamer framework. Examples of this are the official GNOME applications such as Totem, Rhythmbox, Sound Recorder, etc. Any application that doesn't use GStreamer (which consist of the majority of applications on the Linux platform) won't respect the settings in this application.

Since Hardy (and especially in the recent release, Jaunty), PulseAudio is now responsible for audio mixing in applications. The way you have configured your Sound preferences will result in mixing errors, because PulseAudio and Gstreamer applications will both try to gain exclusive access to your sound device, and mixing will break on your system.

In a nutshell, you need to reset the preferences in this Sound application (Sound Playback options should be set to Autodetect, and the Sound Capture should be set to ALSA) - this will allow GStreamer applications to pass sound to the PulseAudio server successfully. Then, set the default card in the PulseAudio Volume Control application.

I suggest you read my guide on PulseAudio to gain a better understand of how things work, and it's recommended that you follow the guide to the letter.

PS. I see you changed the Default Mixer track to OSS. Change that back to the default, too (it should be the Master track of the ALSA mixer).

---

### Post by rtarrigo on 2009-05-12
> **psyke83 said:**
> You need to understand that the user interface for sound is a little convoluted lately.

The Sound preference application (presented in your screenshot) is misleading. It does not control the sound output for your entire system; it only affects applications which use the GStreamer framework. Examples of this are the official GNOME applications such as Totem, Rhythmbox, Sound Recorder, etc. Any application that doesn't use GStreamer (which consist of the majority of applications on the Linux platform) won't respect the settings in this application.

Since Hardy (and especially in the recent release, Jaunty), PulseAudio is now responsible for audio mixing in applications. The way you have configured your Sound preferences will result in mixing errors, because PulseAudio and Gstreamer applications will both try to gain exclusive access to your sound device, and mixing will break on your system.

In a nutshell, you need to reset the preferences in this Sound application (Sound Playback options should be set to Autodetect, and the Sound Capture should be set to ALSA) - this will allow GStreamer applications to pass sound to the PulseAudio server successfully. Then, set the default card in the PulseAudio Volume Control application.

I suggest you read my guide on PulseAudio to gain a better understand of how things work, and it's recommended that you follow the guide to the letter.

PS. I see you changed the Default Mixer track to OSS. Change that back to the default, too (it should be the Master track of the ALSA mixer).

Thanks for your response.  I tried what you recommended, bit when I load PulseAudio and select the Volume Control, the Output Devices only lists HDA Intel - ALC885 Analog.  There is no way to select the Digital output (also, my chip is ALC889A, not ALC885).  As you can see in the original post, aplay and the gstreamer setup see all of my soundcards, but Pulse Audio does not seem to.

What do you suggest?

Also, can you post a link to your guide?  Sounds like it would be helpful.

Thanks,
-Bob

---

### Post by psyke83 on 2009-05-12
> **rtarrigo said:**
> Thanks for your response.  I tried what you recommended, bit when I load PulseAudio and select the Volume Control, the Output Devices only lists HDA Intel - ALC885 Analog.  There is no way to select the Digital output (also, my chip is ALC889A, not ALC885).  As you can see in the original post, aplay and the gstreamer setup see all of my soundcards, but Pulse Audio does not seem to.

What do you suggest?

Also, can you post a link to your guide?  Sounds like it would be helpful.

Thanks,
-Bob

PulseAudio 0.9.14 doesn't show SPDIF/Digital outputs, unfortunately. You can upgrade to PA 0.9.15 (e.g., from [Luke Yelavich's PPA]("https://launchpad.net/~themuso/+archive/ppa")), or manually edit your configuration in /etc/pulse to use your sound card.

---

### Post by ashtone on 2009-05-25
I have the same exact problem.

I have a mainboard GA-MA790FX-DQ6 with an integrated sound card Realtek ACL889A which runs fine in windows XP

Ive installed a clean ubuntu 9.04 jaunty, when I play a video or a mp3 file, I cant hear the sound, instead I just get some kind of noise, just like the sound is playing too fast or too slow but worse than that

Ive followed several guides in order to get sound running fine but its seem impossible, Ive followed the guide of Psyke83 but it didnt work forme, also tried other guides and all combination of configuration Alsa, OSS, autodetect

Im stuck

Also the comand aplay -l outputs the following lines :
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: SB [HDA ATI SB], dispositivo 0: ALC885 Analog [ALC885 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: SB [HDA ATI SB], dispositivo 1: ALC885 Digital [ALC885 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 2: HDMI [HDA ATI HDMI], dispositivo 3: ATI HDMI [ATI HDMI]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

I think all the ATI must be refered to the ATI 4850, the graphics card, but I cant see my integrated Realtek ALC889A anywhere, so I guess maybe its a driver problem ?

Also in the Pulse audio Applet, when i look at volume control in output devices, I just see HDA Ati SB - ALC885 Analog, and thats all, where is the Realtek ALC889A? shouldnt it be there too ?

ashtone@Cubash:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe024000 irq 16
 1 [Camera         ]: USB-Audio - Camera
                      Camera at usb-0000:00:13.0-2, full speed
 2 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfdefc000 irq 19

Maybe the card is number 0

ashtone@Cubash:~$ cat /proc/asound/modules 
 0 snd_hda_intel
 1 snd_usb_audio
 2 snd_hda_intel

Its using the correct module

---

### Post by lancerocke on 2010-05-08
anybody find a fix?

---

