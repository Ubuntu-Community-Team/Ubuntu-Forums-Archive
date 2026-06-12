---
title: "quick mythtv/ ubuntu question"
date: 2008-01-09
forum: Multimedia &amp; Video
---

### Post by kevbuntu on 2008-01-09
I was downloading some programs from the synaptic and clicked on mythtv to check it out. When I installed it, I didnt know I would lose my Ubuntu desktop, I thought it would be a media center feature within Ubuntu/mythbuntu. Now when I start up my pc,(dual boot) and select Ubuntu it goes straight into mythtv. Is there a way I can get back to my Ubuntu desktop? A simple command or something? Thank you for your help.

---

### Post by K.Mandla on 2008-01-09
If you want to get rid of it altogether, you should be able to uninstall mythbuntu either from the command line or through Synaptic. Try

```
sudo aptitude remove --purge mythbuntu-desktop
```
assuming, of course, that it was the *mythbuntu-desktop* package you added. If not, you need to change that name to the proper one.

Does that answer your question? :-k

---

### Post by kevbuntu on 2008-01-09
Hey K.Mandla, thank you for the help, I installed Ubuntu via wubi, basically once I select Ubuntu it boots into mythTv, once in MythTV I am kinda lost, I am trying to find my way back to the desktop. I just don't know how to get out of Mythtv or get back to the synaptic.

---

### Post by kevbuntu on 2008-01-10
opps, I figured out what I did wrong, I installed Myth on the Backend. I wonder if there is a section where I can change the settings to the frontend.

---

