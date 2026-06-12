---
title: "Need Help with Nvidia Drivers."
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by SikEnCide on 2007-04-11
can i please have a "How To", on how to install my Nvidia Drivers on Edgy.  I have the Nvidia GeForce Go 7300, .. yes im running this on a laptop.  im tired of hte 1024 X 768 stretched wide screen

---

### Post by Rospo Zoppo on 2007-04-11
I think you can use Envy, give a look here [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by stchman on 2007-04-11
> **SikEnCide said:**
> can i please have a "How To", on how to install my Nvidia Drivers on Edgy.  I have the Nvidia GeForce Go 7300, .. yes im running this on a laptop.  im tired of hte 1024 X 768 stretched wide screen

I have a procedure on my website to install either nvidia or ATI drivers.

[http://www.stchman.com/video_drivers.html](http://www.stchman.com/video_drivers.html)

Worked on my PCs with nvidia cards.

---

### Post by SikEnCide on 2007-04-11
thnx i was looking at using envy.. works great

stchman  sorry i didnt use your way.. but its all working now and thats all that matters

---

### Post by Rospo Zoppo on 2007-04-12
Great :D

---

### Post by stchman on 2007-04-19
> **SikEnCide said:**
> thnx i was looking at using envy.. works great

stchman  sorry i didnt use your way.. but its all working now and thats all that matters

No problem.  My main thing is to help people get their Ubuntu install working.  I know how frustrating it can be when your stuff won't work.  I use Envy as well now.  Come back to my site from time to time as I update it.

---

### Post by EddieFudd on 2007-04-19
thanks for the link to envy, installed the driver fine with that but when i do it manually i get an error about x server

---

### Post by Rospo Zoppo on 2007-04-20
> **EddieFudd said:**
> thanks for the link to envy, installed the driver fine with that but when i do it manually i get an error about x server

Maybe you made some mistakes configuring xorg.conf....

---

### Post by stchman on 2007-04-20
> **EddieFudd said:**
> thanks for the link to envy, installed the driver fine with that but when i do it manually i get an error about x server

That is because the auto installation edits your xorg.conf file.  Let it do so.

---

### Post by Huffalump on 2007-04-20
What if you can install the drivers without a problem, but X doesn't work?  You're forced back to specify nv in xorg.conf just to get any GUI at all, but how can you make nvidia work instead?  It's installed, but Feisty is unable to use it.  (It was working just fine in Edgy until the Feisty upgrade.)

---

### Post by stchman on 2007-04-20
> **Huffalump said:**
> What if you can install the drivers without a problem, but X doesn't work?  You're forced back to specify nv in xorg.conf just to get any GUI at all, but how can you make nvidia work instead?  It's installed, but Feisty is unable to use it.  (It was working just fine in Edgy until the Feisty upgrade.)

I have very limited exposure to Feisty.  My procedures on my website work on Edgy.  I have a feeling that Feisty will have some teething pains for a little while.  You can try Envy, but I don't believe Albeto had tested it with Feisty as of yet.

In Edgy when you upgraded the drivers to the nvidia proprietary driver then putting "nvidia" in the xorg,conf would run them.

This is the reason I am going to stick with Edgy right now.  I have working installations on all my PCs.  Maybe in a month or so when Feisty gets a few patches under its belt will I try it.  All my hardware seems to work very well under Edgy.

You might want to try a clean install of Feisty.

---

### Post by Rospo Zoppo on 2007-04-21
On Milone's blog he says that Envy works with feisty too >  Package for Ubuntu Feisty Fawn 7.04 and Ubuntu Edgy Eft 6.10

envy_0.9.2-0ubuntu1_all.deb      [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by SikEnCide on 2007-04-22
just a note.. i didnt need to install any other drivers.. feisty  found what it needed and when i installed beryl it worked flawlessly

---

### Post by stchman on 2007-04-22
> **Rospo Zoppo said:**
> On Milone's blog he says that Envy works with feisty too       [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

Yes, in unstable form.

---

### Post by Rospo Zoppo on 2007-04-23
> **stchman said:**
> Yes, in unstable form.

Of  course...

---

### Post by SikEnCide on 2007-04-23
just a note... when i tried to install envy i had a problem..

on the otehr hand ubuntu found the driver it needed and it works fine.. as i am running beryl flawlessly.

---

### Post by Rospo Zoppo on 2007-04-24
So? :D It's good isn't it?

---

### Post by SikEnCide on 2007-04-25
i didnt use envy for it... but i love beryl.. and feisty.. i dont notice to much of a difference. it does come with 2 compize options tho

---

### Post by Rospo Zoppo on 2007-04-26
Yeah, cube and wobbly right?

---

### Post by Tanker Bob on 2007-04-26
> **Huffalump said:**
> What if you can install the drivers without a problem, but X doesn't work?  You're forced back to specify nv in xorg.conf just to get any GUI at all, but how can you make nvidia work instead?  It's installed, but Feisty is unable to use it.  (It was working just fine in Edgy until the Feisty upgrade.)
How did you install the drivers?  I found that using the repository didn't work for me.  I successfully installed directly from NVidia's driver download.  Envy 0.9.2 (linked in an earlier post here) also works quite well.  Envy is usually my first choice for installing video drivers.

If Envy doesn't work the first time, run it again and tell it to remove the driver first, restart your PC, then use Envy to install it.  It may also be helpful to uninstall the repository version before using Envy--i.e., start clean.

---

### Post by SikEnCide on 2007-04-26
it has wobbly windows.. and that basically it.. a transition btwn workspace no cube with regular feisty

---

### Post by Huffalump on 2007-05-25
> **Tanker Bob said:**
> How did you install the drivers?  I found that using the repository didn't work for me.  I successfully installed directly from NVidia's driver download.  Envy 0.9.2 (linked in an earlier post here) also works quite well.  Envy is usually my first choice for installing video drivers.

If Envy doesn't work the first time, run it again and tell it to remove the driver first, restart your PC, then use Envy to install it.  It may also be helpful to uninstall the repository version before using Envy--i.e., start clean.

Thanks, I'll give things another try.

Originally, I installed Edgy some months ago and got nVidia installed via Envy as well as had Beryl working without much trouble at all (thanks to help on the IRC channel).  Later, I upgraded to Feisty and that's when things went wrong.  In the end, I had to throw everything away and go through the pain of starting new with a clean install of Feisty much to my dismay.  Now, I'm sitting on a clean install but unable to get the nVidia acceleration to work (no Beryl, no games, etc).

[B]
UPDATE[/B]: I just tried again (with an updated nvidia-glx module) and it still fails to work. X won't load, gives the same old error, and dumps me to a terminal.  I have to use nano to edit the config file manually just to get back to "nv" and have a basic desktop functional.

---

### Post by SikEnCide on 2007-05-27
try installing envy again... also make sure the restricted drivers are enabled

---

