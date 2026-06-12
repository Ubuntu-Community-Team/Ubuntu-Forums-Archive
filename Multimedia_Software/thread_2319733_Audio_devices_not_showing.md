---
title: "Audio devices not showing"
date: 2016-04-06
forum: Multimedia Software
---

### Post by sergio38 on 2016-04-06
Hello! I'm running Ubuntu Desktop 15.10

I've been in trouble since I installed pavucontrol (I think). I don't remember tweaking anything, but I don't know. It just stopped working. My last question was discussed here, about problems configuring the output: [http://ubuntuforums.org/showthread.php?t=2317782](http://ubuntuforums.org/showthread.php?t=2317782)

One day I realized that when I went to the Config menu -> Sound, there were no output devices. It is only showing "Clumsy output" (Free translation from Spanish "Salida para torpes").

I searched across the web for a solution, and after a while the only thing that worked was to uninstall pulseaudio and alsamixer, and then installing again. Then, the three output devices I had were appearing.

This worked for yesterday.

Now, today, it is not working again, and reinstalling pulseaudio and alsamixer doesn't work. I've tried some askubuntu recommendations but none of them worked.

I noticed that alsamixer is recognizing OK the devices. Here I send you info.

&#9474; &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; /proc/asound/version &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488; &#8594;
&#9474; &#9474;Advanced Linux Sound Architecture Driver Version k4.2.0-34-generic.&#9474; &#8594;
&#9474; &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; &#8594;

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; /proc/asound/cards &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; 0 [PCH            ]: HDA-Intel - HDA Intel PCH                        &#9474;
&#9474;                      HDA Intel PCH at 0xdf520000 irq 327              &#9474;
&#9474; 1 [U0x46d0x825    ]: USB-Audio - USB Device 0x46d:0x825               &#9474;
&#9474;                      USB Device 0x46d:0x825 at usb-0000:00:14.0-12, hi&#9474;
&#9492;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;        &#9496;


&#9474;                &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; /proc/asound/devices &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;                 &#9474;
&#9474;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9474;  1:        : sequencer             &#9474;&#9488;     &#9484;&#9472;&#9472;&#9488;       &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9474;  2: [ 0]   : control               &#9474;&#9474;     &#9474;&#9618;&#9618;&#9474;       &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9474;  3: [ 0- 0]: digital audio playback&#9474;&#9474;     &#9474;&#9618;&#9618;&#9474;       &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9474;  4: [ 0- 0]: digital audio capture &#9474;&#9474;     &#9474;&#9618;&#9618;&#9474;       &#8594;
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9474;  5: [ 0- 1]: digital audio playback&#9474;&#9474;     &#9474;&#9618;&#9618;&#9474;       &#8594;
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9474;  6: [ 0- 2]: digital audio capture &#9474;&#9474;     &#9474;&#9618;&#9618;&#9474;       &#8594;
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9474;  7: [ 0- 3]: digital audio playback&#9474;&#9474;     &#9474;&#9618;&#9618;&#9474;       &#8594;
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9474;  8: [ 0- 7]: digital audio playback&#9474;&#9474;     &#9474;&#9618;&#9618;&#9474;       &#8594;
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9474;  9: [ 0- 8]: digital audio playback&#9474;&#9474;     &#9474;&#9618;&#9618;&#9474;       &#8594;
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9474; 10: [ 0- 0]: hardware dependent    &#9474;&#9474;     &#9474;&#9618;&#9618;&#9474;       &#8594;
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9474; 11: [ 0- 2]: hardware dependent    &#9474;&#9474;     &#9474;&#9618;&#9618;&#9474;       &#8594;
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9474; 12: [ 1]   : control               &#9474;&#9474;     &#9474;&#9618;&#9618;&#9474;       &#8594;
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9474; 13: [ 1- 0]: digital audio capture &#9474;&#9474;     &#9474;&#9618;&#9618;&#9474;       &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9474; 33:        : timer                 &#9474;&#9474;     &#9474;&#9618;&#9618;&#9474;       &#9474;
&#9474;      &#9500;&#9472;&#9472;&#9508;     &#9500;&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;&#9496;     &#9500;&#9472;&#9472;&#9508;       &#9474;

&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;  &#9484; /proc/asound/oss/devices &#9488;  &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;       &#8594;
&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;  &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;       &#8594;

&#9474;      &#9474;&#9618;&#9618;&#9474; &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; /proc/asound/timers &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488; &#9474;&#9618;&#9618;&#9474;       &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474; &#9474;G0: system timer : 4000.000us (10000000 ticks)&#9474; &#9474;&#9618;&#9618;&#9474;       &#9474;
&#9474;      &#9474;&#9618;&#9618;&#9474; &#9474;P0-0-0: PCM playback 0-0-0 : SLAVE            &#9474; &#9474;&#9618;&#9618;&#9474;       &#8594;
&#9474;      &#9474;&#9618;&#9618;&#9474; &#9474;P0-0-1: PCM capture 0-0-1 : SLAVE             &#9474; &#9474;&#9618;&#9618;&#9474;       &#8594;
&#9474;      &#9474;&#9618;&#9618;&#9474; &#9474;P0-1-0: PCM playback 0-1-0 : SLAVE            &#9474; &#9474;&#9618;&#9618;&#9474;       &#8594;
&#9474;      &#9474;&#9618;&#9618;&#9474; &#9474;P0-2-1: PCM capture 0-2-1 : SLAVE             &#9474; &#9474;&#9618;&#9618;&#9474;       &#8594;
&#9474;      &#9474;&#9618;&#9618;&#9474; &#9474;P0-3-0: PCM playback 0-3-0 : SLAVE            &#9474; &#9474;&#9618;&#9618;&#9474;       &#8594;
&#9474;      &#9474;&#9618;&#9618;&#9474; &#9474;P0-7-0: PCM playback 0-7-0 : SLAVE            &#9474; &#9474;&#9618;&#9618;&#9474;       &#8594;
&#9474;      &#9474;&#9618;&#9618;&#9474; &#9474;P0-8-0: PCM playback 0-8-0 : SLAVE            &#9474; &#9474;&#9618;&#9618;&#9474;       &#8594;
&#9474;      &#9474;&#9618;&#9618;&#9474; &#9474;P1-0-1: PCM capture 1-0-1 : SLAVE             &#9474; &#9474;&#9618;&#9618;&#9474;       &#8594;
&#9474;      &#9474;&#9618;&#9618;&#9474; &#9474;  Client application 1325 : running           &#9474; &#9474;&#9618;&#9618;&#9474;       &#8594;
&#9474;      &#9474;&#9618;&#9618;&#9474; &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; &#9474;&#9618;&#9618;&#9474;       &#9474;

&#9474;   &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; /proc/asound/pcm &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;   &#8594;
&#9474;   &#9474;00-00: ALC1150 Analog : ALC1150 Analog : playback 1 : capture 1&#9474;   &#8594;
&#9474;   &#9474;00-01: ALC1150 Digital : ALC1150 Digital : playback 1          &#9474;   &#8594;
&#9474;   &#9474;00-02: ALC1150 Alt Analog : ALC1150 Alt Analog : capture 1     &#9474;   &#8594;
&#9474;   &#9474;00-03: HDMI 0 : HDMI 0 : playback 1                            &#9474;   &#8594;
&#9474;   &#9474;00-07: HDMI 1 : HDMI 1 : playback 1                            &#9474;   &#8594;
&#9474;   &#9474;00-08: HDMI 2 : HDMI 2 : playback 1                            &#9474;   &#8594;
&#9474;   &#9474;01-00: USB Audio : USB Audio : capture 1                       &#9474;   &#8594;
&#9474;   &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;   &#8594;

Now also, the sound icon from the top right corner has disappeared magically. And also the configuration menu looks strange. Here I send the pictures.

I'd appreciate help. Thank you a lot!

---

### Post by sergio38 on 2016-04-07
Anyone?

---

### Post by Bucky Ball on 2016-04-07
*Thread moved to **Multimedia Software**.*

Maybe that will help things along ...

---

### Post by sergio38 on 2016-04-08
Anyone?

---

### Post by Yellow Pasque on 2016-04-08
> It is only showing "Clumsy output" 

Dummy (fake) output. It means pulseaudio cannot find your sound device. Usually, this means that the kernel module/driver for your sound device is not loading properly. From the information you gave in the first post, it appears your system is okay with the sound module.
So, this is the first thing I would try:
```
rm -r ~/.config/pulse*
```
Then, log out and log in.

If your sound issue persists, give more information:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
[https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

---

### Post by sergio38 on 2016-04-11
Thank you a lot, Temüjin.

I performed what you told me, and it stil is not working.


This is the log of Alsa [http://www.alsa-project.org/db/?f=bfbadfe7fbf124efcee72f4e78f70c83e534125d](http://www.alsa-project.org/db/?f=bfbadfe7fbf124efcee72f4e78f70c83e534125d)

And this is the log of PulseAudio while trying to listen to any song. [https://drive.google.com/open?id=0BxyiF-x9VOX1cWo5VXBYUXBLSzA](https://drive.google.com/open?id=0BxyiF-x9VOX1cWo5VXBYUXBLSzA)

It was strange that at some point while I was preparing the logs, the three outputs (2 HDMI and 1 optical) showed in the Sound Devices. But when I tried to listen to the music it just blew up.


Thank you for the guide!

---

### Post by Yellow Pasque on 2016-04-11
It looks like the kernel module is crashing.
Try this to update audio kernel module:

```
sudo apt-get install dkms
sudo update-pciids; sudo update-usbids
cd ~/
wget https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201604110502~ubuntu15.10.1_all.deb
sudo dpkg -i oem-audio-hda-daily-dkms_0.201604110502~ubuntu15.10.1_all.deb
```

Based on: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

If it does not work after reboot, get a new copy of ALSA info (do not worry about the pulseaudio log yet).

---

