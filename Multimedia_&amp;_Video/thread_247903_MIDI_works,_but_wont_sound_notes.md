---
title: "MIDI works, but wont sound notes"
date: 2006-08-31
forum: Multimedia &amp; Video
---

### Post by capsid on 2006-08-31
Hi everybody.  

So here's the deal.  I'm running Dapper on a Dell Latitude D800.  I'm using the latest kernel from running apt-get dist-upgrade.  I've been playing with the Ubuntu Studio launcher and trying to get my apps to work.  Most stuff works just fine, but I'm having some MIDI trouble.  

After playing with aconnectgui, puredata, and VirtualKeyboard, I realized I'm able to create and route MIDI notes.  When I try to do a noteout in puredata, however, there is no sound. I pulled some MIDI files over from my windows drive and tried to play them in xmms, rythmbox, vlc, and they didn't work in any program.  It seems like the MIDI can travel between programs, but can't get sent to the sound card.  

If I go to System/Preferences/Sound,  My default sound card is listed as Intel 82801DV-ICH4, which is funny because in windows it is a Sigmatel.  Is Sigmatel a division of Intel or is there some basic onboard sound card that is getting loaded before the Sigmatel?  Or is that a signal that it's loading the wrong driver?

Here's my lsmod |grep snd:
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
snd_seq_midi            9376  0
snd_rawmidi            25504  1 snd_seq_midi
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51984  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          8716  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_intel8x0           33692  2
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  2 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_seq,snd_pcm
snd                    55268  12 snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  2 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm

and here's my /etc/modules:
lp
psmouse
sbp2
sr_mod
snd-seq

Many thanks for any help you can provide.  I've got a Midines coming in a few days and I want to get my sequencing started without resorting to windows.

---

### Post by dolson on 2006-08-31
Please read through this to get a basic understanding of how JACK works:
[http://ubuntustudio.com/wiki/index.php/QjackCtl_Connections](http://ubuntustudio.com/wiki/index.php/QjackCtl_Connections)

Chances are good that you need to route your audio output of Puredata into the ALSA PCM input (which goes out to your speakers).

---

### Post by capsid on 2006-08-31
thanks for the quick reply.  

I'm still in the midst of testing this, but i had a question.

In qjackctl setup/input device/output device, what do the comma separated values signify?  I'm talking about the part where it says hw: 0,0 or hw: 0,3.
How do those differ from the options that only specify one device, like hw:0?

EDIT

Yatta!!!  Thanks for the help.  I was able to connect Vkeybd to ZynAddSubFX. How exciting!!!  

My problem earlier was stemming from improper jack configuration.  jackd kept crashing.  

Remember how I said I couldn't play MIDI files in rythmbox or xmms (using the soundcards default samples), do I have to route them through qjackctl also?  I'm going to try.

---

### Post by dolson on 2006-08-31
MIDI is currently handled by ALSA on the backend (confusing, because it's in the QjackCtl connections window...).

I don't know how to play MIDI files other than with playmidi on the commandline, but even then, I don't really play MIDI files. Perhaps a sequencer like seq24 or Rosegarden can load it? You still need to drive a synth or sampler to actually hear anything, because MIDI is only note data, not audio.

Those options hw0,1 or whatever, that's only for the specific card I mention on the wiki page. Nobody has added any information for how to configure JACK for other sound cards yet.

---

