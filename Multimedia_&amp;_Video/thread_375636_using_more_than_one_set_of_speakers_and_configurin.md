---
title: "using more than one set of speakers and configuring them"
date: 2007-03-04
forum: Multimedia &amp; Video
---

### Post by fakie_flip on 2007-03-04
I do not have surround sound speakers, but I do have a sound card with six sound jacks for surround sound on my motherboard. I have two normal sets of speakers. I got both sets of speakers working with sound coming out of both of them by enabling "duplicate front" in the gnome volume control, but there are a few problems. When I change the volume from the Volume Control in the gnome-panel , it only changes the volume for one set of speakers. How can I get it to change the volume for both sets of speakers? I just want for them to be at the same volume, and when I change the volume from the panel, it does not change the volume of both of them. The volume control in the gnome panel is controlling the master volume only, which is only controlling one set of speakers.

The same thing happens when using mute. It only controls one of set of speakers using one of those sliders that you see in "volume control" (right click sound icon and click open volume control) or alsamixer. There is another slider that controls the other set of speakers labeled as "Surround".  It would be nice if master volume controlled all sets of my speakers. I would like to keep them synchronized  so both sets of speakers have the same volume and both mute and unmute with one control instead of having to go into preferences everytime I want to mute both of them or change the volume. The master volume control in gnome-volume-control (the same slider that is controlled from the gnome panel volume applet), only changes the volume for one of the sets of speakers. gnome-volume-control shows my sound card as a NVidia CK804 (alsa mixer). lspci shows this.

```
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
```

Now, I have a keyboard with volume control buttons on it, but it is doing the same thing. Only one set of speakers volume and mute/unmute is getting changed by it. It is a hassle to go into preferences or alsamixer each time I want to change the volume for both sets of speakers. Most people would not want to have to always control their right speaker and left speaker separately. It's the same for me, I want both sets of speakers to be the same and not just changing one of set of speakers. I want mute to mute both sets of speakers and a volume control to change both sets of speakers, not just one. I figured this might help.

```
chris@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
chris@ubuntu:~$
```

---

