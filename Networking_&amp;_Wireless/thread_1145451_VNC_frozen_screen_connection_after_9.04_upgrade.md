---
title: "VNC: frozen screen connection after 9.04 upgrade"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by mobrien118 on 2009-05-01
Hello,

I upgraded 3 (very similar in configuration) machines to Jaunty (oh, and installed one fresh), and only one of them is having this issue:

When I make a VNC connection (from Vino on other Ubuntu or UltraVNC on Windows) the screen appears, but locks. STRANGELY, any input I make to the VNC screen, via mouse or keyboard, is interpreted by the VNC host machine. So if I go clicking and typing things, it does what it normally would, only I am not getting the graphical feedback.

If I drop the connection and re-connect, it will show a new screen, of the current state, but will be locked at that position.

Please note, this happened immediately after upgrading to the stable version of 9.04 on release day. I have another, wlmost identically configured system, that I followed the same procedure for, but it is not afflicted with this problem.

Anyone else having this problem? Any ideas? Maybe 'dpkg-reconfigure'ing some package somewhere? maybe eliminatins some settings file and having it re-created? I am open to all kinds of suggestions.

Thanks!!!

--mobrien118

---

### Post by cybergalvez on 2009-05-01
you're connecting to the 9.04 machine right? if so your affected by the vnc bug that seems to have come with the ubgrade.  I think its actually a bug in X but I'm not sure.  Hopefully there will be a patch out soon as its a big pain right now.

---

### Post by mobrien118 on 2009-05-02
Thanks cybergalvez,

I searched and didn't find any threads about this. Maybe in a different section? Anyone remember where you saw it off hand?

If not, no big deal. I know more about it than I did before and maybe I can find a bug filed for it and if not maybe I will file one.

Thanks,

--mobrien118

---

### Post by jfhopkin on 2009-05-02
For the record, I'm experiencing an identical problem, although using RealVNC client on Windows, and would also be interested in any fix that's been found.

---

### Post by Just_SomeGuy on 2009-05-02
Same problem here.
I'm lucky I didn't mess something up because I didn't realize until I actually went to look at the machine that the mouse and keystrokes.
Oddly enough if the screen is locked and I vnc in it works up until the point where I log in. Then the screen refreshes freeze.

Is there a bug report about this somewhere?

---

### Post by hotstovejer on 2009-05-02
I experience the same thing. It's kinda unnerving. 

Jeremy

---

### Post by jfhopkin on 2009-05-02
I've had to carry on trying to do some work with VNC like that, and it's a case of: type something, quit and reload VNC client, reconnect, and check my typing.  :eek:

---

### Post by bone2006 on 2009-05-02
I just upgraded a system (server side) to ubuntu 9.04 and now I can't control it via VNC.

What's being refreshed isn't being shown on the screen.  The fix is to keep disconnecting after each task and reconnecting.

---

### Post by bone2006 on 2009-05-03
I got it to work by going into the server side of VNC and turning off all visual effects under systems, apperance, visual effects and selecting none.

---

### Post by doas777 on 2009-05-03
I've been unable to use desktop effects on vnc servers consistently back as long as i can remember. just disable them on the target host, and it should work for ya.

good luck

---

### Post by jfhopkin on 2009-05-03
Excellent!  That worked perfectly.  I had turned it all off previously in Hardy and Intrepid as a matter of course, so presumably that setting was overriden during the Jaunty upgrade.

Many thanks.

---

### Post by azzid on 2009-05-04
Seems to be a bug: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126")

---

### Post by cybergalvez on 2009-05-04
I tried the x11vnc server workaround, and then I got hit by the the key sticking problem! this is really a mess

---

### Post by azzid on 2009-05-05
Is there a way to disable desktop-effects from the command line?
I want to use the effects when I am home, but sometimes I just need to use the machine remotely, then it would be a working workaround to ssh into the machine, disable the effects, connect through vnc and then do whatever I need to do.

I could of course use the connect/disconnect-method to do it graphically, but that seems rather cumbersome...

---

### Post by zir0n on 2009-05-19
> **azzid said:**
> Is there a way to disable desktop-effects from the command line?
I want to use the effects when I am home, but sometimes I just need to use the machine remotely, then it would be a working workaround to ssh into the machine, disable the effects, connect through vnc and then do whatever I need to do.

I could of course use the connect/disconnect-method to do it graphically, but that seems rather cumbersome...

I just tried this and it works. VNC into the machine, then open a terminal blindfolded and type ```
metacity --replace
``` hit enter, close the connection and reconnect. It should work and allow the windows to refresh properly. Wish there was a patch for it but this work around is all I can think of.

---

### Post by ALIENDUDE5300 on 2009-05-22
> **mobrien118 said:**
> Hello,

I upgraded 3 (very similar in configuration) machines to Jaunty (oh, and installed one fresh), and only one of them is having this issue:

When I make a VNC connection (from Vino on other Ubuntu or UltraVNC on Windows) the screen appears, but locks. STRANGELY, any input I make to the VNC screen, via mouse or keyboard, is interpreted by the VNC host machine. So if I go clicking and typing things, it does what it normally would, only I am not getting the graphical feedback.

If I drop the connection and re-connect, it will show a new screen, of the current state, but will be locked at that position.

Please note, this happened immediately after upgrading to the stable version of 9.04 on release day. I have another, wlmost identically configured system, that I followed the same procedure for, but it is not afflicted with this problem.

Anyone else having this problem? Any ideas? Maybe 'dpkg-reconfigure'ing some package somewhere? maybe eliminatins some settings file and having it re-created? I am open to all kinds of suggestions.

Thanks!!!

--mobrien118

I am also experiencing this really unusual bug... :( Can't wait for a proper fix.

---

### Post by Kleber on 2009-08-03
> **doas777 said:**
> I've been unable to use desktop effects on vnc servers consistently back as long as i can remember. just disable them on the target host, and it should work for ya.

good luck

It worked here. Thank you

---

### Post by Clarke187 on 2010-01-13
Turning off desktop effects fixed everything.  THanks

---

### Post by HectorG on 2010-02-03
Solution proposed on entry 15 worked for me as well :popcorn:

I wish I wouldn't have to do that as it's pretty annoying.  Is there any alternative vnc server that might be able to handle this problem correctly? Anyone know if a bug report has been submitted with vino?

---

### Post by Tikeb on 2010-04-26
Same problem in 9.10 - I'll disable all the themes for now - thx for the answer :)

---

### Post by jfhopkin on 2010-04-26
The '**metacity --replace**' hack works for me, too, where disabling desktop effects had only been partially effective. But I agree: one shouldn't have to do this sort of thing.

---

### Post by HectorG on 2010-04-26
dont waste your time use x11vnc it just works! Even with compiz! :)

---

### Post by krunge on 2010-04-27
> **HectorG said:**
> dont waste your time use x11vnc it just works! Even with compiz! :)
Yes x11vnc is great ;-)

BTW, there is a recent discussion of this problem here:
[INDENT][http://www.nvnews.net/vbulletin/showthread.php?p=2239566](http://www.nvnews.net/vbulletin/showthread.php?p=2239566)[/INDENT]
The NVIDIA developer suggests that 'compiz --use-root-window' may help.

---

