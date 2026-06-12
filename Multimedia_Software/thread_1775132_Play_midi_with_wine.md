---
title: "Play midi with wine"
date: 2011-06-04
forum: Multimedia Software
---

### Post by RobertLos on 2011-06-04
For some time I have been trying to get a windows program 'Harmony Assistant' from the French company 'Myriad' to run under ubuntu. First I tried to set it up using a windows installation under virtualbox. That worked for small files but larger files just hang in the playback.
The solution came by installing Harmony Assistant using wine under ubuntu 11.04. The installation went smooth, but no sound. 
The trick is to install timidity as an alsa midi server. This can be done by issuing the following command in a terminal window:

> timidity -iA -Os -B2,8 &

and than start the midi playing program with

> wine [path to midi]\midiprogram.exe

in this case I used 

> wine .wine/drive_c/Program\ Files/Harmony\ Assistant/harmony.exe

Since timidity can use very good sound fonts the output is terrific.

to whom it may concern.

---

