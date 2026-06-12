---
title: "no sound in games, spdif on"
date: 2010-02-05
forum: Mythbuntu
---

### Post by kmallick on 2010-02-05
I am puzzled by this. I am running Mythbuntu 9.10 on a ION 330 motherboard.  I have the set the sound to come out from spdif i.e IEC958, channeled through my receiver.  

I have Mythtv working and there is sound when I am watching Live TV and recordings and when playing CDs, mp3s etc. But there is no sound when I am playing Linux or xmame games, whether inside or outside of Mythtv. :(

I can hear the sound playing games when I connect to the analog jacks. But no sound thru spdif.

Do I need to change anything in the sound setup?

---

### Post by lidex on 2010-02-05
Start here:[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by kmallick on 2010-02-06
Thank you for the link. I followed all suggestions, but still no sound in any Linux games, inside or outside of Mythtv. I also tried running games like Tuxracer and Secret Maryo Chronicles in a console and still no sound. 

I have everything else running on Mythbuntu with sound like Mythtv and XBMC. I am just puzzled as to why there is no sound in games. I have sound connected through optical spdif.

---

### Post by jdk82 on 2010-02-06
I had the same problem, no sound outside of Mythtv, but with different hardware. I solved it by creating a file called ".asoundrc" in my home directory and putting the following in it:

```

pcm.!default {
type plug
slave {
pcm "spdif"
rate 48000
format S16_LE
}
}


```

As always, YMMV. In particular, you may not need the rate and format lines. I needed these due to my particular sound card. The main idea here is to create a default that routes pcm sound through the spdif connector. Someone may be able to give more precise instructions if you list the output from the following commands:

```
aplay -l
```
```
aplay -L
```

These will list the details about your sound card.

Josh

P.S. I'm not sure about your linux proficiency, but note the "." in the ".asoundrc" file name, it is essential.

---

### Post by kmallick on 2010-02-07
> **jdk82 said:**
> I had the same problem, no sound outside of Mythtv, but with different hardware. I solved it by creating a file called ".asoundrc" in my home directory and putting the following in it:
......


Thank you jdk82 for the suggestion. In the meantime I think I have found a solution that works for me. Hopefully this helps someone who is having a problem with sound while playing games. 

To restate my problem, my Mythbuntu box is connected to my sound receiver through optical spdif only. I could hear sound playing everything (LiveTV, Recordings, Movies etc.) in MythTV and XBMC except when playing games.

This is what I did....

I used synaptic to install pulseaudio, including the package padevchooser.

Then I went to Multimedia->PulseAudio Device Chooser This started a PulseAudio applet in the taskbar right next to the clock. I clicked the applet and chose 
Volume Control. I went to Configuration and for Internal Audio I chose Digital Stereo Duplex (IEC958). 

Then, I went to Applications->Multimedia-> Sound Mixer, and for HDA NVidia (Alsa Mixer) I selected the tab Switches, and made sure that both boxes IEC958 and IEC958 PCM are checked. You may also want to check the third switch IEC958 1 if you plan to have sound output by HDMI.

Now I can checked and made sure that I hear sound while playing games from desktop or starting a game from console.

In MythTV and XBMC and I went through Sound settings and chose to output sound through ALSA: spdif and spdif respectively. This is because I only plan to output sound through optical spdif. If you plan to output through HDMI you may want to change these settings. This way, watching LiveTV, Recordings and Movies in MythTV and XBMC have proper 5.1 sound.

Now with this setup, when I access the games through Mythgame (this needs separate setup for Mythgames) I can hear sound. Wooohooo!
:P

---

