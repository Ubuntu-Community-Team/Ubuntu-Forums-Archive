---
title: "Pulseaudio in  Karmic"
date: 2010-01-06
forum: Multimedia Software
---

### Post by Robbyx on 2010-01-06
I have been following the advice at [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Does any one know how to repair this?

```
rob@rob-desktop:~$ pulseaudio & pavucontrol
[1] 20657
W: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
W: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
W: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
W: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
W: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
W: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
W: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

(pavucontrol:20658): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed
[1]+  Exit 1                  pulseaudio
rob@rob-desktop:~$ 

```

Robin

---

### Post by pstickar on 2010-01-07
I have a similar problem. I get not sound and I can read that error message in /var/log/messages.

I tried the suggestion in
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/410887](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/410887)
to no avail.

It is very sad not to have sound. I will register to increase the count of affected people and find out if I can contribute with context information.

---

### Post by Robbyx on 2010-01-07
I have the sound working on mine. I think I had to work my way through all the sound settings in the pulse audio manager and the volume control within the pulse audio applet until I found the correct working connections.

---

### Post by Robbyx on 2010-01-13
pstickar

Have you managed to get the sound working? I have worked out how I did it.
I had to set it up again today and I have it working.

---

### Post by TygerTy on 2010-01-13
Would you mind passing that on to me? I'm about to go out of my mind with no sound! Thanks

---

### Post by Robbyx on 2010-01-13
> **TygerTy said:**
> Would you mind passing that on to me? I'm about to go out of my mind with no sound! Thanks

My problem was with the mic in skype. The principle should be the same whether it is sound to  a device or from a mic:

Install the pulseaudio manager (PA). It is in the Software Center.
Click on the icon for the PA manager in the panel.
Choose devices and find the mic or output you want to send your sound to. Sink= playback, Source = Recorder such as a mic.
Look at the properties for the device and copy the complete name.
Reopen the PA manager and choose the default options on the opening screen. If you are setting up a source then choose default source--- other--- and paste the complete name of the device into the box.  I have found this works with skype and sets the webcam mic to be used as a mic.

---

### Post by ktb on 2010-01-13
I was having the same problem. Thanks for your post, changing settings with the pulseaudio manager worked perfectly!

---

