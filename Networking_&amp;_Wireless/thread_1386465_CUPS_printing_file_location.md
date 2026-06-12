---
title: "CUPS printing file location?"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by cereal killer on 2010-01-20
I'm trying to print a PDF from Windows through CUPS. I'm guessing it is supposed to appear somewhere on my Ubuntu machine, but I cannot find any files. When I go on the CUPS server and look at "completed jobs", it shows every print that I did, but I have no idea where the file is located.

It is not in my Home directory.

---

### Post by cereal killer on 2010-01-20
Whoops, nevermind, found it.

In case anyone runs into this, the directory I got was: /var/spool/cups-pdf/ANONYMOUS

Any way to edit this directory?

---

### Post by stinger30au on 2010-01-20
theres bug with the cups pdf printer and a bug submitted


there is suppoesed to be off your home directory a directory called

PDF

it is supposed to be created when u install pdf printer, but not


fireup nautils and got to home directory and oyu will see the usual like downloads, music, pictures, 

create a direcotry called
PDF

now hold shift and CTRL and left click 'n drag with mouse to the left window pand and shove it under where it says, music, downloads, pictures etc


now go and print a pdf test page and it will now put it where it is supposed to go

---

### Post by cereal killer on 2010-01-21
Thanks for the help.

I created the PDF forlder, but here is the problem. When i do the "prints" from my Ubuntu computer, they do indeed show up in the PDF folder. However, the majority of these will be done from a Windows XP computer (not dual boot, a separate machine), and all of these show up in only in the directory I posted above. Not only that, but they also can't be deleted.

---

