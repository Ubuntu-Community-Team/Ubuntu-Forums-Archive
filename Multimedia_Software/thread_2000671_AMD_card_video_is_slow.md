---
title: "AMD card video is slow"
date: 2012-06-09
forum: Multimedia Software
---

### Post by coleix on 2012-06-09
Guys I have a couple of problems, thought someone might give me a hand. I'm using **x64 12.04**, my gpu is an **AMD 6950** and an** intel 4600k** cpu, I have **fglrx** installed but I don't know if it's 64bit, any other info you need let me know.

The **videos** (HD or SD) **look **kinda **slow**, watchable but it bothers me, I have tried using smplayer and the default video player so or it's video supposed to look like this on ubuntu or is a problem with **drivers(?)**, in 11.10 i also had the slowish video it bothered me but I tryed to fix it a couple of times but gave out after 2 weeks of irc chat with a couple of suggestions that didn't work.

Other 2 problems I have that I think are related to this but that I didn't have on 11.10 are (1) **Audio through HDMI** doens't get recognized every time the tv turns of because of inactivity so I have to physically unplug the hdmi and reconnect it so it gets recognized again on the audio out configuration. (2) On** youtube** the** videos** look a little slow too but the main problem is when I pause the videos so they buffer the audio keeps playing and at times when I hit play again I have two audios, could this be flash player's problem (couldn't find a 64bit version) instead of AMD drivers?

Hope someone can give me a hand, thanks.

---

### Post by lavinog on 2012-06-10
There are known issues with the 12-4 fglrx driver.
The 12-6 driver should be released shortly and is supposed to bring some fixes for ubuntu 12.04.

I am not sure if the standard fglrx driver will be updated automatically though.  I did an dist upgrade and was given to options for fglrx drivers.

can you open a terminal and see what the output is of the following?
```

dmesg|grep 'fglrx 8'

```

```

[   18.226484] [fglrx] module loaded - fglrx 8.96.4 [Mar 12 2012] with 1 minors

```

---

### Post by lavinog on 2012-06-10
Info about 12.6: [http://www.phoronix.com/scan.php?page=news_item&px=MTExMTU](http://www.phoronix.com/scan.php?page=news_item&px=MTExMTU)

---

### Post by coleix on 2012-06-10
Umm, so you mean this audio issue is unfix able on the moment? I'll have to wait then but I hope it fixes both problems, do you think the youtube audio is related to it thought?
Thanks for the help and I expect is gonna be released soon, from the support steam is giving linux it should help motivate them a little more. :)
The output of the command is mostly what you expected:
```
[   15.680679] [fglrx] module loaded - fglrx 8.96.4 [Mar 12 2012] with 1 minors
```

---

