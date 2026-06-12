---
title: "Help in getting my TV tuner card to work in Feisty"
date: 2007-06-19
forum: Multimedia &amp; Video
---

### Post by darthchaosofrspw on 2007-06-19
Here's my dilemma. I want to get my AVerTV GO 007 FM Plus TV tuner working with Ubuntu Feisty. Well, I can get it to work by running "sudo modprobe saa7134" and "sudo modprobe saa7134-alsa" in the terminal and then open up TV Time, but I can't hear any audio. I heard somewhere that the saa7134-oss is better audio-wise than saa7134-alsa, but every time I go to run "sudo modprobe saa7134-oss", I get the following:

```
FATAL: Error inserting saa7134_oss (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/saa7134/saa7134-oss.ko): Device or resource busy
```

Here's what I get about the TV tuner when I run "sudo lspci -v -v" :

```
00:0a.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d0)
        Subsystem: Avermedia Technologies Inc Avermedia AVerTV GO 007 FM
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (63750ns min, 63750ns max)
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at fa000000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=3 PME-
```


Any help would be greatly appreciated. Feel free to reply on here on give me a PM.

---

### Post by eldragon on 2007-06-19
ok, probably you already knew this, but just to make sure:

you need to run a stereo cable from your capture card's sound output to the line in jack in your soundcard. these cheapo cards wonth run audio through the pci bus.

then you will have to fiddle with the recording panel for your card and make it capture throught the line in.

---

### Post by darthchaosofrspw on 2007-06-19
> **eldragon said:**
> ok, probably you already knew this, but just to make sure:

you need to run a stereo cable from your capture card's sound output to the line in jack in your soundcard. these cheapo cards wonth run audio through the pci bus.

then you will have to fiddle with the recording panel for your card and make it capture throught the line in.

If that's the case, then I'm SOL and JWF because my TV tuner card doesn't have a sound output jack. The only jacks on the card are the cable input jack, the A/V input jack (to connect composite audio/video from a device like a VCR to the card), the S-video port, and the IR receiver port. 

I guess I could run a 1/8" Y-cable from the VCR's stereo audio output ports to my sound card.  

But the picture is working just fine on TV Time.

If all else fails, I'll just use my Windows partition for TV/radio and Ubuntu for everything else.




EDIT: I got the sound to work! I had to install sox from Synaptic Package Manager, and then I had to run the following command in the terminal:

sox -c 2 -sw -r 32000 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp

That command dumps the audio from the TV tuner to the sound card.

Is there any way I can add that command to TV Time's command so it will open when TV Time is opened?

---

### Post by Celil Rifat on 2007-07-30
> **darthchaosofrspw said:**
> 
sox -c 2 -sw -r 32000 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp

That command dumps the audio from the TV tuner to the sound card.

Is there any way I can add that command to TV Time's command so it will open when TV Time is opened?

Thanks. This worked for me. Has anybody gotten the card to work on MythTV?

---

### Post by darthchaosofrspw on 2007-12-23
> **Celil Rifat said:**
> Thanks. This worked for me. Has anybody gotten the card to work on MythTV?

I did, but I had to connect a 1/8" stereo Y-adapter to my VCR and my PC's line-in jack and use the VCR as a tuner/cable box.

I may buy another TV tuner in the future, and since we're a little over a year away from the analog switch-off date, I may as well go for a HDTV card. And it will prolly be a Win TV card.

---

