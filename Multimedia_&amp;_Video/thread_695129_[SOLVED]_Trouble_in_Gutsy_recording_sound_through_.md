---
title: "[SOLVED] Trouble in Gutsy recording sound through a mic"
date: 2008-02-12
forum: Multimedia &amp; Video
---

### Post by dansan on 2008-02-12
Here is a new twist on the "no recording with a mic" problem:

I have not been completely successful in Gutsy in digitally recording sound through a microphone, either plugged into a jack on the MB or one of the USB sockets. Being able to do this is crucial to shifting my business off of the Windows Vista/XP platform to Ubuntu. The desktop computer involved has a 2 GHz Core Duo processor and 2 GB of RAM. The onboard sound chip is Intel HDA. 

I installed Ubuntu Sound Studio because of its RT-kernel and sound processing software. It is on a second hard disc. Three microphones, all of them with speaker capability for earphones, are plugged into USB ports, and the external speakers are plugged into the MB. After much googling and searching of the Ubuntu Forums, I finally got Audacity to record my voice through any of the microphones, but that is because the program options enabled me to fine tune the capture channels. 

On the other hand, no matter how I manipulate alsamixer, I cannot get, for example, Sound Recorder to record my voice through a mic. In fact, Audacity won't do this either if I just rely on alsa mixer. When I click Play, I can hear hiss through the speakers, but none of the mics picks up my voice. I have tried differents settings in the Preferences -- Sound dialog and alsamixer but without success. I need to be able to record on Sound Recorder to move to Ubuntu. I'll skip the details, just trust me.

Are there other ways to set capture channels? Something like alsamixer but more sophisticated?

---

### Post by dansan on 2008-02-27
Since nobody has answered this query, I've been considering another approach to this problem.

Here is what lspci returns about my audio:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

According to the ALSA Soundcard Matrix [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel"), this chipset is not yet supported for ALSA.

I could add a soundcard to my box that ALSA does support, for example Club 3D Theatron Agrippa 7.1. Has anyone tried this kind of solution? If so, were you trying to get Ubuntu to record from a mic, and did the new card solve the problem?

Any clues are welcome!

Dansan

---

### Post by dansan on 2008-02-28
I guess this thread is a monologue so far, but I'd like to show what Gnome Volume Control displays. Take a look at the screenshots below. GVC has Microphone on the Playback tab and PCM as a Microphone on the Recording tab, and Revolabs (one of my mics) is listed for both. 

How are these things configured? I need a mic other than Revolabs doing the recording (three are connected to the box via USB), and I want playback coming out the speakers. Is the problem that ALSA has no support for the chipset on the MB?

If so, what about the idea in my second post about adding a sound card supported in ALSA?

Dansan

---

### Post by dansan on 2008-03-02
I solved this problem, so there is no reason to leave this thread open. See _[here]("http://ubuntuforums.org/showthread.php?p=4440614#post4440614")_.

---

