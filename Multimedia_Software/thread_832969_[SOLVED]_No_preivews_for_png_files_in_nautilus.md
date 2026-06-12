---
title: "[SOLVED] No preivews for png files in nautilus"
date: 2008-06-18
forum: Multimedia Software
---

### Post by stinkinrich88 on 2008-06-18
Hello,

Nautilus does not show previews for my png files on my desktop or in my file browser. I've found one example where it does, and the mime type for this image is the same as the others: application/x-extension-png. 

Preview or not, gThumb cannot save any png files in another location. If I open a png file with gThumb it displays fine but if I SaveAs to a different location is says:

> Image type not supported: application/x-extension-png

Thanks, 
Rich

---

### Post by stinkinrich88 on 2008-06-18
FIIIIIXXXXXEEEDDD!!

Rich, dude, just delete these folders:

~./thumbnails
~/.local/share/mime

That'll also sort out all the other problems you had with video thumbnails etc.

---

