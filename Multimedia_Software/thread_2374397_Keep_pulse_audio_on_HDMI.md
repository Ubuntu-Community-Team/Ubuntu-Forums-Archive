---
title: "Keep pulse audio on HDMI"
date: 2017-10-15
forum: Multimedia Software
---

### Post by jcwjcw42 on 2017-10-15
I have a three-year old laptop that I installed XUbuntu on to use as a dedicated HTPC. The laptop is logged in to the user "TV" at all times. Everything is working fine except for one annoying problem. I can set the audio to use the HDMI interface manually using pauvcontrol. However, it always switches back to the analog stereo output a short time after the receiver it is connected to is shut down. I have to manually switch it again every time I turn the receiver+television on again to use the HTPC. This is the behavior using 17.04 and the 17.10 pre-release (which I tried in desperation).

I also tried adding both of the following lines (individually and together) to both /etc/pulse/default.pa and ~/.config/pulse/default.pa

set-default-sink alsa_output.pci-0000_00_1b.0.hdmi-stereo
set-card-profile 1 output:hdmi-stereo

Is there any way to make pulse audio stay on HDMI even when the receiver is shut down?

---

### Post by ajgreeny on 2017-10-15
*Thread moved to **Multimedia Software**.* which is more appropriate and a better fit.

---

### Post by Autodave on 2017-10-15
Possibly not. When you shut the TV off or turn it on after the laptop is already running, the laptop is not picking up the HDMI. My desktop hooked to the TV does the same thing.

---

### Post by jcwjcw42 on 2017-10-15
A work-around on the [the Arch Linux wiki](https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting#No_HDMI_sound_output_after_some_time_with_the_monitor_turned_off) that seems to work is to comment out 

load-module module-switch-on-port-available

in /etc/pulse/default.pa. I'll mark this as solved.

---

### Post by Autodave on 2017-10-16
Thank you for the update: I will add it to my library of Ubuntu fixes!

---

