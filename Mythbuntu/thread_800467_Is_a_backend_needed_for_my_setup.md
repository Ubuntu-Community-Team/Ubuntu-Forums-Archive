---
title: "Is a backend needed for my setup?"
date: 2008-05-19
forum: Mythbuntu
---

### Post by futaihikage on 2008-05-19
I'm not doing the DVR recording with MYTHbuntu, do I still need to setup a mythtv backend and MYSQL? 

Right now I just have Mythbuntu installed and just the frontend role active with all the necessary codecs and plugins installed.

All i want to do I stream videos, music from another ubuntu server that has SAMBA shares, but on the initial configuration of the frontend I get the error "Can't connect to database." which is due to the fact that I'm not running a backend.

Is there a way around this? Or does one NEED to have a backend in order to just get through the setup and get Mythbuntu up and running?

---

### Post by ian dobson on 2008-05-19
Hi,

I would say yes, you need MySQL/Myth-Backend installed. Myth-front relies on being able to communicate with a backend to get it's configuration and "find" available video sources.

Regards
Ian Dobson

---

