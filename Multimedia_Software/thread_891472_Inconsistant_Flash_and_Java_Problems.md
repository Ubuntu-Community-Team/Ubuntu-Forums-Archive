---
title: "Inconsistant Flash and Java Problems"
date: 2008-08-16
forum: Multimedia Software
---

### Post by CorvusViridis on 2008-08-16
Hi everyone! So (with lots of help from the people on this forum) I've finally managed to install the flashplayer, and ALMOST everything works. Except (so far), I can't play any of the Daily Show episodes (- full or partial - on [http://www.thedailyshow.com/full-episodes/](http://www.thedailyshow.com/full-episodes/)), and I also can't run the facebook photo uploader. I've tried every step that is recommended in the Sticky Multimedia & Video Guide thread, to no avail.

Any ideas?

(I'm running ubuntu 8.04 on a F-S Amilo AMD 64...).

Thanks!

---

### Post by cozmicharlie on 2008-08-16
I think the problem is the 64 bit - you might want to try this. 
[http://ubuntuforums.org/showthread.php?t=202537&highlight=xmms](http://ubuntuforums.org/showthread.php?t=202537&highlight=xmms)

FYI - I can play the Daily show and I have a 64 bit amd but I installed a 32 bit system rather than the 64 bit.  It just works better.

---

### Post by CorvusViridis on 2008-08-16
Thanks for your help ... I'm still not happy, though :-( I installed the 32bit Firefox and also got the 32bit Java, but when I start the 32bit Firefox and try to watch the daily show, the browser crashes...

---

### Post by cozmicharlie on 2008-08-17
Apparently it is a problem in FF - this thread has a lot of info and maybe something in it will help your situation.  
[http://ubuntuforums.org/showthread.php?t=711080&highlight=firefox+crash](http://ubuntuforums.org/showthread.php?t=711080&highlight=firefox+crash)

This site also has some suggestions - you might try installing the newest version 9.  
[http://tombuntu.com/index.php/2007/06/14/updated-flash-9-beta/](http://tombuntu.com/index.php/2007/06/14/updated-flash-9-beta/)

You might try installing Opera and see if that works for you

If nothing works you can stream though VLC.  This is very simple to do and may be your best solution for now.

I never have any problems playing flash but it appears many do.

---

### Post by CorvusViridis on 2008-08-18
Again thank you, again ... maybe the problem is somewhere else?

So first thing, I upgraded flash player to v10, which was suggested in this thread: [http://ubuntuforums.org/showthread.p...=firefox+crash](http://ubuntuforums.org/showthread.p...=firefox+crash).

-no change.

I installed the VLC-player and the FF-plugin:

-no change

I installed Epiphany and tried that:

-no change

Flashplayer might be running more stable now, but still, the only thing I get from the Daily Show are grey rectangles where the stream is supposed to be. This obviously isn't killing my complete switchover to ubuntu, but still it's annoying ... What am I overlooking?

---

### Post by cozmicharlie on 2008-08-18
I am not sure what you are missing.  It seems to me you have everything installed that should be installed.  

FYI - you probably want to go back to flash 9.  Flash 10 is still beta and you may have more problems. 

I wish I could be of more help but I have run out of ideas.  Hopefully someone will come along that knows more than I do.

---

### Post by andguent on 2008-08-18
Some people are also mentioning the audio support being a possible problem. I'm currently testing the "libflashsupport" package to see if that fixes anything.

[http://ubuntuforums.org/showthread.php?t=888306](http://ubuntuforums.org/showthread.php?t=888306)
[http://ubuntuforums.org/showthread.php?t=889811&page=2](http://ubuntuforums.org/showthread.php?t=889811&page=2)

---

### Post by cozmicharlie on 2008-08-19
To add to those links from andguent you should have a look at this.
[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

---

### Post by Samie_Mazhar on 2008-08-19
hey guys..

i wanted to capture audio from  [here]("http://www.broadjam.com/player/playerhosting.asp?play_file=23373_348912")

Now i have set up the whole recording thing.. using capturing in the sound recorder.. and all.

Now when i go to this website, the FF wont play it.

Can anyone help me with this?

---

### Post by Orlsend on 2008-08-19
BTW Facebook Photo uploader is Java not flash

---

### Post by cozmicharlie on 2008-08-19
> **Samie_Mazhar said:**
> hey guys..

i wanted to capture audio from  [here]("http://www.broadjam.com/player/playerhosting.asp?play_file=23373_348912")

Now i have set up the whole recording thing.. using capturing in the sound recorder.. and all.

Now when i go to this website, the FF wont play it.

Can anyone help me with this?

It is a flash app so do you have flash set up and working?

---

### Post by TygerFish on 2008-08-28
> **CorvusViridis said:**
> Again thank you, again ... maybe the problem is somewhere else?

So first thing, I upgraded flash player to v10, which was suggested in this thread: [http://ubuntuforums.org/showthread.p...=firefox+crash](http://ubuntuforums.org/showthread.p...=firefox+crash).

-no change.

I installed the VLC-player and the FF-plugin:

-no change

I installed Epiphany and tried that:

-no change

Flashplayer might be running more stable now, but still, the only thing I get from the Daily Show are grey rectangles where the stream is supposed to be. This obviously isn't killing my complete switchover to ubuntu, but still it's annoying ... What am I overlooking?

I have the gray rectangles on the Daily Show also!  There are a lot of problems with Flash, but most people on the forums are describing crashes, or a blank "loading" graphic on the Daily Show site.  I'm getting no crashes, just gray boxes, which sounds like what you have.

I also tried upgrading to Flash 10 and although it makes everything else run a lot faster (I can actually use fullscreen!) but, alas, no Daily Show on my 64-bit machine.  My 32-bit laptop plays Daily Show clips just fine, so I'm assuming it's something about the 64-bit system.

Just to confirm: you're also using Firefox 3 on 64-bit Hardy and get the gray boxes on the Daily Show site?  But Flash works okay on every other site?

---

### Post by CorvusViridis on 2008-08-31
> **TygerFish said:**
> Just to confirm: you're also using Firefox 3 on 64-bit Hardy and get the gray boxes on the Daily Show site?  But Flash works okay on every other site?

Yes, exactly. Only grey boxes, using Firefox 3 on 64-bit Hardy. I tried using the 32 bit Firefox 3 on the 64-bit Hardy, but that didn't make a difference; I assume the problem has to be in the 64-bit Hardy and not in 64bitFF3 ... I think there were a couple of other pages that didn't work, but youtube or news sites work just fine.

---

### Post by patrickballeux on 2008-08-31
Have you tried with Gnash as a replacement of the origianl Flash player.  It is getting better with time.

Also, have to tried disabling the acceleration of the flash applet (in the properties when right clicking on a flash applet).  Your video card driver could be related to the problem.

Occasionaly, I have the problem.  I reload the page and the Flash applet will work.  Sometimes, I need to close Firefox completely and then, the Flash applets will work again...  Let's hope for a real 64bits flash version really soon...

---

### Post by reader4 on 2008-10-01
same deal here - grey boxes where video should be. ff3 on hardy-64. not even possible to disable acceleration because the applet is blank - right-click gives the ff3 right-click menu.

---

