---
title: "No more sound after using VLC"
date: 2008-01-01
forum: Multimedia &amp; Video
---

### Post by hypnosis on 2008-01-01
Hello,

I'm running Ubuntu Feisty and the sound was working well before.

I'm not sure but I think the sound has disappeared since I ran VLC and do:
open
video4linux
video: /dev/video
audio: /dev/dsp
OK

Since that I don't have any sound any more. When I try to play a music, there's no warning, it seems to be working fine but there's no sound.

Someone have an idea ?

Thanks

---

### Post by keeper of the wheel on 2008-01-01
The exact same thing happened to me and I ran nothing between uses, but I found that rebooting the computer helped restore the missing sound.
Since upgrading to 7.10, I have not had that problem.

---

### Post by hypnosis on 2008-01-01
Sometimes the sound stopped working (I didn't know why) and after rebooting it it was ok
But this time I tried to reboot the PC and it didn't fix the problem which I guess is caused by what I did with VLC (I'm not sure).

Any other idea ?

---

### Post by keeper of the wheel on 2008-01-01
Try a complete uninstall using Synaptic, reboot and then reinstall VLC.
You might also want to install one of the sound mixers (alsamixergui or GNOME ALSA mixer).
Make certain that it registers your native sound card, either on board or add on.

---

### Post by hypnosis on 2008-01-04
I tried to uninstall and reinstall VLC but it didn't work.

Then I uninstalled almost every packet with the word sound or alsa or esd or gstreamer,... I wanted to reinstall them after rebooting but ubuntu didn't start any more.

I formated and the sound worked.

Now it stopped working again, without using VLC this time.

I noticed it stopped working after a crash of SMPlayer.

I also have an error when I go into System > Settings > Sound and I test ESD:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Impossible d'établir une connexion au serveur de son.
With OSS, Alsa, Conexant Digital and Conexant Analog, the sound test seems to work but there's no sound.

What can I do ?

Thanks

---

### Post by hypnosis on 2008-01-04
Do I have to format all again and again each time the sound disappears ??? :confused::confused:

---

