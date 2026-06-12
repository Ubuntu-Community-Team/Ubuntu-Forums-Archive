---
title: "DVD Authoring"
date: 2007-04-13
forum: Multimedia &amp; Video
---

### Post by Higgo on 2007-04-13
Hello,

I'm trying to work out how to author avi (xvid dvi) files on to dvd. I was using an application called DeVeDe but it lacked the ability to create dvd menu's. I was recommended an app called QDVDAuthor. I don't know how to get it working. I just watched a flash video of how it works I think it's cause my files are in the avi format and not mpeg. Is there a gui app that will help me convert my avi's to mpegs? I googled around and found a command called ffmpeg (or something) but I get lost trying to run it.

Thanks for any help.

Higgo

---

### Post by Syke on 2007-04-13
QDVDAuthor is available through Synaptic. Go to System -> Administration -> Synaptic Package Manager, and search for qdvdauthor. It should be able to import your AVIs.

---

### Post by Metz on 2007-04-13
I started on this last weekend and got ffmpeg working perfectly to convert from avi to mpeg2. Unfortunately, all my code is at home. I'll update this post tonight with the command line that I use.

And BTW....persevere with QDVDAuthor. It may not be a perfectly wrapped up commercial application, but it more than does the job. I'm very pleased with the results of the DVDs I've put together since the weekend :) Be prepared to make a few 'coasters' ;), but you will get your own formats/templates sorted in no time...and then it becomes plain sailing :)

---

### Post by bayvista on 2008-06-05
I am trying to use qdvdauthor and need the Manual.Has anyone tried to print out the Manual? This is what I get:

david@david-desktop:~/programs/qdvdauthor-1.1.0/manual$ sudo make
[sudo] password for david: 
latex -interaction=batchmode qdvdauthor.tex
This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6)
 %&-line parsing enabled.
entering extended mode
make: [tex] Error 1 (ignored)
latex -interaction=batchmode qdvdauthor.tex
This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6)
 %&-line parsing enabled.
entering extended mode
make: [tex] Error 1 (ignored)
 
Making html

latex2html -dir html qdvdauthor.tex
make: latex2html: Command not found
make: *** [html] Error 127
david@david-desktop:~/programs/qdvdauthor-1.1.0/manual$

Any ideas?

OK Problem solved - use DVDSTYLER. It has documentation and it works.

---

