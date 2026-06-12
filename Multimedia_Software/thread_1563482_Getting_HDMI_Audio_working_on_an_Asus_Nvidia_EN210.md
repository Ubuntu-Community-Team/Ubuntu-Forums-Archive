---
title: "Getting HDMI Audio working on an Asus Nvidia EN210"
date: 2010-08-29
forum: Multimedia Software
---

### Post by changlinn on 2010-08-29
Ok so I have looked through a few threads and followed a heap of how to's and managed to get the HDMI Audio showing up in Gnome sound preferences.
First my setup

Asus p6t motherboard
Asus EN210 video card
Intel i7 930

lspci |grep -i audio
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

cat /proc/asound/devices 
  0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
 16: [ 0- 0]: digital audio playback
 17: [ 0- 1]: digital audio playback
 24: [ 0- 0]: digital audio capture
 26: [ 0- 2]: digital audio capture
 32: [ 1]   : control
 33:        : timer
 36: [ 1- 0]: hardware dependent
 37: [ 1- 1]: hardware dependent
 38: [ 1- 2]: hardware dependent
 39: [ 1- 3]: hardware dependent
 51: [ 1- 3]: digital audio playback
 55: [ 1- 7]: digital audio playback
 56: [ 1- 8]: digital audio playback
 57: [ 1- 9]: digital audio playback

Like post 13 here I have managed to get pink noise using the below
speaker-test -Dhw:1,7 -c2
speaker-test -Dhw:1,3 -c2

I have upgraded Alsa to 1.0.23 using backports, and have played with asound.conf but I have found if the file exists I have nothing in /proc/asound/card1

Oh yeah contents of /proc/asound/card1
codec#0  codec#1  codec#2  codec#3  eld#0.0  eld#1.0  eld#2.0  eld#3.0  id  oss_mixer  pcm3p  pcm7p  pcm8p  pcm9p

cat'ing any of those eld files gives the same result:

monitor_present		0
eld_valid		0
monitor_name		
connection_type		HDMI
eld_version		[0x0] reserved
edid_version		[0x0] no CEA EDID Timing Extension block present
manufacture_id		0x0
product_id		0x0
port_id			0x0
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x0]
sad_count		0

Anyone got any tips or advice, I really want to get HDMI with HDMI audio working on this new box as it is my new media center and virtual server.

---

### Post by changlinn on 2010-09-04
hmm pavucontrol and alsamixer failed with an ~/.asoundrc file that was mentioned in another thread.
I think in my case the plot is a bit thicker, without that .asoundrc file I seem to get the audio meter on pavucontrol displaying sound on the HDMI but nothing through the TV, so either it is a faulty cable or a fault with the TV. I am going to have to loan the cable to someone and see.

---

