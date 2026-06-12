---
title: "Exaile and bad character range error"
date: 2008-12-02
forum: Multimedia Software
---

### Post by sammy888 on 2008-12-02
Hi. When I want to play some song I get message "bad character range". It is really disturbing, because if I click "OK" (V redu in my language) button the song stops playing. Fortunately this happens only on some songs. How can I fix this problem? I use Ubuntu 8.10.

Here is image of problem: [img]http://www.shrani.si/f/3r/ZN/2IhoeLBu/error.jpg[/img]

---

### Post by farstrider on 2009-01-11
I have the same problem and what I discovered was that in the folder name where the songs are kept, square brackets [song.mp3] cause the problem! Change the square bracket to (song.mp3) and no problem!

This is an example: The Cure - Pornography [1982][320][MP3]causes the problem where:The Cure - Pornography (1982)(320)(MP3) does not! So as you can see this is a bug and needs to be fixed! I am sorry but that's the best I can tell you for the moment!

---

### Post by noomninam on 2009-05-03
I can confirm the square bracket bug theory! Here's the folder that set it off for me:

Steely Dan - Gaucho [MCA-6102] Vinyl 192khz

After replacing the brackets w/ dashes, all is well.:guitar:

---

### Post by fr_eevan on 2009-05-16
That worked for me too! Thanks!

---

### Post by amksep on 2009-06-02
Same problem and the same solution..thx.

---

