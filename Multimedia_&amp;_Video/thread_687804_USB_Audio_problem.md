---
title: "USB Audio problem"
date: 2008-02-04
forum: Multimedia &amp; Video
---

### Post by wolterh on 2008-02-04
Hi. I use a philips woox sound machine as the sound of my computer.
it plays MP3 alright, but firefox doesn't play any sounds when watching flash videos.
Pidgin DOES play the login/logout sounds as my buddies do.

Also, the OS sounds don't play, like the login and logout sound. I hear nothing.

The driver I downloaded on my windows session for this thing to work was UAC3553B. 
In ubuntu, when I go under the sound preferences, all the sound tests work, except the recording one (we'll fix that one later). But, when I go to system tab, and I click on play in any of the sounds, I get no sound.

---

### Post by wolterh on 2008-02-04
Why Can't Anybody Ever Post One Of My Threads!!!!!!!!!!!?!?!?!?!?!?!?

---

### Post by Sabot on 2008-02-08
Try this

Open a terminal and enter:

```
asoundconf list
```

This gave me the name of my sound card.  In my case it was default.  In the same terminal I entered:

```
asoundconf set-default-card default
```

This command is key because without it I was unable to hear startup sounds and flash in firefox would not play audio through my usb headset. This command also makes skype work correctly.

---

