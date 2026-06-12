---
title: "Ubuntu 9.10 breaks spotify?"
date: 2009-10-29
forum: Multimedia Software
---

### Post by calebk on 2009-10-29
After updating to ubuntu 9.10, spotify running under wine does not play songs well and the audio play stutters.

Is there anyway to solve this problem and why is ubuntu 9.10 causing this.

---

### Post by jberger on 2009-10-29
I have exactly the same problem after upgrading to 9.10. Help!

---

### Post by richlowe101 on 2009-10-30
I have this problem too, I'm running the 64-bit version of Karmic upgraded from Jaunty rather than a re-install. Spotify does not list any unusual errors when run from the command-line.

---

### Post by richlowe101 on 2009-10-30
Getting the wine1.2 package from the repos seems to fix this, at least for me! Previous version was wine-1.01

---

### Post by orbital on 2009-10-30
> **richlowe101 said:**
> Getting the wine1.2 package from the repos seems to fix this, at least for me! Previous version was wine-1.01

This fixed the problem thanks!

---

### Post by jberger on 2009-10-30
> **richlowe101 said:**
> Getting the wine1.2 package from the repos seems to fix this, at least for me! Previous version was wine-1.01

That did the trick for me too, thanks richlowe101! :D

---

### Post by orbital on 2009-10-30
Too bad from time to time songs still get distorted...

---

### Post by Gorlist on 2009-10-30
Same  problem, however occurs on Eternal Lands?

---

### Post by applecake on 2009-10-30
((Sorry for being so noobish, but "getting from the repos", does that mean like add the PPA and do an update?
When adding the "PPA for Ubuntu Wine Team", I can't seem to fetch the signing key from the key server.. This has happend many times today, e.g. when I tried adding Chromium to the Software Sources..))

EDIT: Found it in synaptic, and got the signing keys to work.. ;)

---

### Post by calebk on 2009-11-03
Thanks that worked for me, thanks! I really wish they included the latest version of wine in the Ubuntu store, the whole point of the store is to make easier for people new to ubuntu to download software.

---

### Post by Spinor_08 on 2009-11-03
I also had this problem. The sound started to stutter/distort after a few songs, or sometimes immediately. I first tried upgrading to Wine 1.2, which did not work. I then disabled hardware acceleration in spotify, as suggested in this thread:
[http://www.spotify-forum.com/viewtopic.php?f=4&p=621](http://www.spotify-forum.com/viewtopic.php?f=4&p=621)

That didn't work either, so i fiddled a little with settings in winecfg, and have now listened for 4-5 hours without problems after I **set hardware  acceleration to Full under Directsound in the audio tab in winecfg**. It is still disabled in Spotify. Hope this works for some of you too!

---

### Post by mumutum on 2009-11-09
Thank you very much! 
i had the same problem and installing wine1.2 worked for me too.

---

### Post by jonaskarlsson on 2009-11-09
I did like Spinor_08 suggested and it works now. Thanks.

---

### Post by Zweibart on 2009-11-15
Upgrading to Wine 1.2 fixed my problem too. 

I went to System -> Administration -> Synaptic, then searched for Wine. I chose to install the Wine 1.2 windows emulator.

As a total Linux noob, i was impressed that Ubuntu itself took care of all dependencies and selected packages for installation/removal. Just clicked on Use. 

I didn't even have to reinstall Spotify. 

Works fine now, thx.:P

---

### Post by randomsearch on 2010-02-10
**Fixed.**

I had the same problem with Ubuntu 9.10 Karmic Koala and Spotify.  I tried the instructions on the Spotify page and also, as suggested elsewhere in this thread, I tried installing Wine 1.2.

However, none of this is necessary.  The solution is to do what Spinor_08 posted earlier - without changing your version of Wine.

**Set hardware acceleration to Full under Directsound in the audio tab in winecfg.**

This will fix your problem.  I am running Wine 1.1.38 (the default version from the Ubuntu Software Centre) and have listened to about 20 songs flawlessly since reading this thread.

Kudos to **Spinor_08** who worked this out.

---

### Post by orbital on 2010-02-11
Thanks Spinor finally Spotify works 100%!

---

### Post by megamaced on 2010-02-22
> **Spinor_08 said:**
> I also had this problem. The sound started to stutter/distort after a few songs, or sometimes immediately. I first tried upgrading to Wine 1.2, which did not work. I then disabled hardware acceleration in spotify, as suggested in this thread:
[http://www.spotify-forum.com/viewtopic.php?f=4&p=621](http://www.spotify-forum.com/viewtopic.php?f=4&p=621)

That didn't work either, so i fiddled a little with settings in winecfg, and have now listened for 4-5 hours without problems after I **set hardware  acceleration to Full under Directsound in the audio tab in winecfg**. It is still disabled in Spotify. Hope this works for some of you too!

Thanks, this solved the problem in Crossover 8.0 Pro as well

---

### Post by svamppi on 2010-03-09
Thanks for these varying tips, I had given up on spotify for a while because I was too lazy to look for a fix. I had to apply various combinations of these tips. In the end what worked for me was:

- upgrade to wine1.2
- disable the hardware acceleration inside spotify's preferences
- hardware acceleration: full in winecfg

---

### Post by kovan on 2010-09-06
Thanks a lot!. That what did it for my was simply:

aptitude install wine1.2
aptitude reinstall pulseaudio

---

