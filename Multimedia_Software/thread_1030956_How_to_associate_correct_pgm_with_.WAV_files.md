---
title: "How to associate correct pgm with .WAV files"
date: 2009-01-04
forum: Multimedia Software
---

### Post by kkruecke on 2009-01-04
I have a CD of .WAV files (created under Windows). How I associate the correct audio player, which seems to be RhythmBox, with the file type of .WAV. 
 If I go to Places->Removable Media->Audio Disc, I get an error pop-up that says,
> could not open location 'cdda://scd0/'
Failed to execute child process "soundjuicer" (no such file or directory)

If I go to Places->Computer->Audio Disc, I see the .WAV files listed. But when I double click a .WAV, Totem Move Player starts. But can'tly play the file.  If start RhythmBox, I can play the .WAV files. 

How to get Ubuntu to automatically start the correct player?

---

### Post by kkruecke on 2009-01-05
Using Nautilus, navigate to the .WAV, right click, go to Properties,   Open With tab, choose Rhythm Box.

To get Totem or Mplayer or Gnome Mplayer to successfully play .WAV files burned to a CD using iTunes on Windows, install **sox** .
```
#sudo aptitude install sox
#sox track1-input.wav track1-ouput.wav
```
Totem, Mplayer, Gnome Mplayer (and Rhythm Box) will now all successfully play track1-output.wav.

---

