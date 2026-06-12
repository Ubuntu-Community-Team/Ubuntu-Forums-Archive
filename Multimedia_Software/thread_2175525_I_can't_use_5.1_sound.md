---
title: "I can't use 5.1 sound"
date: 2013-09-19
forum: Multimedia Software
---

### Post by Barney_Stilson on 2013-09-19
Hi everyone.

I have a problem with my new sweex 7.1 external usb sound card (chip CM6206). I can hear music in Stereo but I can't use 4.0, 4.1, 5.0, 5.1, 7.1 configurations

The driver has been loaded well and In the KDE configuration I can select The apropiate 5.1 device. ALSA seems to be well because I can run the speaker-test command and hear all the speakers in the correct order and the alsamixer shows all the channels (front, center and rear without mute), but no alsa client (vlc, qmmb, firefox, etc) works with surround configurations like 5.1 (if I force the 5.1 device it works only in stereo). In the Channels menu in VLC don't appear de 5.1 option (only stereo, left and rigth)

Another funny thing is that if I configure upmix in my ~/.asoundrc It works and I can hear the stereo signal in the rear speakers!!


** :~$ cat /proc/asound/cards**
 0 [Device         ]: USB-Audio - USB Sound Device
                      USB Sound Device at usb-0000:00:0b.0-2, full speed
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 5

**:~$ speaker-test -Dplug:surround51 -c 6**
speaker-test 1.0.25
Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 96 to 87381
Period size range from 48 to 43690
Using max buffer size 87380
Periods = 4
was set period_size = 21845
was set buffer_size = 87380
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 14,581877

**i:~$ cat ~/.asoundrc**
pcm.upmix51 {
    type upmix
    slave.pcm "surround51"
    delay 15
    channels 6
}
pcm.!default "plug:upmix51"


Anyone can help me??

P.S: sorry for my bad English ;)

---

