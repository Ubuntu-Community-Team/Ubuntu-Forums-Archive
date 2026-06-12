---
title: "I want to loop my audio output back to my skype input"
date: 2008-10-07
forum: Multimedia Software
---

### Post by the_it on 2008-10-07
so that people can hear me playing street fighter. At the same time, I don't want skype's audio output looping back to my audio input, because it'll create feedback.

How do I do this? I am using xmame to play street fighter, and the syntax to get xmame to change sound devices is xmame -ad device... However, there is no syntax listed for the choice of devices int he manual, and even if there was, I don't know how to get xmame to loop back to audio input anyway.

---

### Post by the_it on 2008-10-08
bump

---

### Post by aeiah on 2008-10-08
what you really need is jack. i havent enough experience to give you much more information on it though

[http://jackaudio.org/](http://jackaudio.org/)

its available in the ubuntu repos (or in ubuntu studio repos at least)

---

### Post by markbuntu on 2008-10-08
You could also possibly set up a virtual device in pulseaudio to do that...I am thinking about trying something like that soon. Don't hold your breath though.

---

