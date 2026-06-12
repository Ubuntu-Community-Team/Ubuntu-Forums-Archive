---
title: "zoom virual background goes on the person and not the background."
date: 2024-05-11
forum: Multimedia Software
---

### Post by irv on 2024-05-11
The Visual background in Zoom started putting the background on the person and not the background. I think this started happening in the last Ubuntu update. I tried different versions of Zoom and it does this in all of them.
I was wondering if anyone else was having this same problem. I have an open ticket with Zoom and we have not got the problem solved as of yet.

---

### Post by irv on 2024-05-12
My work-around is to use OBS, set the background and then use a Visual Camera in Zoom until I get this fixed.

---

### Post by irv on 2024-05-13
I got a fix from Zoom support. I ran this command in the terminal.
> rm -rf ~/.cache/zoom && mv ~/.config/zoomus.conf ~/.config/zoomus.conf-old && mv ~/.config/zoom.conf ~/.config/zoom.conf-old && mv ~/.zoom ~/.zoom-old

---

