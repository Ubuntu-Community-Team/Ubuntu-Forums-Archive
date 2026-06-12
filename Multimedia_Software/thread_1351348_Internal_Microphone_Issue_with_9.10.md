---
title: "Internal Microphone Issue with 9.10"
date: 2009-12-10
forum: Multimedia Software
---

### Post by Meetze on 2009-12-10
My internal microphone doesn't work with the 9.10 install.

I tried a number of things and found something that works.  I thought I'd pass this on.  I'm currently running a RealTek soundcard on an Averatec 7100.

Applications-->Accessories-->Terminal
type: sudo gedit /etc/modprobe.d/alsa-base.conf

Scan to the end of the file and find the line that starts with:
options snd-hda-intel

I added: model=6stack-dig to the end of this line and saved the file.  However, unless you're using a Realtek ALC882, you'll most likely want to use a different model code.  Some of them can be obtained from: [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

I rebooted my machine and open up the terminal again.
Applications-->Accessories-->Terminal
type: sudo apt-get install gnome-alsamixer

If it's already installed - great!

type: gnome-alsamixer

I un-muted everything and closed the program.

Next I went to the Sound Preferences.

System-->Preferences-->Sound

I selected the input tab and made sure a sound device was selected at the bottom.  In the connectors area, now there are multiple microphones to choose from.  Turned up the gain a bit and the internal microphone is working fine. Skype works as well.

Just an added note about gnome-alsamixer, I had to run the following command from a terminal in order to make sure the changes I made were still there after I rebooted.

Terminal-->alsactl store

---

