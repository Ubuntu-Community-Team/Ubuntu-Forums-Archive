---
title: "[SOLVED] Audacity - no sound output in hardy 8.04"
date: 2008-06-26
forum: Multimedia Software
---

### Post by fsando on 2008-06-26
Hi
The last two days I've tried all kinds of tricks to make Audacity work. It appears to work, when playing back a sound fiile the meters are moving as you'd expect but no sound comes out.

I did a lot of tinkering installed all kinds of extras that was suggested in various threads to no avail - I removed almost all jack-related, still no dice. Finally I installed the ubuntustudio-sound (reinstalles jack etc.) and the ubuntustudio-sound-plugins.

Eventually I tried this command (I don't remember which link provided this advice) which seems to solve the problem:
```
padsp audacity
```
It worked so now I added it in the menu link.

Hope this helps someone.

EDIT:
Turns out this is far from ideal. Audacity will play the sound file - even at same time as other programs (like Amarok) play too. Problem is that Audacity playback sound is filled with digital cracks and pops and cpu runs at 100%.

I've used Audacity with no problems in Feisty but in Hardy it's only trouble. A cautious guess is that it's caused by the new pulseaudio/jack setup. Does anyone have a suggestion how to make it work? It would be nice if we could make sound really work in Ubuntu.

---

### Post by timcredible on 2008-06-26
it works with no problems on my vostro 1000 without any packages installed except for audacity from synaptic.  however, i checked the prefs and see that it doesn't support pulse audio, so if you have any other app running that would be using pulse (like rhythmbox or amarok or totem, etc), you'll have to exit out of that program since 2 different audio subsystems can't access the sound card at the same time (or change the audio output of that app to alsa and set audacity to alsa too).  

you can have as many audio streams from as many programs as you want playing at the same time, but they have to use the same audio subsystem (like pulse, or alsa, etc.).

---

### Post by fsando on 2008-06-26
Thanks for your reply.
Good to know that it works flawlessly for you which means that my problems may be caused by some oddity in my setup.

I should probably have mentioned the following:
Ubuntu 8.04
```
~$ uname -a
Linux username 2.6.24-19-rt #1 SMP PREEMPT RT Wed Jun 18 16:35:41 UTC 2008 i686 GNU/Linux

```

and```
~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 22
 1 [SAA7134        ]: SAA7134 - SAA7134
                      saa7133[0] at 0xfeaff800 irq 18

```

And```
~$ lsmod | grep -i snd
snd_hda_intel         344728  5 
snd_hwdep              10628  1 snd_hda_intel
snd_pcm_oss            42400  0 
snd_mixer_oss          18048  1 snd_pcm_oss
snd_seq_dummy           4868  0 
snd_pcm                78724  4 snd_hda_intel,saa7134_alsa,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_seq_oss            35968  0 
snd_seq_midi            9376  0 
snd_rawmidi            25632  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54992  9 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    57636  22 snd_hda_intel,saa7134_alsa,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_seq_dummy,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9312  1 snd

```
I've got it to work now but not entirely to my satisfaction and I'm not sure of the wider implications of how get it to work yet:

I've installed Jack Control (qjackctl). If I open that app and start jack server from here and make sure to also press the 'play' button and then start Audacity and set its output to "jack connection kit" it actually does what I expect it to.

I guess the connection kit must be installed as well - but I suppose that all jack-related is installed when you install ubuntustudio-audio. I also fiddled some with the 'setup in jack control because of a lot of cracks and pops - don't know if it's fiddling or the 'play' button that did the trick.

Another trick I saw somewhere was to start Audacity with the command:
```
$ padsp audacity
```
And then choose 'oss' as output. Unstable sound quality but allowed me to have Amarok and Audacity output sound at the same time - guess that's what you mean by using the same subsystem. Anyway it works reasonably well with jack. 

Perhaps all this has to do with a shift away from alsa to pulse or something, that will be sorted out in the next half year or so?

---

### Post by fsando on 2008-06-27
I found the solution:

Turns out the solution is to install Jack. I'm not sure if it's installed by default or it came when I installed the ubuntustudio-audio (and the ubuntustudio-plugins).

Then you have to start the JACK Server first (from the app>sound&vid choose 'JACK Control' and click 'start') only then should you start Audacity.

In Audacity you go to Edit > Preferences and choose JACK Connection Kit as output.

If you use Amarok you can have that play through JACK at the same time too if you follow the advice given here:
[http://ubuntuforums.org/showthread.php?t=267417&page=3](http://ubuntuforums.org/showthread.php?t=267417&page=3)

---

### Post by hubiedo on 2009-11-30
i am on hardy 8.04 and just went thru this on audicity, the solution for me was to change the preferences> audio I/O to alsa default which is related to my choices etc. to use alsa as my sound player etc. 
i tried the pulse setup and didn't seem to work for me. probably just me as a noob. use rhythmbox and kdaudio creator a lot and both work great now - heh heh, i have audacity working. can't wait to do some editing with audacity. neato, keeno.

previously used great audio mixer/editor on windoze but had to pay for it (audio edit deluxe), is the name i think. 

hope this helps someone else

---

