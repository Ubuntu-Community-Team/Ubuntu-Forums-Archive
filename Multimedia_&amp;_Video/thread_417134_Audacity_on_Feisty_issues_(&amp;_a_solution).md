---
title: "Audacity on Feisty: issues (&amp; a solution?)"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by ratbagradio on 2007-04-21
I had not been able to install Audacity audio editor so it worked on Edgy. Over this last day or so when I upgraded to Feisty there was no resolution of my problems. But it seems I may have solved it for now.

**On the Lame codec**: Audacity demands a file* libmp3lane.so *but it cannot be found. So what I had to do was RENAME the source file so Audacity would link to it for converting files to Mp3. You have to fiddle a bit but it can be done. Just don't let Audacity know about the lie.

But when I went to save my editing work by exporting it either to Wav. Mp3, etc Audacity refused to budge and insisted that it was "unable to target file." This seems to be an occasional Audacity bug from what I read. 

That said my solution was to save each audio file to ***.mp3*** (thats' "dot Mp3")as letters or numbers used for a name won't get you around the stonewalling. . I can label it OK in Audacity's tag editor(and identify the file that way) and once the file is saved I simply visit it  & rename it  --- such as: [I]2000422.mp3.
[/I]

That's my present work around. If anyone has a better way of using Audacity ghiven these frustrating issues  I'm all ears.

---

### Post by mahiyar on 2007-04-28
If you can play your mp3 files some encoder is in your lib file. The trick is to link the file to it. First in the CLI run the command locate libmp3, then after finding the mp3 file link it in audacity, audacity will look for an exact file name however use the closest file you have found.

---

