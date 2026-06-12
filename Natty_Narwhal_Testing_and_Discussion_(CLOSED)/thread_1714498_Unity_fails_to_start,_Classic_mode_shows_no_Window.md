---
title: "Unity fails to start, Classic mode shows no Window border"
date: 2011-03-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by lachild on 2011-03-25
Hey Guys,

Just updated and rebooted.  Found that when I came back from the reboot Unity fails to load and when I select Classic mode I get no window borders and the places menu is unable to open nautils.

Is this happening else where or did I mess up my install?


Attached is a screenshot in classic mode.


Thanks in advance for any assistance,
LaChild

[IMG]content.reliv.com/docs/Screenshot-1.png[/IMG]

---

### Post by VMC on 2011-03-25
Try running "gtk-window-decorator" from a terminal.

---

### Post by lachild on 2011-03-25
Wow.  That was a quick response.  

I tried that command in the terminal and it just sits there.  Does anyone know if there's a log file I can check to try and track down the problem?

---

### Post by lachild on 2011-03-25
Ok I found that if I do a "compiz --replace" the borders come back up.  Now why wouldn't compiz start at login?

---

### Post by cariboo on 2011-03-25
Compiz still crashes on occassion, so it may have started and crashed.

---

### Post by PaulW2U on 2011-03-25
> **lachild said:**
> when I select Classic mode I get no window borders and the places menu is unable to open nautils.

I had a similar problem in as much as every mode was working except Classic. I decided to play around with my compiz settings rather than delete them all. I installed ccsm, CompizConfig Settings Manager and repeatedly changed all my compiz settings one by one. Eventually my window decorations came back as did Alt-F2 which had also stopped working. I now have a stable Classic mode which was not the case two days ago. Presumably my settings had become corrupted and, after extensive changes using ccsm, had become good again.

It might work for you........

---

### Post by lachild on 2011-03-25
Thanks for the help everyone.

It turned out that this problem was self inflicted.  I don't know what I did but creating a new account and moving over my non system files has fixed the problem.

Thanks again,
LaChild

---

### Post by VMC on 2011-03-25
> **lachild said:**
> Wow.  That was a quick response.  

I tried that command in the terminal and it just sits there.  Does anyone know if there's a log file I can check to try and track down the problem?

For some reason  Ithought you were running classic and not unity. Maybe "/usr/bin/compiz-decorator" was a more appropriate response.
Also ccsm is a great tool - look under "effects, Window Declaration".

---

