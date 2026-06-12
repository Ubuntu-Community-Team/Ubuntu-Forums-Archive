---
title: "Mic not working in skype in ubuntu 13.10"
date: 2013-11-09
forum: Multimedia Software
---

### Post by lvgandhi on 2013-11-09
My machine is Asus S400CA.
lvgandhi@lvgasus:~$ lspci |grep Audio
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
lvgandhi@lvgasus:~$ 

lvgandhi@lvgasus:~$ lsmod |grep snd
snd_hda_codec_hdmi     41117  1 
snd_hda_codec_via      27860  1 
snd_hda_intel          48171  5 
snd_hda_codec         188738  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd

As per this site
[http://www.webupd8.org/2013/10/get-sound-working-in-skype-with-ubuntu.html?m=1](http://www.webupd8.org/2013/10/get-sound-working-in-skype-with-ubuntu.html?m=1)
I have installed skype from ubuntu partners. 
I also tried with command 
sudo sed -i 's/^Exec=.*/Exec=env PULSE_LATENCY_MSEC=30 skype %U/' /usr/share/applications/skype.desktop
Still Mic is not working in skype. 
Where as Mic works ok in audacity.

---

### Post by rrofes on 2014-04-10
hello lvgandhi,
I observe the same problem: mic works for other applications but not for skype. did you manage to solve it?

Using ubuntu 13.10 and skype 4.2.0.11 installed from ubuntu repositories (which should solve problems with audio)

---

### Post by rrofes on 2014-04-10
another clarification: I start skype with:
env PULSE_LATENCY_MSEC=30 skype %U

---

### Post by lvgandhi on 2014-04-10
I have left using skype in ubuntu.

---

