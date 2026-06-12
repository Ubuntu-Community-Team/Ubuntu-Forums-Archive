---
title: "weird sound issue"
date: 2009-05-14
forum: Multimedia Software
---

### Post by jhecker on 2009-05-14
Hello all,

I am running Jaunty x86_64 (via upgrade, not a fresh install) on an AMD64 machine with Intel ALC883 (analog and digital) and USB audio drivers (per aplay -l).  As this is an at-work machine I listen using the headphones (USB audio).

I am having two problems: one - playback is working for some services not others.  E.g., listening to last.fm via Rhythmbox works perfectly; but using the last.fm linux client gives no sound (though otherwise behaves well).  Same for Pandora and Rhapsody (via firefox 3.0.10 with the flash and Sun java plugins working fine - the only problem is sound).

Even for Rhythmbox I occasionally have to reload alsa (alsa force-reload).  

I have reviewed the composite sound FAQ for Ubuntu but it appears oriented towards getting drivers installed and loaded.  lsmod looks like it sees everything:

snd_usb_audio         108832  3 
snd_pcm                99336  4 snd_hda_intel,snd_usb_audio,snd_pcm_oss
snd_usb_lib            27392  1 snd_usb_audio
snd_hwdep              16776  1 snd_usb_audio
snd                    78792  23 snd_hda_intel,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

and using the sound test app blows my ears out via the 'phones. 

Looking at what I've written, I'll leave problem #2 (using the microphone on the headset) for another time.

I am wondering what my next troubleshooting steps should be.

Thanks in advance for any and all advice on this-

jh

---

### Post by kostkon on 2009-05-19
Use the *PulseAudio Device Chooser* to set a default input and output device and to move audio streams from your sound card to your USB headset and vice versa.

For more info, check [this thread here]("http://ubuntuforums.org/showthread.php?t=1130384").

---

