---
title: "Change pitch and speed of audio files"
date: 2015-08-28
forum: Multimedia Software
---

### Post by palmgrower on 2015-08-28
I have 100+ voice recordings in WAV format. I would like to change pitch and speed. I know I can import individual files into Audacity, change speed and pitch, and export. Doing this over 100 files is a work. I wonder if there is a line command. Thank you.

---

### Post by papibe on 2015-08-28
Hi palmgrower.

You can do an script and use ffmpeg.

Here's a couple of examples:
Reduce speed by half:
```
ffmpeg -i ./input.mp3 -filter:a "atempo:0.5" -vn ./output.mp3
```
Double the speed:
```
ffmpeg -i ./input.mp3 -filter:a "atempo:2.0" -vn ./output.mp3
```
Higher pitch (assuming your audio is 44.1KHz):
```
ffmpeg -i ./input.mp3 -filter:a "asetrate=r=48K" -vn ./output.mp3
```
Lower pitch (assuming your audio is 44.1KHz):
```
ffmpeg -i ./input.mp3 -filter:a "asetrate=r=36K" -vn ./output.mp3
```
Hope it helps. Let us know if you need help with the installation of ffmpeg, or the script itself.
Regards.

---

### Post by palmgrower on 2015-08-28
Thanks for the note. Can I save typing individual file names by dragging the entire folder? If I can, how do I do it?

---

### Post by papibe on 2015-08-28
A script would take care of that.

Something like this would work, but you have to make some tests first to determine the actual ffmpeg command. In other words, you want alter speed and pitch, or only speed, and by how much.
```
#!/bin/bash

SOURCE="/path/to/wavs/"

while read -d '' -r file
do
    newfile="${file/.wav/.mp3}"
    ffmpeg -i "$file" -filter:a "atempo:0.5" -vn -y "$newfile"

done< <(find "$SOURCE" -iname '*.wav' -print0)
```
Let us know if you need more help with that.
Regards.

---

### Post by Rob Sayer on 2015-08-29
Audacity does indeed do batch processing ...

[http://manual.audacityteam.org/man/Chains_-_for_batch_processing_and_effects_automation](http://manual.audacityteam.org/man/Chains_-_for_batch_processing_and_effects_automation)

---

### Post by palmgrower on 2015-08-29
> **papibe said:**
> A script would take care of that.

Something like this would work, but you have to make some tests first to determine the actual ffmpeg command. In other words, you want alter speed and pitch, or only speed, and by how much.
```
#!/bin/bash

SOURCE="/path/to/wavs/"

while read -d '' -r file
do
    newfile="${file/.wav/.mp3}"
    ffmpeg -i "$file" -filter:a "atempo:0.5" -vn -y "$newfile"

done< <(find "$SOURCE" -iname '*.wav' -print0)
```
Let us know if you need more help with that.
Regards.

Name of my folder: NKJV NT
Location of the folder: Desktop
File names: jn1.flac jn2.flac ......... (total 260 files) (WAV files from multiple CDs were converted to FLAC)

Combining your two posts, in order to raise pitch and lower speed,
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
#!/bin/bash

SOURCE="./desktop/NKJV NT"

while read -d '' -r file
do
    newfile="${file/.flac}"
    ffmpeg -i "$file" -filter:a "atempo:0.9" "asetrate=r=49K" -vn -y "$newfile"

done< <(find "$SOURCE" -iname '*.wav' -print0) 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Am I replacing original file with a new file? 
What goes after this? Save it as ? How do I execute it?
What does the last command do?

Thanks.

---

### Post by palmgrower on 2015-08-29
> **Rob Sayer said:**
> Audacity does indeed do batch processing ...

[http://manual.audacityteam.org/man/Chains_-_for_batch_processing_and_effects_automation](http://manual.audacityteam.org/man/Chains_-_for_batch_processing_and_effects_automation)

Thanks a lot. I thought this would be equivalent to writing a macro, creating each key stroke. No, it wasn't. Audio processing cannot be simpler!

For anyone who may be interested, this is what I had to do.

AUDACITY > FILE > EDIT CHAIN
A window with 2 columns appears. 

in the left column, ADD > Name the chain (event) Slower Higher Pitch.

In the right column, INSERT > CHANGE TEMPO (by double clicking) and edit percentage (-10 is 10% slower). Again, INSERT > CHANGE PITCH and edit either half notes or percentage. I chose 2 half notes = 12%. Again, INSERT > EXPORT FLAC . OK

FILE > APPLY CHAIN > FILES > Choose all files > Select safe processing (it creates a new folder for new files. Original files are intact)

So easy. Thanks a lot.

---

