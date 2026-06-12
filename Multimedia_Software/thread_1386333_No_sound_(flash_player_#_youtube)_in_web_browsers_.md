---
title: "No sound (flash player # youtube) in web browsers (Firefox and Chrome) in ubuntu 9.10"
date: 2010-01-20
forum: Multimedia Software
---

### Post by CLINERDE on 2010-01-20
Hello everybody, I'm no audio when viewing videos (flash) in Firefox and Chrome, I've installed all packages possible, as suggested in various forums, but still with this problem. By downloading the flash file I have no problems with audio, only if the browsers. 

Ask help! 

Thank you all.

---

### Post by Stochastic on 2010-01-20
Moved to Multimedia & Video.

---

### Post by ratcheer on 2010-01-20
I am with you, clinerde. Let me know if you find a fix and I will do the same for you.

Tim

---

### Post by ratcheer on 2010-01-22
Ok, I got mine fixed by following the instructions on post #24 page 3 of this thread:

[http://ubuntuforums.org/showthread.php?t=1313831&page=3](http://ubuntuforums.org/showthread.php?t=1313831&page=3)

Flash 10 works *only* with the ALSA default sound card. If your PC has more than one soundcard, the default one may not be the one you are using to drive your speakers. The fix involves adding a line of code to force the unwanted sound card to be second instead of first.

I hope this helps you.

Tim

---

### Post by dostyvsky on 2010-06-07
Removing pulse might be a little radical.  You might just install flashplugin-nonfree-pulse

But what actually worked was I accidentally installed a package referring to it.
**sudo apt-get install flashplugin-nonfree-extrasound**

---

### Post by Yellow Pasque on 2010-06-08
> **dostyvsky said:**
> Removing pulse might be a little radical.  You might just install flashplugin-nonfree-pulse

But what actually worked was I accidentally installed a package referring to it.
**sudo apt-get install flashplugin-nonfree-extrasound**
flashplugin-extrasound is known to be buggy. It would probably be better to just make ALSA apps use pulseaudio with the libasound2 pulse plugin: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

---

### Post by dostyvsky on 2010-06-14
I will defer to Temüjin's solution.  My method did not hold but his link worked.  Except I had to modify ~/.asound.conf as Vectorferret recommends.

---

### Post by kb-linux-2 on 2010-11-03
I an running Ubuntu 10.04 and have edited both of the /etc/asound.conf and then~/.asoundrc files with the suggested changes and then re-booted my machine but I still don't have any sound with YouTube videos. The other sounds sources all seem to work just fine.

Any suggestions on what to try next?

Note:  Before I upgraded to 10.04 everything worked just fine.

Thanks in advance for any help you can provide.

Thanks,

kb-linux-2


Later...
A little more information:
I noticed was that when I looked at the Sound Preferences - Applications page, There were no applications listed. When I started a YouTube video, there were lines of text that very quickly flashed across the screen but it flashed so quickly that I could not read what the text said.

Thanks again.

kb-linux-2

---

