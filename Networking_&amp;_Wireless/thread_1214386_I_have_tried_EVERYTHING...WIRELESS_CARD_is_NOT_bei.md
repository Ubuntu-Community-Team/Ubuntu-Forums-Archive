---
title: "I have tried EVERYTHING...WIRELESS CARD is NOT being recognized."
date: 2009-07-15
forum: Networking &amp; Wireless
---

### Post by acbtheolympian on 2009-07-15
Hello Ubuntu community,

So far I am a fan of Ubuntu. But for the past week + I have been reading other forums and researching on how to get my BCM4311 [14e4:4311] working. My wireless networks icon is greyed out, and i have tried installing ndiswrapper and fwcutter and thought they were sucsessfully installed but the icons are still greyed even after restarts. Now I have resorted to posting up my first thread. If there is anyone who is willing to walk a nuub through this process, I will greatly appreciate it.

Compaq Presario V5000

Thanks,


Olympic-Hopeful

---

### Post by Panzor on 2009-07-16
I got this working on my dad's HP by installing something like "bcm4311-fwcutter" or something (DO NOT TRY THAT IT'S WRONG AND A COMPLETE GUESS). It might have been this:

((googling just jogged my memory))

I think the package was "bcm43xx-fwcutter" so try ```
sudo apt-get install bcm43xx-fwcutter
``` Feel free to use the autocomplete tab feature to get the package name right.

source of memory jogging: [http://ubuntuforums.org/showthread.php?t=416934](http://ubuntuforums.org/showthread.php?t=416934)

---

