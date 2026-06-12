---
title: "No Audio Whatsoever"
date: 2007-12-31
forum: Multimedia &amp; Video
---

### Post by Hideousness on 2007-12-31
I'm baffled. I've spent a few hours trying to figure this out, but to no avail.  I'm using a Turtle Beach Santa Cruz audio card, and I've followed a guide to try to get things working. Clicking volume control yields a message saying "No volume control GStreamer plugins and/or no devices found". Typing alsamixer in the shell won't work, and only gives me a message: "No mixer elems found". Help, anyone?

---

### Post by NilsE on 2007-12-31
Go into Synaptic Package Manager and make sure the following are installed.

alsa-base
linux-sound-base
alsa-utils
gstreamer0.10-alsa

They will also install some dependencies.

```
In a terminal run:

asoundconf list

and see if your card shows up.
```

```
In a terminal run: 

asoundconf set-default-card xxxxxx

Then again with sudo: 

sudo asoundconf set-default-card xxxxx

Replace xxxxx with the name of your card found in the above list exactly as it shows up
```

---

### Post by Hideousness on 2007-12-31
That did nothing. All of the packages were already installed, and my card was apparently named "UART".

---

### Post by Yellow Pasque on 2007-12-31
Try OSSv4. It supports the TB/SC. The link's in my sig.

---

