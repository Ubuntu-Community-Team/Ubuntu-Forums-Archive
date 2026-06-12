---
title: "libqt4-webkit and xine install"
date: 2010-10-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by forcecore on 2010-10-07
Something is wrong that libqt4-webkit wants to pull xine in but i dont need it ever.

---

### Post by Colonel Kilkenny on 2010-10-07
Just a guess: 
libqt4-webkit is using xine to do <video> and <audio>

So you do need it in order to be able to do what webkit does.

---

### Post by mc4man on 2010-10-07
It depends on phonon and phonon needs a backend. You can choose one other than xine if so desired

---

### Post by forcecore on 2010-10-07
but who was that "brainiac" that included xine, QT4 is independent library and libqtwebkit4 should pull only phonon.

---

### Post by seeker5528 on 2010-10-07
> **forcecore said:**
> but who was that "brainiac" that included xine, QT4 is independent library and libqtwebkit4 should pull only phonon.

Phonon requires a back-end, the Xine backend was always the suggested one. Going forward phonon-vlc will be the one supported backend, how long it takes for the vlc backend to be considered complete and how long it takes for the others to go away is a whole different question.

I've been using the vlc backend and it works for what I do.

Any way you look at it, currently, if you don't want the default backend to be pulled in automatically, you have to select one of the others for installation first.

Later, Seeker

---

