---
title: "Sound gone after webcam install [Dapper]"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by DirtDawg on 2007-05-03
We recently got a webcam and I tried to get it working the other day. I didn't change any sound settings, but since I've had it plugged in, I cannot get sound anymore. I have looked through these forums, but answers range from "make sure mute is not on", to "recompile your driver". Well my mute is not on and recompiling a driver seems extreme. Any ideas would be appreciated.

Here's my settings in full:

The Intel is the correct card, the usb is the webcam, and I'm not sure what the OSS device is.
Currently, the Intel card is chosen (always has been).
I use external speakers that plug into a 1/8" jack, so I use "headphones" to control volume levels.
[IMG]http://a550.ac-images.myspacecdn.com/images01/52/l_4162bed82ad93f006bf72a1fda000185.png[/IMG]

As you can see, nothing muted volume control.
[IMG]http://a371.ac-images.myspacecdn.com/images01/56/l_93230e8427142a189c60e2ae91f5bec2.png[/IMG]

Here's my ALSA settings.
[IMG]http://a393.ac-images.myspacecdn.com/images01/31/l_f5a7d0e77b344e54f8f6ab783bdd7b48.png[/IMG]

I also installed some multimedia packages as well including lmms, audacity, Kino, and avidemux. Could one of these packages have created a problem?

Soon, I will be upgrading to Feisty. In the meantime, It would be really great if I could get sound to function. Any help would be appreciated. Thank you.

---

### Post by DirtDawg on 2007-05-03
::bump::

---

### Post by DirtDawg on 2007-05-04
Well I found [this]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/31109"). I *think* what the thread is talking about is a bug in the sound drivers that was updated for Edgy, but not Dapper.

Still, sound would sure be nice.

---

### Post by DirtDawg on 2007-05-04
After reading through the bug report above and a new one I found [here]("https://launchpad.net/ubuntu/+bug/66210"), I found out that the webcam was being used as the default sound device. I believe 0 is default, then 1, 2, etc, as demonstrated by:
```
cat /proc/asound/modules
```
which returns
```
0 snd_usb_audio
1 snd_intel8x0
```
The Intel is my actual sound card and the webcam is usb, so I assume that's what snd_usb_audio is.

Anyways, I changed the defaults manually by opening 
```
/etc/modprobe.d/alsa-base
```
and adding these lines to the end:
```
options snd_intel8x0=0
options snd_usb_audio=1
```
This did the trick to reset the Intel card as the default, but there is still. no. sound.

I am really running out of tricks. If anyone has even an idea what direction I should start looking into, it would be greatly appreciated. This is madness.

---

### Post by DirtDawg on 2007-05-06
[solved]
I undid the changes from the previous post, then installed the webcam driver following [these]("http://ubuntuforums.org/showthread.php?t=303330") instructions. 

After that I installed gnome-alsamixer and unchecked headphone jack sense as suggested in [another post]("http://ubuntuforums.org/showthread.php?p=2601303#post2601303").

Sound works again! Next to test recording.

---

### Post by nvrpaul on 2007-05-06
also upgrading to fiesty will help a lot, fiesty is EASILY the most compatible and the best ubuntu release thus far. go for it man.
glad you got it working man!

---

