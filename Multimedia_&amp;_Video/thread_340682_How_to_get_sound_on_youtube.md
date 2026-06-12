---
title: "How to get sound on youtube"
date: 2007-01-17
forum: Multimedia &amp; Video
---

### Post by SimonLoftus on 2007-01-17
After reading all of the hugely jumbled up tutorials I got annoyed because non of the stuff seemed to work, or was like a 10 page instruction to do the simplest thing i've seen.

Like my other tutorial for wide screen resolution here is another that is SUPER noob friendly :)

I had a pretty much clean install of ubuntu, except for a few things to do with my monitor resolution.  So this is what is needed to update to flash 9 to use youtube videos that had no sound before.  

It takes 30 secs.

Download this:   [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

Extract it somewhere, desktop is easiest.  

Then open up your terminal, Applications/Accessories/Terminal 

First we have to get you to the folder, assuming it is on the desktop,

Type "cd ~/Desktop"
Then "cd install_flash_player_9_linux"

Type "sudo cp -r libflashplayer.so /usr/lib/firefox/plugins"

Close off all of your firefox browsers and reopen and it will be working perfect :D

You may be wondering why you cant just copy the file into that folder, because that is all the commands do.  This is because the folder is protected, this stops viruses etc I believe.

Hope you all find it super simple, after all it is, cya xx

---

### Post by jake3988 on 2007-01-17
Use flash_player 7 from the repositories on mozilla.  Works perfectly on YouTube.

Very few websites require the flashplayer 9.


Edit: Sorry, I totally didn't realize that was a How-To.  Might want to consider moving this there. But I'll take the advice if I wish to upgrade!

---

### Post by Lord Illidan on 2007-01-17
> After reading all of the hugely jumbled up tutorials I got annoyed because non of the stuff seemed to work, or was like a 10 page instruction to do the simplest thing i've seen.

That's because flash player 9 wasn't released yet.

> **jake3988 said:**
> Use flash_player 7 from the repositories on mozilla.  Works perfectly on YouTube.

Very few websites require the flashplayer 9. Flash Player 7 had audio sync errors with youtube and a number of sites. Also, many sites **did** explicitly require flash 9. And anyway, it is worth the upgrade.

---

### Post by apunc1 on 2007-01-17
> **SimonLoftus said:**
> 
It takes 30 secs.

Download this:   [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

Extract it somewhere, desktop is easiest.  



thanks for the tip

to extract do i enter this in the terminal:

tar xvfz desktop/install_flash_player_9_linux.tar.gz

---

### Post by SimonLoftus on 2007-01-18
yes or just double click the icon, and click extract and select your desktop, or right click and extract here :D.

@Jake, yeah it was for the ones which didnt work.  Mainly all the naruto episodes I was watching :)

---

### Post by chimps49 on 2007-01-23
i couldnt fix my sound on youtube until i found this thread

thanks much!

---

### Post by moisessalum on 2007-10-23
Hey, I can't get my sound fixed, what's the problem?

---

### Post by moisessalum on 2007-10-27
If this doesn't work (beacuse it didn't worked for me)
Check out this post.
[http://ubuntuforums.org/showthread.php?t=535312](http://ubuntuforums.org/showthread.php?t=535312)

---

