---
title: "Faulty Jpeg rendering on Gutsy"
date: 2008-06-19
forum: Multimedia Software
---

### Post by adpsimpson on 2008-06-19
Hi all, have tried searching for this but can't find anything. Jpeg rendering is odd across the platform - jpeg artifacts are being rendered as black blocks. Happening both in Firefox and EOG - see screenshots at the links [_here_]("http://img508.imageshack.us/img508/128/screenshotic2.png") (see the phone) and [_here_]("http://img107.imageshack.us/img107/7233/screenshot1pp1.png").

Running Ubuntu Gutsy on my desktop machine, and jpeg rendering seems broken after some recent updates. Afraid I don't know which update - I've not used the machine much recently and ran about 200MB of updates yesterday.

Graphics:
$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]

Don't know if this is just a display issue - converting a good .png image to .jpg using imagemagik creates the artifacts, converting back to .png APPARENTLY leaves them there on the .png but viewed on another (good) computer BOTH images are good.

---

