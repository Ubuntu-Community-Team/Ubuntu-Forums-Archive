---
title: "exteranl microphone use on Lenovo T440p"
date: 2016-07-12
forum: Multimedia Software
---

### Post by rawlins02 on 2016-07-12
I want to use an external microphone on my Lenovo T440p, which has a single "headphone" jack. I've used Audacity to record music using the internal microphone located on upper part of the monitor. Sounds OK, but I'm sure I can do better with a decent external mic. I understand the headphone jack also serves as an input jack for external mics equipped with a 3.5mm plug. In volume control I can not determine how to disable the internal mic. The Lenovo manual says to open control panel, click hardware and sound, then select Realtek HD manager. Guessing that's for a Windoze install. If I go to Dashboard and select "sound" and then "input" (I think this is called PulseAudio), the window will lengthen and contract as I put the microphone plug into and out of the jack, but it only shows the internal microphone under "record sound from". That is, I don't think my external mic is being detected. Interestingly when I plug in headphones the "play sound from" selection changes from saying speakers to headphones.

I'd intended to buy a USB mic thinking that it would be "seen". Unfortunately I bought the wrong mic.

Also having trouble getting sound output into powered USB speakers, but that's a problem for another post...

---

### Post by Bucky Ball on 2016-07-13
If Pulseaudio Volume Control, you have Playback tab, Recording, output, input, configuration. Plug mic in, go to input, there is a drop down list for devices, or the entry for the device might be further down that page and you'll need to scroll down. Sometimes takes some experimentation. 

If I may: What exactly are you wanting to record in the analogue world? A live band? Vocals? If you want to record from another device, a mic is not the way to go about it. Directly plugging the device in via its audio output or USB is. But you probably know that ... :)

---

### Post by Yellow Pasque on 2016-07-13
If it's not detected at all, try retasking the jack. (It doesn't always work, especially when retasking an input to output or vice versa).

```
sudo apt-get install alsa-tools-gui
hdajackretask
```

---

