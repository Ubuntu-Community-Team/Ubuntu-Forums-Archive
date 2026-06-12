---
title: "Shipping packaged software for Ubuntu"
date: 2010-05-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by D1986 on 2010-05-30
Hi there.

I would like to develop a game for Ubuntu, and sell it to people in packaged form (by "packaged" I mean in a DVD).

Since I do not want to force users to download patches everytime a new version of Ubuntu rolls out (in order to fix stuff that breaks everytime an API element changes) is there a standard API that I can use? Where can I find documentation for it?

I am asking because Ubuntu has a long history of breaking API stuff every time a new version rolls out. For example, some years ago, ALSA was Ubuntu's 'standard' sound API. Then came pulseaudio, and broke half of the ALSA API and, as a result, any software previous to that version.

So, in order to avoid this, are there any API functions that Canonical is commited not to break in the next versions of Ubuntu? Just like most of Windows's XP API works flawlessly in Vista and Seven?

PS: Please don't start asking me to "open the source". Real money will go to this project, and employees have to be paid. I just want to ship a game, just like I 'll do for Windows. I don't want to start my own open source project.

---

### Post by Longinus00 on 2010-05-30
This isn't the right forum to be asking in. Try "Packaging and Compiling Programs" or maybe "Programming Talk".

---

### Post by cariboo on 2010-05-30
Your best bet would be to build on the LTS versions, as once they are released, you only get bug fixes for the three year lifespan, no new surprises.

This is to general a question to be put in packaging or programming talk.

---

