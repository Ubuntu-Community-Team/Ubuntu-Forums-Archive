---
title: "xfce4-mixer and ALSA"
date: 2010-05-30
forum: Multimedia Software
---

### Post by Praxicoide on 2010-05-30
I'm having problems getting xfce4-mixer to work.

I have a VIA AC 97 (rev20) audio card, and it has worked fine under ALSA.

The problem is that now the Xfce4-mixer gives me as the only option the OSS-Mixer, not ALSA. I can't get any sound from it, and I've moved all volume levels.

Using the command "alsamixer" in the terminal gives me the levels that used to appear on my Xfce4-mixer, and unmuting the master volume, I can once again get sound in my computer.

The problem is that I don't have a volume gauge then, because Xfce4-mixer doesn't work, and so I would have to use the terminal every time I wanted to turn the volume up or down.

Any help is appreciated. Thank you in advance.

---

### Post by Yellow Pasque on 2010-05-30
Try starting the mixer from the terminal to see if it outputs errors:
```
xfce4-mixer
```
Also, make sure the gstreamer alsa package is installed:
```
sudo apt-get install --reinstall gstreamer0.10-alsa
```

---

### Post by Praxicoide on 2010-05-30
I'm at work right now, but I'll post the output from that the minute I'm back home.

Thanks.

---

### Post by Praxicoide on 2010-05-30
The reinstall did the trick. Thank you so much!

---

### Post by Praxicoide on 2010-05-31
I may have gotten ahead of myself.

The mixer again shows only OSS-Mixer and I again don't have sound.

What's worse is that I can't get alsamixer to open. Now I get the following message:

```
alsamixer: function snd_ctl_open failed for default: No such device
```

And sure enough, asound -l gives me "no sound card detected".

....

This is a disheartening regression. Any ideas on what I could do?

---

### Post by Praxicoide on 2010-05-31
Sorry for the triple post, but pressing the edit button does nothing.

Here's the relevant part of lspci -v

```
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
	Subsystem: Sony Corporation Device 80e3
	Flags: medium devsel, IRQ 5
	I/O ports at 1000 [size=256]
	I/O ports at 1c54 [size=4]
	I/O ports at 1c50 [size=4]
	Capabilities: <access denied>
	Kernel driver in use: VIA 82xx Audio
	Kernel modules: snd-via82xx

00:07.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 20)
	Subsystem: Sony Corporation Device 80e3
	Flags: medium devsel, IRQ 5
	I/O ports at 1400 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: VIA 82xx Modem
	Kernel modules: snd-via82xx-modem
```

---

