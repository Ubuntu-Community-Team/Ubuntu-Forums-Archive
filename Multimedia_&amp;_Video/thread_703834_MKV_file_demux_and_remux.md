---
title: "MKV file demux and remux"
date: 2008-02-21
forum: Multimedia &amp; Video
---

### Post by truxntrax on 2008-02-21
I am trying to accomplish the following:

I have a couple of .mkv files that have dts encoded audio.   I have no dts amp/ tv to decode the audio so when I watch them using my media extender I cannot here any audio.

I want to be abe to demux the MKV file.  Seperate the audio, convert the audio to an analogue (AC3 probably) format then remux back into the .mkv file. 

I have been trying to research this but now need some help.  I think I should be able to use mkvextract and mkvmerge to do the demux then the remux.  And possible be able to use neroaacenc to convert the audio or perhaps mencoder.

I am very new to ubuntu so would appreciate if anyone can help guide me to the correct tools.  I can work my way throw terminal with a howto or figure out how to use easier wih a gui.

Ifr anyone has alrady achieved these steps any howto's would be much appreciated.  Ideally I would like to acheive a script that would allow the source file to be selected, the conversion to happen and a destination file to be produced (without re-encoding any video).

O/S = Gutsy.

Many thanks for any help.

trux

---

### Post by gsmanners on 2008-02-21
If you have mkvtoolnix-gui installed from the repos, that will give you a couple GUI apps (mkvinfo-gui and mmg) for information and merging.

Using mkvextract is pretty simple:

mkvextract tracks movie.mkv 3:audio.dts

Use something like the above if the DTS is in track 3. Converting DTS is tricky. I'm not sure about that one.

---

### Post by disturbedite on 2008-02-21
avidemux can prolly do this.

also, mkvmerge prolly can as well & may be more of what you're looking for.

---

### Post by truxntrax on 2008-02-22
Thanks both I will try these apps tonight and report back success.  Thanks so much for the suggestions.

Trux

---

### Post by truxntrax on 2008-02-23
Hey guys thanks for your help - the tools I used are mkvmerge, mkvextract and afect.   I ended up getting some help from another forum (network media tank) and used the following script.  It works a treat - so hopefully someone elxe will be able to use it to help convert .mkv file with dts audio to mkv files with ac3 audio.

Thanks all

Trux

#!/bin/sh 
 NAME=$(basename ${1%.*}) 
 DTSFILE="$NAME.audio.dts" 
 WAVFILE="$NAME.audio.wav" 
 AC3FILE="$NAME.audio.ac3" 
 MKVFILE="$NAME.ac3.mkv" 
 
 DTSTRACK=$(mkvmerge -i "$1" | grep audio | cut -d: -f1 | cut -d" " -f3) 
 
 mkvextract tracks "$1" $DTSTRACK:"$DTSFILE" 
 
 mplayer -channels 6 -quiet -vo null -vc null -ao pcm:waveheader:file="$WAVFILE" "$DTSFILE" 
 
 aften "$WAVFILE" "$AC3FILE" 
 
 mkvmerge -o "$MKVFILE" -A "$1" "$AC3FILE" 
 
 rm "$DTSFILE" "$AC3FILE" "$WAVFILE"

---

