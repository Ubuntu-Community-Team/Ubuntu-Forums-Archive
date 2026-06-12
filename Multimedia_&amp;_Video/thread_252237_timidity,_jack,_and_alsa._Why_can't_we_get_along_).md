---
title: "timidity, jack, and alsa. Why can't we get along? :)"
date: 2006-09-06
forum: Multimedia &amp; Video
---

### Post by capsid on 2006-09-06
So I've got qjackctl open and I'm trying to get the hang of routing MIDI into timidity and out to the soundcard.  I posted a thread a few days ago about getting general midi stuff working, but this problem is a little bit different and more in-depth, so I thought I'd make a new thread.  Thanks to all those who helped me though.  Anyway, onto the ](*,) fun.  

If I run 
> timidity -Oj -ia
or 
> timidity -Oj -ig
which are the XAW, and GTK interfaces, it works, but has no MIDI in.  If I run
> timidity -Oj -iA
which is jack output/alsa interface, the MIDI in works, but the timidity to alsa_pcm connection appears for just a second and then disappears. If I run
> timidity -Os -iA 
which is alsa output/alsa input, i get the following:
> ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
Can't open pcm device 'default'.
Couldn't open ALSA pcm device (`s')


I'm pretty sure I want Jack output and Alsa interface, but neither the message window in Jack or the terminal from which I'm launching Timidity are giving me any idea why Timidity Audio output is only showing up for a split-second, even when I pass the 'v' verbose option to Timidity.  

Any suggestions would be appreciated.  If i'm neglecting to mention useful diagnostic information, please give me a clue as to what it is:) Thanks!

---

### Post by capsid on 2006-09-06
This is my lsmod:
> snd_ac97_codec        100224  1 snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
nvidia               4553556  12
snd_pcm                96708  5 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  3 snd_rtctimer,snd_seq,snd_pcm
psmouse                40004  0
i2c_core               22848  2 i2c_acpi_ec,nvidia
pcspkr                  2244  0
snd                    60004  18 snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11304  2 snd_intel8x0,snd_pcm

Do you think I'm having a problem from a neccesary module getting loaded too late in the chain??? I'm just guessing...This is a bit out of my league.

---

### Post by zettberlin on 2006-09-06
So if i get you right, you want to play a soundfont via jackd?

What happens, if you use fluidsynth to load the font?

---

### Post by capsid on 2006-09-06
> So if i get you right, you want to play a soundfont via jackd?
What happens, if you use fluidsynth to load the font?

So i got a soundfont, uncompressed it, and loaded it into fluidsynth via qsynth. Puredata is sending MIDI into fluidsynth, qsynth is routing out to alsa_pcm (and the light is blinking as it receives the midi), but there is no sound.  Maybe my soundfont is bad?  I tried adjusting the offset and changing the MIDI program data.  I went into Channels on Qsynth and tried to preview the samples and they didnt make any sounds...  I'm really new to soundfonts...  

When I just run "fluidsynth" by itself from the commandline I get:> 
cca_open_socket: could not connect to host 'localhost', service '14541'
cca_init: could not connect to server 'localhost' - disabling ladcca
fluidsynth: warning: Requested a period size of 64, got 1881 instead
fluidsynth: warning: Requested 16 periods, got 8 instead
fluidsynth: ALSA driver: Using format s16, rw, interleaved

What are some other ways to easily play a soundfont?

---

### Post by capsid on 2006-09-06
I don't know what black arts I used, but I was able to get timidity running in -Oj -iA mode, but it is very laggy.  Does anyone know how to control this?    It doesn't seem like a Jack thing because I can send midi out from Vkeybd to Timidity and ZynAddSubFx at the same time and Zyn responds in realtime while Timidity has a problematic amount of lag.  I guess it's not a big deal cause I'm going to be sending MIDI out to an external synth eventually, and then it wont make a difference.  

I wasnt able to get Qsynth working, but I will test some more soundfonts tomorrow in case the one I got was corrupted.

---

