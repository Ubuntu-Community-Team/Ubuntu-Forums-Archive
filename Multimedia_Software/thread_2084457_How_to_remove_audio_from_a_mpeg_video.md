---
title: "How to remove audio from a mpeg video?"
date: 2012-11-15
forum: Multimedia Software
---

### Post by filborges on 2012-11-15
Hi everyone!

I need to know how to remove or separate the sound file from a mpeg video!!! 

Can anyone help me?

Thanks a lot!

---

### Post by evilsoup on 2012-11-15
You can use the commandline tool, avconv, for this (you'll need to install it, of course):
```
avconv -i input.avi -an -c:v copy output.avi
```To remove video instead:
```
avconv -i input.avi -vn -c:a copy output.avi
```Obivously replace input.avi and output.avi with the input file and whatever the output file is. Make sure the output file has the same extension as the input file (so if the input is .avi, the out put should be .avi; if the input is .mp4, then so should the output). I'm sure there are GUI tools to do this, WinFF is a graphical frontend that is often recommended.

---

### Post by filborges on 2012-11-15
thanks, but doesn't work...

---

### Post by evilsoup on 2012-11-15
If it didn't work, it should have spit up an error somewhere.
Highlight the output text in your terminal and use ctrl+shift+c to copy it, then paste it onto a post here, between [code ][/code] tags.

---

### Post by cybrsaylr on 2012-11-15
Audacity will do that for you.

---

