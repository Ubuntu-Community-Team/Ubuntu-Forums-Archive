---
title: "LIRC is driving me crazy... how do I make apps react?"
date: 2008-12-21
forum: Multimedia Software
---

### Post by Keith_Beef on 2008-12-21
Please, please, please, can somebody help me to understand what is wrong?

I have installed LIRC, and when I run the configuration program from the panel () I can see that LIRC is getting the signals and is interpreting them correctly, but my applications are not reacting as I expect.

I stopped the daemon and restarted it like this:
```
sudo /etc/init.d/lirc stop
sudo lircd -d /dev/lirc0
```
and now some apps react, but not to all events, and some apps just don't react at all.

For example,
[LIST]
[*]gxine reacts to pause, play and stop, but nothing else,
[*]Rhythmbox and Elisa react to nothing
[*]oxine reacts to up, down, left, right and OK, but nothing else (e.g. to volume controls, skip forward or back, etc). :confused:
[/LIST]

How does this work?

K.

---

