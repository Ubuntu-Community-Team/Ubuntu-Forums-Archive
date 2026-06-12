---
title: "[SOLVED] Sound too low on tv/fm card"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by wild_oscar on 2008-01-13
I've recently installed a TV/FM tuner (Philips 3139 147).

I connected an audio output plug to my motherboard's CD-IN audio connection (the one used to connect a cd/dvd rom drive).

I can hear sound but unfortunately it's too low. If I turn the volume up on my amplifier to hear the fm/tv sound well, all other sounds will be extremely loud.

I have all volumes maximized on both gnome-volume-manager and alsamixer.
I also can't see a "cd" volume control on either (or aux, for example).

I'm running Ubuntu 7.10 and, for that matter, my motherboard is a Gigabyte GA-P35C-DS3R.

Any help would be appreciated!

---

### Post by wild_oscar on 2008-01-19
I solved this issue here:

[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

The problem was that Linux didn't recognize my soundcard (Azalia Audio with the Realtek ALC885 codec).

I solved the issue by following this procedure:

> cat /proc/asound/card0/codec#* | grep Codec

It will return model of your sound card(s), for example: "Codec: Realtek ALC260", so your sound card is ALC260.

    *

      You should open a file in ALSA documentation. This file is here (replace KERNEL_VERSION with your kernel's version!):

/usr/src/KERNEL_VERSION/Documentation/sound/alsa/ALSA-Configuration.txt

If you didn't have this file, for version 2.6.22, you can check out [WWW] this link or you can find ALSA-Configuration.txt in the subdirectory /alsa-kernel/Documentation/ of the alsa-driver-1.x.x directory you created.

    *

      Search for your model, and take a look at its types, for example I found the following lines for ALC260:

hp              HP machines
hp-3013         HP machines (3013-variant)
fujitsu         Fujitsu S7020
acer            Acer TravelMate
basic           fixed pin assignment (old default model)
auto            auto-config reading BIOS (default)

Read all of them and try to find the one which is more similar to your sound card, for example if you have a laptop, you can choose "acer".

    *

      Open /etc/modprobe.d/alsa-base with the following command:

sudo nano /etc/modprobe.d/alsa-base

Then paste the following line at the end of the file (change MODEL with the type of sound card's model, in our example it should be "acer" (without quotation marks)):

options snd-hda-intel model=MODEL

    *

      Reboot


---

