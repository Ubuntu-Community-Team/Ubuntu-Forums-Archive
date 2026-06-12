---
title: "Lost built-in audio after accidentally enabling HDMI audio, and can't get it back."
date: 2018-07-26
forum: Multimedia Software
---

### Post by John Nagle on 2018-07-26
16.04LTS, x86-64 updated to current today, but before the audio problem. System updater says "The software on this computer is up to date".

Lost all sound except the startup "thump" sound after trying to fix a problem with audio in a multimedia application. I briefly un-muted the HDMI audio output in Settings->Audio->Output by mistake, and audio hasn't worked at all since. 

The startup sound still plays on every reboot, so the hardware works fine. Nothing else plays. Not even system sounds play. 

Speakers are connected to the motherboard analog port. Display is connected to an HDMI port on an NVidia card, but the display does not have speakers. 

Settings->Audio->Output shows

    HDMI / Displayport 2 OFF, 0% volume.
    Digital output (S/PDIF) - Built in audio ON, 100% volume.
    Test Speakers does not produce sound.

Did most of the suggested stuff - killed and restarted ALSA, reinstalled ALSA, rebooted a few times, got an ALSA dump.

This has to be something simple, but what? Thanks.

ALSA dump, per instructions:

[https://paste.ubuntu.com/p/hxXs6swWrW/](https://paste.ubuntu.com/p/hxXs6swWrW/)

---

### Post by westie457 on 2018-07-26
Something simple, unplug the hdmi cable.

---

### Post by John Nagle on 2018-07-26
> **westie457 said:**
> Something simple, unplug the hdmi cable.

Which, of course, disconnects the display. Then what?

Actually tried that. Started some music playing with Video Player. No sound. Unplugged HDMI cable to display. Still no sound.

Sound settings still look like this:

[IMG]https://image.ibb.co/d4COJo/soundsettings.png[/IMG]

---

### Post by John Nagle on 2018-07-26
As suggested by one of the many contradictory and outdated troubleshooting guides, here's "pavucontrol" and "alsamixer". Muting and unmuting things there seems to have no effect.

[img]https://image.ibb.co/jh1YJo/pavuplaying.png[/img]
[B]
pavucontrol, [/B]while playing something. The bar graph there moves as an audio file is played, but no sound comes out of the speakers. So audio gets at least that far.


[img]https://image.ibb.co/mvfqW8/alsamixer.png[/img]
[B]
alsamixer

[/B]As before, the startup sound works, but nothing else produces sound.So the hardware is fine.

---

### Post by John Nagle on 2018-07-26
Getting closer: speaker-test works.

[B]speaker-test -Dplug:front -c 2 -t wav

[/B]yields a female voice saying "Front left"  "Front right".Other device names that work:[B] "sysdefault", "hw", "plughw", "front".

[/B]So the hardware is fine, and the low-level drivers are fine.What I think is wrong is that audio is being routed to the S/PDIF digital output instead of the analog output.That's what the "Sound" config tool and "pavucontrol" says is the output port. But neither of those offers any other option. The drop-down under "built-in Audio Digital Stereo (IEC958)" only offers "Digital Output (S/PDIF)" as an option. There's no option to select the analog port.

---

### Post by John Nagle on 2018-07-26
Fixed. Opened "pavucontrol", and scrolled the top menu right to reach "configuration". Set it to "Analog stereo line out (unplugged)", which diverted output to the analog line out, where it should be.

---

