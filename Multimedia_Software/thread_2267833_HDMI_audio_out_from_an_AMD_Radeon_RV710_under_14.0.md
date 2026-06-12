---
title: "HDMI audio out from an AMD Radeon RV710 under 14.04"
date: 2015-03-04
forum: Multimedia Software
---

### Post by rjvbertin on 2015-03-04
Hello,

We have 2 laptops that when they were under MS Windows took turns at being the audio source for the main HiFi rig, connected over HDMI to an AV amp. Once under Linux (KUbuntu 14.04 using the open source Radeon driver), only the netbook of the 2 still plays audio over HDMI. The other, an AMD-based HP G62 with an RV710 discrete graphics board won't play audio. Both systems are configured to mirror the internal screen at its native resolution (1366x768) to the AV amp. The amp doesn't have a display connected, but seems to be fine with that. Sadly Linux has not foreseen the possibility someone would want to use HDMI for audio out only (MS Windows supports this just fine).

Symptoms:
- Using PulseAudio, everything seems to be fine, pavucontrol shows the signal being streamed to HDMI ... but as far as I can tell from the amp it receives no signal at all.
- Trying to use ALSA directly (VLC or aplay), I either get a "resource busy" error, or the same behaviour as with PA (sound disappearing who knows where).

I've tried to find solutions through google, but the hits are either too old or not relevant, suggesting things that don't help.

I had Mint Debian Edition on both machines before (about a year ago), and from what I recall I was obliged to use the proprietary fglrx driver in order to get sound output. That is no longer an option because AMD have dropped support for the RV710 quite a while ago, and as far as that legacy driver is still available it is no longer compatible with new Xorg server versions.

Additional symptoms on the G62 after having had the AV amp connected (and streamed to) include issues to suspend the computer, and a hang somewhere in the shutdown sequence.

Any ideas?

---

### Post by Yellow Pasque on 2015-03-04
Try this: [https://help.ubuntu.com/community/RadeonDriver#HDMI_Audio](https://help.ubuntu.com/community/RadeonDriver#HDMI_Audio)
Reboot after you try it. I could have sworn that AMD enabled HDMI audio by default as of Trusty's kernel version, but it won't hurt to make sure.

> - Trying to use ALSA directly (VLC or aplay), I either get a "resource busy" error, or the same behaviour as with PA (sound disappearing who knows where).
Just a note; Pulseaudio "grabs" the ALSA hardware device (that's why you see "resource busy"). Also, if you want to try and bypass pulse to use the audio device directly, you need to suspend pulseaudio (pasuspender) and you need permissions by either using sudo or adding your user to the audio group in /etc/group. It is not recommended to leave your user in the audio group, especiallt on multi-user systems.

---

### Post by rjvbertin on 2015-03-04
"
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV710/M92 [Mobility Radeon HD 4350/4550]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV710/730 HDMI Audio [Radeon HD 4000 series]
"

That's the exact identification of the hardware given by lspci.

I guessed that pulseaudio might be grabbing the ALSA device, but I haven't seen that error anymore lately, and in fact never on the netbook where "things just work". Possibly because I'm indeed in the audio (and video) group, but so is the main user on the G62 laptop. Hmmm.

I'll try the "audio=1" trick and see if that changes anything. But from what I understood from the Arch wiki it shouldn't be required with the 3.13 kernel.

---

### Post by rjvbertin on 2015-03-06
Well, enabling audio and connecting HDMI makes the system unstable and prone to freezes which can only be resolved with a power-cycle :(
It may have to do with the fact that I use Paragon's ufsd driver to mount the NTFS MS Windows partition, but I don't see why that would interfere with HDMI audio out ...

---

