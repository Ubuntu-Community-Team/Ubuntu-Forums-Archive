---
title: "MP3's just stop working randomly"
date: 2008-08-16
forum: Multimedia Software
---

### Post by frog4044 on 2008-08-16
For some reason ill be listening to my songs and they will stop working. it never stops while I'm listening to it but ill stop it to watch something or do something that requires sound and then when i go back to listening to music in 15 minutes it just wont work. I have no idea what triggers it and the only way to fix it that i know of is logging out and back in or just rebooting. Has anyone else had a similar problem, and if anyone does is there a fix for it? Its really frustrating to reboot my system all the time. 8.04 has been crashing lately a lot. I really like Ubuntu and just installed it about a week ago but so far it has been giving a lot of problems. I just hope 8.10 is stable or I'm going to 7.10. Also does anyone know if doing a 8.10 clean install would help when it comes out.

---

### Post by chezzo on 2008-08-16
well i've been having problems with mp3's recently because of some dodgy updates to xine (see [http://ubuntuforums.org/showthread.php?t=882932](http://ubuntuforums.org/showthread.php?t=882932)), but this sounds different

---

### Post by phylae on 2008-09-08
I have the same problem! Only a restart gets it working. My additional symptoms:
* it isn't just mp3s; flac won't play either.
* Flash audio works
* `sudo /etc/init.d/alsa-utils restart` doesn't help.

---

### Post by phylae on 2008-09-08
I just found this: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/228020](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/228020)

this worked for me > pulseaudio -k

Or you can try this:  > sudo /sbin/alsa force-reload

or this:
> sudo /etc/init.d/alsa-utils stop
sudo rmmod snd_hda_intel (your driver might be different)
sudo modprobe snd_hda_intel (your driver might be different)
sudo /etc/init.d/alsa-utils start


---

