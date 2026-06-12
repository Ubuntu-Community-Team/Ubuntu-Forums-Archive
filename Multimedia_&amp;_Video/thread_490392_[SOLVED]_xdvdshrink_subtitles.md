---
title: "[SOLVED] xdvdshrink subtitles"
date: 2007-07-02
forum: Multimedia &amp; Video
---

### Post by paradoxni on 2007-07-02
I like this program, but I am trying to get subtitles to be included, however subtitles are listed as "disabled" and I cannot click on "Select from DVD". If i hit title information it lists 3 subtitle channels available, but how do i select them for my rip?

---

### Post by Terry of Astoria on 2007-07-26
I still have this problem. The title says (solved). Good. So what do I do? 
Any ideas?

---

### Post by supremum on 2007-08-18
you can type 
dvdshrink -u list 
from the console to see the available subtitle stream and then 
dvdshrink -u n 
where n the number of your prefered subtitle stream
Alternatively you can edit the xdvdshrink.pl and change the properties of the subtitle
button of the gui to set it to enable and then choose the subtitle with a simple click

---

### Post by willz06jw on 2007-09-16
> You must edit /usr/bin/xdvdshrink.pl to enable subtitles:

1)sudo gedit /usr/bin/xdvdshrink.pl
2) Go to line 969 and change
if ( qx/subtitle2pgm -h 2>&1/ !~ /-X/ ) {
to this
if ( qx/subtitle2pgm -h 2>&1/ !~ // ) {

I had the same problem and this was the only solution I found.

mcrosmar gave this advice (in 2005).

This worked for me.  I hope this helps. :guitar:
Willz06jw

---

