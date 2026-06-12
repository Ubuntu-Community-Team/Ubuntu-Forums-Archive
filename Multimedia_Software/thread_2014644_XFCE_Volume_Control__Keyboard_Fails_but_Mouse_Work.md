---
title: "XFCE Volume Control | Keyboard Fails but Mouse Works"
date: 2012-07-02
forum: Multimedia Software
---

### Post by neu5eeCh on 2012-07-02
I upgraded to 4.10, but I'm not sure this is the cause.

I can no longer adjust the volume via the keyboard. Strangely, if I use the keyboard volume control, the slider "notifier" will respond up or down, but the volume won't change. If I want to adjust the volume, I have to mouse to the volume applet in the panel and adjust it with the mouse.

Seems like there ought to be a simple solution for this, but Googling hasn't helped me yet.

Sony VAIO VGN-FW373J running Xubuntu 12.04 | XFCE 4.10

---

### Post by neu5eeCh on 2012-07-02
Ah-ha! Now I'm getting somewhere:

I notice that when I use RadioTray or Clementine, the "Volume Control" Applet (under the "Playback" tab) shows that  "Playback" is assigned to the "Built-in Audio Analog Stereo".

However, my keyboard volume buttons are **not** bound to the "Built-in Audio Analog Stereo".

If I pick the "Output Devices" Tab, I discover that the keyboard's Volume Buttons are bound to the sound card (RV635 HDMI Audio [Radeon HD 3600 Series] Digital Stereo (HDMI)) .

I don't see an option to re-assign the volume keys. Any advice?

---

### Post by neu5eeCh on 2012-07-02
Solved. I turned off HDMI AUDIO under the configuration tab of the Pulse Audio control center, rebooted, and could once again control the volume (of the Built-in Analog Audio Stereo) with the keyboard's volume button.

---

