---
title: "M-Audio Delta audio issues"
date: 2014-08-24
forum: Multimedia Software
---

### Post by steevc on 2014-08-24
This has been an on and off problem for a while, but I've not reported it here before. Tried on AskUbuntu and Google+ with no resolution.

I built this new PC a while back and transferred my Delta 66 audio interface. Most of the time I've had problems with it. It generally starts up on 48kHz sampling rate instead of 44.1, which causes audio to play too slow. If I turn the card off and on again in Pulseaudio Volume Control it reverts to 44.1, so there seems to be some issue with initialisation. Once I fix that the sound is still distorted, regardless of how I set the levels. I've just had to tolerate it, but it's a shame to not be getting the best from my hardware. I tried my first recording session (Ardour, Jack etc) this week and the recorded sound was distorted too. I tried turning everything down, but it doesn't seem to be happening in the hardware.

This is in Kubuntu on kernel 3.13.0-34. I booted into Mint with 3.11.0-12 and audio is fine with that. I suspect that either the kernel driver or something in Pulseaudio has broken it. I don't know who I should report a bug to. I think it was okay on some previous update, but then the problems came back again. I can't tell which update broken it.

I'm happy to report a bug, but I don't know who I should report it too or what further information I should given them.

---

### Post by tgalati4 on 2014-08-24
I have my Delta66 plugged into an older PC with Dynabolic--an older, real-time audio distribution.  I only use it for recording so I keep it slim.  The Delta66 is a sweet-sounding card with decent 24-bit, 96 kHz recording.  The I/O breakout box has 2 quiet mic preamps and a mix of 1/4" and XLR connections.  Do you have the I/O breakout box?  You really need microphone preamps, because the card only records professional line level signals.  Anything less requires a lot of gain from your sources, which can drive guitars and microphones into distortion if you have them turned up to max.

PulseAudio is a framework that allows the system to have a different volume level than the applications and allows each application to set its volume level separately.  There is also the ability to send network audio and the ability to make complicated software patches for audio routing.  These features reduce the real-time responsiveness of live recording cards--so either turn off pulseaudio, remove it, or run it with the Jack audio server.  I would also be running a minimal distro like dynebolic or Linux Mint MATE with real-time kernel enabled.  Ubuntu Studio should work as well, but it may be too heavy to get the best audio quality out of a Delta66.

I believe that KDE uses the Phonon audio server, which behaves differently than pulseaudio.  If you remove pulseaudio, that might fix the 44.1/48 kHz as well, because pulseaudio uses a default setting and if pulseaudio crashes and auto-resets, that would account for the changing settings.

Live recording in Linux requires patience and a lot of testing to get the best configuration and best results.

---

### Post by steevc on 2014-08-26
I've had the Delta for a while, bought second hand along with the I/O box. It has worked fine on Kubuntu (12.04 I think) on my old PC with Pulseaudio etc. I've done a load of recording with it on that system and the audio was perfectly good. As I said, it worked okay in Mint too, which was also using Pulseaudio. I have a suspicion that it's related to the kernel driver, but  I'm not sure how to prove that. I think I'd have to install a fairly old kernel to get back to one that might have worked. I was just hoping that there is someone out there with a similar configuration who might have seen this and have some suggestions, or people who just know what to do. I've spent some time searching for solutions, but not come with anything yet.

Thanks

---

