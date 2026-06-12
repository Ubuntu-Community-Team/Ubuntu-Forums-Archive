---
title: "Ahhhhh no more xruns please!!!!!!!!"
date: 2010-04-25
forum: Multimedia Software
---

### Post by ntaforge on 2010-04-25
Ok so I can't take it anymore!

I've tried 
Ubuntu 8.10, 9.0.4, 9.10
Ubuntu Studio 8.0.4, 8.10, 9.10
64 Studio 2.0, 2.1, 3.0 beta

All versions of Ubuntu I've completed the "Studio Preperation" guide [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

It's not the interface or the computer. I've tried on two different computers, a m-audio box, a Line 6 GuitarPort, the onboard audio and my Lexicon Omega. 

At just about every setting possible, I get lots of xruns.

Now on the 64 studio, it all worked just fine! but since it seems like no one keeps 64 Studio up to date, I can't get it to work with my wifi or my ATI HD4650.

I don't want to go back to Windows!
Ideas anyone?
Noah

---

### Post by cchhrriiss121212 on 2010-04-25
Two things that might be giving you xruns: compiz effects and wireless internet connections. Since I removed compiz I can get a latency of 2.33ms with no interference. Or you could just have the latency set too high for you soundcard.

---

### Post by ntaforge on 2010-04-25
> **cchhrriiss121212 said:**
> Two things that might be giving you xruns: compiz effects and wireless internet connections. Since I removed compiz I can get a latency of 2.33ms with no interference. Or you could just have the latency set too high for you soundcard.

I don't have compiz enabled and I've tried the no wireless thing and it still gives me trouble. I would rather use Ubuntu Studio over 64 Studio. But, in 64 Studio I can run jack at 64 frames and not get a xrun, EVER!

---

### Post by cchhrriiss121212 on 2010-04-25
> I don't have compiz enabled and I've tried the no wireless thing and it still gives me trouble. I would rather use Ubuntu Studio over 64 Studio. But, in 64 Studio I can run jack at 64 frames and not get a xrun, EVER!
Have you tried removing it completely by uninstalling the packages using synaptic, and switching to metacity?
Could you also describe what jack settings you are using, and also how many xruns you get and what you are doing when you get them?

PS These audio production questions should also be in the Ubuntu Studio section, could someone move it there?

---

### Post by ibuclaw on 2010-04-25
What kind of limits do you have setup in Ubuntustudio?

Are audio processes setup to be given more nice time than normal processes?

(PS: I prefer 64studio).

---

