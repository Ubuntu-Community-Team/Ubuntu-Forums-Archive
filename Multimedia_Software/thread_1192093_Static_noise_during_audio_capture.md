---
title: "Static noise during audio capture"
date: 2009-06-19
forum: Multimedia Software
---

### Post by liliana_ba1 on 2009-06-19
Hi there

I installed Ubuntu 9.04 in my laptop two weeks ago and I'm having some problem with audio capture. When I try to record any sound with Sound Record (the program that comes installed by default) all I get is static noise.

First thing I tried was to change the volume levels in the volume control menu. I placed everything at max but still nothing. I also checked that the mic icon at the bottom of the bar had no red cross (I have a screenshoot [here]("http://picpaste.com/Screenshot-2.png")). In that menu I noticed that there's more than one tab so I choose the tab named "Capture" and 2 bars appear here named "Capture" and "Digital". I moved both bars to the max and tried to click on the red cross to unmute them (I have a screenshoot [here]("http://picpaste.com/pics/Screenshot-3.1245439158.png")). However, every time I do it and close the window, when I go back to it, the red cross is there again. I tried to record audio with that window open and the cross didn't reappeared but still, all I was able to record was noise.

I've read in the forums that skype can auto-adjust the volume levels so I did it it all again with skype closed but the problem persisted.

Another post mentioned that it could be some problem with the module and to add the line "options snd-hda-intel model=acer-aspire" to the file /etc/modprobe.d/alsa-base.conf but that also didn't solve it after restarting and I already removed it.

I also thought it could some be problem with the audio format Sound Record was using so I changed it to flac, but I kept listening to noise.

Here's the output of lspci

```

$ lspci | grep Audio
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)

```

and lsmod

```

$ lsmod | grep snd
snd_hda_intel         435636  2
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm

```

By the way, my laptop is an Acer Aspire 5052WXMi running Ubuntu only with a built-in microphone.

Thanks in advance

---

### Post by carandraug on 2009-06-25
Are you sure you're not recording whatever's coming from the microphone jack? Try to hit the socket a few times while you're recording to check if that's it. Or try to get your hands on a external mic if you can.

---

