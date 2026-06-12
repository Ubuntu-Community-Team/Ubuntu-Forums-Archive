---
title: "No sound with CMI8738 on new installation"
date: 2008-08-27
forum: Multimedia Software
---

### Post by vendingmachine on 2008-08-27
I am unable to get any sound from any application.  On the sound mixer, PCM is muted, and attempting to unmute it doesn't work.  When I press play for a song in Rhythmbox, the song does not play.

I had installed a TurtleBeach Montego DDL, with the CMI8738 chipset and performed a fresh installation of 8.04.  The system recognizes that the card is present, after I ran a few terminal commands as instructed in the the sticky thread, "Comprehensive Sound Problem Solutions Guide".

The output of aplay -l :

comp:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8768 [C-Media CMI8768], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

The output of lspci -v :

01:07.0 VGA compatible unclassified device: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
	Flags: bus master, medium devsel, latency 32, IRQ 23
	I/O ports at ac00 [disabled] [size=256]
	Capabilities: <access denied>

I didn't see "cmi8738" as a chipset option when I was performing the modprobe snd- command, but I followed instructions further in the guide to compile the module, and the program said that "cmipci" is the module used for cmi87x8 chipsets.  I ran "sudo modprobe snd-cmipci" to make sure that the module is running.

---

### Post by vendingmachine on 2008-08-27
I went to Sound Preferences to run an audio test, with the device set as Auto-detect, and it gave me the following:

audiotestsrc wave=sine freq=512 !
audioconvert ! audioresample !
gconfaudiosink: Failed to connect stream:
Invalid argument

---

### Post by markbuntu on 2008-08-27
You should change the Sound Preferences from autodetect to alsa. I have the same CMI8768 (but not turtle beach) and have had no problems. You can try my guide here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

It is sort of long winded, but it will teach you a lot about getting your sound to work properly.

---

