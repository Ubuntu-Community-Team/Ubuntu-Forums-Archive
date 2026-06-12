---
title: "Firefox not working properly"
date: 2009-05-29
forum: Multimedia Software
---

### Post by Wired84 on 2009-05-29
Hi, had a few issues with flash recently, which I have managed to get sorted recently. Everything was working fine then my computer went a bit mad and crashed (think it was caused by adobe air)

Anyway I restarted and firefox would not stay open, kept closing itself
Managed to get round it by opening firefox as su, which is annoying each time. But now the sound has stopped working within the browser.

Any ideas what could be causing this or a way to fix either of the problems??

---

### Post by Wired84 on 2009-05-29
> **Wired84 said:**
> Hi, had a few issues with flash recently, which I have managed to get sorted recently. Everything was working fine then my computer went a bit mad and crashed (think it was caused by adobe air)

Anyway I restarted and firefox would not stay open, kept closing itself
Managed to get round it by opening firefox as su, which is annoying each time. But now the sound has stopped working within the browser.

Any ideas what could be causing this or a way to fix either of the problems??

Also getting the error **E: core-util.c: Home directory /home/andy not ours.** when I load firefox through terminal and im using kubuntu 9.04

---

### Post by lovinglinux on 2009-05-29
Using Firefox with sudo will only make things worse.

This is probably an issue with your profile. 

Run Firefox profile manager (without sudo) 

```
firefox -P
```

Create a new profile and start it. If it works, then you might be able to restore some settings from the old profile into the new one, by copying the necessary files from the old profile directory into the new one. Don't copy everything at the same time. Copy a single file each time and start Firefox new profile to see if it works. When it stops working you will know which file is causing the problem.

If you don't need to preserve anything from your old profile, then deleting ~/.mozilla/firefox is the easiest way to fix it.

---

### Post by Wired84 on 2009-05-31
Cheers, seems to have fixed it, just remaking my profile now, removed my old one. The sound is back to normal also. :)

> **lovinglinux said:**
> Using Firefox with sudo will only make things worse.

This is probably an issue with your profile. 

Run Firefox profile manager (without sudo) 

```
firefox -P
```Create a new profile and start it. If it works, then you might be able to restore some settings from the old profile into the new one, by copying the necessary files from the old profile directory into the new one. Don't copy everything at the same time. Copy a single file each time and start Firefox new profile to see if it works. When it stops working you will know which file is causing the problem.

If you don't need to preserve anything from your old profile, then deleting ~/.mozilla/firefox is the easiest way to fix it.

---

### Post by Wired84 on 2009-06-18
Right I have reset my profile, but it is still crashing, first time I reset it and added nothing to my profile, then reset it twice more without changing anything. Both times it works for a while, then crashes randomly.

Right now the only way I can get firefox to run is in root :/

Could it be related to adobe air apps atall? When Im using destroytwitter it almost always crashes.
Im considering reinstalling standard ubuntu as much as I love KDE, Kubuntu 9.04 does not seems to be stable atall, unless there is some way I can fix this and make it useable

---

### Post by Wired84 on 2009-06-18
Right I have reset my profile, but it is still crashing, first time I reset it and added nothing to my profile, then reset it twice more without changing anything. Both times it works for a while, then crashes randomly.

Right now the only way I can get firefox to run is in root :/

Could it be related to adobe air apps atall? When Im using destroytwitter it almost always crashes.
Im considering reinstalling standard ubuntu as much as I love KDE, Kubuntu 9.04 does not seems to be stable atall, unless there is some way I can fix this and make it useable

---

### Post by lovinglinux on 2009-07-06
See **Solution** [*[COLOR="Red"]**FOT001**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT001).

---

