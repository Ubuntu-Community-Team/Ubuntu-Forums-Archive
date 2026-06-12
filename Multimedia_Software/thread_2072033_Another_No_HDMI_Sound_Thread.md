---
title: "Another No HDMI Sound Thread"
date: 2012-10-16
forum: Multimedia Software
---

### Post by Samsicle on 2012-10-16
Hey guys,

So I just installed 12.04 onto a new machine I put together and there is no sound through HDMI. Here's a bit of info on my setup:

- Motherboard: Asus F2 A85X-M CSM (HD audio is enabled and output is HDMI in the BIOS)
- CPU/APU: AMD A10-5800k
- proprietary FGLRX drivers are installed (not the post-release ones, they failed to install for some reason)

- the output to aplay -l:[INDENT]**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Generic [HD-Audio Generic], device 3: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0[/INDENT]- and my alsa information script [link]("http://www.alsa-project.org/db/?f=b12b8f809991877a4082c8eaf532e24ebfb330d2")
- Under sound settings: HDMI built in audio is selected
- plugging a pair of headphones into the front audio produces sound and when i run pulseaudio volume control the orange volume bar is bouncing around
- I followed the troubleshooting guide which led me to procedure Ac (didn't work) so I tried Ad, Af, and Ag to no avail.

I'm running out of ideas and patience trying to get this to work. And the only remaining solution I can think of with a decent chance of success is to install Windows instead (and I don't want to have to resort to that). Hopefully this is enough info for someone to give me a hand, otherwise just ask and I will provide.
Thanks in advance, Sam

---

### Post by nntp on 2012-10-16
it works for me:

[http://ubuntuforums.org/showthread.php?t=1967755](http://ubuntuforums.org/showthread.php?t=1967755)

---

### Post by Samsicle on 2012-10-17
> it works for me:Could you be more specific? It looks to me like you're suggesting I install Nvidia drivers. Or do you mean the very end where they edit the file [COLOR=#000000][FONT=Courier New]/etc/pulse/default.pa?[/FONT][/COLOR]

---

### Post by Time Sheep on 2012-10-19
I found the device ID by using 
[B]aplay -l

[/B]and then I switch to it with
[B]amixer cset numid=3 <ID>

[/B]Where you obviously have to put in your ID :)
When switching back, you just need to use the same command with the ID of your speaker device.

I also added **option snd-intel-hda **to the modprobe file, forgot it's name. Also I'm not sure if this did a difference, but if the first thing doesn't work, try this.

---

### Post by Samsicle on 2012-10-19
I tried that amixer command to set the device ID but it returns an error
```
amixer: Control default element write error: Operation not permitted
```Thanks for the help Time Sheep, but I'm not competent enough to know which modprobe file you are referring to.

I also just discovered that if I have both an SPDIF and DVI cable connected I get sound, but SPDIF and HDMI there is still no sound. I have also upgraded to 12.10. Maybe if I get a DVI to HDMI cable my problem will be solved. Just seems weird that having an HDMI cable plugged into my motherboard mutes the sound.

---

