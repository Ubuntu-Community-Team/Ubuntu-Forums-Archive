---
title: "No sound if not root"
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by R%&amp;92GH&amp; on 2007-05-06
since a few weeks ago, I cannot hear any sound on my ubuntu feisty (the same happened in edgy) unless I play any music or sound as root. For example, if I use totem as my main music player, every time I start session i must open a console and type: "sudo totem". And then everythink works ok (even as a normal user).

if I just start totem (or any other music player with my username, it does not work and I get the following error:

```
marc@Equip-1:~$ totem
- using device default
- using device default
ALSA lib pcm_dmix.c:831:(snd_pcm_dmix_open) unable to create IPC semaphore
- using device default
- using device default
ALSA lib pcm_dmix.c:831:(snd_pcm_dmix_open) unable to create IPC semaphore
** Message: Error: No s'ha pogut obrir el recurs per a l'escriptura.
gstalsasink.c(625): gst_alsasink_open (): /audio-sink/bin1/alsasink0:
Playback open error on device 'default': Permission denied

```

(the error message says that it's not possible to open the device for writing)

if I try any other software, like rhythmbox, the error is similar:
```
ALSA lib pcm_dmix.c:831:(snd_pcm_dmix_open) unable to create IPC semaphore
- using device default
- using device default

```

my username (marc) is in the audio group. I supose it's a permissions problem, but I don't know  to what files i need to give permissions. Any idea? thnx

PS: if any1 wants to know my soundcard:
```
marc@Equip-1:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by R%&amp;92GH&amp; on 2007-05-06
Ok, forget it. It seems to be solved. I just deleted /etc/asound.conf and now everything works ok.

---

