---
title: "Upgraded to 8.10 - no sound and flash problems"
date: 2008-10-31
forum: Multimedia Software
---

### Post by rosyatrandom on 2008-10-31
I've just upgraded to 8.10 from 8.04 and have run into a couple of problems.

_No sound_

Try as I might, I just can't get any sound out. The volume isn't muted, and altering the playback device in Preferences>Sound>Devices doesn't help. Trying to use any of the hardware specific options produces errors, e.g.: 

*HDA Intel ALC883 Analog ALSA* returns *audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback*

In the terminal, I get:

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
rosy@rosy-laptop:~$ 

and

lspci -vv
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

_Flash video problems_

I've reinstalled the flash plugin, but in Firefox videos stop playing (though continue downloading) after just a few seconds. I've adjusted the settings to let it store more data, but it hasn't helped. In Opera, not even the player loads up - I just see a gray box.

__________________________
**EDIT 1:**

I've tried playing some media files (aac, avi) and most programs just flat out don't do anything - they either crash and quit (BMP), crash and stop responding (VLC), silently refuse to play the file (Exaile), or come up with error messages (Totem - "An error occured / Could not get/set settings from/on resource.", MPlayer - "Could not open/initialize audio device -> no sound.")

**EDIT 2:**

It seems to be a kernel issue: booting with  2.6.24-21-generic solves both these problems.

**EDIT 3:**

Or maybe not; the laptop's just come out of suspension and the issues have cropped up again.

**EDIT 4:**

I've rebooted with 2.6.27-7-generic and, again, all is working. So whatever is causing this only happens after some time has passed - I don't know what actually precipitates it.

aplay -l and  lspci -vv give the same results.


I will also note that alsamixer, both when the sound is and isn't working, only shows one bar ("Master") via PulseAudio.

---

### Post by smonteith on 2008-10-31
I also am having sound problems.  Although if I boot with the 2.6.24 kernel from 8.04 the sound is working again.  So it seems to be related to the 2.6.27 kernel.

When I try aplay -l I get this:

aplay -l
**** List of PLAYBACK Hardware Devices ****
Bus error

I also get an error from the volume control applet: Volume Control has quit unexpectedly.

lspci shows this as the sound card:
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 12bc
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 17
	Region 0: I/O ports at 2000 [size=256]
	Region 1: I/O ports at 2400 [size=64]
	Region 2: Memory at fc480400 (32-bit, non-prefetchable) [size=512]
	Region 3: Memory at fc480600 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0


cat /proc/asound/cards shows:


 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with AD1981B at irq 17
 1 [U0x46d0x8d7    ]: USB-Audio - USB Device 0x46d:0x8d7
                      USB Device 0x46d:0x8d7 at usb-0000:00:1d.1-1, full speed

What other tests can I perform?

Thanks

---

### Post by mrburns on 2008-10-31
I've just done a fresh install of 8.10 on a system with both an onboard audio chip and an Audigy 2. The onboard is disabled in the BIOS though, but a VIA device is still showing up in the list of devices under System > Preferences > Sound.

I've read through most of the posts about sound problems, including the Audigy specific ones. I  have unchecked the analog/digital output jack check in the volume control applet.

I've managed to get test sounds to play in the Sound Preferences applet, and Totem is successfully playing videos with sound. However, neither Amarok nor the built in system sounds are working.

The Audigy is displayed in the output of aplay -l.

Using alsamixer from the console gives me only one channel (Master) with both card and chip given as PulseAudio. The gnome volume control applet however has the Audigy device selected, and can set volumes for about a billion different channels.

It seems, naively, like most of the system is using the wrong sound device or driver, but that I've somehow managed to get totem to use the correct one. Has anyone got any suggestions on how to proceed?

---

### Post by rosyatrandom on 2008-11-01
Bumped due to repeated edits

---

### Post by rogerp1 on 2008-11-02
I have the same problem. If I kill the pulseaudio process and then run alsamixer it shows my correct card and sound works fine...dont really want to kill pulseaudio though everytime I want to listen to some tunes

---

### Post by smonteith on 2008-11-03
Pulseaudio does not start on my system:
Nov  3 07:30:24 juxta-linux pulseaudio[8169]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov  3 07:30:24 juxta-linux pulseaudio[8170]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov  3 07:30:24 juxta-linux pulseaudio[8170]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov  3 07:30:24 juxta-linux pulseaudio[8169]: main.c: read() failed: Success
Nov  3 07:30:24 juxta-linux pulseaudio[8169]: main.c: daemon startup failed

When I try to run alsamixer I get BUS ERROR and nothing more as a result.

---

### Post by peacewithall on 2008-11-03
I am also having 'no sound' problems with 8.10, but when I first boot sounds work ok, but I noticed if my sound is switched or changed within applications, my sound completely stops, the only fix is to kill pulseaudio, then almost all returns back to working again.

For example having a conversation on pidgen, when the sound event that plays with a new message, is repeated over and over as it does during a chat session, pulseaudio seems to fall apart, and all system sounds become muted, again killing pulseaudio is the solution, but other applications like secondlife voice, will stop working without pulseaudio running. The pulseaudio crash seems to be random and I can only reproduce it when I constantly switch from sound to sound, or sound off and on, in most applications.

Again the problem is pulseaudio, I've read many posts here where people are having to kill it to have any sounds at all, so it does seem to be a very wide spread problem.

Oh well, hopefully it will be fixed soon.

---

### Post by teaguepatrick on 2008-11-03
I also have no sound in 8.10 sees hardware but the drivers won't work in alsa

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Nothing is muted, permissions are good, I think the problem is that Alsa fails to load i8x0 drivers for some reason - fails everytime - and Test fails in system>preferences>sound saying: audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

I've been trying to fix this for a week now, followed [http://ubuntuforums.org/showthread.php?t=205449&highlight=detect+soundcard](http://ubuntuforums.org/showthread.php?t=205449&highlight=detect+soundcard) all to no avail because loading the drivers always results in a failure.

---

