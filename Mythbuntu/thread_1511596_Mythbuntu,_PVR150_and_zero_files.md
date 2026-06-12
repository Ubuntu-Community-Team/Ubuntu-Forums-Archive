---
title: "Mythbuntu, PVR150 and zero files"
date: 2010-06-17
forum: Mythbuntu
---

### Post by Furry_Fighter_20x66 on 2010-06-17
Hi everyone.

I am posting this as an answer for anyone having this similar problem. After two days of hunting through forums for clues I was still left baffled until I came across the solution to a unique problem I encountered.

Here's the situation:
I did a fresh install of Mythbuntu onto my backend server. It has a Hauppauge PVR-150. No hardware was changed from the previous version (9.04) to 10.04 and after copying over the files for Lirc to control my ShawDirect dish receiver, everything seemed to be set up perfectly. The dish channel changed and everything was going great, or so I thought. Instead of recording, the computer made an empty file and aborted. The logs had only listed the following:
> MPEGRec(/dev/video0) Error: Failed to start recording
                        eno: Input/output error (5)
ProgramInfo(1536_20100616104556.mpg), Error: Unknown type, recording width was 0

Not a very useful clue. But I finally found my answer. I changed the video card. It worked perfectly then. I plugged the old one back in and fiddled with IRQ assignments and the problem returned even with different IRQ settings. So a video card later, the mythbox is happily recording my shows again. 

The old card was an Intel i815 chipset.

Hope this helps anyone else who finds themselves troubleshooting. Don't hesitate to swap out the video card if all else fails.

---

