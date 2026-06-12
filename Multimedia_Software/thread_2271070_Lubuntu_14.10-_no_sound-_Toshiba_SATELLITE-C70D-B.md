---
title: "Lubuntu 14.10- no sound- Toshiba SATELLITE-C70D-B"
date: 2015-03-27
forum: Multimedia Software
---

### Post by Freiklite on 2015-03-27
Hi,
I use Lubuntu 14.10 on Toshiba SATELLITE-C70D-B and there is no sound at all.

Pieces of information:
ALSA error: snd_pcm_open failed: Aucun fichier ou dossier de ce type.

dominique@dominique-SATELLITE-C70D-B:~$ speaker-test
speaker-test 1.0.28

Le périphérique de lecture est default
Les paramètres du flux sont 48000Hz, S16_LE, 1 canaux
Utilisation de 16 octaves de 'pink noise'
ALSA lib pcm_dmix.c:1022:(snd_pcm_dmix_open) unable to open slave
Erreur d'ouverture à la lecture: -2,Aucun fichier ou dossier de ce type

dominique@dominique-SATELLITE-C70D-B:~$ aplay -l
**** Liste des Périphériques Matériels PLAYBACK ****
carte 0: Generic [HD-Audio Generic], périphérique 3: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 1: Generic_1 [HD-Audio Generic], périphérique 0: ALC269VC Analog [ALC269VC Analog]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0

dominique@dominique-SATELLITE-C70D-B:~$ lspci -nn | grep '\[04[80][13]\]'
00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio [1002:9840]
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller [1022:780d] (rev 02)


&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.28 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474;    Carte: HD-Audio Generic                         F1:  Aide                 &#9474;
&#9474;     Puce: Realtek ALC269VC                         F2:  Informations Système &#9474;
&#9474;      Vue: F3:[Lecture] F4: Capture  F5: Tout       F6:  Choisir la carte son &#9474;
&#9474; Contrôle: Master [gain dB: 0,00]                   Esc: Quitter              &#9474;

dominique@dominique-SATELLITE-C70D-B:~$ lspci -v | grep -A7 -i "audio"
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
    Subsystem: Toshiba America Info Systems Device f938
    Flags: bus master, fast devsel, latency 0, IRQ 82
    Memory at f2c60000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 156b
--
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, slow devsel, latency 32, IRQ 83
    Memory at f2c64000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)

Thank you very much for your attention,
Bye.

---

### Post by ajgreeny on 2015-03-27
I don't think **pulseaudio** is installed by default in lubuntu, nor is **pavucontrol** which allows you to configure pulse, so my first recommendation is to install those two packages.  You can then get to pulseaudio **Sound Settings** from the volume icon in the panel, and that may show you that something is set at too low a volume or is totally muted.

---

### Post by Freiklite on 2015-03-28
Hi,
Thank you very much for your answer.
I installed Pulseaudio and Pavucontrol packages >>> no sound.
I installed Flashplugin-installer package >>> sound.
Thanks and regards,
Ciao

P.S.: How can I write "Solved" in the post title?

---

### Post by Vladlenin5000 on 2015-03-28
So, at the end of the day, your only problem was with flash videos/apps...

You can use the thread tools to mark your thread as solved.

---

### Post by Freiklite on 2015-03-29
Thank you very much.
Bye.

---

