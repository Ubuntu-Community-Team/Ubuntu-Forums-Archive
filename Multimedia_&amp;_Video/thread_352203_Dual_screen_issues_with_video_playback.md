---
title: "Dual screen issues with video playback"
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by lukeo on 2007-02-03
Hello,

Ubuntu using VLC to playback video. Dual 19" TFT running on Nvidia card.

Ok playback is fine if thats all I am doing, but if on my screen screen I am browsing say these forums with Firefox the playpack stutters every 5-8 seconds. 

My Dual Core 4800+ surely should be able to play a movie and browse the web at the same time? Has no issues doing this in XP (Dual boot),

Any tips to make it smoother? Ubuntu 6.10 if that helps.

---

### Post by lukeo on 2007-02-03
No one else has trouble running two screens, one with a movie via VLC the other browsing the web? I mean it works, and it's not really bad but as I said every few seconds is small stutter in the video which just doesn't happen in ole Windows...

---

### Post by lukeo on 2007-02-03
?

---

### Post by lukeo on 2007-02-03
So no one else on that reads these forums, has an nvidia card, runs ubuntu 6.10, has two monitors, and has ever in their life played a movie on one screen (with vlc) and browsed the web on the other screen? My configuration is unique? Hard to believe....would appreciate some response.

---

### Post by Mike'sHardLinux on 2007-02-03
:)  Hi. maybe you are a bit impatient. Some of my posts didn't get answers for a day or two.

Anyway, I am running dual 17" flat panels, 1280x1024, in Ubuntu Edgy, with an nVidia 7600GT, but I don't have any stuttering.

Are you using the nVidia driver, or generic driver (nv)?

When you type glxinfo at the terminal, does it say you have direct rendering?

---

### Post by lukeo on 2007-02-03
Thank you for the reply, sorry i seemed impatient but there is plenty of forum activity I watched this post fall to page 3 twice over the course of the day.

That tip was exactly what I needed, I honestly expected after going through all the rigmarole of getting the nvidia drivers installed properly, and finally having the Nvidia logo come up at startup, along with manually adding the TwinView lines to the xorg.conf file that Direct Rendering had to be enabled. I was getting 7 000 fps in glxgears etc... however typing glxinfo it said Direct Rendering No.

Some more searching found I needed to add Load "dri" to my xorg.conf, which should have been bloody added by the 25 steps in order to install the nvidia drivers in the first place, it's not mentioned anywhere in the FAQ. Google knows all I guess.

On another note my glxgears score has fallen to about 6 000 fps, but things feel smoother with Beryl. And the video slight lag has gone away I can browse and watch movies once more. 

Any tips to get more out of my card? It's PCI express obviously. Any obscure xorg.conf tips?

---

### Post by lukeo on 2007-02-04
Thanks all you can probably stop trying to offer advice now, see my other thread related to dual core...

[http://www.ubuntuforums.org/showthread.php?p=2104602#post2104602](http://www.ubuntuforums.org/showthread.php?p=2104602#post2104602)

---

