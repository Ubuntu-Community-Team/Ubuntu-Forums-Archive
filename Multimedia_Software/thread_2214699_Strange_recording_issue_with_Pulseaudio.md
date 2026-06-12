---
title: "Strange recording issue with Pulseaudio"
date: 2014-04-02
forum: Multimedia Software
---

### Post by Ranko Kohime on 2014-04-02
Google seems not to be able to understand what I'm trying to ask it.  ;)

I have a laptop, with it's internal sound device, and a USB XLR interface, an M-Audio MobilePre.

I've used Audacity in the past (as recently as Sunday) to record from the XLR mic, and it's worked fine.

Today however, when I click Record in Audacity, the indicator that sweeps across the screen as Audacity records is standing still.  Normally, if Audacity is recording from a muted source, it will still record silence, and advance the recorded time appropriately, but this time, it doesn't even begin recording.  Now if I go in to Pavucontrol, and switch it over to some other source, such as the laptop's internal mic or a monitor of either soundcard, it will immediately start recording, but then if I switch back to the XLR mic, it stops again.  I've unplugged and plugged in the interface, stopped and restarted Pulseaudio, and even rebooted, but no change.

Any clues as to what's going on here?

ETA: This is happening with ANY program reading from the mic as well, such as TeamSpeak, Skype, etc...

---

### Post by dannyboy79 on 2014-04-02
i have no experience with XLR. i have a usb webcam which i record with audacity and don't have any issues besides with playback which you informed me of the work around. i just opened audacity and muted my webcam mic, then started recording and the slider sweeps to the right and records nothing and then when i unmute the webcam mic it starts recording my voice. So I am at a loss for what to say. Maybe your xlr mic has died?

---

### Post by Ranko Kohime on 2014-04-02
I'm thinking the XLR part has nothing to do with it, as when I move the interface to another computer, it still works normally.

---

### Post by Ranko Kohime on 2014-04-03
So that everyone can see what's happening, I made a short video.

[Youtube: Pulseaudio issue]("http://youtu.be/Rr1Z6BSlLyg")

---

### Post by Ranko Kohime on 2014-04-03
Well I feel stupid.  It was my USB hub acting up.  -_-

---

