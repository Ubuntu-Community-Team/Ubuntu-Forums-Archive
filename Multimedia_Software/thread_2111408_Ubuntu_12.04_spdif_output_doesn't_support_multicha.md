---
title: "Ubuntu 12.04 spdif output doesn't support multichannel sound"
date: 2013-02-01
forum: Multimedia Software
---

### Post by Belgarath1610 on 2013-02-01
Hi there, I'm a relatively new Ubuntu-user, and I need a bit of help!


  I just recently discovered that my laptop (an Acer Aspire 5670), has  an optical-spdif output and since it's connected to a 5.1 Yamaha  Receiver I bought a special optical cable and connected them properly.


  Now, I noticed most people usually find at this point that they  cannot configure their sound cards to output an spdif signal, but that  is definitely not the problem in my case, since when I made the  connection Ubuntu automatically changed the output to spdif (and  properly gave me the option to choose between spdif and analog) and I  could hear everything just fine (more than fine actually, since the  sound was greatly improved!).


  However, what did happen was that the spdif signal was set to 2  Channel Stereo and there is no option whatsoever for multichannel sound  through the spdif output! (while, there is a 5.1-analogue output option,  which I tried while the laptop was connected with the spdif cable and  obviously nothing happened) So even though I played video files with  multichannel sound (6Channel AC3 and DTS) the audio reached the receiver  as 2-Channel PCM. I tried playing the files through different players  (Movie Player, VLC, SMplayer) but nothing changed. 



  So, here's hoping someone could help me figure out whether this is a  software/driver problem (and if so, how and if I could possibly fix it)  or a hardware problem, for instance that, maybe, my sound card can  output spdif but only for 2Ch. Audio (which would be weird but possible I  guess) and in which case, I suppose, I can't do much more than accept  my defeat!


  Thanks in advance to anyone that answers! :)

---

### Post by BicyclerBoy on 2013-02-02
Multi-channel over S/PDIF is a AC3 or DTS bit-stream & not just more channels of PCM. S/PDIF is bandwidth limited.

AC3/DTS bitstream pass-thru' (excepting a52 encoder plugin) has to be invoked by the media player & supported by audio device.

Alsa is okay & recent pulse audio should be okay.
To configure pulse audio to handle iec958 pass-thru you need to use "pavucontrol" & pulse audio >=1.0.

The best test players are VLC or mplayer.

VLC:
- need to configure the right alsa output device
- select use iec958 output
- need to select AC3/DTS audio track when start playing

Or easier to start from cmd line..
vlc --spdif
vlc --aout alsa --alsa-audio-device=iec958

This might be close guess:
mplayer -ac hwac3,hwdts, -channels 6 -ao alsa:device=iec958

Note: the above do not upmix..stereo is still stereo.

---

