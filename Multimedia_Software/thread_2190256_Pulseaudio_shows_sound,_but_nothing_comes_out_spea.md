---
title: "Pulseaudio shows sound, but nothing comes out speakers after 13.04 to 13.10 upgrade"
date: 2013-11-26
forum: Multimedia Software
---

### Post by pumpkinslayer on 2013-11-26
I finally got audio working a month ago in 13.04 (lubuntu) by installing pulseaudio.

After upgrading to 13.10 the indicators in pulseaudio still show that sound is coming through. They register for both microphone input and sound output. But I still can't hear anything from the headphones plugged into my usb audio. Pulseaudio registers the sound from the microphone too.

I also double-checked through alsamixer that the volume was turned up.

I've gone through multiple guides on the forums, but to no avail. 

In summary...
-- usb sound device is working
-- sound is not muted
-- microphone input is working
-- audio output is NOT working

Any suggestions to get audio output working? Thanks.

---

### Post by MibunoOokami on 2013-11-26
Hi, I had a similar problem with both video and audio. For me it was a permissions thing, yours could be completely different but try the following code. My knowledge is limited, more experienced people will be along with alternative options should this not work.

```

sudo usermod -a -G audio youruser
``` Remember to replace 'youruser' for your actual username.

---

### Post by pumpkinslayer on 2013-11-26
> **MibunoOokami said:**
> Hi, I had a similar problem with both video and audio. For me it was a permissions thing, yours could be completely different but try the following code. My knowledge is limited, more experienced people will be along with alternative options should this not work.

```

sudo usermod -a -G audio youruser
``` Remember to replace 'youruser' for your actual username.

Added my user to audio group and restarted. Still no sound.

---

### Post by Yellow Pasque on 2013-11-27
Try this:
[https://wiki.ubuntu.com/PulseAudio#Ubuntu_13.04.2BAC8-Raring_.28and_later.29](https://wiki.ubuntu.com/PulseAudio#Ubuntu_13.04.2BAC8-Raring_.28and_later.29)

---

### Post by pumpkinslayer on 2013-11-28
> **Temüjin said:**
> Try this:
[https://wiki.ubuntu.com/PulseAudio#Ubuntu_13.04.2BAC8-Raring_.28and_later.29](https://wiki.ubuntu.com/PulseAudio#Ubuntu_13.04.2BAC8-Raring_.28and_later.29)

This, plus random clicking around in "Pulse Volume Control" afterwards, got things working. Thanks a ton.

---

### Post by pumpkinslayer on 2013-12-19
One final follow-up on this topic.

I have had no problems since switching to a different (cheaper) USB audio device. So it appears to be some hardware related issue.

Problem device: appears in Pulseaudio as "USB audio device" (this item: [http://www.amazon.com/Channel-External-Sound-Audio-Adapter/dp/B003MN1LTQ/](http://www.amazon.com/Channel-External-Sound-Audio-Adapter/dp/B003MN1LTQ/) )
Working device: appears in Pulseaudio as "TP6911 Audio Headset Analog Stereo" (this item: [http://www.amazon.com/External-Sound-Adapter-Desktop-Notebook/dp/B000BUDHNQ](http://www.amazon.com/External-Sound-Adapter-Desktop-Notebook/dp/B000BUDHNQ) )

Just for the record. Over and out.

---

