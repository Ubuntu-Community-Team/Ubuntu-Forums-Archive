---
title: "flash killed my 7.1 audio? (and more)"
date: 2011-10-22
forum: Multimedia Software
---

### Post by borednerds on 2011-10-22
So I've been struggling with getting mythbuntu to output 7.1 sound all day, due, most likely, to my own ignorance.

So, after a fresh reinstall, I navigate to the sound page on the mythtv frontend, viola! DAC 7.1 sound, Perfect! (ALSA:hw:CARD: CMI8768, DEV=1) 

Then I go to youtube to test the sound and can't because I don't have flash installed. So I installed the ubuntu flash pack and it informed me prior to that two libraries would be deleted in the process.

Well, now not only does the sound not come out of my coaxial s/pdif, when I re-navigate to mythtv, it tells me again that the max it will put out is 5.1

I'm running mythbuntu 11.10
Sound card is Diamond Xtreme sound 7.1/24 bit, Chipset CMI8768

Running [FONT="Courier New"]aplay -l[/FONT]

```
borednerds@HAL9000b:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8768 [C-Media CMI8768], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
I do not believe this is the same output it would give if I had run it before installing flash.


In reinstalls past, I was able to get VLC to output sound over s/pdif, but only either stereo or 5.1 after (somehow) tinkering around in alsamixer (gui and terminal). 

Running [FONT="Courier New"]alsamixer[/FONT] gives this:
```


&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.24.2 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: C-Media CMI8768                                                                                                                                                                                                                             F1:  Help               &#9474;
&#9474; Chip: CMedia PCI                                                                                                                                                                                                                                  F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All                                                                                                                                                                                                          F6:  Select sound card  &#9474;
&#9474; Item: 3D Control - Switch [Off]                                                                                                                                                                                                                   Esc: Exit               &#9474;
&#9474;                                                                                                                                                                                                                                                                           &#9474;
&#9474;                                                                                                                                                                                                                                                                           &#9474;
&#9474;     &#9484;&#9472;&#9472;&#9488;                    &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;                    &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;                                &#9484;&#9472;&#9472;&#9488;                                                                                                        &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;                  &#9474;
&#9474;     &#9474;  &#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;        &#9474;  &#9474;                    &#9474;  &#9474;        &#9474;  &#9474;                                &#9474;  &#9474;                                                                                                        &#9474;  &#9474;        &#9474;  &#9474;                  &#9474;
&#9474;     &#9474;  &#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;        &#9474;  &#9474;                    &#9474;  &#9474;        &#9474;  &#9474;                                &#9474;  &#9474;                                                                                                        &#9474;  &#9474;        &#9474;  &#9474;                  &#9474;
&#9474;     &#9474;  &#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;        &#9474;  &#9474;                    &#9474;  &#9474;        &#9474;  &#9474;                                &#9474;  &#9474;                                                                                                        &#9474;  &#9474;        &#9474;  &#9474;                  &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                    &#9474;  &#9474;        &#9474;  &#9474;                                &#9474;  &#9474;                                                                                                        &#9474;  &#9474;        &#9474;  &#9474;                  &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                    &#9474;  &#9474;        &#9474;  &#9474;                                &#9474;  &#9474;                                                                                                        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                  &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                    &#9474;  &#9474;        &#9474;  &#9474;                                &#9474;  &#9474;                                                                                                        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                  &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                    &#9474;  &#9474;        &#9474;  &#9474;                                &#9474;  &#9474;                                                                                                        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                  &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                    &#9474;  &#9474;        &#9474;  &#9474;                                &#9474;  &#9474;                                                                                                        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                  &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                    &#9474;  &#9474;        &#9474;  &#9474;                                &#9474;  &#9474;                                                                                                        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                  &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                    &#9474;  &#9474;        &#9474;  &#9474;                                &#9474;  &#9474;                                                                                                        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                  &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                    &#9474;  &#9474;        &#9474;  &#9474;                                &#9474;  &#9474;                                                                                                        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                  &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                    &#9474;  &#9474;        &#9474;  &#9474;                                &#9474;  &#9474;                                                                                                        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                  &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                    &#9474;  &#9474;        &#9474;  &#9474;                                &#9474;  &#9474;                                                                                                        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;                  &#9474;
&#9474;     &#9492;&#9472;&#9472;&#9496;        &#9484;&#9472;&#9472;&#9488;        &#9500;&#9472;&#9472;&#9508;        &#9500;&#9472;&#9472;&#9508;        &#9500;&#9472;&#9472;&#9508;       Line-In      &#9500;&#9472;&#9472;&#9508;        &#9500;&#9472;&#9472;&#9508;        &#9484;&#9472;&#9472;&#9488;     Center/LFE     &#9500;&#9472;&#9472;&#9508;        &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;        &#9500;&#9472;&#9472;&#9508;        &#9500;&#9472;&#9472;&#9508;        &#9484;&#9472;&#9472;&#9488;      &#9474;
&#9474;                 &#9474;MM&#9474;        &#9474;OO&#9474;        &#9474;OO&#9474;        &#9474;MM&#9474;                    &#9474;MM&#9474;        &#9474;MM&#9474;        &#9474;MM&#9474;                    &#9474;MM&#9474;        &#9474;OO&#9474;        &#9474;OO&#9474;        &#9474;OO&#9474;        &#9474;OO&#9474;        &#9474;OO&#9474;        &#9474;OO&#9474;        &#9474;OO&#9474;        &#9474;OO&#9474;        &#9474;OO&#9474;        &#9474;OO&#9474;        &#9474;OO&#9474;      &#9474;
&#9474;                 &#9492;&#9472;&#9472;&#9496;        &#9492;&#9472;&#9472;&#9496;        &#9492;&#9472;&#9472;&#9496;        &#9492;&#9472;&#9472;&#9496;                    &#9492;&#9472;&#9472;&#9496;        &#9492;&#9472;&#9472;&#9496;        &#9492;&#9472;&#9472;&#9496;                    &#9492;&#9472;&#9472;&#9496;        &#9492;&#9472;&#9472;&#9496;        &#9492;&#9472;&#9472;&#9496;        &#9492;&#9472;&#9472;&#9496;        &#9492;&#9472;&#9472;&#9496;        &#9492;&#9472;&#9472;&#9496;        &#9492;&#9472;&#9472;&#9496;        &#9492;&#9472;&#9472;&#9496;        &#9492;&#9472;&#9472;&#9496;        &#9492;&#9472;&#9472;&#9496;        &#9492;&#9472;&#9472;&#9496;        &#9492;&#9472;&#9472;&#9496;      &#9474;
&#9474;    77<>77                 100<>100     77<>77       0<>0                    0<>0         0                                   0                                                                                                           67         0<>0                  &#9474;
&#9474;    Master   <3D Control >    PCM        Synth       Line     Line-In Mod     CD          Mic      Mic Boost  Mic-In Mode    Phone     S/PDIF 5V  S/PDIF Copy S/PDIF In M S/PDIF In P S/PDIF In S S/PDIF In V S/PDIF Loop S/PDIF Outp    Beep         Aux     Four Channe  &#9474;
&#9474;                                                                                                                                                                                                                                                                           &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

```

So my questions are:[LIST=1]
[*]How do I get those libraries back?
[*]How do I get it to output 7.1 sound over s/pdif?
[/LIST]
I went through the audio sticky above before my most recent reinstall, but I think I just mucked things up even more (and so performed a reinstall). I'm not a fan of reinstalling over and over, but at this stage, I don't have anything set up that would be labor intensive to do again.

---

### Post by BicyclerBoy on 2011-10-22
It is not possible to do 7.1 over S/PDIF..not unless you write some new firmware for the HT amp AVR & rewrite alsa..

S/PDIF supports matrix encoded 5.1 AC3 (640K) DTS (1M5) 48KHz or stereo PCM 192KHz/24bit (if your amp supports).

The only way DEV=1 gave you 7.1 is if your amp has some DSP 7.1 surround nonsense from a stereo signal. (pro-logic stuff).
OR you have 8 discrete analogue cables from soundcard to the amp.

The best audio solution if you have a HT amp AVR is to throw the soundcard away & use HDMI from video card or just S/PDIF from mobo.
HDMI lets you have AC3/DTS & the HDA modes + LPCM multi-channel all at full bitrates your amp will support.

This will get you AC3/DTS 5.1 digital pass-thru' over S/PDIF.
vlc --aout alsa --alsa-audio-device iec958

I doubt flash installer would do anything to your audio except maybe install some pulse-audio stuff.

---

### Post by borednerds on 2011-10-23
man, I had no idea s/pdif only supported 5.1. Thats the whole reason I bought the card. My amp does support prologicIIx, so that explains that, unfortunately. could you point me to documentation that states that s;pdif is only 5.1, explicitly? I can't find any. It seems to me that, if it's a digital signal, it should be able to handle it?

my video card, Nvidia 8400 GS, only supports stereo out PCM via HDMI so that wont do me any good.

Flash itself didn't do anything to  my audio, but it forced me to remove two libraries before I could install it.

---

### Post by BicyclerBoy on 2011-10-23
I'm fairly sure 5.1 is all S/PDIF supports via matrix AC3.
It it possible to do 6.1 using DTS-ES.

Why would S/PDIF support it ? It is an old standard designed for stereo PCM with non-audio data pass-thru' matrix encoded audio.
You would need to get your audio into that matrix encoded format..

There is no open source DTS encoder in linux.
There could be a h/w encoder soundcard that works in linux.
So the soundcard just streams the digital pass-thru'.

I don't understand why 'hifi' soundcards still exist..
There is no point buying a soundcard unless you want clean analogue output or the card has some digital I/O like McI2S.

You can not beat HDMI because it is the only way to get HDA into consumer HT amps .

Sell the soundcard & buy a nVidia GT430.
If your amp has HDMI then you get full 8 channels of 192KHz 24bit LPCM & DTS-MA & HD DD..

---

### Post by borednerds on 2011-10-23
Yeah, that makes sense. Well, dang it, the whole reason I bought the card was to avoid buying an all new card! haha

Now my question is how do I know the card supports it and how do I know the mobo  supports it? I mean, I have your report for that card, but what of others? Newegg doesn't explicitly list audio over hdmi support, so how can I be sure?

I bought the sound card because I didn't think the mobo natively supported 7.1 sound.

I'll look around the forums, I'm sure this is answered somewhere. Thanks for your help!

---

### Post by BicyclerBoy on 2011-10-23
Look up the technical specs on nVidia website..never rely on retailers or sales people..

I only mentioned GT430 because it does support full HDA over HDMI & it is the best HTPC card now.

If you want more openGL/gaming power get something else..GTX480 GTX560ti or GTX580 or equivalent AMD..

The 8400GS was a good HTPC card about 4 years ago & would make a good backup box or 2nd frontend for a smaller TV with no DLNA..

---

