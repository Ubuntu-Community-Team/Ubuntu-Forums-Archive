---
title: "No Sound Juicer in 9.04 - where'd it go?"
date: 2010-02-21
forum: Multimedia Software
---

### Post by kismul on 2010-02-21
Until now, I've been using Rhythmbox for ripping CDs but it is awfully slow.  I noted on a forum thread that Sound Juicer was the thing to use so I decided to give it a try.  I've got an absolutely standard 9.04 Jackalope installation and I've done no tinkering - my skills don't extend to that.  But there's no trace of Sound Juicer under "Applications - Sound and Video" and it's not in the list of options in "Add/Remove".

Can anyone explain what the problem is here and how I can resolve it?

Many thanks.

---

### Post by Robster2 on 2010-02-21
Sound Juicer is in the Synaptic for 9.10

System>Administration>Synaptic

I don't have my 9.04 machine at the moment.

---

### Post by kismul on 2010-02-21
> **Robster2 said:**
> Sound Juicer is in the Synaptic for 9.10

System>Administration>Synaptic

I don't have my 9.04 machine at the moment.

 I checked synaptic and there it was.  A little confused once I'd installed it as it didn't seem to be on the Sound and Video menu.  I was fooled by the odd practice of installing Sound Juicer but, in the menu, calling it "Audio CD Extractor" - a strange world, the lateral world of linux......

Many thanks Robster.

---

### Post by MichaelBurns on 2010-04-13
I can't even find it in Synaptic.  I also tried searching for "sound" and "juice", but didn't see any candidate.  I tried a command-line install with "sudo apt-get install sound-juicer".  I enabled universe and multiverse repos.

What is the name of the package?  Can I use apt-get to install it?

---

### Post by WinterRain on 2010-04-14
> **MichaelBurns said:**
> I can't even find it in Synaptic.  I also tried searching for "sound" and "juice", but didn't see any candidate.  I tried a command-line install with "sudo apt-get install sound-juicer".  I enabled universe and multiverse repos.

What is the name of the package?  Can I use apt-get to install it?

```
sudo apt-get install sound-juicer
```

---

### Post by MichaelBurns on 2010-04-14
Thanks for the reply, WinterRain.  Unfortunately, I'm having trouble to identify the difference between the command that you suggest, and the one that I tried.

EDIT:
*Just for kicks, I tried that command again, and **it worked.**  I think there may be a bug in Synaptic's repo updater.  (I've had similar problems with other packages in the past.)  I'll start a new thread for discussion.*

---

