---
title: "XMMS Equalizer Not Working"
date: 2008-06-21
forum: Multimedia Software
---

### Post by sidk47 on 2008-06-21
The equalizer is graphically functional but not audibly so. What libraries are required to make the equalizer function? I would be glad to produce more information if asked for it. Please help me make my equalizer work. Thank you.

---

### Post by atomkarinca on 2008-06-21
(Just to make things clear) You turned on the equalizer, right? On the upper left corner of the equalizer window there should be an ON button.

---

### Post by sidk47 on 2008-06-21
> **atomkarinca said:**
> (Just to make things clear) You turned on the equalizer, right? On the upper left corner of the equalizer window there should be an ON button.

Yes, I have had this problem since I installed XMMS, my equalizer has not been working. Just to clarify I have downloaded the XMMS - eq library from Synaptic. Recently I downloaded the .rpm version 0.6 of the equalizer from sound forge, the equalizers don't work no matter what I try. What do you guys recommend?

Umm, sorry, an update, the downloaded equalizer seems to work.

---

### Post by markbuntu on 2008-06-21
remove those packages and get the one in this thread:

[http://ubuntuforums.org/showthread.php?t=765609&highlight=streamtuner](http://ubuntuforums.org/showthread.php?t=765609&highlight=streamtuner)

It worked for me, equalizer and all.

This is xmms right? not xmms2?

---

### Post by sidk47 on 2008-06-22
> **markbuntu said:**
> remove those packages and get the one in this thread:

[http://ubuntuforums.org/showthread.php?t=765609&highlight=streamtuner](http://ubuntuforums.org/showthread.php?t=765609&highlight=streamtuner)

It worked for me, equalizer and all.

This is xmms right? not xmms2?

Yes, it is xmms, I wasn't aware that there was an xmms2, is it better? Where do I get xmms2? By the way isn't installing xmms from Synaptic a better idea?

---

### Post by atomkarinca on 2008-06-22
> **sidk47 said:**
> Yes, it is xmms, I wasn't aware that there was an xmms2, is it better? Where do I get xmms2?

[XMMS2]("http://wiki.xmms2.xmms.se/wiki/Main_Page") is a music daemon like [MPD]("http://www.musicpd.org/"). After you install it you should also get a frontend for that, like Esperanza. They are both in the repositories so you can install it like this:

```
sudo apt-get install xmms2 esperanza
```

> By the way isn't installing xmms from Synaptic a better idea?XMMS's development stopped long time ago so they decided to drop it from the repositories in 8.04. You can try its forks, though. BMP is a fork of XMMS and its development also stopped and now they are working on BMPx:

```
sudo apt-get install bmpx
```Audacious is the most famous fork of XMMS.

```
sudo apt-get install audacious
```

---

### Post by sidk47 on 2008-06-22
OK I have managed to uninstall, and then re-install XMMS from the launchpad.net website as per your suggestions. It works fine now, equalizer and all.

Also thanks for pointing out the alternatives to XMMS, I'll have a look at them later.

---

### Post by sidk47 on 2008-06-22
By the way I'm using Ubuntu 7.10. I know I'm going off topic, but can someone tell me how to play .flac audio files? Also when is firefox 3.0 going to show up on Synaptic?

---

### Post by atomkarinca on 2008-06-22
> **sidk47 said:**
> By the way I'm using Ubuntu 7.10. I know I'm going off topic, but can someone tell me how to play .flac audio files?

As far as I know XMMS can't play .flac files. You can play them with Audacious, though.

> Also when is firefox 3.0 going to show up on Synaptic?

I don't think the final version will be in Gutsy's repos. But you can use [aysiu's howto]("http://www.psychocats.net/ubuntu/firefox#terminal").

---

### Post by sidk47 on 2008-06-22
Thanks all.

---

