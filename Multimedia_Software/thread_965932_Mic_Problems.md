---
title: "Mic Problems"
date: 2008-10-31
forum: Multimedia Software
---

### Post by lostdata on 2008-10-31
I am having some problems with my USB headset. I have a built in soundcard and a USB headset I wish to use for skype and teamspeak. I am running Ubuntu 8.10. I am able to get audio playback on my speakers connected to the bult in sound card, and on my USB headset, however I cannot get the mic on the usb headset to work.

I have went into the Sound Preferences and have tried different things, here is how it is currently setup

```
Sound Events
Sound playback: Autodetect (HDA Intel ALC888)

Music and Movies
Sound playback: Autodetect (HDA Intel ALC888)http://ubuntuforums.org/editpost.php?do=editpost&p=6077830

Audio Conferencing 
Sound playback: Plantronics CS50 USB headset USB audio (OSS)
(get an error with alsa)

Sound capture: Plantroncis CS50 USB headset USB audio (ALSA)
(locks up when OSS is selected)
```

Any help would be greatly appreciated.

Thanks

---

### Post by lostdata on 2008-11-01
I think I may have found the problem but i don't know how to fix it. When I open the Volume Control my USB headset shows muted on the microphone, when I unmute it and hit close and reopen the Volume Control it is back to being muted? any Ideas on how i can unmute it?

---

### Post by Simplicius on 2008-11-08
I'm having the same problem. Anyone wants to help?

---

### Post by redfox666 on 2009-01-10
Hi, I had a similar problem, now I'm no expert, but I saw this in dmesg when the headset device is assigned to vmware

usb 2-1: usbfs: interface 0 claimed by snd-usb-audio while 'vmware-vmx' sets config #1

However I don't see anything else similar for the usbhid module (which I gather is used for the mic).

If I modprobe -r usbhid and then assign the device to vmware I can use the mic in windows guest.

HTH, Steve.

---

