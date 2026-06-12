---
title: "Lame &amp; LMMS"
date: 2007-12-22
forum: Multimedia &amp; Video
---

### Post by lacandu on 2007-12-22
I Have installed Lame but i cant open it from anywhere, I want to make an icon how can i do this? when i ask whereis lame it tells me that /usr/bin/lame /usr/share/man/man1/lame.1.gz is there now how can i open it?  thank you very much


How can i open any application from terminal i think i know the basi just typing the name but it will not work for lame is there another way?

---

### Post by DirtDawg on 2007-12-22
I believe lame is a command line tool. I'm not familiar with lame, but you would probably enter something like, "lame musicfile.wmv musicfile.mp3". Try 'man lame' or 'lame --help' for more info.

---

### Post by lacandu on 2007-12-22
it does give me the manual but i can't open it still!! im new to linux so please bare with me

---

### Post by DirtDawg on 2007-12-22
Lame does not have a GUI. So to convert musicfile.wmv into musicfile.mp3, you would enter something like 'lame musicfile.wmv musicfile.mp3' into the command line.

Could you please give more detail about what you are trying to accomplish? Are you trying to convert files? If you are trying to convert one kind of music file into another, there is probably an easier way.

You mentioned LMMS, if you're trying to get that started, enter 'lmms' into the command line or try looking in the applications menu under 'Sound and Video'.

EDIT: HA! I just realized "wmv" is not even a sound file. Oh well.

---

### Post by lacandu on 2007-12-22
all i am trying to accomplish is convert files from mp3 to wav so i can import them into lmms? if there is an easier way please let me know. and as im searching i ran across lame to many times it said it was really good

---

### Post by DirtDawg on 2007-12-22
I see. There are two ways I am aware of that will probably be easier. 

Sound Converter is in the repositories and can be found in Applications>Add/Remove or by entering ```
sudo apt-get install soundconverter
```
into the command line. Once you have it, it can be found under Applications>SoundAndVideo. Once it's started, open the file or directory you want to convert, then go into the preferences and under "type of result", click the WAV radio button. I can't remember if it replaces the original file, so you might want to make backups.

The other is "naudilus". This will add a "convert audio" option under "scripts" when you right-click an mp3 (or other) audio file. To get naudilus, close the file browser and enter
```
sudo apt-get install nautilus-script-audio-convert
```
into the command line. Again, you should probably make a backup as I don't know if naudilus overwrites the original file. 

Play with them both. Hopefully one or the other will be what you're looking for.

---

### Post by lacandu on 2007-12-23
Thank you, the first one worked very well!! i would recomend the one is very friendly as well

---

