---
title: "80Hz sound with SB live! on dapper"
date: 2006-06-08
forum: Multimedia &amp; Video
---

### Post by morphis on 2006-06-08
Hey!
I got the SB live! sound card which worked well on breezy, but after upgrade my desktop to dapper, i have a big problem...
When i listen to anything i have an odd sound like a broken speaker (like 80Hz for who know)with distortion. Quite anoying thing! If anyone have the same problem or know how to solve it, It would be nice to make a note..
Anyway CHeeRS...

---

### Post by Sutekh on 2006-06-09
I know that with my SB Live 24bit (CA0106) if the channel volume is over around 70% the sound becomes very poor, like a dead speaker.  I don't know if its the same phenomenon you are relating.

You could try anyway.  Use the alsamixer and check that all the channels are not to high.
```
alsamixer
```

---

### Post by morphis on 2006-06-09
Nice to answer me...
After trying a lot of configurations with alsamixer, the problem can't really be solved by this way, it makes the sound better and the anomalies becomming scarce but it doesn't fix it...

---

### Post by Sutekh on 2006-06-09
Ok.  What is the type of SB sound card?
```
cat /proc/asound/cards
``` What modules are loaded for the card?  emu10k1?
```
lsmod | grep snd
``` Some good places to look for the same issue and solutions are the [ALSA Soundcard Matrix]("http://www.alsa-project.org/alsa-doc/") for your specific card and [ALSA Openserc Org]("http://alsa.opensrc.org/")

---

### Post by morphis on 2006-06-09
one more time thx for reply...
I gave no informations about my card on the lasts posts...have a look:

```
morphe@master:~$ cat /proc/asound/cards
0 [rev50          ]: VIA686A - VIA 82C686A/B rev50
                     VIA 82C686A/B rev50 with ICE1232 at 0xdc00, irq 12
1 [Live           ]: EMU10K1 - SBLive! Value [CT4832]
                     SBLive! Value [CT4832] (rev.6, serial:0x80271102) at 0xe800, irq 12
morphe@master:~$ lsmod | grep snd
snd_seq_dummy           4164  0
snd_seq_oss            37696  0
snd_emu10k1_synth       8384  0
snd_emux_synth         40320  1 snd_emu10k1_synth
snd_seq_midi            9888  0
snd_seq_virmidi         8640  1 snd_emux_synth
snd_seq_midi_event      8064  3 snd_seq_oss,snd_seq_midi,snd_seq_virmidi
snd_seq_midi_emul       8000  1 snd_emux_synth
snd_seq                58832  9 snd_seq_dummy,snd_seq_oss,snd_emux_synth,snd_seq_midi,snd_seq_virmidi,snd_seq_midi_event,snd_seq_midi_emul
snd_emu10k1           133348  3 snd_emu10k1_synth
snd_util_mem            5184  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10272  2 snd_emux_synth,snd_emu10k1
snd_via82xx            31192  1
snd_ac97_codec         98912  2 snd_emu10k1,snd_via82xx
snd_ac97_bus            2688  1 snd_ac97_codec
snd_pcm_oss            56352  0
snd_mixer_oss          20800  1 snd_pcm_oss
snd_pcm                96772  5 snd_emu10k1,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              27204  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         11592  3 snd_emu10k1,snd_via82xx,snd_pcm
snd_mpu401_uart         8896  1 snd_via82xx
snd_rawmidi            27552  4 snd_seq_midi,snd_seq_virmidi,snd_emu10k1,snd_mpu401_uart
snd_seq_device          9548  8 snd_seq_dummy,snd_seq_oss,snd_emu10k1_synth,snd_emux_synth,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd                    60068  20 snd_seq_oss,snd_emux_synth,snd_seq_virmidi,snd_seq,snd_emu10k1,snd_hwdep,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              11040  1 snd
gameport               17032  3 snd_via82xx,emu10k1_gp
morphe@master:~$
```

Im a noob on linux... I really cant see where it is from..and those lines have no real meaning to me anyway if it can help u to find a solution it would be great...

---

### Post by Sutekh on 2006-06-09
[quote=morphis]one more time thx for reply...
I gave no informations about my card on the lasts posts...have a look:

...

Im a noob on linux... I really cant see where it is from..and those lines have no real meaning to me anyway if it can help u to find a solution it would be great...[/quote] That's ok, I'll try to explain them to the best of my knoweledge, see if we can't work this out.

[quote=morphis]
morphe@master:~$ cat /proc/asound/cards
0 [rev50          ]: VIA686A - VIA 82C686A/B rev50
                     VIA 82C686A/B rev50 with ICE1232 at 0xdc00, irq 12
1 [Live           ]: EMU10K1 - SBLive! Value [CT4832]
                     SBLive! Value [CT4832] (rev.6, serial:0x80271102) at 0xe800, irq 12[/quote] This means you have *two* sound cards, the first (card 0) looks like an onboard one (VIA chipset).  The second card (card 1) is the SB Live! card, it uses the emu10k1 chipset like I thought.

This next output lists the sound modules (drivers if you like) that are loaded into the kernel.  I wanted to make sure you have the appropriate ones loaded for your card.  

According to the [ALSA Soundcard Matrix]("http://www.alsa-project.org/alsa-doc/"), your onboard card the [VIA82C686A needs the snd-via82xx module]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=VIA&card=VIA+southbridge+AC97+audio.&chip=VIA82C686%2C+VIA8233%2C+VIA8233A%2C+VIA8235%2C+VIA8237&module=via82xx") (look about a page or two down for the *modprobe *command).   The [SB Live! needs the snd-emu10k1 module]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+5.1.&chip=emu10k1&module=emu10k1").  

So let's check that the correct modules are loaded.
[quote=morphis]
morphe@master:~$ lsmod | grep snd

....

snd                    60068  20 snd_seq_oss,snd_emux_synth,snd_seq_virmidi,snd_seq,**snd_emu10k1**,snd_hwdep,**snd_via82xx**,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device

....

morphe@master:~$[/quote]So the correct modules are loaded.


Knowing this and the fact you have two sound cards, perhaps it is because the onboard sound is being used, rather than the SB Live!?  

You can change the default card by using a special config file ~/.asoundrc.

If you create a new file
```
gedit ~/.asoundrc
``` then paste in these lines
```

pcm.!default {
    type hw
    **card 1**
}
ctl.!default {
    type hw
    **card 1**
}           
``` 
Card 1 to use the SB Live!

I hope this makes a difference.

---

### Post by morphis on 2006-06-10
Hey!

Thank you to explain me a bit what i'm doing ...
After setting the sb live as the default sound card, no real changes...
I really dont know where is that sound from if the drivers are working properly, maybe the settings of the alsa mixer..or maybe its only a mechanical problem...But i can notice that it is  not due to a saturation of the sound...It looks to be random like...

Anyway I learned a bit about how my computer was working which is nice!

---

