---
title: "Listen Music Player 0.5"
date: 2009-03-07
forum: Multimedia Software
---

### Post by old_dope on 2009-03-07
Is there anyway i could configure 'Listen Music Player 0.5' to play an entire cd without stopping? Would appreciate and help or advice. Thanks

---

### Post by Jose Catre-Vandis on 2009-03-07
Have to confess Listen was the first thing I removed when I installed xubuntu.

if you have mplayer installed:

1. Put Audio Cd in your drive
2. open a terminal
3. Type:
```
mplayer cdda://
```

Enjoy your full cd :)

To play in background (you can close the terminal after the command)
```
mplayer cdda:// &
```

To play specific tracks, just specify the number, e.g., to play track 2:

```
mplayer cdda://2
```

or to play tracks 1-4:

```
mplayer cdda://1-4
```

Doesn't answer the question, but gives alternative :)

---

### Post by old_dope on 2009-03-07
Hi Jose
I have also removed Listen Music Player 0.5 and eventually settled for Banshee 1.2.1. Thanks for the reply

---

