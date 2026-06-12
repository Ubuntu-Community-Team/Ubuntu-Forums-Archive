---
title: "No surround  sound"
date: 2008-06-08
forum: Multimedia Software
---

### Post by TerminusEst on 2008-06-08
I've unsuccessfully been trying to get my 5:1 surround sound working since upgrading to hardy, after extensive googling and searching on various forums and blogs, testing dozens of howtos I'm close to giving up :(.

However, I had it working in the alphas (after following some howto) but I lost it in the beta... I'm assuming it has do with an updated kernel?
Right now I'm stuck with just 2 speakers + the subwoofer, the other 3 speakers are quiet. 


Soundcard: nVidia Corporation MCP67 High Definition Audio

Could someone please give me a hand getting this to work? thanks.

---

### Post by Pjotr123 on 2008-06-08
Try this:
[http://ubuntutip.googlepages.com/sound](http://ubuntutip.googlepages.com/sound)

However, a clean installation is always best:
[http://ubuntutip.googlepages.com/upgrading](http://ubuntutip.googlepages.com/upgrading)

---

### Post by TerminusEst on 2008-06-08
Well, that didn't help I'm afraid. The link gives some instructions on specific cards that I don't have, or move the sliders in alsamixer (those don't show up for me). and advising me to wait for a new release (which I shouldn't need to because it worked before).

And yes, it is a clean install already :)

Thanks for trying

---

### Post by issih on 2008-06-08
I'll probably offend your intelligence by suggesting this, but I'll say it anyway :)

If you open up the the volume control by double clicking on the volume icon, then edit the preferences, try enabling the various "audio tracks" one by one, some of them actually provide switches rather than volume controls for different outputs. On my hardware (apple macbook and an nforce 2 box) enabling one of those provided a tick box for 2 channel or 5.1.

Have a look anyway if you haven't already

---

### Post by TerminusEst on 2008-06-08
> **issih said:**
> I'll probably offend your intelligence by suggesting this, but I'll say it anyway :)

If you open up the the volume control by double clicking on the volume icon, then edit the preferences, try enabling the various "audio tracks" one by one, some of them actually provide switches rather than volume controls for different outputs. On my hardware (apple macbook and an nforce 2 box) enabling one of those provided a tick box for 2 channel or 5.1.

Have a look anyway if you haven't already


Nope, I've tried that a couple of times already, wish it was that simple :)

---

### Post by Yellow Pasque on 2008-06-08
Have you configured the alsa-base file?
[http://ubuntuforums.org/showpost.php?p=5131958&postcount=2](http://ubuntuforums.org/showpost.php?p=5131958&postcount=2)

---

### Post by TerminusEst on 2008-06-08
> **Temüjin said:**
> Have you configured the alsa-base file?
[http://ubuntuforums.org/showpost.php?p=5131958&postcount=2](http://ubuntuforums.org/showpost.php?p=5131958&postcount=2)

Thanks, I tried it with "3stack-6ch" and "auto" but that didn't help either :(.



**EDIT**: It's working now! Not sure what I did, most likely it was just rebooting after the above tip :).
Just suddently all the options were there in alsamixer!

---

