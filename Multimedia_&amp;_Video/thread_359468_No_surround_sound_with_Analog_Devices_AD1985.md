---
title: "No surround sound with Analog Devices AD1985"
date: 2007-02-12
forum: Multimedia &amp; Video
---

### Post by khaeru on 2007-02-12
Hi. I'm having a problem, which after hours of googling and browsing the forums I've been unable to solve.

I'm unable to get surround sound to play on my Ubuntu Edgy desktop. I have an Asus P4P8X motherboard, with a SoundMAX AD1985 audio codec. I have a set of 4-channel Altec Lansing speakers; the front channel cable is plugged in to the Line Out jack, and the rear channel cable is plugged into the Line In jack, which is supposed to function as the rear channel output in 4-channel mode. Some information, following suggested commands from [http://www.ubuntuforums.org/showthread.php?t=120488:](http://www.ubuntuforums.org/showthread.php?t=120488:)

```
khaeru@khaeru-desktop:~$ cat /proc/asound/cards
 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with AD1985 at 0xfebff800, irq 209

khaeru@khaeru-desktop:~$ lsmod | grep snd
snd_intel8x0           34844  5 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  2 snd_pcm_oss
snd_pcm                84612  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  2 snd_pcm
snd                    58372  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  2 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
```

From [http://alsa.opensrc.org/SurroundSound](http://alsa.opensrc.org/SurroundSound), I found a link to [ftp://ling.lll.hawaii.edu/pub/greg/Surround-SDL-testfiles.tgz](ftp://ling.lll.hawaii.edu/pub/greg/Surround-SDL-testfiles.tgz) (large file!), which contains a chan-id.wav that supposedly contains a voice saying something like "Front Left, Front Right, Centre, Subwoofer, Left Surround, Right Surround". I play this with:

```
$ aplay chan-id.wav
```

and hear only "Front Left, Front Right" from the appropriate speakers, then silence. If I type:

```
$ alsamixer
```

I find (some settings omitted):

[LIST]
[*]Master 81%
[*]Master Mono: off
[*]Master Surround: 81%
[*]Headphone Jack Sense: off
[*]PCM: 81%
[*]Surround: off
[*]Surround Jack Mode: Shared (other option is Independent)
[*]Center: 81%
[*]LFE: 81%
[*](omitted)
[*]Channel Mode: 2ch **4ch** 6ch
[*]Downmix: Off
[*](omitted)
[*]Exchange Front/Surround: Off
[*]Spread Front to Surround and Center/LFE: Off[/LIST]
Some additional symptoms:

[LIST]
[*]If I set "Spread Front to Surround and Centre/LFE" to on, I hear "Front Left" from *both* the front and rear left speakers, and "Front Right" from *both* the front and rear right speakers. This tells me the Line Out jack is, in fact, generating an output signal.
[*]If I set "Exchange Front/Surround" to On, I hear "Front Left" from the rear left speaker, and "Front Right" from the rear right speaker.
[*]If I set both of the above options, the result is the same as setting only "Spread Front to Surround and Centre/LFE"
[*]If set "Channel Mode" to 6ch the results are identical. If I set it to "2ch", the results are the same only there is never any sound from the rear speakers. 
[/LIST]
I conclude that for some reason alsa or something else is only seeing or using the front two channels of the device, even though the rear channels exist. How do I make it see the rear channels so I can get true surround sound? Do I have to edit my .asoundrc file? Any help is appreciated.

---

