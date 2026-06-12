---
title: "ATI 7500 TV-out?"
date: 2007-10-24
forum: Mythbuntu
---

### Post by isecore on 2007-10-24
Alright, trying to setup Mythbuntu on one of the older machines that me and the girlfriend decided would be fine as a moviecomputer. Mythbuntu fit the bill perfectly, and install went excellent.

But I could really use some help in getting the graphics card to talk to the TV. It's a Radeon 7500 All in Wonder, and I don't really care about the "all in wonder"-stuff as long as I get it to output to TV.

I've found a bunch of different howto's, not a single one manages to coherently explain what's needed. There's no graphical utility, and about the only thing I've managed to deduce so far is that the "ati" driver supports TV-out but the "radeon" doesn't. After that everything stops. I have no idea as to how to make it display on the TV.

This is going to be a machine for watching various media. It's not going to record anything, and I've got it running perfectly EXCEPT for the aforementioned lack of TV-out.

I'm no stranger to the command-line, and every other computer (except for the server, running Debian) in the househould runs regular Ubuntu so I'm not a greenhorn there either. But I would REALLY, REALLY appreciate if someone could point me in the right direction.

---

### Post by superm1 on 2007-10-24
I'm not positive that this code has made it into Ubuntu, but given the date of this article, I would be apt to believe so.

[http://www.phoronix.com/scan.php?page=article&item=806&num=1](http://www.phoronix.com/scan.php?page=article&item=806&num=1)

```

xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600
```

---

### Post by isecore on 2007-10-24
Cool, I'll have to try that out tomorrow. Too late now, tired already and workday tomorrow :)

Thanks for the tip, I appreciate it!

---

### Post by isecore on 2007-10-29
> **superm1 said:**
> I'm not positive that this code has made it into Ubuntu, but given the date of this article, I would be apt to believe so.

[http://www.phoronix.com/scan.php?page=article&item=806&num=1](http://www.phoronix.com/scan.php?page=article&item=806&num=1)

```

xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600
```

Well, I tried it the other day and it didn't work. All it did was cause the output on the TV to momentarily flicker and then it went back to being black. The limit on the resolution (800x600? What is this, 1995?) put a damper on the situation as well. XP runs it easily at 1024x768.

So until I can buy some card with better Linux-support than the ATI 7500 I'll stick to running Windows XP on the htpc. It sucks, I'd really prefer running Mythbuntu but with the current lack of support for TV-out on older ATI cards I'm left with little choice.

---

### Post by superm1 on 2007-10-29
> **isecore said:**
> Well, I tried it the other day and it didn't work. All it did was cause the output on the TV to momentarily flicker and then it went back to being black. The limit on the resolution (800x600? What is this, 1995?) put a damper on the situation as well. XP runs it easily at 1024x768.

So until I can buy some card with better Linux-support than the ATI 7500 I'll stick to running Windows XP on the htpc. It sucks, I'd really prefer running Mythbuntu but with the current lack of support for TV-out on older ATI cards I'm left with little choice.
Well did you try 1024x768?  See if that does anything?  Or even better, information in /var/log/Xorg.0.log about the attempts to switch over.

---

