---
title: "Ekiga and audio conversation"
date: 2008-09-26
forum: Multimedia Software
---

### Post by spacemarc on 2008-09-26
Hi all
I searching for a way to play an audio file during a conversation via Voip in Ekiga (or with also other programs/plugin, i don't know).

The audio file will be heard, obviously, by me and by my interlocutor.

It's possible?

---

### Post by spacemarc on 2008-09-27
suggests?

---

### Post by ipburbank on 2008-09-27
I'v been wondering something similar, but more general; how to feed the sound output into the audio input with no feedback issues, and will work in all programs... I'd appreciate any help with this thread!

---

### Post by spacemarc on 2008-09-29
there is a solution?

---

### Post by markbuntu on 2008-09-29
Hmmm.....Theoretically, if you are using the microphone through your sound card and your sound card mixer also has a pcm capture/record switch, you could do it. Some cards have these, many do not.

---

### Post by markbuntu on 2008-09-29
> **ipburbank said:**
> I'v been wondering something similar, but more general; how to feed the sound output into the audio input with no feedback issues, and will work in all programs... I'd appreciate any help with this thread!

In the PA Device Chooser/Configure Local Sound Server/Multicast/RTP Sender there is an option to Create separate audio device for Multicast/RTP and a switch for loop back audio to local speakers. You can supposedly send any app to this sink in the PA Volume Control and it will loopback to your sound card. 

If you have more than one sound device, like a sound card and usb headset or usb speakers, you can go to ...Configure Local Sound Server/Simultaneous Output and check the box. This will make a virtual output device in the PA Volume Control/Output Devices that will go to all your devices at once.

What exactly are you trying to do?

---

### Post by markbuntu on 2008-09-29
Ooops DP, sorry

---

### Post by ipburbank on 2008-10-04
> **markbuntu said:**
> In the PA Device Chooser/Configure Local Sound Server/Multicast/RTP Sender there is an option to Create separate audio device for Multicast/RTP and a switch for loop back audio to local speakers. You can supposedly send any app to this sink in the PA Volume Control and it will loopback to your sound card. 

If you have more than one sound device, like a sound card and usb headset or usb speakers, you can go to ...Configure Local Sound Server/Simultaneous Output and check the box. This will make a virtual output device in the PA Volume Control/Output Devices that will go to all your devices at once.

What exactly are you trying to do?

I am trying to add the ability to play audio to another person on skype.

---

