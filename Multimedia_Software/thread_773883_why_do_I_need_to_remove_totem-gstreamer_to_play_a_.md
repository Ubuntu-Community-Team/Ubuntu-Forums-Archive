---
title: "why do I need to remove totem-gstreamer to play a dvd?"
date: 2008-04-29
forum: Multimedia Software
---

### Post by parkejr on 2008-04-29
I've struggled with this in the last few versions of ubuntu. I followed the instructions to get DVD playback working on 8.04, but it still didn't work. I've found in the past that using synaptic to remove totem-gstreamer seems to fix it, but I don't know why? Is there some problem with having totem-gstreamer and totem-xine installed at the same time?

Thanks,

Jeff

---

### Post by duckgoesoink on 2008-04-29
You don't, you can just set totem-xine as default (sudo update-alternatives --config totem).

---

### Post by rphil2008 on 2008-04-30
> **duckgoesoink said:**
> You don't, you can just set totem-xine as default (sudo update-alternatives --config totem).

THANK YOU VERY MUCH!

---

### Post by duckgoesoink on 2008-04-30
> **rphil2008 said:**
> THANK YOU VERY MUCH!

(Someone else on these forums told me that trick just 3 days ago. :-) Very useful.)

---

