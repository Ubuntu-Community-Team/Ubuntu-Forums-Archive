---
title: "Problems in/with TeamSpeak"
date: 2008-08-10
forum: Multimedia Software
---

### Post by o_portista17 on 2008-08-10
I didn't know where else to put this, sorry if it's in the wrong place...




I'm using Ubuntu 8.10 (intrepid), with teamspeak-client (2.0.32-3ubuntu1), and i have no sound at all...
Sometimes when i start the program, it starts muted, other times, start's normal, but i never have sound.
I can hear myself in the microphone, but no one hears me.

My laptop is an Amilo 1718
here's "lspci"

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)

Help please.

If you need any other kind of info, just let me know.

Thanks in advance

---

### Post by acidy7clan on 2008-08-18
I have Ran Into The same problem but soon realized it was because i was on a Youtube page while trying to use Teamspeak. There is only one fix that i know of to allow you to listen to music/watch Youtube videos/ and talk on Teamspeak all at the same time. You would have to use "aoss" but i don't recommend it because the sound quality is horrible but I will still tell you how to install it and you can try it out. 

*In Terminal Type
```
sudo apt-get install alsa-oss
```

*Then after its finished type this in terminal
```
aoss teamspeak
```
Now every time you want to use teamspeak with other audio programs type that in console and it will work but as i said the quality is horrible.

IF YOU FIND ANOTHER METHOD PLEASE POST IT HERE....

---

### Post by o_portista17 on 2008-08-20
Hello, first off all, thanks for answering, but even that way, i can't get the teamspeak to work properly.
it's kinda bad, that i have to use the other pc that have windows (for games) to use team speak ;<

---

