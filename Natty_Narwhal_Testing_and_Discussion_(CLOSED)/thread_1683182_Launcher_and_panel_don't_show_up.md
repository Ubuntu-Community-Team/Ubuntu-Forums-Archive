---
title: "Launcher and panel don't show up"
date: 2011-02-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Bou on 2011-02-07
Hi,

After being unable to boot the latest versions of Natty for some time, I tried to install today's daily which apparently does work. Partly at least, it boots but there is no way to make the launcher appear. I've tried unchecking the unity plugin in CCSM and checking it again, launching "compiz --replace" and "unity --replace" but I still get no launcher.

I've also tried to use the classic desktop but I don't get any panels either. Have you guys gotten this too? How did you fix it?

---

### Post by dino99 on 2011-02-07
on my system compiz is removed too, so no unity. About the kernel crashes on boot, i have installed linux-crashdump and hope it can collect usefull info to fix that issue. I've seen that the kernel mostly crash while detecting sata and usb, got this morning a trace with compatibility.c. Now with linux-crashdump all these crashes details might be logged, will see later.

---

### Post by Bou on 2011-02-07
> **dino99 said:**
> on my system compiz is removed too, so no unity.

Compiz seems to work here, though. I get window decorations, shadows and transparencies. Only no Unity.

---

### Post by ikt on 2011-02-07
Mine is a bit of hit and miss at the moment, sometimes logging in to Ubuntu Desktop Edition will result in unity, sometimes just the wallpaper is showing.

---

### Post by Peter09 on 2011-02-07
Yes - my unity is also hit and miss - sometimes OK sometimes a blank background with no clickable links. I do find I can control-ALT -F2 into a session and do an update and upgrade from there.

---

### Post by webme on 2011-02-07
> **Bou said:**
> Compiz seems to work here, though. I get window decorations, shadows and transparencies. Only no Unity.
Did you try unity --reset ?

---

### Post by Bou on 2011-02-07
> **webme said:**
> Did you try unity --reset ?

Definitely. Even installed natty on a separate partition, with a fresh /home to make sure I wasn't using any conflicting settings. No use, Unity just won't appear.

---

### Post by dsevastakis on 2011-02-07
did that happen to you after you installed the GPU drivers? if so then i guess that the same thing happened to you as it happened to me.. while you install the drivers (for me it was nvidia) the xorg server gets un-installed so you can't load any UI.. try from terminal mode 

```
sudo apt-get install xorg
```


and then reboot..  you will be able to load UI but you probably won't have the GPU drivers, so no unity, no compiz, blah blah.. 
you can downgrade to ubuntu 10.10 or wait for update to see if it gets fixed.. good luck, hope i was of help:)

---

### Post by savantelite on 2011-02-07
Same problems here. But also under applications when I highlight some apps the icon changes to a different app?

---

