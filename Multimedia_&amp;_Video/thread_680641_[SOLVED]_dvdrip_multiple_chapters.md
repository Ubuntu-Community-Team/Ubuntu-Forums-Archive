---
title: "[SOLVED] dvd::rip multiple chapters"
date: 2008-01-28
forum: Multimedia &amp; Video
---

### Post by aphirst on 2008-01-28
Right. I am having a problem which (just typically) only I have had.

I have the DVDs of ROBOTECH, and I want to make backup AVIs of each episode. However, unlike normal DVDs (one episode per title), this has all 6 episodes in one single title, split up by chapters. Even worse, it isn't as simple as one chapter per episode. Oh no, it's TWO chapters for an episode.

"Who cares" you may think. Well, dvd::rip doesn't seem to want to do what I want ( :( ) . dvd::rip will only seem to convert full titles to AVIs, or SINGLE chapters (i.e. one chapter to one avi).

Does anyone know of a way to either:

1) Make dvd::rip put TWO chapters into one avi

or

2) re-author my dvd-backup (I used ripit4me through a script I made that fixes a problem with it, so the backup on my HDD is the same format as on the disc), splitting the large 3hr title into 6 2-chapter single-episode titles (which dvd::rip would recognise and convert as I want)

It's just my luck that I want to something awkward and faddy, but a reply within the forseeable future would be nice.

Thanks in advance!

---

### Post by disturbed1 on 2008-01-28
I can't say I'm familar with dvd::rip. I used it quite a while ago, and frankly did not like it :(

Of course, there's a whole slew of other gui's that can do exactly what you want (OGMRip comes to mind), but rather than having to compile this or that, I offer the solution of a simple shell script.

[http://xvidenc.sourceforge.net/](http://xvidenc.sourceforge.net/)

I download/extract the tarball and just run ./xvidenc -1p or -2p or -fq. The problem with going this route, instead of telling the program to split at every chapter, you would have to encode chapter 1+2, then restart the program and encode chapter 3+4.

Other than that, you can instruct PGCEdit to only rip certain chapters with DVDDecrypter, or use IFOEdit and strip out either VOBIDs or CELLIDs. But that would be a bit time consuming ;).

---

### Post by aphirst on 2008-01-28
Well, what a pillock I am.

It just occured to me that DVD Shrink, the Windoze app that Works (Yay.) in Wine, can jiggery-pokery your titles and keep/omit chapters as needed. Job done.

I'm so happy I could cry.

disturbed1: your talk of DVDDecrypter and IFOEdit reminded me of DVDShrink, so THANKS!

*waves small flag of happiness*

*holds spoon*

---

### Post by disturbed1 on 2008-01-28
](*,)

Forgot about reauthor mode. Saved you from trying xvidenc, too bad. If you feel the desire, I'd still check  it out ;)

---

