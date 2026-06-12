---
title: "Sound configuration problems"
date: 2010-07-12
forum: Multimedia Software
---

### Post by maghoxfr on 2010-07-12
I have just bought an usb interface (Alesis Multimix 4 USB). What I noticed is that through its headphone out, I hear what I play straight before entering the pc and simultaneously I hear what comes out of the pc with a little latency. What I want is to separae those signals and send what I hear from the pc to the onboard output to be able to listen to it independently.

I went to Preferences>Sound and chose the preferences shown on the thumbnails. It's in spanish but the main items are in english, if anyone don't understand something please tell me and I'll translate.

The problem is that now all I have is no signal from my interface but a huge constant noise.

Does anyone know how could I solve this and acomplish my goal?
Thank you

---

### Post by maghoxfr on 2010-07-12
One thing I can't understand is that on the input levels meter (thumbnail #2) I can see properly when I play, and I don't see any constant noise signal. In the attachment I ishow what I'd like to do.

---

### Post by maghoxfr on 2010-07-12
I keep fighting, I've found this two links that looks promising, and frightening. I wish the solution was GUI but I'll try to descifer what this links say, if anyone gives me a hand it'll be a great relief.

[http://alsa.opensrc.org/MultipleCards#Multiple_USB_Audio_Devices]("http://alsa.opensrc.org/MultipleCards#Multiple_USB_Audio_Devices")

[http://alsa.opensrc.org/index.php/MultipleUSBAudioDevices]("http://alsa.opensrc.org/index.php/MultipleUSBAudioDevices")

---

### Post by maghoxfr on 2010-07-13
I can say I solved it. This is what I did:

I've read many things and got really confused because I'm not a programmer.

On this [_[COLOR="Blue"]link[/COLOR]_]("http://manpages.ubuntu.com/manpages/lucid/man1/jackd.1.html") I've found this paragraph that was exactly what I was loking for

> Run jackd in full-duplex mode using the ALSA hw:0,0 device for playback and the hw:0,2 device for capture.

              jackd -d alsa -P hw:0,0 -C hw:0,2

So what I did to find out the names of my cards was running on a terminal
```
aplay -l
```
and type the command on the quote on a terminal substituting the names of the example for the ones of my cards.

As it was uncomfortable to open a terminal and typing the command everytime I created a launcher which I launch before opening Qjackctl.

If anyone has a more elegant way to do it I'd be very interested to know it, for instance, not having to use any launcher and leaving the action of the command as a preset.

---

### Post by maghoxfr on 2010-07-17
Ok, i don't know what happened, I didn't do anything besides this, but now I can use the setup options in Qjackctl and works fine, I can go without the launcher.

---

