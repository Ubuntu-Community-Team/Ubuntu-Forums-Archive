---
title: "how do I convert lossless to .wav?"
date: 2009-06-10
forum: Multimedia Software
---

### Post by NIHrebel on 2009-06-10
How exactly does one convert lets say a shorten file (.shn) or a FLAC file into wave format running Ubuntu?

---

### Post by mc4man on 2009-06-11
For flac I'd just use flac (the package flac

Then simply 

```
flac -d /path/to/[COLOR="Blue"]whatever[/COLOR].flac
   or at a directory prompt
flac -d [COLOR="Blue"]whatever[/COLOR].flac  
   or to convert a folder full of them them (at dir. prompt
flac -d *.flac
```

```
For .shn,  soundKonverter or ffmpeg amomg others would be fine
ffmpeg -i /path/to/[COLOR="Blue"]whatever[/COLOR].flac [COLOR="Blue"]whatever[/COLOR].wav

   or at your folder's directory prompt
for f in *.shn; do ffmpeg -i "$f" "${f%.shn}.wav"; done
```

---

### Post by NIHrebel on 2009-06-11
Sorry if this is a stupid question, I am very new to Linux, how do you get to the folders directory prompt?

---

### Post by NIHrebel on 2009-06-11
I got it to work. But now I have WAVE files that won't play with any media player that I have. I prefer Audacious and it wont play the .wav files.

---

### Post by mc4man on 2009-06-11
> but now I have WAVE files that won't play with any media player that I have. I prefer Audacious and it wont play the .wav files

Wouldn't really know why there, for ex. took a flac, used flac, ffmpeg and soundkonverter to convert (decode) to .wav, all play fine including in audacious

Took a .shn, used ffmpeg, soundkonverter and shntools to convert to .wav, all are fine.

As a small test install sox
```
sudo apt-get install sox
```

Then at a directory prompt for the folder containing an 'unplayable' .wav, go 
```
sox [COLOR="Blue"]whatever[/COLOR].wav [COLOR="Blue"]whatever[/COLOR]-1.wav
```

Then compare the file sizes in the properties of both (if there is a difference it would be 70 bytes), and see if whatever-1.wav works

As far as cd'ing to a folder (directory), there are a couple of 'shortcuts', useful for music folders that may contain spaces, characters, ect.


One is to install nautilus-open-terminal, then after logging out and back in a right click option on a folder will open a terminal at the correct prompt

```
sudo apt-get install nautilus-open-terminal
```

The other is to open a terminal, type cd, press the space bar and drag the folder onto it. Then left click in the terminal to restore focus to it and press 'enter' on the keyboard.

---

### Post by andrew.46 on 2009-06-12
Hi mc4man,

> **mc4man said:**
> As a small test install sox
```
sudo apt-get install sox
```


As a side-note I only really found out the other day it is a great idea perhaps to run:

```
sudo apt-get install sox *libsox-fmt-all*
```

to unlock the full capabilities of SoX although of course this is not required for the conversion that you are demonstrating.

All the best,

Andrew

---

### Post by mc4man on 2009-06-12
> As a side-note I only really found out the other day it is a great idea perhaps to run:.......

Excellent point, i tend to forget that from building sox which is then all inclusive.

(though possibly am leaning towards the idea of, in several cases, of doing new sources as debian package sets, though sox is not one of those cases

---

