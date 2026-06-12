---
title: "Xubuntu 11.04 upgrades?"
date: 2011-04-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by loukingjr on 2011-04-24
I've had Xubuntu 11.04 installed for awhile now and normally there would be a number of upgrades daily. I haven't used it for a week or so and suddenly there are no more upgrades. I've tried in the terminal, with the upgrade manager and synaptic. I get no errors, it just says there are no updates. Is Xubuntu 11.04 beta 2 frozen or is something wrong with my setup all of a sudden?

---

### Post by el_koraco on 2011-04-24
maybe there's just nothing to fix :D

---

### Post by loukingjr on 2011-04-24
> **el_koraco said:**
> maybe there's just nothing to fix :D
lol I wish. :)

---

### Post by teachop on 2011-04-24
I got just a few updates this morning, but I don't remember if they were Xubuntu specific or not.  They were simple little things, one was a Gnome documentation package, not sure if that would come with a straight Xubuntu or not, my present install has Ubuntu with Xubuntu-desktop added on top.

---

### Post by KegHead on 2011-04-24
Hi!

Try this:

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo aptitude install linux-image -f

Restart

advise.

KegHead

---

