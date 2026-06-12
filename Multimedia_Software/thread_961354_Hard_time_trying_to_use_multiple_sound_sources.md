---
title: "Hard time trying to use multiple sound sources"
date: 2008-10-28
forum: Multimedia Software
---

### Post by Silent Ninja on 2008-10-28
I've been reading almost every tutorial on the ubuntu planet, but I cannot get my soundcard to play multiple sounds at once (eg. totem playing some mp3 and ekiga ringing, is what I need first)

This is my /etc/asound.conf file:
```
pcm.card0 {
        type hw
        card 0
}

pcm.!default {
        type plug
        slave.pcm "dmixer"
}


pcm.dmixer {
        type dmix
        ipc_key 1025
        slave {
                pcm "hw:0,0"
                period_time 0
                period_size 2048        #1024
                buffer_size 32768       #4096
                #periods 128
                rate 48000      #44100
        }
        bindings {
                0 0
                1 1
        }
}
```

This is what shows up on lspci:
```
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
**00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)**
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
```

And this is some other information:
```
#$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xdfff8000 irq 10

#$ asoundconf list
Names of available sound cards:
NVidia

#$ cat ~/.pulse/default-source
alsa_input.pci_10de_3f0_sound_card_0_alsa_capture_0

#$ cat ~/.pulse/default-sink
alsa_output.pci_10de_3f0_sound_card_0_alsa_playback_0

```

This is the contents of /home/emisho/.pulse/volume-restore.table (i don't know what it does, but it had Ekiga on it and some Alsa containing lines.
```
pulsecore/protocol-native.c$ALSA plug-in [firefox]
2 65536 65536
alsa_output.pci_10de_3f0_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$ALSA plug-in [gnome-sound-properties]


alsa_input.pci_10de_3f0_sound_card_0_alsa_capture_0
pulsecore/protocol-native.c$gnome-sound-properties
2 65536 65536
alsa_output.pci_10de_3f0_sound_card_0_alsa_playback_0
alsa_input.pci_10de_3f0_sound_card_0_alsa_capture_0
pulsecore/protocol-native.c$Rhythmbox
2 65536 65536
alsa_output.pci_10de_3f0_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$Adobe Flash
2 65536 65536
alsa_output.pci_10de_3f0_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$MPlayer
1 65536
alsa_output.pci_10de_3f0_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$Pidgin
2 65536 65536
alsa_output.pci_10de_3f0_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$Reproductor de películas Totem
2 65536 65536
alsa_output.pci_10de_3f0_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$totem-audio-preview
2 65536 65536
alsa_output.pci_10de_3f0_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$brasero
2 65536 65536
alsa_output.pci_10de_3f0_sound_card_0_alsa_playback_0

pulsecore/protocol-native.c$ALSA plug-in [ekiga]
1 65536
alsa_output.pci_10de_3f0_sound_card_0_alsa_playback_0
alsa_input.pci_10de_3f0_sound_card_0_alsa_capture_0
pulsecore/protocol-esound.c$mozillaSound
1 65536
alsa_output.pci_10de_3f0_sound_card_0_alsa_playback_0
```

It's kinda wierd that lspci tells me that I have an Nvidia sound card since alsamixer tells me that I have a **Realtek ALC662 rev1** card. It's the onboard sound card of an Asus Mainboard. I believe that Nvidia is the nforce chipset and Realteak the real chip.. or maybe something about north/southbridge comunication.. dunno.

Is there any way to do this? because when I'm playing music at Totem, I can listen to the alsa audio test on Preferences > Sound, but I cannot listen to the PulseAudio test nor the OSS (only while playing, I can listen to them normally), but since I've configured Ekiga to use Alsa I don't know why it doesn't work if I have Totem or Flash on Firefox playing.

Could there be that alsa-oss is malfunctioning, or that something is forcing them to go out via the pulseaudio / oss ?

---

### Post by Silent Ninja on 2008-10-28
This are the both tests that I came up from the Ekiga site...
[http://wiki.ekiga.org/index.php/Getting_several_applications_using_the_sound_card_at_the_same_time_%3F](http://wiki.ekiga.org/index.php/Getting_several_applications_using_the_sound_card_at_the_same_time_%3F)

While nothing is playing:
```
emisho@emisho:~$ arecord -D plughw:0,0 -c 1 -r 8000 -f S16_LE - | aplay -D plughw:0,0 -c 1 -r 8000 -f S16_LE -
Grabando WAVE '-' : Signed 16 bit Little Endian, Ratio 8000 Hz, Mono
Sonando WAVE 'stdin' : Signed 16 bit Little Endian, Ratio 8000 Hz, Mono
Abortado por la señal Interrupción...
Abortado por la señal Interrupción...

emisho@emisho:~$ arecord -D plughw:0,0 -c 1 -r 16000 -f S16_LE - | aplay -D plughw:0,0 -c 1 -r 16000 -f S16_LE -
Grabando WAVE '-' : Signed 16 bit Little Endian, Ratio 16000 Hz, Mono
Sonando WAVE 'stdin' : Signed 16 bit Little Endian, Ratio 16000 Hz, Mono
Abortado por la señal Interrupción...
Abortado por la señal Interrupción...
```
(It seems to work but since nothing is on the stdin, i cannot listen anything)

While I'm playing something on Totem:
```
emisho@emisho:~$ arecord -D plughw:0,0 -c 1 -r 8000 -f S16_LE - | aplay -D plughw:0,0 -c 1 -r 8000 -f S16_LE -
aplay: main:564: error al abrir audio: Dispositivo ó recurso ocupado
Grabando WAVE '-' : Signed 16 bit Little Endian, Ratio 8000 Hz, Mono

emisho@emisho:~$ arecord -D plughw:0,0 -c 1 -r 16000 -f S16_LE - | aplay -D plughw:0,0 -c 1 -r 16000 -f S16_LE -
aplay: main:564: error al abrir audio: Dispositivo ó recurso ocupado
Grabando WAVE '-' : Signed 16 bit Little Endian, Ratio 16000 Hz, Mono
```

PLEASE tell me that you have an Idea, because it's way too boring to keep the music turned off all time just because Ekiga won't ring if I have it on.

---

### Post by k.eight.a on 2008-10-28
Hello,
I'm a beginner and I don't have the knowledge to show my configuration as **Silent Ninja** but after reading few lines I think I have the same problem.
I have **ASUS A7N8X-E Deluxe** ([X-bit labs review]("http://www.xbitlabs.com/articles/mainboards/display/asus-a7n8xe-deluxe.html") or [[H] Enthusiast review]("http://www.hardocp.com/article.html?art=NTc3")) with *[nForce 2]("http://en.wikipedia.org/wiki/NForce2") Ultra* chipset equipped with [SoundStorm]("http://en.wikipedia.org/wiki/SoundStorm").
I believe it is RealTek ALC650 sound chip.

The problem is that only the first application plays sound. In my case it is **Aqualung** music player. When I want to run a video in **VLC player** it is played without sound.
Sometimes when I run other app earlier than **Aqualung** it refuses to run. It helped to *kill pulseaudio* but didn't solved that I can't run multiple sound on my rig and setup. :(

@ **Silent Ninja**: I'm sorry for not helping and stealing your thread.

---

### Post by Silent Ninja on 2008-10-28
I don't know well why, but it started working now :D

I've edited the file of firefox conf: **/etc/firefox-3.0/firefoxrc** and added... 
FIREFOX_DSP="aoss"

And also edited /etc/modprobe.d/alsa-base and added this:
options snd-hda-intel model=3stack

Then ubuntu also told me that there was a new kernel around so I've installed it and rebooted, and then.. it worked :D

k.eight.a if you match your configurations of the following files, just as I've putted them up here, they'll work on multiple ways. Remember also to install alsa-oss

---

### Post by Silent Ninja on 2008-10-28
I don't know well why, but it started working now :D

I've edited the file of firefox conf: **/etc/firefox-3.0/firefoxrc** and added... 
FIREFOX_DSP="aoss"

And also edited /etc/modprobe.d/alsa-base and added this:
options snd-hda-intel model=3stack

Then ubuntu also told me that there was a new kernel around so I've installed it and rebooted, and then.. it worked :D

k.eight.a if you match your configurations of the following files, just as I've putted them up here, they'll work on multiple ways. Remember also to install alsa-oss

---

### Post by k.eight.a on 2008-11-14
> **Silent Ninja said:**
> ...edited the file of firefox conf: **/etc/firefox-3.0/firefoxrc** and added... 
FIREFOX_DSP="aoss"

And also edited /etc/modprobe.d/alsa-base and added this:
options snd-hda-intel model=3stackI've done both of the above steps. I didn't have the *firefoxrc* file so I created one in the above mentioned location.> **Silent Ninja said:**
> Then ubuntu also told me that there was a new kernel around so I've installed it and rebooted, and then.. it worked :D...not in my case, nothing worth to mention have happened. :( No new kernel was introduced to me.> **Silent Ninja said:**
> k.eight.a if you match your configurations of the following files, just as I've putted them up here, they'll work on multiple ways. Remember also to install alsa-ossI've also installed *alsa-oss*, so far no change that I've encountered.

---

