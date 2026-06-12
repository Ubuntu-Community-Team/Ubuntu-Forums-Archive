---
title: "Audacity Stopped Working"
date: 2007-05-24
forum: Multimedia Production
---

### Post by Ingla on 2007-05-24
Hello.

I had a problem with my microphone. Installed new sound card. Dapper recognized it by itself (to
my surprise) and sound is working fine ... including recording with the default Sound Recorder.

However, on starting Audacity, I get an error notice: "There was an error initiating the audio I/O layer. You will not be able to play or record."

Then the program loads and, when I push "Record", I get:"Error while opening sound device. Please check the input device settings and the project sample rate." However, I see no way to do this. The program has an inactivated field for sound device. I can't do anything with it.

I tried a complete removal with Synaptic and tried to reinstall with Automatix, hoping it would pick up the system configuration. Automatix returned "Fatal apt error...Installation unsuccessful". Installed with Synaptic but got the same problem I started with.

Does anyone know how to fix this?

Thanks very much.

---

### Post by kayosiii on 2007-05-24
Chances are you have a soundcard that does not support hardware mixing. It needs to be setup to allow this is in software (I think what you are looking for is called dmix - which I have never been able to get to run properly)...

To fix your immediate problem it is likely that some other program is hogging the soundcard. If you are running KDE artsd is usually the cuprit but jackd can also be a problem. If neither of these are running try turning off every other application that uses sound.

---

### Post by Ingla on 2007-05-24
Thanks for the reply. I'm not running KDE (except for some programs which are not running). Running TOP doesn't seem to show the processes you mention, and I don't think anything is using sound. Strange the default Sound Recorder has no problem.

The previous sound card is built in, so it's still in the machine. So on Windows I installed a driver that came with the new one, which got it working. I booted into Linux and it just worked. I was expecting to have to configure something and am still wondering why I didn't need to.

I'm wondering if Audacity didn't configure itself for the old sound card when it installed originally. Do you know anything about configuring Audacity itself? I can't find a way to tell it anything... or even see how it's set up.

Any ideas?

---

### Post by kayosiii on 2007-05-24
what does Audacity say under Audio IO under edit->preferences

---

### Post by Ingla on 2007-05-25
It shows nothing but greyed-out fields for for "Device" under both Playback and Recording. Only the "Channels" field allows changing the number.
(By the way, I was just in Windows and Audacity is working fine there, so I don't think it's an issue of the sound card itself.)

---

### Post by nedecor on 2007-05-25
> **Ingla said:**
> It shows nothing but greyed-out fields for for "Device" under both Playback and Recording. Only the "Channels" field allows changing the number.
(By the way, I was just in Windows and Audacity is working fine there, so I don't think it's an issue of the sound card itself.)

Windows and Linux have two entirely different sound architectures, so just because the application works on one platform doesn't mean it will work exactly the same way on another.

If both of the fields are grayed out then it means audacity is not detecting your sound card. Can you paste the output of aplay -l and lsmod |grep snd

Jake

---

### Post by Ingla on 2007-05-26
Thanks for the reply. Sorry, I was away for the day.

I mentioned Windows because a previous reply had suggested that the sound card might not support what was needed. I thought the fact that Audacity worked on Windows meant that the issue wasn't the card itself, but that Audacity (on Linux) couldn't find it ... or something like that.

Outputs requested are:

Output for aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
===============================================================
Output for lsmod |grep snd:
snd_ens1371            24800  1
gameport               15496  1 snd_ens1371
snd_rawmidi            25504  1 snd_ens1371
snd_seq_device          8716  1 snd_rawmidi
snd_ac97_codec         93216  1 snd_ens1371
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  10 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  1 snd_pcm
snd_ac97_bus            2304  1 snd_ac97_codec
===============================================================
I'm afraid this doesn't mean too much to me. Can you see anything from it?

By the way, the sound card doesn't list a brand name on the box, but the driver it said it was installing on Windows was Creative. The box says 32-bit PCI bus master, PCI plug and Play (PnP) bus interface with C-Media 8738 chipset.

Thanks a lot.

---

### Post by postolar on 2008-01-24
Hello.

Sorry for my English.

I've installed Linux Ubuntu 7.10 - desktop i386, interface Kubuntu. I've two soundcards. VIA 8237 is soundcard integrated and the second is C-Media PCI CMI8738-MC6. I want close VIA 8237. VIA 8237 closed in BIOS, but it's not effectively. 

Help! Please!

---

