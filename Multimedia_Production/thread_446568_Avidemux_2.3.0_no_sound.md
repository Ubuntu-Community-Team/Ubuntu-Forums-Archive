---
title: "Avidemux 2.3.0 no sound"
date: 2007-05-17
forum: Multimedia Production
---

### Post by foxtrotniner on 2007-05-17
Hi. I currently have Avidemux 2.3.0 installed on Ubuntu 7.04. I'm getting an error with the audio when opening an AVI file to edit.

This is what gets dumped to CLI when I try:

```
... 
 Editor :Audio streamer initialized
 Audio codec:  MP2-3

** conf updated **

MPInfo:** CANNOT FIND MPEG START CODE**
MPInfo:** CANNOT FIND MPEG START CODE**

 OVR: 31495916 rel:0 lentogo:0 blocklen 4344Grabbed :656
**PKTZ:READ ERROR
**END OF AUDIO STREAM
MPInfo:** CANNOT FIND MPEG START CODE**
**PKTZ:READ ERROR
**END OF AUDIO STREAM
MPInfo:** CANNOT FIND MPEG START CODE**
**PKTZ:READ ERROR
**END OF AUDIO STREAM
Pkt : incoming buffer empty
EditorPacket:Read failed; retrying (were at seg 0sample 738
/ 11966131)
EditorPacket : End of *last* stream
 read failed, end of stream ? 
[Bridge] End of stream
[bridge] No data in 0 max 5512 out 0
No accel used for rendering
[mpeg4 @ 0x85e26f4]frame skip 8
Probably pseudo black frame...
EditorPacket:Read failed; retrying (were at seg 0sample 738
/ 11966131)
EditorPacket : End of *last* stream
 read failed, end of stream ? 
[Bridge] End of stream
[bridge] No data in 0 max 2910 out 0

```

I've been searching for an answer to the problem for the past few hours but nothing turned up. I hope someone can help me. 

Thank you in advance!

---

