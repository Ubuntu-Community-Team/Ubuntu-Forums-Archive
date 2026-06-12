---
title: "Animated GIFs in GIMP - avoiding loss of quality?"
date: 2009-10-11
forum: Multimedia Software
---

### Post by Gallienus on 2009-10-11
OK, here's my problem - I need to join three animated GIFs so that they will play sequentially in a single GIF.

I opened each GIF in GIMP (I'm using Hardy, so it's GIMP 2.4.5), where they appear as multilayer images, and lifted all the layers from these images and pasted them as new layers in the new (combined) image. Then I save the new image as a GIF, and I am presented with the option of saving the GIF as an animation.

Great - the job is done.

Or so I thought.

The trouble is, there's a severe loss in the picture quality. Many colours are changed, replaced by colours that are similar but not similar enough. Now, I'm aware that GIFs have a 256 colour palette to work with. At first, I assumed this loss in quality was due to the three original GIFs having three different colour palettes, so it was natural that the colour palette of the new combined GIF (limited to 256 colours) would not be able to faithfully reproduce the colours of the three GIFs (3*256 = 768 colours). However, after researching on the net, I have found several references to animated GIFs storing a SEPARATE palette for each frame. So theoretically, there is no reason why my new GIF should have any loss of quality whatsoever, as the original files were already GIFs.

Can anyone suggest where I'm going wrong?

---

