---
title: "Exaile Sound Problem"
date: 2010-08-13
forum: Multimedia Software
---

### Post by GaryTheCat on 2010-08-13
Hi

I'm having a strange problem with Exaile - when I play music, the sound appears to 'woosh' or sound a bit like it's under water.

This doesn't seem to be a problem with other players (Banshee and Rythmbox are both fine).

Am I missing a dependency somewhere or doing something else silly?

TIA

G

---

### Post by lidex on 2010-08-14
What plugins do you have enabled? Is this with streaming audio only or also with, say, CD playback?

---

### Post by wizis on 2010-12-05
I've been having the same problem with "underwater" playback in Exaile.  This problem was exactly the same with mp3 and ogg files so it's not a codec problem.  It appears to be bug in the 0.3.1 version of Exaile provided in 10.04.  The bug is fixed in the latest version of Exaile, which can be obtained by adding the ppa:exaile-devel/ppa repository.

---

### Post by wizis on 2010-12-05
Actually, I take back that fix.  When I start Exaile 0.3.2, the play back for the first file is now OK, but any file played after that, including the first file played, has the same problem.

---

### Post by crissi22 on 2010-12-14
I had exactly the same problem. The solution here helped me: [http://www.linuxquestions.org/questions/linux-software-2/exaile-player-no-sound-654782/](http://www.linuxquestions.org/questions/linux-software-2/exaile-player-no-sound-654782/)

Peace.

---

### Post by John Krow on 2011-01-14
Hey thanks that solved my exact same problem too, which for me only started when I installed 0.3.2. :)

Is it anything to do with the Karaoke  plug-in?

---

### Post by sandeepbhat on 2011-07-11
@crissi22 Thanks. The link you posted was life saving. It works !!

---

### Post by Marky FAQ on 2011-07-11
Ubuntu Restricted extras

---

