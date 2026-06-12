---
title: "gnome-volume-control shows recording levels, no apps record sound"
date: 2010-08-08
forum: Multimedia Software
---

### Post by darkpixel on 2010-08-08
I'm stumped.

If I go into gnome-volume-control and look at the input tab, I see two devices for recording.  One is the internal soundcard, and the other is my Logitech QC.  If I click on the QC (0808 Analog Mono), I can see the input meter bouncing around when I talk--it's definitely picking up on my voice.  Then I close gnome-volume-control.  If I re-open it, it shows that my settings change has been saved.

If I open up Audacity and click record, Audacity shows up in gnome-sound-record under the 'Applications' tab--showing that it's recording, and it records me speaking.

For any other application (Cheese Webcam Booth, Sound Recorder, etc...) it completely fails to record audio, and the applications do not show up under the 'Applications' tab in gnome-sound-recorder.

Any pointers?  I see nothing in the preferences of the individual applications that would tell them what sound system or input to use.

Edit: I should also mention that this is a new system (~1.5 months old), and everything has been working up until a few days ago when I installed updates and rebooted.

---

### Post by darkpixel on 2010-08-08
Posted this on answers:
[https://answers.edge.launchpad.net/ubuntu/+question/120424](https://answers.edge.launchpad.net/ubuntu/+question/120424)

---

### Post by lidex on 2010-08-08
Try removing any cruft in the form of config files:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**
Now run this:
```
gstreamer-properties
```
and make sure your defaults are set to pulseaudio

---

