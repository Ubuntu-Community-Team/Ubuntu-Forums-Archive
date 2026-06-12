---
title: "maximize ati big desktop to 1 monitor no maximiz  to dual monitors spanning acrorss"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by twizler on 2007-10-27
FIX ati big desktop maximize to only one monitor.  no max spanning on dual-head ati or dual-monitor maximize issue resolved.
My dual-head ati card annoyance
(card x1300 ati)
Screen window would maximize on both monitors HUGE.
(answer was found [http://ubuntuforums.org/showthread.php?t=301941&highlight=dual-head+maximize](http://ubuntuforums.org/showthread.php?t=301941&highlight=dual-head+maximize)) 
[COLOR="Red"][SIZE="5"]The fix was so simple it makes me mad... searched for days ...so i did a how to[/SIZE][/COLOR]
> 
Use this command to find out what is connectd ...in my case 2 LCD monitors
 crt1 and crt2. 
[QUOTE]sudo aticonfig --query-monitor[/QUOTE]> If you are running compiz already with ati big desktop ...and when you do aticonfig you get
[COLOR="Blue"]Connected monitor none
Enabled monitors: none[/COLOR]
 in terminal.
[QUOTE][COLOR="Blue"]export Display=:0[/COLOR]
[/QUOTE]
OUTPUT --
Connected monitors: crt1, crt2
Enabled monitors: crt1, crt2
[COLOR="Blue"]READ THIS PAGE for other setups you may not have crt1,crt2
[http://ubuntuforums.org/showthread.php?t=301941&highlight=dual-head+maximize](http://ubuntuforums.org/showthread.php?t=301941&highlight=dual-head+maximize)
This tells me that ati thinks i have to monitors ... crt1 and crt2[/COLOR]
[SIZE="5"][COLOR="Red"]THE COMMAND THAT MADE IT WORK.[/COLOR][/SIZE]
> sudo aticonfig --enable-monitor=crt1,crt2
This made my one monitor go black and bounced me out of big desktop in cloned mode.
I then did the restart xorg.conf file command that got me back to the login screen.
Quote:
> CTRL+ALT+BACKSPACE
Quote:
> Log out login ubuntu
clicked -->preferences-->resolutions -->display - "LARGE" big desktop mode.
I also changed my workspaces (gnome desktops for compiz cubes to 2
NOW IT WORKS LIKE I WANT IT TO NO MORE maximize on both screens. ( works like a dream)
Now when i use big desktop and maximize a window it goes to the correct size of the monitor i am in .. maximize to size of monitor 1 move screen over to monitor 2 hit maximize and it maximizes to mon2. NOT both.
__________________
Edit/Delete Message

---

