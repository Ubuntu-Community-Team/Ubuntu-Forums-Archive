---
title: "No libasound_module_pcm_a52.so in Ubuntu 9.10 x86_64?"
date: 2010-01-09
forum: Multimedia Software
---

### Post by craftyguy on 2010-01-09
I'm a long-time user of Gentoo, and have decided to migrate my desktop to Ubuntu. I brought over my asoundrc.conf file that was configured to encode non-a52 streams into a52 (while upmixing sterio along the way to 5.1) and forwarding to spdif. Placing my asoundrc.conf file into /etc and restarting alsa results in all audio being output to spdif as sterio (not encoded a52 as it should). 

I've installed everything I can find in synaptic that has to do with alsa and its various plugins, however when i execute speaker-test, I receive a message about "libasound_module_pcm_a52.so is not found". Sure enough, the required a52 plugin for alsa is no where to be found on my system. As a last resort, I've tried building alsa-drivers/libs/utils from source (version 1.0.21), yet no luck in getting the a52 encoding plugin to show.

Is there something I am missing here?

Here is a simplified version of my asoundrc.conf that I just recently tested with no luck (obviously since there's no a52 alsa encoder):
```

# Actually existent hardware
pcm.HW_analog {
    type hw
    card 0
    device 0
}
pcm.HW_digital {
    type hw
    card 0
    device 1
}

# Encode AC3 -&gt; Directly on hardware
pcm.Filter_A52Encode {
    type a52
    bitrate 448
    card 0
}
pcm.Filter_SimpleUpmix {
    type upmix
    slave.pcm "Filter_A52Encode"
    channels 6
}

# Make last filter the default device
pcm.!default {
    type plug
    slave.pcm "Filter_SimpleUpmix"

```

---

### Post by svartson on 2010-11-17
to get the libasound_module_pcm_a52.so you have to do the following:

cd /tmp
apt-get source libasound2-plugins
sudo apt-get build-dep libasound2-plugins
sudo apt-get install libavcodec-dev
cd alsa-plugins-1.0.XX
sudo ./configure
sudo make
cd a52/.libs
sudo cp libasound_module_pcm_a52.la libasound_module_pcm_a52.so /usr/lib/alsa-lib/

---

