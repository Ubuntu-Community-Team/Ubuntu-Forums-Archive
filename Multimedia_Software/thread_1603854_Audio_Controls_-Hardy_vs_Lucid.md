---
title: "Audio Controls -Hardy vs Lucid"
date: 2010-10-23
forum: Multimedia Software
---

### Post by MaindotC on 2010-10-23
Is there a way to get the same audio controls on Lucid that were available on Hardy?  For example, on Hardy I can right-click the audio icon and it gives me full control over each audio input and output device.  I can change devices and each device is defined or managed by a different service (or whatever the correct term is).  Here's what it looks like and the options I have:

[IMG]http://img710.imageshack.us/img710/2024/screenshotvolumecontrol.png[/IMG]

[IMG]http://img16.imageshack.us/img16/2024/screenshotvolumecontrol.png[/IMG]

[IMG]http://img704.imageshack.us/img704/2024/screenshotvolumecontrol.png[/IMG]

[IMG]http://img840.imageshack.us/img840/2024/screenshotvolumecontrol.png[/IMG]

[IMG]http://img194.imageshack.us/img194/2024/screenshotvolumecontrol.png[/IMG]

[IMG]http://img219.imageshack.us/img219/4677/screenshotvolumecontrolz.png[/IMG]

Is this just available because of the type of soundcard I have in this machine?  On my Lucid machine (different sound card) I'm trying to redirect output from an audio web stream into my uStream channel.  I can do it on the Hardy machine because of the control I have listed above, but on the Lucid machine I don't see this type of control offered.

---

### Post by kostkon on 2010-10-23
You'll need these two tools: gnome-alsamixer and PulseAudio Volume Control.

---

### Post by MaindotC on 2010-10-23
Good suggestions - those tools do help.  I'm still not 100% there but I'm making progress.

---

### Post by sofasurfer on 2010-10-23
I have those 2 packages installed but I can not find my volume control. Where is it?

---

### Post by MaindotC on 2010-10-24
If it's not in the top right (like usual) then the PulseAudio Sound Control will be under Applications -> Sound & Video.

---

### Post by Yellow Pasque on 2010-10-24
If you want the old gstreamer-based volume applet, then use gnome-media and gnome-applets packages from: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

---

### Post by sofasurfer on 2010-10-25
I already have gnome-media and gnome-applets. And there is no volume control in Applications -> Sound & Video. 

I just reinstalled and I see that I have a volume control in the task bar, I also have a mail icon. I deleted the mail icon and the volume control went with it. Hmmm.

---

