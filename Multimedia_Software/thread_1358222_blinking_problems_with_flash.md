---
title: "blinking problems with flash"
date: 2009-12-18
forum: Multimedia Software
---

### Post by Bastien BB on 2009-12-18
Hi everybody,

I am using Ubuntu karmic koala on a few years old dell laptop, and everything works quite fine exepts I can't seem to get some flash based application to run well. 
In games like machinarium or the mmorpg dofus some graphics elements keeps blinking in an annoying way, even though I can run these games on windows xp on the same machine without problems.
Does anyone know what could be the reason for that?

I have got 1 gb of Ram, and my GC is a Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller 

Thanks for the help :)

---

### Post by Grenage on 2009-12-18
x64 or x32, which flash player are you using?

---

### Post by Bastien BB on 2009-12-18
I am using the 32bit version of ubuntu, and shockwave flash 10 r42. I also got the latest version of adobe air with dofus

---

### Post by Grenage on 2009-12-18
Have you tried the non-free (proprietary) flash player from the repositories?

---

### Post by Bastien BB on 2009-12-18
Well, I just installed the flash plugin for firefox and adobe air when asked to. where can I find that non free flash player?

---

### Post by Grenage on 2009-12-18
If you use the GUI package manager, search for *flashplugin*.

---

### Post by Bastien BB on 2009-12-18
I tried both the flashplugin non free package and the adobe flash package listed in synaptic but neither fixed up the blinking/popping elements problem.

---

### Post by Bastien BB on 2009-12-18
Is there a place (or a command) where I can find settings for these plugins?

---

### Post by Grenage on 2009-12-18
Ok, let's try this:

Go to [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
Download the tar file (not the deb)
Extract it (should have libflashplayer.so)
Move it to /usr/lib/firefox/plugins (delete the existing one there)

Any Joy?


P.S: It might even use /usr/lib/mozilla/plugins so throw it in there too (remove any flash stuff already there).

---

### Post by Bastien BB on 2009-12-18
I tried that, but without results. I couldn't find a usr/lib/mozilla rep though, so I just remplaced the one in usr/lib/firefox/plugins

---

### Post by Grenage on 2009-12-18
Oh dear, I do not know what to suggest.  Removing all the flash plugins and packages might be a good place to start, then trying a manual install again?

---

### Post by Bastien BB on 2009-12-18
I guess I might as well try that. But does the applications using flash independentely of the web browser use the same flash plugin than the applications reading the flash embbeded in web pages?

---

### Post by Bastien BB on 2009-12-18
I just removed the proprietary flash plugin in synaptic, but dofus and machinarium still run. (with the same blinking). however flash is disabled in firefox. I guess there these aps use a flash reader located somewhere else.

---

### Post by Grenage on 2009-12-18
I am not sure, but suspect the packages use a link in the firefox plugin folder bacx to the flash files.

---

### Post by Grenage on 2009-12-18
Try this guy's steps:

[http://kevin.vanzonneveld.net/techblog/article/fix_flash_problems_on_ubuntu/](http://kevin.vanzonneveld.net/techblog/article/fix_flash_problems_on_ubuntu/)

---

### Post by Bastien BB on 2009-12-18
Still no better; I wonder if It could come from a bad support of my graphic card causing flash apps to bug like that. Is there a way I could check if my card is well supported?

---

### Post by dentaku65 on 2009-12-18
...or try "my guide"
[http://ubuntuforums.org/showthread.php?t=1346226](http://ubuntuforums.org/showthread.php?t=1346226)
:-)

---

### Post by Bastien BB on 2009-12-18
Actually flash works well in firefox, no problem so far. But I have problems with flash based applications not running in my browser

---

### Post by lovinglinux on 2009-12-18
Removing/Installing flash won't fix it. I'm also experiencing this problem on a notebook with the latest flash from Adobe.

I'm not sure what is causing it, but I guess it could be related to compositing issues (Compiz). It only happens in games.

I'm not sure, but I think I read somewhere that it could be related to pulseaudio.

---

### Post by Bastien BB on 2009-12-18
Is there a way to temporarily disable pulse audio to see if it solves the problem?

---

### Post by saltmore on 2009-12-18
You could remove pulse audio and if that does not help reinstall it.

[http://www.ubuntumini.com/2009/09/fix-most-audio-problems-remove.html](http://www.ubuntumini.com/2009/09/fix-most-audio-problems-remove.html)

---

### Post by Bastien BB on 2009-12-18
I removed pulseaudio and it didn't change anything

---

### Post by saltmore on 2009-12-18
it very well could be one of those flash in Linux quirks. Even though it is much better than it use to be. It is still not quite windows quality. There are a couple of things that have to launch vmware or virtualbox for. :(

---

### Post by Bastien BB on 2009-12-18
Well, playing these game through an emulated environment would slow them down too much on my laptop I think. Guess I'll just wait till flash gets a better support in ubuntu. 
I would have used the xp I installed on another partition but the stupid thing just went down on me because I messed up with the activation procedure :P
Thanks for trying to help me anyway :)

---

### Post by saltmore on 2009-12-18
I would give it a try before wipe an Ubuntu install. Have had really good luck with vmware. Watch netflix, and convert wmv to mp3 all the time in virtual machine np.

---

