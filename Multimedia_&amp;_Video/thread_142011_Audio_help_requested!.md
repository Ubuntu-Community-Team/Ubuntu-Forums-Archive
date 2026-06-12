---
title: "Audio help requested!"
date: 2006-03-09
forum: Multimedia &amp; Video
---

### Post by kudu on 2006-03-09
I have a system with Audigy 2 card and I'm trying to figure out if it's set up correctly. There are two cards on this machine an Intel integrated ICH5 and an Audigy 2 (set as default). I have sound in general but when I compile certain ClanLib programs such as the example MikMod program, I don't get any sound playback when the program runs. So I'm trying to fix that.

Here's my aadebug output:

ALSA Audio Debug v0.1.0 - Thu Mar  9 11:01:06 AKST 2006
[http://alsa.opensrc.org/index.php?page=aadebug](http://alsa.opensrc.org/index.php?page=aadebug)
[http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Kernel ----------------------------------------------------
Linux ubuntu 2.6.12-10-686 #1 Mon Feb 13 12:18:37 UTC 2006 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_emu10k1_synth       7520  0
snd_emux_synth         36032  1 snd_emu10k1_synth
snd_seq_virmidi         7168  1 snd_emux_synth
snd_seq_midi_emul       7584  1 snd_emux_synth
snd_seq_dummy           3620  0
snd_seq_oss            33600  0
snd_seq_midi            9088  0
snd_seq_midi_event      6848  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                50736  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           118340  3 snd_emu10k1_synth
snd_rawmidi            24704  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_seq_device          8460  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_util_mem            4448  2 snd_emux_synth,snd_emu10k1
snd_hwdep               8896  2 snd_emux_synth,snd_emu10k1
snd_intel8x0           33248  0
snd_ac97_codec         83932  2 snd_emu10k1,snd_intel8x0
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  5 snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24164  3 snd_seq,snd_emu10k1,snd_pcm
snd                    54884  17 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         10600  3 snd_emu10k1,snd_intel8x0,snd_pcm

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.9 (Sun May 29 07:31:02 2005 UTC).
0 [ICH5           ]: ICH4 - Intel ICH5
                     Intel ICH5 with AD1980 at 0xfebffa00, irq 17
1 [Audigy2        ]: Audigy2 - Audigy 2 [Unknown]
                     Audigy 2 [Unknown] (rev.4, serial:0x10031102) at 0xdd80, irq 17
 20: [0- 4]: digital audio playback
 27: [0- 3]: digital audio capture
 26: [0- 2]: digital audio capture
 25: [0- 1]: digital audio capture
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  0: [0- 0]: ctl
  1:       : sequencer
 33:       : timer
 36: [1- 0]: hardware dependent
 41: [1- 1]: raw midi
 40: [1- 0]: raw midi
 52: [1- 4]: digital audio playback
 60: [1- 4]: digital audio capture
 51: [1- 3]: digital audio playback
 50: [1- 2]: digital audio playback
 58: [1- 2]: digital audio capture
 57: [1- 1]: digital audio capture
 48: [1- 0]: digital audio playback
 56: [1- 0]: digital audio capture
 32: [1- 0]: ctl
 38: [1- 2]: hardware dependent
 42: [1- 2]: raw midi
 43: [1- 3]: raw midi
01-00: EMU10K1 (FX8010)
01-02: Emux WaveTable
00-00: Intel ICH : Intel ICH5 : playback 1 : capture 1
00-01: Intel ICH - MIC ADC : Intel ICH5 - MIC ADC : capture 1
00-02: Intel ICH - MIC2 ADC : Intel ICH5 - MIC2 ADC : capture 1
00-03: Intel ICH - ADC2 : Intel ICH5 - ADC2 : capture 1
00-04: Intel ICH - IEC958 : Intel ICH5 - IEC958 : playback 1
01-00: emu10k1 : ADC Capture/Standard PCM Playback : playback 32 : capture 1
01-01: emu10k1 mic : Mic Capture : capture 1
01-02: emu10k1 efx : Multichannel Capture/PT Playback : playback 8 : capture 1
01-03: emu10k1 : Multichannel Playback : playback 1
01-04: p16v : p16v : playback 1 : capture 1
Client info
  cur  clients : 5
  peak clients : 5
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
    Connecting To: 63:0
Client  62 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
Client  63 : "OSS sequencer" [Kernel]
  Port   0 : "Receiver" (-we-)
    Connected From: 0:1
Client  72 : "Audigy MPU-401 (UART)" [Kernel]
  Port   0 : "Audigy MPU-401 (UART)" (RWeX)
  Port  32 : "Audigy MPU-401 #2" (RWeX)
Client  73 : "Emu10k1 WaveTable" [Kernel]
  Port   0 : "Emu10k1 Port 0" (-We-)
  Port   1 : "Emu10k1 Port 1" (-We-)
  Port   2 : "Emu10k1 Port 2" (-We-)
  Port   3 : "Emu10k1 Port 3" (-We-)

Dev Snd ---------------------------------------------------
controlC0  hwC1D2    midiC1D2  pcmC0D0p  pcmC0D3c  pcmC1D0p  pcmC1D2p  pcmC1D4p
controlC1  midiC1D0  midiC1D3  pcmC0D1c  pcmC0D4p  pcmC1D1c  pcmC1D3p  seq
hwC1D0     midiC1D1  pcmC0D0c  pcmC0D2c  pcmC1D0c  pcmC1D2c  pcmC1D4c  timer

CPU -------------------------------------------------------
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
cpu MHz         : 2993.386

RAM -------------------------------------------------------
MemTotal:       515824 kB
SwapTotal:     1510068 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: Intel Corp. 82875P Memory Controller Hub (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:02:02.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)

I'd appreciate it if some knowledgeable audio people would look it over and tell me if there's anything wrong with it. Also note the lack of a modprobe conf file. Is that a problem needs attention ?

Thanks!
kudu

---

### Post by John.Michael.Kane on 2006-03-09
[http://www.ubuntuforums.org/showthread.php?t=104388&highlight=sound+cards](http://www.ubuntuforums.org/showthread.php?t=104388&highlight=sound+cards)

---

### Post by kudu on 2006-03-09
[QUOTE=SD-Plissken][http://www.ubuntuforums.org/showthread.php?t=104388&highlight=sound+cards](http://www.ubuntuforums.org/showthread.php?t=104388&highlight=sound+cards)[/QUOTE]

Thanks, but didn't help.

Regards,
kudu

---

