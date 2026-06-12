---
title: "Microphone not working after update"
date: 2014-07-07
forum: Multimedia Software
---

### Post by null3 on 2014-07-07
Hi all!

I am really desperate, because I have the impression that I tried out everything. Yesterday my Ubuntu 14.04 got some system udpates and since then my microphone is not working anymore. I reinstalled pulseaudio and alsa. Sound is working but the microphone remains dead. 

** These are my sound settings:**
[[IMG]http://s1.directupload.net/images/140707/w3n3n8vf.png[/IMG]]("http://www.directupload.net")

**These are my alsa settings:**
[[IMG]http://s14.directupload.net/images/140707/q64tztc8.png[/IMG]]("http://www.directupload.net")

**Pulse VolumeAudio Meter (Capture) shows two moving bars. They are moving up and down, but its rather a trembling.**
[[IMG]http://s7.directupload.net/images/140707/7xbmwifn.png[/IMG]]("http://www.directupload.net")

**Here are some further details about my system:**

cat /proc/asound/card0/codec* | grep Codec
[I]Codec: Realtek ALC271X
Codec: Intel PantherPoint HDMI[/I]

cat /proc/asound/cards
 [I]0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xc2610000 irq 46[/I]


aplay -l
[I]**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC271X Analog [ALC271X Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/I]


I added the last line to /etc/modprobe.d/alsa-base.conf

...
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
**options snd-hda-intel model=auto enable=yes**

My gstreamer-properties:
[[IMG]http://s7.directupload.net/images/140707/fp9v9evh.png[/IMG]]("http://www.directupload.net")



Besides Linux i have a windows 8 partition. The microphone also does not work on Windows. Can anyone help me, please? How can I (re)enable my microphone?
Thanks a lot!

---

### Post by null3 on 2014-07-09
Push!

Does nobody know an answer?

---

### Post by chris259 on 2014-07-09
I had a similar sound problem. None of the sound adapters except "dummy adapater" showed up in sound settings. There was no sound at all after the ubuntu base update which included a new kernel. 

My solution. Use grub (hold shift key at beginnging of boot) and boot into the previous kernel which for me was the -29 kernel. All was well. The new kernel had a problem. This is a bug in the new -30 kernel. You can find out if you are running the new kernel by opening a terminal and typing "uname -a". If the kenrel number ends in -30 then try booting into the previous -29 kernel using the grub menu on system start. It worked for me. See my post "No sound and only dummy sound adapter after update"

**Update** (can you hear sound?)
Well, I just read the last line in your post after posting the above. If your microphone also does not work in Windows 8 then I would think it is a hardware problem. Either the microphone does not work anymore, or there is something in the hardware that is muting the Microphone input. It's worth a try booting into the previous kernel, but if the microphone also does not work in windows 8 on your dual boot system, then I would suspect a problem with the microphone or sound card in the system. Possible a hardware mute on the microphone input. .. my best suggestions..

---

