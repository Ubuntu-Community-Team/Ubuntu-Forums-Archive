---
title: "No sound, card is detected but Pulse Audio cannot see it"
date: 2015-09-05
forum: Multimedia Software
---

### Post by Keith_Beef on 2015-09-05
This is a very weird problem&#8230; I've looked around on Ubuntu forums and a few other places on the web, without finding anything that works to cure my problem.

This afternoon everything was working fine. My son wanted to have a look at some audio software, so I started Hydrogen and played back a sample track. The I showed him Audacity and played back an OGG from my music collection. Then I started Ardour and played back the same OGG file through it. OK.

So I logged out and logged back on his account&#8230; no sound. I tried playing back a video through VLC, still no sound. I tried different settings, Pulse Audio Volume Meter  showed the levels fluctuating as if there was sound being played, but nothing. And yes, I checked the mute buttons, the cables to the amp, and that the volume on the amp was turned up.

Then I noticed something really weird: Pulse Audio volume controller lists only a virtual device, named GK107 HDMI Audio Controller. I don't remember having seen this name anywhere before today.

```
$ lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: Gigabyte Technology Co., Ltd Device a002
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at f9200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
--
01:00.1 Audio device: NVIDIA Corporation GK107 HDMI Audio Controller (rev a1)
	Subsystem: NVIDIA Corporation Device 096f
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f6000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel

03:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02) (prog-if 01 [AHCI 1.0])

```

And modules look like they are loaded.
```
$ lsmod | grep -i snd
snd_seq_dummy          12798  0 
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_realtek    65580  1 
snd_hda_intel          56531  10 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  6 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  3 snd_seq_midi_event,snd_seq_dummy,snd_seq_midi
snd_seq_device         14497  4 snd_seq,snd_rawmidi,snd_seq_dummy,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69322  29 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_dummy,snd_seq_midi
soundcore              12680  1 snd

```

I've rebooted a couple of times, and after the first reboot things changes a little. Pulse Audio Volume Controller now still shows the GK107 HDMI device, but also lists  a Built-in Audio Digital Stero (IEC958) device, but I cannot change the port which is set as Digital Output (S/PDIF). I'm running a 3.5mm jack to two RCA connectors plugged into a NAD amplifier.




I am starting to think that I need to stop and restart Pulse Audio, giving it an argument to tell it which sound device to use.

---

### Post by yoshii on 2015-09-06
I can't add much to the conversation except to note that IEC958 = SPDIF.  Without a SPDIF connection, that audio will go nowhere (and be thus silent).  You need to find a full duplex ANALOG output connection setting.  But you probably already know that.  Sorry I can't be of more assistance.

---

### Post by Keith_Beef on 2015-09-06
Well, I did manage to get sound working from VLC, but this only works when the volume setting in VLC is at exactly 100%. Lower than that, and the sound is louder (yes, louder than at 100%) and with what sounds like white noise added.

And the volume controller for the Pulse Audio mixer does not change the volume, I need to use the volume control on the amp.

Oh, and sound does not work from Battle for Wesnoth, but works in Hydrogen and Ardour).

I just tried the   Applications - System Tools - System Settings - Sound. Here, I can see in the output tab that I have the choice of:
[LIST]
[*]Digital Output (S/PDIF) *Built-in Audio*
[*]Analogue Output *Built-in Audio*
[*]Simultaneous output to GK107 Audio Controller Digital Sertro  (HDMI)
[/LIST]

Now when I select Analogue Output, close the settings tool and open it again, I find it has gone back to Digital Output (S/PDIF).

Worse, VLC now complains on startup.
Audio output failed:
The audio device "front:card=Intel,DEV=0" could not be used:
Device or resource busy.

---

### Post by Yellow Pasque on 2015-09-06
Try resetting pulseaudio user config (sometimes it gets corrupted). The following command deletes the user config and restars pulseaudio so it will generate new config files:
```
rm -r ~/.config/pulse; pulseaudio -k
```

---

### Post by Keith_Beef on 2015-09-11
Well, after a lot of struggling, I think I might have fixed the problem. At least sound works for now on my account, though I don't yet know if it works on the other accounts.

I used Synaptic to completely remove:
	alsa-base
	linux-sound-base
	paman
	pulseaudio
	pulseaudio-module-x11

Then selected them for re-installation.
	alsa-base
	linux-sound-base
	paman
	pulseaudio
	pulseaudio-module-x11 

When I selected "Apply" I got a big white space under "NOT AUTHENTICATED" and under "To be installed" I saw:
	alsa-base
	linux-sound-base
	pulseaudio
	pulseaudio-module-x11 

Since paman was missing from the list, I thought that this was the package that was not authenticated. For now I can live without it, so I removed it from the selection to install.

But no&#8230; when I applied the filter Marked Changes, I saw that only those four packages were selected for installation.
	alsa-base
	linux-sound-base
	pulseaudio
	pulseaudio-module-x11

Oh! When I applied, I heard a system noise alert! And I got a message that I had "held broken packages", so Syanptic refused to install the four packages!

So, I selected the filter Broken, reloaded the list, and I saw in the bottom of Synaptic's window:
0 packages listed, 4547 installed, 0 broken, 4 to install/upgrade, 0 to remove; 4266kB will be used.

I tried to apply the changes, this time I didn't get any "NOT AUTHENTICATED".
And this time, I didn't get a message about broken packages, and installation completed.
Still no sound.
But in GNOME ALSA Mixer, I heard a system sound when I unchecked the Mute for headphones, and I got a system sound when I minimized or restored a window. Still no sound from VLC, though. But if I muted and then unmuted headphones again, the system sounds stopped.

Rebooted to see what would happen.


Started GNOME ALSA Mixer and saw that all the output lines were muted.
I unmuted from left to right and heard a system sound when I unmuted Side. But after muting and unmuting again, there were no sounds. But in PulseAudio volume control I see ALSA plug-in [gnome-panel] flash up each time a system sound should be played, and VLC media player: audio stream shows volume when I play a video through VLC..

Trying to set up a new printer, I saw that I did not have System Settings in my menu any more. I reinstalled ubuntu-desktop to fix that, and found that System tools - Preferences - Sound had come back. In there, I found that the output volume was at 0. I increased that to 100% and sound worked! 

Could that have been the problem all along? That the lack of an entry in my main menu stopped me from making a small change that could cure the problem? And that I cured the sound problem by configuring my new printer? 

Crazy!!

---

