---
title: "Banshee freezes"
date: 2010-10-15
forum: Multimedia Software
---

### Post by grantmeaname on 2010-10-15
I'm running Ubuntu 10.10 (AMD64), and I use banshee as my media player. Before my update and for the first few days after my update to 10.10, it worked fine. Yesterday, upon launch, it began freezing up as soon as I clicked anywhere inside the user interface or hit any key that it reacted to (enter, spacebar, etc.). I reinstalled it with synaptic, and it worked fine until this morning. It did the same thing, so I searched around for a solution.

I found [this one]("https://lists.ubuntu.com/archives/ubuntu-mono/2010-September/026562.html"), and though my banshee --debug results were not the same, I tried it. It fixed it, or so I thought. I can now select a song, and it will play it, but within one or two actions after that the UI will freeze up (the music continues playing and will even switch tracks and continue).

What do I try now?

P.S. I've attached the results of me starting up banshee, picking a song, and then switching the song.

---

### Post by !nkubus on 2010-10-15
I have the same issue. I had to switch to another player. The problem is because Maverick use the new version of sqlite 3.7.2 which causes the issue

In the meantime Quodlibet is a great replacement :)

---

### Post by directhex on 2010-10-15
Do you have any addins enabled like Mirage? I think the worst of the SQlite 3.7.0 hell was worked around in the main Banshee, but I don't know if all addins which make heavy database usage were also altered

---

### Post by !nkubus on 2010-10-15
I only use the default plugins and removed anything podcast and music store.

---

### Post by grantmeaname on 2010-10-17
I did the same.

---

### Post by directhex on 2010-10-18
Hm. Talk to the folks in #banshee on gimpnet - there are lingering issues with SQlite 3.7.2 which you might be able to help them isolate and fix

---

### Post by poubelle on 2010-10-25
Anyone find a fix? I have the same problem with the same setup.

I was trying Banshee because I could finally update my iPod without using VirtualBox... but while it's worked a few times, it freezes like this at least half the time.

---

