---
title: "[SOLVED] Best CD burning app?"
date: 2008-10-18
forum: Multimedia Software
---

### Post by cybrsaylr on 2008-10-18
Want to burn some audio CDs with Ubuntu.

Looking for the burning program that will show Album titles and show the song title being played like Nero does. Nero was my fave with windozs. 
Which linux app will do this?
Thanks.

---

### Post by wolfen69 on 2008-10-18
K3B probably comes closest to nero.

---

### Post by cybrsaylr on 2008-10-18
OK. 
I opened up K3B and set up a CD to burn.
When I go to add the mp3 files to burn it won't let me and kicks out this error message:

SORRY K3B

!   Problems while adding files to the project.

> Unable to handle the following files due to an unsupported format:
You may manually convert these audio files to wave using another application supporting the audio format and then add the wave files to the K3b project.
/home/tt/.azureus/Documents/Azureus Downloads/Elis & Tom - Elis Regina e Tom Jobim (1974)/01 - Aguas de março.mp3

What's wrong?
Brasero just loads up them same mp3 files, then burns them to CD.

---

### Post by cybrsaylr on 2008-10-18
Got the solution from Ringi:

> In Synaptic Package Manager install:

libk3b2
libk3b2-extracodecs

I installed:
libk3b2-extracodecs

and the mp3 files now load like Brasero.

---

