---
title: "id3 tag 'comment' max length cast in stone?"
date: 2008-07-02
forum: Multimedia Software
---

### Post by larryfroot on 2008-07-02
Hi...I have been faffing around in flash via wine - which works really, really well, btw. Anyhows I have bashed together a streaming mp3 player for a friend of mine. The music is a tad obscure and sung in sanskrit. Now I thought  it would be a fab idea to include info about what each song was about by sucking out id3 comment tag info and placing it after artist and song as it scrolls along. Trouble is, comment seems to accept 30 characters. is this absolutely the limit? Is there any wayy around it using MP3 - I know, flash, mp3 its all as proprietary as Bill Gates loo roll...but if anyone can help I would be really grateful.It would be so elegant,easy and nice if i could just plonk the info in with the id3 tags...thanks in advance for any help rendered.

---

### Post by larryfroot on 2008-07-03
Solved! :) via linuxquestions.org all I had to do was to go into easytags preferences and turn off any id3v1 stuff, untick the convert old id3v2 versions and enable the write id3v2 by checking the box.Result? Unlimited characters in the comments tag. And a full English translation of the sanskrit lyrics available to listeners via xml into flash. All good.

---

