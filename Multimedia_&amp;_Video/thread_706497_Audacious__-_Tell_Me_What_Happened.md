---
title: "Audacious  - Tell Me What Happened?"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by NoVista on 2008-02-24
Version 1.4.5, installed via Synaptic.

Always ran fine, and like it mainly for the allowance of WinAmp type skins.
But now when I go to start it, it won't even come up..
The only error message, via a terminal start, is:
Segmentation fault (core dumped)

I've tried re-installing. Where/how do I begin to locate the problem?

---

### Post by ahaslam on 2008-02-24
What happens if you sudo it?

---

### Post by NoVista on 2008-02-24
Well, I've never had to run it that way, but I tried and I get the same error

---

### Post by Melcar on 2008-02-24
The Audacious package seems to have been updated recently.  Mine runs fine, with a few annoyances (volume level resets every time it's launched).  Did you try purging the package and then re-installing?

sudo apt-get purge audacious

---

### Post by ahaslam on 2008-02-24
That shows that it's neither a permission or config problem. I don't know what to suggest as I've not been on a .deb system for a long time. In my current situation I'd try getting the package from another mirror...

---

### Post by NoVista on 2008-02-24
I've been avoiding a purge because i didn't want to lose my custom settings.
I was hoping I could try repairing.

---

### Post by NoVista on 2008-02-26
I purged it. I manually searched out any trace of it.
I re-booted. I re-installed via Synaptic.
I re-booted.
And when I go to start my nice fresh install, guess what?
Same exact error;   Segmentation fault (core dumped)
Now what's up with that?

---

### Post by jonssoni on 2008-03-26
Have you found any solution for your problem?
I updatet my audacious (source [http://morgoth.free.fr/ubports/#intro](http://morgoth.free.fr/ubports/#intro)) and now version 1.5 says "illegal instruction (core dumped)" when I'm trying to start it.
I tried sudo apt-get purge audacious and then installing again but it didn't help.

Any solutions...?

---

### Post by NoVista on 2008-03-27
I have not found a solution .. ..

---

### Post by publicurinal598 on 2008-04-02
Do you have audacious-crossfade installed? It seems to be broken. I was having the same problem, and a complete removal of that package made audacious play nice again.

---

### Post by Kyllerss on 2008-04-21
Removing crossfade worked for me. Thanks!

---

### Post by Grove on 2008-04-26
same here... ty vm

god speed,
G

---

### Post by legalizemeth on 2008-04-27
> **Kyllerss said:**
> Removing crossfade worked for me. Thanks!

That worked for me too.  Thanks!

---

