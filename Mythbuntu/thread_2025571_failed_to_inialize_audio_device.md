---
title: "failed to inialize audio device"
date: 2012-07-14
forum: Mythbuntu
---

### Post by SuperFreak on 2012-07-14
I am setting up my HP Pavillion DV7 laptop as a HTPC device and I am getting no sound. I get this message when viewing a video from Youtube "failed to inialize audio device" (I am using XBMC).I have installed the latest version of Mythbuntu (12.04 64 bit)as a dual boot with Win 7. Win 7 has sound. 
I notice that under Applications>Settings there is no option for Sound. I tried installing Alsa mixer and PulseAudio but no difference.

specs: HP Pavilion dv7-6113cl Notebook AMD A-Series A6-3400M(1.4GHz) 17.3" 6GB Memory DDR3 750GB HDD 5400rpm DVD Super Multi AMD Radeon HD 6520G

---

### Post by Lester_Burnham on 2012-07-14
> **SuperFreak said:**
>  I notice that under Applications>Settings there is no option for Sound. I tried installing Alsa mixer and PulseAudio but no difference.

Hi, 

From memory I don't think there ever has been.
Easiest way, is probably go into mythfrontend utilities > setup > audio do a rescan and work through the options, depending on how you're connecting to you TV. (make sure spdif is unmuted in alsamixer if using spdif/HDMI)
When trying the different devices, you will see lower down, the detected capabilities of that device or guessed capabilities. After you know what works, you can work it out from there.

Otherwise, in a terminal
aplay -l
aplay -L

To see devices. 

Lester

Ps: I'm no expert on the technical side of this, just keep trying until it works.

---

### Post by SuperFreak on 2012-07-14
That helped greatly.

---

