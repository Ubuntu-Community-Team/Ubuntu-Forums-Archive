---
title: "Novation X-station soundcard, ALSA &amp; PulseAudio"
date: 2010-01-12
forum: Multimedia Software
---

### Post by joelgrrr on 2010-01-12
I'm trying to use a novation x-station as my soundcard so I can use some external speakers, via the usb adaptor, on ubuntu 8.04, Hardy.

The novation x-station is detected fine when I plug it into the usb socket:

```
joel@bohr:~$ amidi -l
Dir Device    Name
IO  hw:1,0,0  X-Station MIDI 1
```

and in /var/log/messages

```
Jan 12 18:08:31 bohr kernel: [ 2351.148213] usb 5-1: new full speed USB device using uhci_hcd and address 10
Jan 12 18:08:31 bohr kernel: [ 2351.181859] usb 5-1: configuration #1 chosen from 1 choice
Jan 12 18:08:32 bohr kernel: [ 2351.339448] input: Novation DMS X-Station as /devices/pci0000:00/0000:00:1d.1/usb5/5-1/5-1:1.3/input/input20
Jan 12 18:08:32 bohr kernel: [ 2351.396264] input,hidraw2: USB HID v1.00 Device [Novation DMS X-Station] on usb-0000:00:1d.1-1
```

It even plays the ubuntu startup theme when I plug it in, so it's sort of working.

The problem is I can not get exaile, or any other music player, to route audio through it. Audio just comes out of my regular laptop speakers. Should I be using the ASIO or PulseAudio sink from multimedia players?

Is the following PulseAudio message anything to worry about?

```
Jan 12 18:08:32 bohr pulseaudio[9843]: alsa-util.c: Cannot find fallback mixer control "PCM".
```

I have pulseaudio 0.9.10 and alsa-utils 1.0.15-3

Update: I have updated alsa to 1.0.20, and i can confirm that a speaker test of the soundcard works (speaker-test -Dplughw:1,0 -c2), but still not luck using it from any app, like exaile.

Thanks
Joel

---

### Post by joelgrrr on 2010-01-12
OK, fixed.

The problem was that I had not configured the correct default sink in PulseAudio. This can be configured using "padevchooser", but in my case padevchooser was not starting:

```
joel@bohr:~$ sudo padevchooser

** (padevchooser:7990): WARNING **: pa_browser_new() failed.
```

The reason for this error was that I was not running "avahi-daemon".

So, by ensuring that avahi-daemon was running I could then tun padevchooser and the select the correct sink to use.

---

