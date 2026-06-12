---
title: "Xfi no 5.1-7.1 surround with default driver in 9.10"
date: 2009-12-01
forum: Multimedia Software
---

### Post by papalevies on 2009-12-01
Just installed Ubuntu 9.10 and it detects my Xfi Xtreme Gamer out of the box (finally!), but I have 2 problems:

1.I can't play 5.1 or 7.1 surround sound. In movies, I only hear the background music and not the speech. I used "speaker-test -c 8channels" and while I can (barely) hear noise coming out of the side and rear speakers, it has a very low volume. In my Sound Preferences I have set the Hardware to "Analog 7.1 output - Analog mono input". If I use "Analog Stereo output - Analog mono input" I get all the sound, but only from my 2 front speakers. I checked alsamixer but side and rear are unmuted and full.

2.The mic doesn't work at all!

Any suggestions are welcome.

---

### Post by papalevies on 2009-12-02
After some snooping I found out that the "Center/l" option in alsamixer was muted, so I just pressed M and voila! I have 5.1 sound in movies.

EDIT: fixed the mic too. Just write "alsamixer -c 0" in the terminal and UNmuted the Line-In in the PLAYBACK tab. I didn't want to hear my voice so I turned Mic and Line-In all the way down in the Playback tab and turned the Mic all the way up in the Recording tab, so it will still record my voice.

For more info about sound problems check [here]("https://help.ubuntu.com/community/SoundTroubleshooting")

---

