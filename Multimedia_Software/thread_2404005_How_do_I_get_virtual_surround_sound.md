---
title: "How do I get virtual surround sound?"
date: 2018-10-18
forum: Multimedia Software
---

### Post by gottaslay on 2018-10-18
I've tried plenty of methods to get virtual surround sound to work on my headphones without success. I'm using the newest Ubuntu version with the latest kernel.

---

### Post by Claus7 on 2018-10-19
Hello,

providing more info about your ubu box and your hardware/headphone specs will be more helpful. Have you tried to open pulseaudio and see if you can achieve the desired effect? Also more info about what you tried and did not work will be useful as well.

Regards!

---

### Post by gottaslay on 2018-10-19
I'm using a Xonar DGX card which supports 5.1 and a pair of headphones called Sennheiser HD 598SR. I've tried changing my audio device from PAVO to "Analog Surround 5.1 Output" but this way i'm only able to hear music + sound effects in movies and not the actor voices.

---

### Post by #&amp;thj^% on 2018-10-19
Many folks have a surround sound card, but have speakers for just two channels, so PulseAudio cannot really default to a surround sound setup. To enable all of the channels, edit "/etc/pulse/daemon.conf": uncomment the default-sample-channels line (i.e. remove the semicolon from the beginning of the line) and set the value to 6. For a 5.1 setup, or 8 for a 7.1 setup etc.
```

# Default
default-sample-channels=2
# For 5.1
default-sample-channels=6
# For 7.1
default-sample-channels=8
```

If your channels are not correclty mapped or the volume controls for the individual channels do not work as expected in pavucontrol, and you have a HDMI and an analog soundcard, then try to add the following line to /etc/pulse/default.pa
```

load-module module-combine channels=6 channel_map=front-left,front-right,rear-left,rear-right,front-center,lfe
```

Note that this example is for a 5.1 setup.

After doing the edit, restart PulseAudio. 
```
pusleaudio -k
```

---

### Post by gottaslay on 2018-10-19
I'm not using a HDMI. My headphones are connected via 3.5mm jack. I just enabled 6 channels and restarted PulseAudio. I downloaded a Dolby trailer and played it on VLC and only could hear the music but no actor voices. As previously.

---

### Post by Claus7 on 2018-10-19
Hello,

Could you please try a 4.1 setup and let us know?

Regards!

---

### Post by gottaslay on 2018-10-20
4.0 works, i can hear voices and music. However when performing a speaker test in Ubuntu's sound settings, only Front left and Front Right produce noise.

---

### Post by Claus7 on 2018-10-20
Hello,

there might be another solution to this issue, yet while looking at the forums I remember that this is a combination of hardware and media sound characteristics. In other words I do not know if you can do anything more, yet someone else might shed more light.

Regards!

---

### Post by gottaslay on 2018-10-21
I appreciate all the received help. Hopefully we can resolve this eventually.

---

