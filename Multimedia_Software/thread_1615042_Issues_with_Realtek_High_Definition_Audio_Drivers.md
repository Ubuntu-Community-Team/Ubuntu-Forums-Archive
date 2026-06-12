---
title: "Issues with Realtek High Definition Audio Drivers"
date: 2010-11-06
forum: Multimedia Software
---

### Post by mlupton on 2010-11-06
Hi, I'm currently running Maverick Meerkat (64 Bit) and I have been having some issues with the Realtek Audio Codec and ALSA. My speakers work, but whenever I try to plug in speakers, headphones, etc., there is no output and the speakers do not shut off. For  clarification, the audio hardware is the Intel 5 Series/3400 Series Chipset High Definition Audio and the audio controller is listed in the terminal as an nVidia High Definition Audio Controller. Is this a problem with the Realtek audio codec, or the hardware itself? My nVidia video card works perfectly fine, so why not the audio controller? If any of you have any solutions (other than updating ALSA because I am currently running version 1.0.23) please post to this thread.

---

### Post by efflandt on 2010-11-06
I assume you are discussing a laptop, because with a desktop, if speakers work in one output jack, then headphones or amplified speakers should work in any output jack (assuming you are not plugging headphones into a microphone jack).

For example my desktop with i5 cpu has Realtek ALC887 which was automatically recognized.  The only thing I had to configure myself was to also enable HDMI audio.  If I have speakers plugged into rear jack and connect headphones to front jack, both work.  If I wanted to use headphones quietly, I would need to turn off or unplug my speakers.

Look in Sound Preferences and see if switching Output from "Analog Output" to "Analog Headphones" switches off your internal speakers, and outputs sound to the headphone jack instead.  Forum search "headphones" to see how how others handle or automate that on laptops.

---

### Post by lidex on 2010-11-06
If you still have problems...Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by mlupton on 2010-11-06
Actually I figured it out from this forum [http://forum.ubuntuusers.de/topic/medion-akoya-p4010-d-md8850-all-in-one-mini-h/#post-2233491 ]("http://forum.ubuntuusers.de/topic/medion-akoya-p4010-d-md8850-all-in-one-mini-h/#post-2233491")
All I had add this line to /etc/modprobe.d/alsa-base.conf
```
options snd-hda-intel model=medion-md2 power_save=10 power_save_controller=N
```
Except for where "medion-md2" I replaced it with "auto". I also added this line (not sure if it was necessary)
```
options snd-hda-intel model=medion-md2 
```
Once again replacing "medion-md2" with "auto". And I apologize for not specifying my computer type. I am running Maverick Meerkat on an Asus N82. For anyone else that is encountering a similar problem, this is the only reasonable solution I could come across. Thanks to everyone for the advice anyway, I will remember to be more specific in my future forum posts.

---

