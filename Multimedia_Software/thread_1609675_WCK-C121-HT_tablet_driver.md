---
title: "WCK-C121-HT tablet driver?"
date: 2010-10-30
forum: Multimedia Software
---

### Post by xixo7 on 2010-10-30
Good day, 

I need help with my tablet WCK-C121-HT
12.1 SLIM TABLET link> [http://www.cdrking.com/index.php?mod=products&type=view&sid=1469&main=68](http://www.cdrking.com/index.php?mod=products&type=view&sid=1469&main=68) 

I can't run it the way I use it in windows please help me to run it please... its a generic brand unlike wacom or genius.It will be nice if you can help me with these :) 

btw I'm using ubuntu 10.10 
Hp G60-441us Notebook pc


I'm a new Ubuntu User and I'm amaze how it run in my laptop
If anyone can help me I will be glad and be thankful to it...


I really want to be a linux user... please help me ...

thanks 

xixo7

[http://xixo7.deviantart.com/](http://xixo7.deviantart.com/)

---

### Post by Favux on 2010-10-30
Hi xixo7,

Welcome to Ubuntu forums!

That looks like it may be the Waltop slim tablet.  Enter in a terminal (Applications > Accessories > Terminal):
```
xinput --list
```
and post the output.

---

### Post by xixo7 on 2010-10-31
[FONT=monospace]jophet@jophet-HP-G60-Notebook-PC:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Slim Tablet      id=10    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; HP Webcam-101                               id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=13    [slave  keyboard (3)]
[/FONT]

---

### Post by xixo7 on 2010-10-31
> **Favux said:**
> Hi xixo7,

Welcome to Ubuntu forums!

That looks like it may be the Waltop slim tablet.  Enter in a terminal (Applications > Accessories > Terminal):
```
xinput --list
```and post the output.


thanks :)

---

### Post by Favux on 2010-10-31
Hi Hi xixo7,

OK, it is a Waltop tablet.  You should be able to set it up on the Wacom driver.  See the Waltop HOW TO:  [http://ubuntuforums.org/showthread.php?t=1595648](http://ubuntuforums.org/showthread.php?t=1595648)

Ask if you have any questions.  Good luck!

---

