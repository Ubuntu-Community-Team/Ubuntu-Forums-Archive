---
title: "No Sound 12.04"
date: 2012-09-18
forum: Multimedia Software
---

### Post by shadedpixel on 2012-09-18
Hi, Ive tried IRC, google, searching the fourms, etc. And nothing seams to be working for me. Im getting pretty frustrated so this is my last resort before I pass out on my keyboard :|. 

Anyway, I dont have any sound on my new **[_Ubuntu Minimal_]("https://help.ubuntu.com/community/Installation/MinimalCD")** installation, I do have alsa and pulseaudio installed (and I belive correctly, I have unmuted channels and it sees and recognizes my sound card) but I dont have any sound. Any help is _**GREATLY**_ apreciated, here is some info I think may help.

```
noah@aperture:~$ lspci | grep "audio"
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)]
``````
noah@aperture:~$ aplay -l
aplay: device_list:252: no soundcards found...

``````
noah@aperture:~$ sudo aplay -l
[sudo] password for noah: 
**** List of PLAYBACK Hardware Devices ****
Home directory /home/noah not ours.
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``````
noah@aperture:~$ groups noah
noah : noah adm cdrom sudo audio dip plugdev lpadmin sambashare

```Thanks in advance! 

It has worked on normal ubuntu, and Arch!

Help Ubuntu fourms! Your my only hope! :)

Bump if you want to help me but dont know how

---

### Post by BicyclerBoy on 2012-09-19
You should not need to use sudo with aplay -l...this is one problem.

Shouldn't noah be a member of users (&video) ?

Have you compiled alsa from source ?

You could try changing permissions of /proc/asound/card0/* ...but this does not survive reboot/restart.

---

### Post by meditatingfrog on 2012-09-19
> **shadedpixel said:**
> Hi, Ive tried IRC, google, searching the fourms, etc. And nothing seams to be working for me. Im getting pretty frustrated so this is my last resort before I pass out on my keyboard :|. 

Anyway, I dont have any sound on my new **[_Ubuntu Minimal_]("https://help.ubuntu.com/community/Installation/MinimalCD")** installation, I do have alsa and pulseaudio installed (and I belive correctly, I have unmuted channels and it sees and recognizes my sound card) but I dont have any sound. Any help is _**GREATLY**_ apreciated, here is some info I think may help.

```
noah@aperture:~$ lspci | grep "audio"
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)]
``````
noah@aperture:~$ aplay -l
aplay: device_list:252: no soundcards found...

``````
noah@aperture:~$ sudo aplay -l
[sudo] password for noah: 
**** List of PLAYBACK Hardware Devices ****
Home directory /home/noah not ours.
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``````
noah@aperture:~$ groups noah
noah : noah adm cdrom sudo audio dip plugdev lpadmin sambashare

```Thanks in advance! 

It has worked on normal ubuntu, and Arch!

Help Ubuntu fourms! Your my only hope! :)

Bump if you want to help me but dont know how

Are you sure the kernel module is loaded for your soundchip?

This command should list a module under your soundchip.
```
sudo lshw
```

Also investigate driver modules with
```
lsmod
```

---

