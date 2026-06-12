---
title: "Getting MIDI keyboard to play"
date: 2010-12-30
forum: Multimedia Software
---

### Post by Cerapter on 2010-12-30
I'm running Ubuntu 10.04 with the Kubuntu desktop environment. I'm trying to use my MIDI keyboard through ALSA, Linuxsampler and Qsampler. But I still haven't got a sound out of it, and I fear that the information about the existence of the keyboard doesn't get through. That, or I don't know how to configure properly.

In sndstat, both my sound card (Guitar Rig) and my keyboard (Hua Xing) is showing up:
> cerapter@Ancalagon:~$ cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.21 emulation code)                                             
Kernel: Linux Ancalagon 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 10:14:11 UTC 2010 x86_64
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA Intel at 0xfc300000 irq 21
Native Instruments Guitar Rig Mobile IO (usb-0000:00:1d.7-4)
Hua Xing Hua Xing at usb-0000:00:1d.2-1, full speed

Audio devices:
0: ALC268 Analog (DUPLEX)
1: Guitar Rig Mobile IO (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
2: Hua Xing

Timers:
31: system timer

Mixers:
0: Realtek ALC268
1: Guitar Rig Mobile IO
2: USB Mixer
But I'm only getting the sound card to show up in Pulseaudio. In Qsampler, I cannot seem to find either (though I suppose this is just the - to me - cryptic interface of the software).

Do you know what I need to do?

If it's of any use, here's my /proc/modules:
> cerapter@Ancalagon:~$ cat /proc/modules
snd_usb_audio 92747 0 - Live 0xffffffffa03a0000
snd_usb_lib 19193 1 snd_usb_audio, Live 0xffffffffa024f000
snd_usb_caiaq 23526 2 - Live 0xffffffffa01cd000
binfmt_misc 7960 1 - Live 0xffffffffa01ec000
ppdev 6375 0 - Live 0xffffffffa01d8000
snd_hda_codec_realtek 279008 1 - Live 0xffffffffa0359000
fbcon 39270 72 - Live 0xffffffffa02d6000
tileblit 2487 1 fbcon, Live 0xffffffffa01ca000
font 8053 1 fbcon, Live 0xffffffffa0199000
bitblit 5811 1 fbcon, Live 0xffffffffa0135000
softcursor 1565 1 bitblit, Live 0xffffffffa00ae000
vga16fb 12757 0 - Live 0xffffffffa0096000
vgastate 9857 1 vga16fb, Live 0xffffffffa0058000
joydev 11072 0 - Live 0xffffffffa0033000
pcmcia 35580 0 - Live 0xffffffffa034e000
snd_hda_intel 25741 3 - Live 0xffffffffa0345000
snd_hda_codec 85759 2 snd_hda_codec_realtek,snd_hda_intel, Live 0xffffffffa032e000
snd_hwdep 6924 2 snd_usb_audio,snd_hda_codec, Live 0xffffffffa01b1000
snd_pcm_oss 41394 0 - Live 0xffffffffa029f000
snd_mixer_oss 16299 1 snd_pcm_oss, Live 0xffffffffa0138000
snd_pcm 87946 6 snd_usb_audio,snd_usb_caiaq,snd_hda_intel,snd_hda_codec,snd_pcm_oss, Live 0xffffffffa0316000
snd_seq_dummy 1782 0 - Live 0xffffffffa007d000
snd_seq_oss 31191 0 - Live 0xffffffffa0189000
snd_seq_midi 5829 0 - Live 0xffffffffa00a0000
snd_rawmidi 23420 3 snd_usb_lib,snd_usb_caiaq,snd_seq_midi, Live 0xffffffffa012d000
snd_seq_midi_event 7267 2 snd_seq_oss,snd_seq_midi, Live 0xffffffffa0079000
snd_seq 57481 7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event, Live 0xffffffffa00e6000
arc4 1473 2 - Live 0xffffffffa0030000
iwl3945 79436 0 - Live 0xffffffffa02f9000
snd_timer 23649 2 snd_pcm,snd_seq, Live 0xffffffffa02ec000
snd_seq_device 6888 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq, Live 0xffffffffa02e4000
iwlcore 125179 1 iwl3945, Live 0xffffffffa02b5000
tifm_7xx1 4674 0 - Live 0xffffffffa02ae000
mac80211 238896 2 iwl3945,iwlcore, Live 0xffffffffa0262000
i915 323510 3 - Live 0xffffffffa01fe000
nsc_ircc 21412 0 - Live 0xffffffffa01f1000
yenta_socket 22901 1 - Live 0xffffffffa01e4000
rsrc_nonstatic 9830 1 yenta_socket, Live 0xffffffffa01db000
sdhci_pci 6700 0 - Live 0xffffffffa01d4000
snd 71251 24 snd_usb_audio,snd_usb_caiaq,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xffffffffa01b6000
drm_kms_helper 30742 1 i915, Live 0xffffffffa01a7000
acer_wmi 15829 0 - Live 0xffffffffa019d000
tifm_core 7654 1 tifm_7xx1, Live 0xffffffffa0195000
cfg80211 148725 3 iwl3945,iwlcore,mac80211, Live 0xffffffffa0162000
psmouse 64576 0 - Live 0xffffffffa0150000
serio_raw 4918 0 - Live 0xffffffffa0084000
sdhci 17928 1 sdhci_pci, Live 0xffffffffa0149000
led_class 3764 4 iwl3945,iwlcore,acer_wmi,sdhci, Live 0xffffffffa0069000
pcmcia_core 38176 3 pcmcia,yenta_socket,rsrc_nonstatic, Live 0xffffffffa013d000
irda 205667 1 nsc_ircc, Live 0xffffffffa00f8000
crc_ccitt 1675 1 irda, Live 0xffffffffa0010000
soundcore 8052 1 snd, Live 0xffffffffa002c000
drm 198948 4 i915,drm_kms_helper, Live 0xffffffffa00b3000
i2c_algo_bit 6024 1 i915, Live 0xffffffffa000c000
intel_agp 29319 2 i915, Live 0xffffffffa00a4000
snd_page_alloc 8500 2 snd_hda_intel,snd_pcm, Live 0xffffffffa009b000
video 20623 1 i915, Live 0xffffffffa008e000
output 2503 1 video, Live 0xffffffffa0088000
lp 9336 0 - Live 0xffffffffa007f000
parport 37160 2 ppdev,lp, Live 0xffffffffa006d000
ohci1394 30260 0 - Live 0xffffffffa005f000
tg3 122382 0 - Live 0xffffffffa0038000
ieee1394 94771 1 ohci1394, Live 0xffffffffa0012000
ahci 37870 3 - Live 0xffffffffa0000000


---

### Post by Cerapter on 2011-02-18
I have figured this out, and I think this is how I did it:

1. I installed JACK and qjackctl.
2. I started qjackctl, pressed Setup and set my external sound card as Interface.
3. When LinuxSampler was up and running, I manually connected it to the external keyboard in qjackctl's Connections window.

---

