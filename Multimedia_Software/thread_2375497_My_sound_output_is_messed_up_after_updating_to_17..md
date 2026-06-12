---
title: "My sound output is messed up after updating to 17.10"
date: 2017-10-25
forum: Multimedia Software
---

### Post by isnipeyt on 2017-10-25
Recently I upgraded to Ubuntu 17.04, which glitched out for me so I upgraded again to 17.10. And I noticed quickly that my audio did not work at all. This is due to this random sink that popped up when I installed Chrome Remote Desktop. Now Gnome takes that as my default sound output. I already deleted it, and I kept trying to follow online guides but they never worked. (Alsamixer is no help either) 
This is my sink info:
1 sink(s) available.
  * index: 0
	name: <chrome_remote_desktop_session>
	driver: <module-pipe-sink.c>
	flags: DECIBEL_VOLUME LATENCY FLAT_VOLUME 
	state: IDLE
	suspend cause: 
	priority: 0
	volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
	        balance 0.00
	base volume: 65536 / 100% / 0.00 dB
	volume steps: 65537
	muted: no
	current latency: 341.33 ms
	max request: 4 KiB
	max rewind: 0 KiB
	monitor source: 0
	sample spec: s16le 2ch 48000Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 0
	fixed latency: 21.33 ms
	module: 1
	properties:
		device.string = "/home/mustafa/.config/chrome-remote-desktop/pulseaudio#19d38190c5/fifo_output"
		device.description = "Unix FIFO sink /home/mustafa/.config/chrome-remote-desktop/pulseaudio#19d38190c5/fifo_output"
		device.icon_name = "audio-card"

aplay-l displays this:
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by wildmanne39 on 2017-10-25
*Thread moved to **Multimedia Software for better a better fit **.*

---

### Post by Yellow Pasque on 2017-10-25
Try this to reset pulseaudio user config:
```
rm -r ~/.config/pulse; pulseaudio -k
```

---

### Post by isnipeyt on 2017-10-25
I tried this in terminal, didn't work.

mustafa@huma-desktop:~$ rm -r ~/.config/pulse; pulseaudio -k
**rm: cannot remove '/home/mustafa/.config/pulse': No such file or directory**

---

### Post by gambs on 2018-01-20
[TABLE]
[TR]
[TD="class: answercell"][FONT=inherit][FONT=inherit]There is some problem with chrome remote desktop with Ubuntu. Getting back your system sound for all applications you should remove the extension from chrome and ubuntu both.[/FONT]
[FONT=inherit]Run command[/FONT]
[FONT=inherit]**apt remove chrome-remote-desktop or apt-get remove chrome-remote-desktop**[/FONT]
[FONT=inherit]and restart your ubuntu :)[/FONT]
[/FONT]
[/TD]
[/TR]
[/TABLE]

---

### Post by isspam404 on 2018-06-06
> **gambs said:**
> [TABLE]
[TR]
[TD="class: answercell"][FONT=inherit][FONT=inherit]There is some problem with chrome remote desktop with Ubuntu. Getting back your system sound for all applications you should remove the extension from chrome and ubuntu both.[/FONT]
[FONT=inherit]Run command[/FONT]
[FONT=inherit]**apt remove chrome-remote-desktop or apt-get remove chrome-remote-desktop**[/FONT]
[FONT=inherit]and restart your ubuntu :)[/FONT]
[/FONT][/TD]
[/TR]
[/TABLE]

Works like magic! Dude, you are a life saver.  It had messed up everything in my system.

---

