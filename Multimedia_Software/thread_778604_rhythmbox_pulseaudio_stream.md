---
title: "rhythmbox pulseaudio stream"
date: 2008-05-02
forum: Multimedia Software
---

### Post by sciff90 on 2008-05-02
after upgrading to Hardy I have been getting used to pulseaudio everything is now working except when I open rhythmbox to play music no other sound applications work.

When I go into the pulse audio applet and check the application audio streams rhythmbox isn't there but when checking other applications they are always displayed.

Whenever ryhthmbox is open I can't get any other sound can someone shed some light??

any input would be appreciated

---

### Post by Zorael on 2008-05-02
Can you change output in rhythmbox, either to pulseaudio or ALSA?

---

### Post by sciff90 on 2008-05-02
i've been looking for that option but can't find it anywhere?

---

### Post by bgeron on 2008-05-18
I'm in Hardy Heron now too, and I had the same problem. I fixed it by setting every to PulseAudio in System -> Preferences -> Audio.

Good luck!

---

### Post by jharkn on 2008-05-28
Rhythmbox goes through gstreamer.

You can edit the gstreamer output by using:

gstreamer-properties

in the terminal.

Seems that you need to do what bgeron said too, thanks bgeron!

---

