---
title: "VNC loads but does not refresh!"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by gnomeout on 2009-12-04
I have had ubuntu for a few years now and I have used VNC as long as I've had it. 

This has always worked by default, I just configure my "Remote Desktop" settings from the main preferences menu. Add a password and bingo, it works. I just have to run vncviewer on my laptop and I can do whatever I want with it. 

Now I have 9.10(clean install) and it does not work. I can still connect to my computer and view the desktop, but if I click or type, the screen does not change, its as though it is frozen. However if I exit and reconnect I can see the changes to my desktop indicating that it at least registered the clicking and typing. The screen is just not refreshing in VNC.

WHAZZUP!??!?!

---

### Post by jonnywombat on 2009-12-04
I think this is due to a bug which means if you have compiz enabled on the remote machine then the viewer will not refresh.

Try disabling compiz on the remote machine.

I believe this is fixed upstream in packages for Lucid.

---

### Post by gnomeout on 2009-12-05
Thats probably it, will repost when I get a chance to try it.

---

### Post by mrgrant on 2009-12-17
Thanks for this chaps. I have tried this and it solves the problems in Ubuntu 9.10. If I stop the effects and put to none, it refreshes OK.

How do you do the updates for this:-
"I believe this is fixed upstream in packages for Lucid"

---

### Post by BrettFace on 2009-12-17
I am running Ubuntu 9.10, and so far have had little issues with vnc until i tried to access one of our computers that has a nvidia graphics card in it. It will open the screen and you can see what is on it, but it does not refresh. It will control the other computer but you just can't see what you are doing. I found another post and the solution has worked for me. 

right click on the desktop, select "Change Desktop Background", click
"Visual Effects", click the "none" option

---

### Post by brianafischer on 2009-12-17
I also would like to know how to fix this.  Currently I cannot use gnome-do since it requires desktop effects.

---

### Post by JetPack on 2010-02-08
I had the same problem but turning off visual effects on the remote machine did not fix it.

Both machines are running Ubuntu 9.10.

I solved it by installing gnome-rdp on the local machine, along with having visual effects on the remote machine turned off.

I like this viewer better than the default viewer and it seems to be faster.

---

### Post by gnomeout on 2010-05-19
I meant to reply earlier, but ya the first solution worked for me. I just turned on the old metacity window manager, and success. Running metacity disables compiz and its effects. 

An easy way to run metacity is to run

```
metacity --replace
```

Or alternatively, I have "fusion-icon" installed and automatically running on startup, which is a useful little tray icon for managing your window managers and decorators. A couple clicks and its changes managers for me.

---

### Post by mrashley on 2010-05-20
I'm really trying to be a good Ubuntu user: report bugs and not make too much of a fuss, but this has really got my undies in a knot.

This has been broken for three versions now! Why the hell isn't this working!?

I want to write someone a tersly worded letter bitterly complaining, but since it's a community effort to make things better I should take a four year programming degree, and then another two or three years apprenticing so that I can spend another year working on the issue that just bursts my eyeballs.

Well I can't, and so here I am just bitching on a forum, where it does no good, and just makes other people feel like crap. So please disregard this message entirely and go on about your day.

EFF!!!

---

### Post by SpyrosB on 2010-06-09
I had this problem with 9.10 and now again with Lucid, is this going to be fixed someday?:-x

---

### Post by hoptimusPrime on 2010-06-16
if you want to keep compiz, try this link (post #2- thanks to jpmorelli):

[http://ubuntuforums.org/showthread.php?t=1496368&highlight=vnc+compiz](http://ubuntuforums.org/showthread.php?t=1496368&highlight=vnc+compiz)

worked for me!

---

### Post by psypher on 2010-06-28
There is a bug report for this: [https://bugs.launchpad.net/xorg-server/+bug/353126](https://bugs.launchpad.net/xorg-server/+bug/353126)

Apparently the latest NVidia binary drivers has patched the problem, I cannot confirm as I have not installed them.

---

### Post by gnomeout on 2010-06-30
> **psypher said:**
> There is a bug report for this: [https://bugs.launchpad.net/xorg-server/+bug/353126](https://bugs.launchpad.net/xorg-server/+bug/353126)

Apparently the latest NVidia binary drivers has patched the problem, I cannot confirm as I have not installed them.

What about ATI??

---

### Post by hoptimusPrime on 2010-06-30
> **psypher said:**
> There is a bug report for this: [https://bugs.launchpad.net/xorg-server/+bug/353126](https://bugs.launchpad.net/xorg-server/+bug/353126)

Apparently the latest NVidia binary drivers has patched the problem, I cannot confirm as I have not installed them.

i have installed driver version **256.35** from Nvidia.

vnc is even slower now, the screen refreshes about every 5 or 10 seconds.  

i have a **GeForce 7100 GS**, maybe i just didn't install the correct driver??

looks like i'm going back to gconf-editor and enabling 'disable_xdamage', for now..

so far this is still the best "fix" for me.

---

### Post by dslink on 2010-07-01
im running latest nvidia drives and it hasn't fixed it.

---

### Post by cosmicharade on 2010-07-11
Argh same here, painstakingly trying to 'remote disable' desktop effects by continually logging in and closing and re-logging in.. is there any easier way?  You'd think even a simple pop up warning would suffice to disable desktop effects if running remote desktop.  Then it would no longer be an issue for the time being.

---

### Post by ikt on 2010-09-22
thank you, what a load of crap this bug is.

---

### Post by KingNewbs on 2010-10-14
> **BrettFace said:**
> I am running Ubuntu 9.10, and so far have had little issues with vnc until i tried to access one of our computers that has a nvidia graphics card in it. It will open the screen and you can see what is on it, but it does not refresh. It will control the other computer but you just can't see what you are doing. I found another post and the solution has worked for me. 

right click on the desktop, select &quot;Change Desktop Background&quot;, click
&quot;Visual Effects&quot;, click the &quot;none&quot; option

Excellent! This solved the problem for me (using Ubuntu 10.04.01). Many thanks! Now I can unplug that power-hungry LCD monitor. :)

---

### Post by UncleFoo on 2011-02-23
> **gnomeout said:**
> I meant to reply earlier, but ya the first solution worked for me. I just turned on the old metacity window manager, and success. Running metacity disables compiz and its effects. 

An easy way to run metacity is to run

```
metacity --replace
```

Or alternatively, I have "fusion-icon" installed and automatically running on startup, which is a useful little tray icon for managing your window managers and decorators. A couple clicks and its changes managers for me.

This worked for me. :D

---

### Post by mausilveira on 2011-07-30
> **KingNewbs said:**
> Excellent! This solved the problem for me (using Ubuntu 10.04.01). Many thanks! Now I can unplug that power-hungry LCD monitor. :)
 
 
Many thanks from me too Kingnewbs! It resolved my problem! Thanks!
 
right click on the desktop, select ;Change Desktop Background; click
;Visual Effects;, click the ;none; option

---

### Post by digitaltruth on 2012-02-29
I have noticed this is an issue while using the fglrx (ATI proprietary drivers). To get around this if you run the ATI Catalyst admin control program and enable the "tear free" option it resolved the issue for me immediately.

---

### Post by onur on 2012-03-28
Hi,
I got the same problem with ATI + ubuntu 11.10.

I installed x11vncserver and access via 5901. now the screen refreshes, and still compiz works.

Cheers

---

