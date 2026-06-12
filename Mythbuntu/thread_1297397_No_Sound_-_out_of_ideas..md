---
title: "No Sound - out of ideas."
date: 2009-10-21
forum: Mythbuntu
---

### Post by johnvan on 2009-10-21
I just built a new frontend and have no sound.
When I started setting this up I installed mythbuntu on the same hard drive on a totally different computer just to get things started while I was waiting for parts.  I had no sound but didn't troubleshoot it since it was going into a different computer.
I finally got all of my new (used) hardware and built the frontend today. Still no sound, different motherboard with onboard sound.
In terminal my sound card is listed and the driver is listed also. It's a VIA 8235.
I get no sound in firefox or anything.  I tried playing a wav file with aplay -vv but got an error about "not PCM or FLOAT encoded" Maybe it was a problem with the file.
I purged and reinstalled alsa. Volumes in alsa-mixer are turned up and not muted.  It's definitely not the speakers.
I'm out of ideas. Is there a configuration file somewhere I should look at? Maybe try an older Kernel?
Thanks.

---

### Post by jwbrown77 on 2009-10-21
What version of Mythbuntu are you using?

Is your system using ALSA or OSS for sound?

What's the output of this:

lsmod | grep snd

Are you using regular analog audio cables or optical?

---

### Post by johnvan on 2009-10-21
Here's my lsmod 

n-mythbox@john-mythbox-desktop:~$ lsmod | grep snd
snd_via82xx            32152  1 
gameport               19468  1 snd_via82xx
snd_ac97_codec        112292  1 snd_via82xx
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         16904  2 snd_via82xx,snd_pcm
snd_mpu401_uart        15104  1 snd_via82xx
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  13 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
john-mythbox@john-mythbox-desktop:~$ 

I'm just using a 3.5mm adapter to RCA cables and I'm using mythbuntu 9.04.

Thanks for the help.

---

### Post by nasha on 2009-10-21
Sorry, didnt read the original post correctly

---

### Post by johnvan on 2009-10-22
How do I know if I'm using ALSA or OSS. In my mythtv setup I've selected ALSA default and I have the ALSA packages installed, is there more to it then that?

---

### Post by johnvan on 2009-10-22
Partial success.  I get sound from the front output.  I never bothered trying it before because I kind of guessed my way through hooking up all of the wires to the motherboard. 
I'd prefer to use the back connector though.

---

### Post by johnvan on 2009-10-22
If anybody has any ideas on how to choose the rear ports instead of the front it would be appreciated.

---

### Post by jwbrown77 on 2009-10-22
Did you try using the audio mixer in the GNOME/XFCE taskbar to play with the volume levels?

Does "lsmod | grep alsa" return anything?  It looked to me like you were using OSS not ALSA.  Did you try finding the setting in the mythfrontend Utilities/Setup menu that allows you to toggle between Alsa and OSS?  I don't think alsamixer works with OSS but I'm not sure.

If your front port is working and your rear isn't, did you ever have any other OS/OS version that you can confirm worked with said port?

---

### Post by johnvan on 2009-10-22
I never had anything work with that port and it's a used motherboard so I think I'll live with it.  I just bought a new 3.5mm adapter that is less obtrusive so I think I'll just leave it alone.

---

### Post by novellahub on 2009-10-23
> **johnvan said:**
> I never had anything work with that port and it's a used motherboard so I think I'll live with it.  I just bought a new 3.5mm adapter that is less obtrusive so I think I'll just leave it alone.

You might want to check the motherboard to see if there are some jumpers disabling the audio from the rear port.

---

### Post by johnvan on 2009-11-15
Thanks for the tip on the jumpers. Never would have thought of that myself. That was the problem, I was just too lazy to put them in until now.

---

### Post by Rocko262c on 2009-11-17
[QUOTE=jwbrown77;8147275]Did you try using the audio mixer in the GNOME/XFCE taskbar to play with the volume levels?

My audio mixer is no where to be found.  How can I get it installed?  I installed Mythbuntu 9.10 with a disk that was checked with no errors.  My sound works in Ubuntu 9.10 and Vista Ultimate.

Thanks for your help in advance!

-Rocko

---

### Post by nunrgguy on 2009-11-20
Install Alsamixer with synaptic - you have to run it from terminal. You should then be able to see if you've got anything muted that shouldn't be

---

