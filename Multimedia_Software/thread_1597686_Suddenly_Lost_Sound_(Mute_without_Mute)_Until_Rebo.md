---
title: "Suddenly Lost Sound (Mute without Mute) Until Reboot"
date: 2010-10-15
forum: Multimedia Software
---

### Post by topviet on 2010-10-15
After I listened to the audio program on the Google Chrome, I downloaded the MP3 to listen again offline. When I clicked on the downloaded MP3 file and using Totem to hear on my computer, there is no sound. I checked the sound preference, there is NO MUTE. 

I restarted computer, clicked on the MP3 file with Totem, I can hear. I can hear the sound on youtube. Which process should I restart without reboot computer.

I'm using Ubuntu 10.10. Here is the output after execute command "sudo lshw -c sound"
```
 
*-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:47 memory:f6afc000-f6afffff

```

---

### Post by lidex on 2010-10-17
My guess is that Chrome was hogging alsa and wouldn't let it go. Did you try closing it? If that's not enough:
```
sudo alsa force-reload
```

---

