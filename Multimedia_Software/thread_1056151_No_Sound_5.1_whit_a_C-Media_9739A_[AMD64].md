---
title: "No Sound 5.1 whit a C-Media 9739A [AMD64]"
date: 2009-01-31
forum: Multimedia Software
---

### Post by gasaqholl on 2009-01-31
¡Hi everybody!

I have a Advent 3419 (info. at the end) whit a C-Media 9739A AC'97 sound card (GNU/Linux reports it as a VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller) and I have a clear a sharp stereo sound.

But I have never got the 5.1 sound, the best a got is a 2.1 to say so.

Right now I have Ubuntu 8.10, PulseAudio and ALSA. ¿Is there a way to enable 5.1 sound in this card?

**Processor**
Name	AMD Athlon(tm) 64 Processor 3400+
**PCI Devices**
Host bridge	VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge
PCI bridge	VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
Multimedia controller	Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder
Communication controller	Intel Corporation 536EP Data Fax Modem
FireWire (IEEE 1394)	VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
IDE interface	VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
USB Controller	VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
USB Controller	VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
USB Controller	VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
USB Controller	VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
USB Controller	VIA Technologies, Inc. USB 2.0
ISA bridge	VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
Multimedia audio controller	VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller
Ethernet controller	VIA Technologies, Inc. VT6102 [Rhine-II]
Host bridge	Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
Host bridge	Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
Host bridge	Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
Host bridge	Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
VGA compatible controller	nVidia Corporation GeForce 7600 GT 

Some captures:
[[IMG]http://lh3.ggpht.com/_xVMq7Z4mPqY/SYSMu-o7B4I/AAAAAAAAACA/qyVxpj3puxg/s144/Pantallazo-Volume%20Control.png[/IMG]]("http://picasaweb.google.es/lh/photo/EqQxiGZXZ6RPgbrzg9pw2A?feat=embedwebsite")

[[IMG]http://lh5.ggpht.com/_xVMq7Z4mPqY/SYSMu9ZxkII/AAAAAAAAACI/19n8lYIHAJQ/s144/Pantallazo-Control%20de%20volumen%3A%20VIA%208237%20%28Alsa%20mixer%29.png[/IMG]]("http://picasaweb.google.es/lh/photo/_cPkBQ1ytPa9OjUu1rbNDg?feat=embedwebsite")

[[IMG]http://lh3.ggpht.com/_xVMq7Z4mPqY/SYSMvDAuElI/AAAAAAAAACY/SUd866qSyvg/s144/Pantallazo-Control%20de%20volumen%3A%20VIA%208237%20%28Alsa%20mixer%29-1.png[/IMG]]("http://picasaweb.google.es/lh/photo/E897Trd8t6Th5FLN1My17w?feat=embedwebsite")

[more captures]("http://picasaweb.google.es/gasaqholl/Linux?feat=directlink")

---

### Post by gasaqholl on 2009-02-12
¿No one knows?:confused:

Please ¡help!

---

### Post by markbuntu on 2009-02-12
Pulseaudio comes by default with only 2 channels enabled. This should get you fixed up. It is written for Hardy but will work with Intrepid since the pulsaudio version is the same.

[http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/](http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/)

---

### Post by gasaqholl on 2009-02-13
Thanks markbuntu but I have already did something very similar.

Anyway I have no Front and Surround volume controls, but I do have Center and LFE volume controls, Surround option (it is on) on "conmutadores" and Surround Jack Mode (it is on share) also.

There must be something lost. I don't have /etc/asound.conf file.

My .asoundrc says this:

# ALSA library configuration file
# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/xxxx/.asoundrc.asoundconf>

the asoundrc.asoundconf says this:

# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
!defaults.pcm.card V8237
defaults.ctl.card V8237
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix.max_periods 0
defaults.pcm.dmix.rate 48000
defaults.pcm.dmix.format "unchanged"
defaults.pcm.dmix.card defaults.pcm.card
defaults.pcm.dmix.device defaults.pcm.device
defaults.pcm.dsnoop.card defaults.pcm.card
defaults.pcm.dsnoop.device defaults.pcm.device
defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device
defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device
defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device
defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device
defaults.pcm.surround40.card defaults.pcm.card
defaults.pcm.surround40.device defaults.pcm.device
defaults.pcm.surround41.card defaults.pcm.card
defaults.pcm.surround41.device defaults.pcm.device
defaults.pcm.surround50.card defaults.pcm.card
defaults.pcm.surround50.device defaults.pcm.device
defaults.pcm.surround51.card defaults.pcm.card
defaults.pcm.surround51.device defaults.pcm.device
defaults.pcm.surround71.card defaults.pcm.card
defaults.pcm.surround71.device defaults.pcm.device
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
defaults.pcm.modem.card defaults.pcm.card
defaults.pcm.modem.device defaults.pcm.device
defaults.pcm.file_format "raw"
defaults.pcm.file_truncate true
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0
defaults.namehint.showall off
defaults.namehint.basic on
defaults.namehint.extended off

I hope this brings any ideas.

Thanks again.

---

