---
title: "Tags created with cuetag not readable by EasyTag?"
date: 2009-06-18
forum: Multimedia Software
---

### Post by GabrielWolff on 2009-06-18
I'm splitting an ape file with the help of a cue file with the following command:
```
cuebreakpoints CDImage.cue | shnsplit CDImage.ape
```
The result are many .wav files.
Afterwards I convert them to mp3 and then add tags by running the following command: 
```
cuetag CDImage.cue split-track*.mp3
```
The tags are added, as I can see when checking the properties in nautilus
But when I open the files in EasyTag in order to mass-rename the files the tags are empty.

Does anyone have a clue why?

---

### Post by Tharmas on 2009-11-20
I'm sory, but Icould not reproduce your issue with EasyTag 2.1.6 in Ubuntu 9.04. Do you still have the problem?

---

