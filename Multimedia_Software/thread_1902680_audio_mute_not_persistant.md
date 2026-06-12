---
title: "audio mute not persistant"
date: 2011-12-31
forum: Multimedia Software
---

### Post by netopalis45 on 2011-12-31
Recently on my panp8 with Ubuntu 11.10 the audio mute is not persistent between reboots. I put it on mute before I turn it off but when I turn it back on the sound is turned all the way up. Any idea what is causing this?

---

### Post by MoreOrLess on 2011-12-31
Mute the audio, then run this command before shutting the system down:
```
sudo alsactl store
```

---

### Post by netopalis45 on 2011-12-31
Is this something I will have to do every time I shut down or is it just a one time thing?

---

### Post by MoreOrLess on 2011-12-31
It should be a one-time thing. If it doesn't work, you can also use an amixer command in /etc/rc.local

---

### Post by netopalis45 on 2011-12-31
I tried it twice and it doesn't seem to have worked at all

---

### Post by MoreOrLess on 2011-12-31
Let's try another method. Use amixer to see what controls your card has. Post output if you can't figure out what channel to mute or if you need to use a different card than the default:
```
amixer
```

Edit /etc/rc.local:
```
gksu gedit /etc/rc.local
```
and add your mute command to the end, for example mine is:
```
amixer set PCM 0
```

---

### Post by netopalis45 on 2011-12-31
Added that line and it sets it to the lowest volume setting without putting it on mute. This is passable since I can't hear it. Thanks for the help

---

