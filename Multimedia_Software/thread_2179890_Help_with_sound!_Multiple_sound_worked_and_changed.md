---
title: "Help with sound! Multiple sound worked and changed after update"
date: 2013-10-10
forum: Multimedia Software
---

### Post by QeMnbhF on 2013-10-10
I recently installed Lubuntu and was really pleased to find that when using XBMC I have multiple sound, both analogue and digital.

Yesterday I did a apt-get upgrade and a number of apps were updated. I shutdown and thought nothing of it. Now my multiple audio is gone :(

It seems that my analogue sound and digital sound are now bound to different sound systems (pulseaudio and alsa). Select Pulseaudio in XBMC plays analogue only (- I don't remember Pulseaudio being an option!), HDA Intel Digital S/PDIF plays digital. But neither will play both. In the Alsamixer only the analogue device can be selected - almost like Alsa can't see the digital card.

My apt history log shows this:

```
Start-Date: 2013-10-09  21:04:50
Commandline: apt-get upgrade
Upgrade: glib-networking-services:i386 (2.36.1-0ubuntu1, 2.36.2-0ubuntu0.1), glib-networking:i386 (2.36.1-0ubuntu1, 2.36.2-0ubuntu0.1), libsasl2-modules:i386 (2.1.25.dfsg1-6, 2.1.25.dfsg1-6ubuntu0.1), glib-networking-common:i386 (2.36.1-0ubuntu1, 2.36.2-0ubuntu0.1), gpgv:i386 (1.4.12-7ubuntu1.1, 1.4.12-7ubuntu1.2), libsasl2-2:i386 (2.1.25.dfsg1-6, 2.1.25.dfsg1-6ubuntu0.1), gnupg:i386 (1.4.12-7ubuntu1.1, 1.4.12-7ubuntu1.2)
End-Date: 2013-10-09  21:04:57


```

Anyone with any ideas what has happened? Thank in advance!

---

### Post by Yellow Pasque on 2013-10-10
> I don't remember Pulseaudio being an option!
> Anyone with any ideas what has happened?

What probably happened is that you unintentionally installed pulseaudio (Lubuntu does not use it by default). If you want to keep pulseaudio, you can configure it to use both outputs: [https://wiki.archlinux.org/index.php/PulseAudio#Simultaneous_output_to_multiple_sinks_on_the_same_sound_card_not_working](https://wiki.archlinux.org/index.php/PulseAudio#Simultaneous_output_to_multiple_sinks_on_the_same_sound_card_not_working)

---

### Post by QeMnbhF on 2013-10-10
Thanks for your reply. That's the strange thing though...I didn't. I've installed and reinstalled Lubuntu a couple of times now. The dual audio worked 'out of the box' so I told myself, don't meddle withe the sound! But now :( I tried the dual-audio from the link you sent but now there music jumps every few seconds where as before it was perfect. 

I was thinking maybe I could examine the asound.conf files in the live usb version and compare with the ones I have now? May be there I might find some clue. Anywhere else I should look?

---

### Post by QeMnbhF on 2013-10-10
I tried uninstalling pulseaudio too by the way. But that seemed to make little difference...alsamixer still showed only the analogue. Do any of those applications that have been updated that are mentioned in my first post have any connection with Alsa or Pulseaudio?

---

### Post by Yellow Pasque on 2013-10-10
> **QeMnbhF said:**
> Do any of those applications that have been updated that are mentioned in my first post have any connection with Alsa or Pulseaudio?
Not that I'm aware of. A little more info may help: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by QeMnbhF on 2013-10-10
[http://www.alsa-project.org/db/?f=68833a0784e101053357e3a9ed83ad7fa40aef28](http://www.alsa-project.org/db/?f=68833a0784e101053357e3a9ed83ad7fa40aef28)


Thanks for your help. Pulseaudio is uninstalled now but still the digital output is not selectable in alsamixer.

---

### Post by QeMnbhF on 2013-10-10
It's working again! I uninstalled Pulseaudio and copied the asound.conf file from the LiveUSB version then rebooted...now I have sound from both digital and audio. Thanks for your help!

---

