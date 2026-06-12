---
title: "Gnome Volume control (and keyboard shortcuts) not controlling sound"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by quagz1 on 2007-11-07
Hi all,

Just dropping a quick line to inform you that I was experiencing volume control problems with Gnome and my HDA Alsa onboard sound card.

A particular problem was that I couldn't control my Rhythmbox volume (once at uni I unplugged my headphones and gave everyone a listen to my pink floyd cd for about 1 min whilest figuring out how to mute without shortcut keys ><).

In order to get the keyboard shortcuts to control the actual sound I:

* Went into alsamixer and set the PCM and front volumes to full
* Opened the gnome sound panel and set all options ALSA
* Selected (by holding ctrl) PCM and front mixer tracks 
* Clicked close and everything worked fine

Hope that helps anybody who is having any similar troubles.

---

### Post by gterzb on 2007-11-07
Thank YOOOOOOOOOOOOOOOU!

It works well noW!

some info. about my laptop as following

hp compaq v3239, amd64(2.0),80G.

I wish it would be helpful for others:guitar:

---

### Post by quagz1 on 2007-11-07
Glad it helped.

I should also mention I'm using an LG F1-PRO Express Dual laptop.

---

### Post by talking_walnut on 2007-11-08
Thanks man. Helped me get my keyboard shortcuts working on the PCM control as opposed to just the front speakers on my desktop. A minor annoyance but a welcome solution :)

---

### Post by High_Yield on 2008-01-14
Well for me here's the details...

My shortcut keys worked fine for next/back, volume up/down and mute.  I do NOT have a fancy multimedia keyboard - just a regular one.

I ran a system update a few days ago around the 10th of January, 2008????

Now today I'm playing music in Rhythmbox and next back shortcuts work, but not volume or mute - strange...

I can see the volume control go up and down in the middle of my screen when I press the keys - so the actual key mapping appears to work - but still no volume change.

So I found this posting and simply went into the sound preferences link (ubuntu Gutsy), clicked test on a few items, exited, and voila - it works now - volume, mute, etc. work like a charm again.

Very strange but I hope this helps somebody.

- B

---

### Post by zeddock on 2008-02-07
Yippeeeee!

That is some sorta bug!

But your suggestion worked!
zeddock

---

