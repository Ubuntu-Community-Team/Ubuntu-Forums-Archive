---
title: "Why is /dev/1394 ONLY readable by root??"
date: 2008-02-29
forum: Multimedia &amp; Video
---

### Post by gilgongo on 2008-02-29
Can anyone tell me why, on a fresh install of Gusty, in the year 2008AD, I have to start up Kino with gksudo so that it can read /dev/1394 to dump video off my camcorder?

It just seems totally strange. I dunno, call me awkward, but if it's my camcorder, why can't I read it?

:confused:

---

### Post by Scarath on 2008-02-29
Weird, tried 'chowning' the device while plugged in? I dont know if it would stay owned by you if you unplugged and plugged it back in again although you would hope so. 
```

sudo chown -R you:you /dev/1394
```

Might work, might not.

---

### Post by gilgongo on 2008-03-01
Nah - tried that already. It works only for that session.

I've had this problem before. Linux seems obsessed with making some devices only readable by root. I can understand this for a server OS, but not a desktop one. I mean, when it comes to a trade-off between me being able to use my own damn video camera compared to some tiny possibility that a script kiddie might find a way to write pr0n to it when it's plugged in is just plain bone-headed.

I've had the same issues with other USB and Firewire media under the last THREE releases of Ubuntu. How do other people manage this? We can't blame newbies for just giving up when they plug in their device, see it available in some cases, but then can't actually use it because they get "permission denied."

Sigh. Makes me want to go on a C++ course just so I can be the first person to solve the Last Great Problem With Linux: stupid permissions on devices.

---

### Post by Scarath on 2008-03-01
You seem a little tense. What desktop environment are you using? Gnome always works for me when I plug in my camera. Could just be your camera isnt supported. If you want to access it quickly I suggest making a launcher on you panel with a command that opens in the terminal. Sort of like /sudo mount /etc/etc /some/place. Then you just type in you password and away you go. If thats not the problem and it's just browsing that you cant do, I suggest trying pcmanfm, you can become root quickly with that and it saves me a lot of time faffing with the terminal while file browsing/editing. 

No real solutions sorry but maybe some work arounds?

---

### Post by gilgongo on 2008-03-01
I'm tense becuase it's just such an uncessary hassle. Would the sky fall in if Ubuntu shipped with /dev/raw1394 world writable?

I'm using a fresh install (as of last week) of Gutsy with Gnome. My camera (Sony DCR-PC110) is supported, and has worked fine since Feisty. I'm just amazed that every time I have to use Kino under Ubuntu to dump video off my camera I have to modify the main menu to start it with gksudo. 

Thanks for your time though. I appreciate it. Maybe one day they'll flick the r bit on raw1394 and I'll be happy.

---

