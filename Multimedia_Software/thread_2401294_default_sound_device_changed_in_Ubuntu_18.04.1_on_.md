---
title: "default sound device changed in Ubuntu 18.04.1 on Intel i5 NUC"
date: 2018-09-16
forum: Multimedia Software
---

### Post by ltburch2000 on 2018-09-16
In the continuing  fun for surround sound  for  ubuntu a new curveball was thrown my a recent update in 18.0.4.1

Although I had the 

default-sample-channels = 8 

in the /etc/pulse/daemon.conf

The sound control applet was not working right at all and working for just stereo (nor was pulseaudio playing surround correctly, though ALSA/spdif was working)

Turns out at some point the pulseaudio default device selection changed.  You can see the pulse audio devices and their default with (default will be marked with a *, and was wrong  for me)

 pacmd list-sources | grep -e 'index:' -e device.string -e 'name:'

    index: 0
	name: <alsa_output.pci-0000_00_1f.3.hdmi-stereo.monitor>
		device.string = "0"
  * index: 1
	name: <alsa_input.pci-0000_00_1f.3.analog-stereo>
		device.string = "front:0"

So I went into /etc/pulse/default.pa

and set the 

set-default-sink alsa_output.pci-0000_00_1f.3.hdmi-stereo.monitor

and restarted pulseaudio (pulseaudio -k)

Now the sound control panel is back to  working and surround sound is playing through pulseaudio as well.

Kind of tedious but as far as surround sound issues with ubuntu this was not that hard to figure out and fix.

---

